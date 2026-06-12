---
title: "error downloading/randomise download location?"
date: 2008-11-22
forum: General Help
---

### Post by thatroom on 2008-11-22
Please, for the love of god, set WUBI to either choose (by ping or some possible indicator of pipe load) or randomise (and hopefully check the speed on) the download location. and/Or perhaps allow us the option to choose the location from where to download the ISO. I got stuck when WUBI switched to downloading the 8.10 version on a site that had been hammered and got a whopping 2 Kb/sec download rate. (I am assuming it was the first location it found that answered before the timeout.)

Worth looking into. I am used to Linux based installers that allow just about any form of tweaking, and although I know the average N00B won't know what to do with it, for some of us who are installing for others, say as a crossover test, being stuck with a slow feed is maddening. 


Also a question: Does Wubi look for ISOs in the directory it's run from? 

One last thing. I was trying (quite unsuccessfully) to install from a wifi connection that cut out once or twice during the progress and the WUBI EXE crashed. Is there a way for it to have a bit more grace when failing out? and hopefully continue the download? 

THanks, I LOVE it, and have told all of my friends about it, posted about it, and whatnot. I just can't wait to USE it!

Thanks

B

---

### Post by ago on 2008-11-25
> **thatroom said:**
> Please, for the love of god, set WUBI to either choose (by ping or some possible indicator of pipe load) or randomise (and hopefully check the speed on) the download location. and/Or perhaps allow us the option to choose the location from where to download the ISO.

The way it works now is that it picks a mirror randomly with preference for mirrors in your country. 

In the future bittorrent will also be supported

You can always download the ISO manually and place it in the same folder as wubi.exe

> 
Also a question: Does Wubi look for ISOs in the directory it's run from? 

yes, and in the Desktop

> 
One last thing. I was trying (quite unsuccessfully) to install from a wifi connection that cut out once or twice during the progress and the WUBI EXE crashed. Is there a way for it to have a bit more grace when failing out? and hopefully continue the download? 

Yes the new version will be a bit more stable (hopefully), in any case wubi supports download resume, so you do not usually lose what you have already downloaded.

---

