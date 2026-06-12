---
title: "Graphics problem on HP 2133 (1024x600)"
date: 2008-11-01
forum: Hardware
---

### Post by Izmo on 2008-11-01
I've got a HP 2133 "mini"-laptop, and I've got some seriously painful graphics problems with it. Out-of-the-box I only get an awful looking 640x480 VESA screen stretched to fit. After following the instructions available here: [https://wiki.ubuntu.com/LaptopTestingTeam/HP2133](https://wiki.ubuntu.com/LaptopTestingTeam/HP2133), I get a screen that stretches beyond the actual size of the monitor. (I.e. I get a 1280x768 pixel screen, but only the top left 1024x600 pixels actually fit.)

One of the problems are apparently that the model I have isn't any one of the ones listed on that page. It would appear that HP got tired of just randomly swapping the WLAN-cards around, and decided to put a cheaper screen on some of their laptops as well... The precise model I have is FU337EA#AK8 - and given that the graphics on the original SLED installation looked borked as well, I've got my own opinion on what the initial letters "FU" are an abbreviation of... :mad:

Changing the resolution either from within KDE, or by editing xorg.conf, replacing 1280x768 with 1024x600 doesn't work as desired. In the first case I get an absolutely horrible looking screen that appears to be a 1024x600 resolution resized from 1280x768, then stretched back, so it still doesn't fit the screen.

The latter results in something that doesn't fit the screen either (although it doesn't miss the mark as much as 1280x768.) but also has the awful looking "jaggies" of a resized screen. I'm guessing that since the screen is different from the one the xorg.conf file was made for, that the Modelines don't match. Then again just commenting them out doesn't seem to help either...

So just to clarify: I'm using Kubuntu Hardy with kernel 2.6.24-16, VIA's binary drivers and the xorg.conf from the page linked to above. Any ideas on how to get this thing working? Oh, and by "working" I don't necessarily mean working 3D - just working 2D that doesn't look like crud.

---

### Post by Izmo on 2008-11-02
Got it working. The solution was just changing 2 lines in xorg.conf, but especially one of them was very non-obvious. This forum has the details if anyone is interested: [http://forums.mininoteuser.com/viewtopic.php?p=4576#p4576](http://forums.mininoteuser.com/viewtopic.php?p=4576#p4576)

---

### Post by Roliat on 2008-12-24
Would you please post your edited xorg.conf here?

---

### Post by sonicQt on 2009-02-02
I got it stable with video working by following this [step-by-step guide]("http://hp2133linux.blogspot.com/2009/01/part-1-installing-ubuntu.html").

---

