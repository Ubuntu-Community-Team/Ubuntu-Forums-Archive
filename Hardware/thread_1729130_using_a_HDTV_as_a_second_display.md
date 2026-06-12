---
title: "using a HDTV as a second display"
date: 2011-04-14
forum: Hardware
---

### Post by dargaardms on 2011-04-14
I'm hoping this will be a quick fix, I use Ubuntu 10.10 as my primary OS, windows 7 came with my system and I use it as a gaming platform only.  I hooked my laptop to my HDTV under windows for gaming and found out my TV doesn't report the EDID information correctly or at all, lucky the nvidia control panel under windows 7 lets you force the standard HDTV modes my TV supports (1080i for desktop and 720p for gaming).

In Ubuntu I didn't worry about getting the TV out working cause I didn't think I would wan't to use it for anything but gaming, however as time went on I have discovered that TV out has many great uses other then gaming.

So here is the problem, Ubuntu just like windows will not offer me HDTV modes for my tv, the PC monitor modes I can pick don't display correctly and I have read that they may be harmful to my tv.  Unlike windows the nvidia control panel in Ubuntu doesn't let me force HDTV modes, I don't know if X supports interlacing so 1080i might not be possible but 720p would be fine.  How do I go about getting 1080i (if possible) and 720p on the list?

My laptop is a Asus G53JW-A1 which has a NVIDIA GeForce GTX 460M and HDMI out,  Sound and video output do work just can't get HDTV resolution.

---

### Post by Hedgehog1 on 2011-04-15
I am using and LED-LCD Samsung as my monitor for Windows and Ubuntu 10.10 & 11.04.

I am connected using HDMI (I don't know if your HDTV offers HDMI, you did not say).

Here are the options I get in the **nVivida X Server Settings** panel:

[IMG]http://img25.imageshack.us/img25/9540/overscan.png[/IMG]

This panel is part of the **nVidia Restricted Drivers**.

If you are not seeing this panel, you may need to install the restricted drivers. Then you should be able to setup your output properly for your HDTV.


***The Hedge***

:KS

---

### Post by dargaardms on 2011-04-16
Yes I'm using HDMI, here is what my Nvidia panel shows.

---

