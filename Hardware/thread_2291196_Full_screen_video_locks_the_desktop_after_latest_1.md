---
title: "Full screen video locks the desktop after latest 14.04 patches"
date: 2015-08-18
forum: Hardware
---

### Post by kvgeorge1-sbcglobal on 2015-08-18
After updating my system (14.04LTS 64-bit) with the latest patches from Software Updater, whenever I view a video from a web-browser (YouTube, FoxNews, anything), coming out of fullscreen locks the desktop up: no video update (I can hear the video in the background), no keyboard control, no mouse control, nothing.

The only way I can get it to work again is to poweroff and power back on.  This was all working just fine before the latest software update (around August 13th 2015 or so).

---

### Post by kvgeorge1-sbcglobal on 2015-08-22
I think I solved this (well, sort of anyway).  The problem is the nVidia proprietary driver.  I removed the proprietary driver and replaced it with the latest open source driver and I am not experiencing any more problems.  However, I do notice that some features are no longer available (Power Mizer cannot be changed and blanking out the screen for the screen saver causes a curious lined copy of my desktop to show up with a black diagonal line across it).  But, I can go into full screen and back without issues now.

---

