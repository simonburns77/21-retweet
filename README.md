# 21-retweet

Sell retweets on Twitter using the [21](https://21.co/).

## Example

You can see an example of this in action on [Twitter @21_retweet](https://twitter.com/21_retweet).
To purchase a retweet with 21 use:

*To use the example you must have 21 installed and be connected to the [21 Network](https://21.co/learn/21-marketplace/)*
```
21 buy --maxprice 1000 url http://21.justinguy.com/retweet/TWEETID
```

## Prerequisites

- [21](https://21.co)
  - Flask (`sudo pip3 install flask`)
  - Connected to the [21 Network](https://21.co/learn/21-marketplace/)

## First setup of server

    cd ~
    sudo pip3 install tweepy
    git clone https://github.com/justinguy/21-retweet.git
    cd 21-retweet
    cp retweet_settings_default.py retweet_settings.py

## Credentials from Twitter

In order for the Tweepy library to interact with Twitter you need API access:

- Go to https://apps.twitter.com/app/new
  - Data doesn't really matter because you will be the only consumer of the App.
- Once created click the tab "Key and Access Tokens"
- Click the button at bottom of the page "Create my access token"
- Open the `retweet_settings.py` on your 21BC
- Copy the following from Twitter -> `retweet_settings.py`
  - Consumer Key (API Key) -> `TWITTER_CONSUMER_KEY`
  - Consumer Secret (API Secret) -> `TWITTER_CONSUMER_SECRET`
  - Access Token -> `TWITTER_ACCESS_TOKEN`
  - Access Token Secret -> `TWITTER_ACCESS_TOKEN_SECRET`

## Starting the Server

    python3 retweet-server.py
    
## Purchasing Retweets

When you start the server it will provide instructions for purchasing retweets from it. This is an example:
```
-----
Server starting, to purchase a retweet run the following command:
21 buy --maxprice 1000 url http://10.154.174.52:5000/retweet/TWEETID
-----
 * Running on http://10.154.174.52:5000/ (Press CTRL+C to quit)
```

# Todo

If you would like to improve on this here are some suggestions:
- [ ] Error handling
  - Needs to handle network errors, Twitter API errors (like rate limiting), etc
- [x] Endpoint for server details
  - Would be nice to have an API endpoint like `/info` that returns some basic information about the retweet server such as what Twitter account is being used and maybe how many followers it has.
- [ ] Connection to BTC/USD price to manage PPP of RT price
  - As bitcoin price moves up and down, a dynamic model to change the bitcoin output would be a great feature.

