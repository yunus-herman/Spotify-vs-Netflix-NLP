
# Spotify vs Netflix

> By: Yunus Herman

---
# Project Files
* README.MD
* 1_data_download
* 2_data_cleaning
* 3_nlp_eda
* 4_modeling
* project3.pptx

## Background

Spotify and Netflix are two popular content providers, whose popularity has increased even more during
the covid-19 pandemic. Spotify is a digital music service that provides access to millions of songs and
other types of audio contents. With Spotify, it’s easy to find the right music or podcast for every
moment – on your phone, your computer, your tablet, and more.
Netflix is a streaming service that offers a wide variety of television shows, movies, anime (Japanese
animated films), documentaries, and more on thousands of internet-connected devices. I havd chosen
these subreddits, because they are my favorite streaming apps for accessing music, movies, and
television shows.

## Dataset collection

In my GA course I’ve been studying data scraping using beautifulsoup and APIs. Using Pushshift&#39;s API, I
have collected posts from the Spotify and Netflix subreddits. I scraped 10,000 rows of each subreddit
using data posted before January 31, 2021. The collected data consisted of subreddit texts, titles, and
self texts. Using a function is the most suitable for this prosess with subreddits and setting the number
of rows as parameters of this fuction. The output of this process consists of CVS files with the subreddit
name as the CSV file name.

## Data Cleaning

Reading the CSV files from the dataset collection process and checking for empty values were the initial
steps. After examining the data, some new columns were added to make the process easier. Then I
made the binary by labeling 1 for Spotify and 0 for Netflix. This would be my target for modeling. The
subreddit column itself thus became redundant and was deleted along with some data duplicates.

Mergin titles and self texts into one text was the next step. This became my feature for modeling. I
calculated the length of this text to determine how many words each text has. Then I stored the lengths
and word counts into new columns to clean the dataframe and saved them as spotify_netflix.csv files.

# EDA and NLP 

First I analyzed the distribution of text word counts and text lengths. I visualized the data using a red line
as median and identified texts which were 10 to 70 characters long, and then decreased this further to
obtain 5 to 10 word texts looks which were the most convenient size. The number of posts decreased as
the word count increased.

Natural Language Processing plays an important role in processing texts obtained from media like reddit.
I used a count vectorizer to get the 10 most common words in the texts. I then plotted them into bar
graphs. The word ‘Netflix’ was the most common with almost 7,000 occurrences in the data. The word
‘playlist’ was the second most common word around 4,500 occurrences.


# Model Selection

I used a count vectorizer and TF-ID with English stop words, and selected Bayes, KNN, and Random
Forest Classifiers.
The baselines of the two datasets were almost were almost equal: Spotify had 51% and Netflix had 49%. 

# Modeling

The binary column which differentiated the Spotify Netflix subreddits was used as a target in all models.
The text column was the feature for the model. To make it easier, I used Pipeline to facilitate the
process. I used a confusion matrix and classification report to evaluate the predictions.

# Evaluate

1. Bayes 
        In this model, precision has a high score, 94% for Netflix and 96% for Spotify.
2. KNN 
        In this model, the precision is lower, with 61% for Netflix and 87% for Spotify.

3. Random Forest Classifier
        In this model, the precision had a high score 93% for Netflix and 97% for Spotify. Both F1 scores were
        95%.
        This was determined to be the best model. 


# Conclutions

Random Forest Classifier was the best model to predict data classification. This model will be used in
future similar projects.