---
title: "Multi-Monitor with Xinerama"
date: 2009-11-30
forum: Hardware
---

### Post by Tallivant on 2009-11-30
From what I can tell this problem has been around for a while, hopefully somebody else has found something on it:

I'm trying to set up a 32" 720p Dynex HDTV to run as a dual monitor with the 15.4" screen on my Alienware Laptop (Running Karmic Koala), which has a Geforce 8600.  After countless renditions of Xorg.conf and restarts due to the "jailed" mouse glitch, i have finally gotten the two x screens to cooperate under Xinerama. (There was a particular problem with the scaling & offset onto the hdtv's widescreen resolution, i would be glad to share my Xorg.conf)  Now I would just like to be able to fullscreen windows on the TV screen while working on the laptop's screen.

I've tried the seperate X screens without Xinerama (had issues with mouse and inability to move programs between screens) and TwinView, but they haven't gotten me far.

Has anyone figured out how to fullscreen a window on one X screen while leaving the other applications free to be run on the other X screen while using Xinerama?

---

### Post by dsjstc on 2010-12-15
I just built a triple-head system with different-sized monitors (1920x1200 flanked by a pair of slightly-shorter 1280x1024).  I'd like to see how Xinerama scaling works.  

If you're still using scaling, could you please post your xorg.conf?

---

