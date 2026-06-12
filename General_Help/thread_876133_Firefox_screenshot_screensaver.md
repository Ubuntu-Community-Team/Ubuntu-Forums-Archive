---
title: "Firefox screenshot screensaver"
date: 2008-07-31
forum: General Help
---

### Post by nezticle on 2008-07-31
This is a cry for help.

I need to make a screensaver that cycles through current pictures of web pages on my domain for a Linux kiosk server I have implemented.  What I need is to take screenshots of a list of web pages every 10 mins and place them in a Screenshot folder where a Slideshow screensaver will cycle through them.  

My current idea is to have a background service open up an xsession and open Firefox with an address specified, then use "xwd" to take a screenshot of the window.  I will have a cron job that runs every 10 mins to take care of this task.  Unfortunately I don't know how to run an Xserver in the background.

Any help would be much appreciated.

---

