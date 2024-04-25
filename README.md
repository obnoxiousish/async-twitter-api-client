# async-twitter-api-client
Async port of twitter-api-client

~ of 2024-04-24 this is being maintained as its being used in a project im being paid to maintain ~

MASSIVE Thank you to Trevor Hobenshield @trevorhobenshield for making this!
All I have done is changed the client to asyncClient 

Key Differences:

linted by ruff
renames tweet and other functions to asyncTweet asyncReply etc
all functions must be awaited
uses httpx asyncclient instead of Client so it supports anyio, trio, curio, asyncio
natively supports proxies, http(s)+socks5
reply & quote support uploading images

# Todo
```
Solve & Submit captcha to unlock account using various captcha solving providers
Maybe fix searching somehwat?
Add signup
```

Original search.py uses asyncio.gather(), i switched to use anyio.create_task_group() with a results list that the tasks append to, might not be a 1:1 behaviour

```pip install asyncTwitterClient```

```
import anyio

from asyncTwitter.asyncAccount import AsyncAccount


async def main():
    twitter = AsyncAccount()
    await twitter.asyncAuthenticate(
        cookies={"ct0": "fuefjwegf89ewg9uiwg9", "auth_token": "je09giewg9iwg9j"}
    )

if __name__ == "__main__":
    anyio.run(main)
```