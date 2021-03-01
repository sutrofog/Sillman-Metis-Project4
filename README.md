## **Project 4: Topical Exploration of Hunger Games Fan Fiction**



**Introduction**

"The Hunger Games" is an extremely popular series of Young Adult novels written by Suzanne Collins. These books were made into films, which were also extremely popular. The attributes that made "The Hunger Games" books and films popular--strong female characters, a theme of young people rising up against an older oppressor, and many well-developed secondary characters--also make them excellent material for fan fiction.

Fan fiction are stories written by fans of the original ("canon") books and films, and are a way for people to create stories about the characters they care about. Of course, much fan fiction is written about the main characters of the canon, Katniss and Peeta. I wanted to know what were the topics and characters that appeared in Hunger Games fan fiction, and whether fan fiction writers would write about the secondary characters (e.g. Haymitch, Johanna, Clove, Cato, Finnick, Annie, Mags, etc.)



**Data Acquisition**

Story texts were scraped from FanFiction.net (https://www.fanfiction.net), using the Web Scraper Chrome extension (https://webscraper.io). Stories were filtered for Hunger Games, and then further filtered for language (English) and all four character filters were set to "Katniss Everdeen", as I wanted to see if secondary characters would feature prominently even in stories that had Katniss in them.

LDA modeling might have been more useful if I had done parts of speech tagging and then removed the verbs. Topics 6, 7, and 8 are verb-heavy. Topics 3, 4, and 5 have some secondary characters (Johanna, Finnick, Effie, Clove, Cato), and Topic 2 seems to deal with home life in District 12 (Katniss, Prim (Katniss's sister), Peeta, mother, father).

Text analysis is coded in Notebooks 1-4. Story text was cleaned of punctuation and numbers, but capital letters were left in, because many names in the story are not recognized as nouns, and I thought leaving them capitalized would allow the parts of speech tagger to tag them as proper nouns. This resulted in many stop words remaining capitalized, and then not removed due to capitalization. I went back to the original data, re-did the text preprocessing including removing capital letters, and then quadgrams were made, and then removal of stop words was attempted. I could not make the stop word removal work (the quadgrams were in tuples, and I could not remove the stop words from the tuples). I therefore went back, tokenized by single words, removed stop words, and then stemmed using Lancaster Stemmer, in order to reduce the number of words to analyze.

Processed text was vectorized using TF-IDF in scikit-learn. Topic modeling by scikit-learn LSA (Truncated SVD) and NMF  was done on the TF-IDF document-term matrix. LDA topic modeling was done from the Count Vectorized processed text.



**Results**

LDA modeling might have been more useful if I had done parts of speech tagging and then removed the verbs. Topics 6, 7, and 8 are verb-heavy. Topics 3, 4, and 5 have some secondary characters (Johanna, Finnick, Effie, Clove, Cato), and Topic 2 seems to deal with home life in District 12 (Katniss, Prim (Katniss's sister), Peeta, mother, father).

NMF modeling resulted in only one or two main components per Topic, ususally a character. This type of modeling does not seem to be very useful for this type of text analysis.

LSA modeling is much more useful and informative. Several Topics (3, 4, 6, 7, 9, 10) have a secondary character as the most prominent component, and contain other secondary characters (Johanna, Gale, Madge, Prim, Cato, Clove, Effie, Haymitch, Finnick, and Annie), indicating that even in fan fiction stories that contain Katniss as a character, there are secondary characters who feature prominently. Fan fiction writers enjoy writng stories about the many well-developed secondary characters in the Hunger Games canon.
