---
title: "Firefox 3 and Flash video observation"
date: 2008-08-29
forum: General Help
---

### Post by sleepingdragon on 2008-08-29
OK. I'm one of the many who's getting the freeze-up with FF3 and Flash video playback (Flash v9)- but I've noticed something when changing a couple of settings in about:config.

It's been listed before about changing the pipelining settings in FF3:

Type in about:config into FF3. Search for "pipelining". 

Change the following values (at your own risk!) - 

*network.http.pipelining* to "**true**"
*network.http.proxy.pipelining* to "**true**"
*http.pipelining.maxrequests* to some higher number - try somewhere between 20 and 30.

I thought I would give it a go to see what happens... and flash video is now stable. Very, very, stable. I've been running twelve tabs, all with video, all from random sites - iplayer, veoh, ebaumsworld... all at the same time. Not a single lockup...

Anyone dare to try?

---

### Post by MickS on 2008-08-29
Trying it now, just had 2 Youtube vids playing at once in different tabs and closed both while they were still playing, no problem.
Thanks for the tip, off to do some more playing.

Mick

---

### Post by mb_webguy on 2008-08-29
Setting the value of network.http.pipelining.maxrequests greater than 8 is pointless, since Firefox only has the capability to send 8 requests at once.

Having said that, I use this tweak and do notice a difference in page load times.  I ran a test using a series of Google image searches with pipelining turned off, and then with pipelining turned on.  Without pipelining, the average page load time was about 2.75 seconds.  With pipelining, the average page load time was about 2.25 seconds.  Pages with lots of small elements (like most MySpace pages) seem to benefit more from this tweak than pages with few large elements (like a YouTube video page).

---

### Post by sleepingdragon on 2008-08-29
mb-webguy: thanks for tip about the max 8 threads. I knew that increasing from the default would help, but never found out how many FF could handle.

---

