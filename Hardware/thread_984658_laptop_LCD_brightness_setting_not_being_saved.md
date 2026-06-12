---
title: "laptop LCD brightness setting not being saved"
date: 2008-11-16
forum: Hardware
---

### Post by BattlePanic on 2008-11-16
I have an annoying issue that has cropped up after installing 8.10 Intrepid Ibex.  Whenever I boot up Ubuntu, the brightness of my laptop's LCD monitor is set to the maximum during Gnome's startup.  This problem did not exist under 8.04 Hardy Heron.  The brightness function keys on my laptop do not work (which is nothing new,) so I use the brightness applet provided by Gnome and I am able to turn down the brightness to my desired setting.

When I was running 8.04 Hardy Heron the LCD brightness level seemed to be saved between bootups but now it always starts up at the maximum brightness and I have manually turn down the brightness.  I find this fairly annoying but I haven't found any posts where people are mentioning a similar problem.  Might anyone out there have some suggestions?

I'm using a Sony Vaio VGN-FS675PH with an Nvidia GeForce Go 6200 graphics card.  The problem seems to exist whether I'm using the Nvidia binary-only restricted drivers or the open source X.org driver.  I don't even think this has much do with my video card anyway since this is simply the brightness setting on my laptop's lcd hardware.

Any thoughts would be greatly appreciated.

---

### Post by lett on 2008-11-19
Hi, I have exactly the same problem with mine acer. I've been browsing net for couple days, but still no solution. There are couple posts on this forum but none of them solve my problem. 
BTW. I've found out that ubuntu installed some special package for nvidia 6200, you might want to check wheter is important for you.

---

### Post by skyline_GT_R34 on 2008-12-07
I have the same issue and I found an explanation and a "patch" here: 
[http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg233289.html]("http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg233289.html")

I think it is needed to recompile the video.c file but I don't know exactly how to do that to date...:sad: I think I'll wait the official fix for the kernel file video.ko... 

Hope this helps.

---

