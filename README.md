## Analysis of Twitter

Read about this project in Medium:  

-[How to build a PostgreSQL database to store tweets](https://towardsdatascience.com/how-to-build-a-postgresql-database-to-store-tweets-1be9c1d48c7)    
-[Keras Challenges the Avengers](https://towardsdatascience.com/keras-challenges-the-avengers-541346acb804)  
-[Visualizing interactions with NetworkX](https://medium.com/@meinzaugarat/visualizing-twitter-interactions-with-networkx-a391da239af5)


## Introduction

Twitter is used every day by people to express their feelings or thoughts, specially about something that it is happening at the moment or has just occurred; by companies to promote products or services; by journalists to comment on events or write news; and the list can go on. There is no doubt that analyzing twitter and tweets is a powerful tool that can give us a sense on the public opinion about a topic that we are interested in.
Fortunately, Twitter provides us with an API (that stands for ‘Application Programming Interface’) which we can interact with creating an app and in that way, access and filter public tweets.
Of particular interest to me is knowing what people are feeling about the Avengers. So I will use “avengers” as my term of interest and analyze the public opinion on this.  
  
Neural networks will be used to perform the sentiment analysis. Check my [repository](https://github.com/ugis22/neuralnetwork) and my [medium post](https://towardsdatascience.com/understanding-neural-networks-what-how-and-why-18ec703ebd31) to learn more about how neural networks work.

## Purpose

The goal of this project is to: 
1) To build a PostgreSQL database in order to store tweets about 'Avengers' streamed from Twitter API
2) Analyse word co-ocurrence with the term 'Avengers'
3) Develop a neural network to perform a sentiment analysis
4) Build a network to visualize interactions between users tweeting about 'Avengers'

## Data Set Information

There are two ways to capture tweets with Tweepy. The first one is using the REST search API, tweepy.API, which searches against a sampling of recent public tweets published in the past 7 days. The second one is streaming realtime tweets by using the Twitter streaming api that differs from the REST api in the way that this one pull data from twitter while the streaming api pushes messages to a persistent session. In this project, the last option was used to capture realtime tweets.

Twitter APIs always return tweets encoded using JavaScript Object Notation (JSON), an unstructured and flexible type which is based on key-value pairs with attributes and associated values that describe objects. Each tweet contains an author, message, unique ID, a timestamp and creation date when it was posted, among others; each user has a name, id and number of followers. 
Relational databases such as PostgreSQL has a great performance handling JSON so a relational database and specifically, PostgreSQL db was built to store the tweets streamed from Twitter API.

## Analysis

This repository contains three files:

- `DatabaseStoreStreaming.ipybn` answers to the goal #1. Connects to a database, creates tables and store tweets in them,   overload tweepy class to listen and capture realtime tweets.
- `Cleaning DB.ipybn` cleans the database by removing any duplicated tweet that was collected.
- `Analysis of Twitter.ipybn`answer to goals #2 and #3. Retrieve tweets stored in the previous step and handle them in a pandas `DataFrame`, preprocess the tweet text, visualize the data and build a neural network to analyse the sentiment. 
- `Interaction Network.ipybn` answers to goal #4. Gets interaction (retweets, replies and mentions) between Twitter users who have tweet about Avengers and generates a Graph to visualize those interactions.

The whole analysis was done using JupyterLab and Python, using libraries such as: psycopg2, tweepy, pandas, matplotlib, networkx, scikit-learn and keras.

![](graphfinal.png)
