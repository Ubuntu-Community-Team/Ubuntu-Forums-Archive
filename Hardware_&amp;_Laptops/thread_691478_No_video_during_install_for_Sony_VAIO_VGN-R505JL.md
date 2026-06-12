---
title: "No video during install for Sony VAIO VGN-R505JL"
date: 2008-02-08
forum: Hardware &amp; Laptops
---

### Post by mrbofus on 2008-02-08
I have a Sony VAIO VGN-R505JL.  I can boot from the Ubuntu 7.10 CD, and once I select the option to install, it begins and shows the loading progress bar.  After a couple minutes, the screen goes blank and I cannot see anything on the screen.  I have tried connecting an external monitor, but that doesn't help.  It sounds like the CD is still being read, and then a sound plays.  But the screen is still blank.  XP installs fine, but Ubuntu goes blank during the install, so I can't even get to the Live CD part to install it.  Any help would be greatly appreciated!

---

### Post by aacero on 2008-03-26
Same here with the Xubuntu 7.10 livecd and a PCG-R505JL.  It does boot up in safe graphics mode (the second boot option), but at a reduced graphics resolution (800x600).  The Xubuntu 8.04 livecd (beta) boots up from the default boot option, but also in 800x600. 

In the first case when there's no graphics, if you use CTRL-ALT-F1 to switch to the first virtual console, I think you'll find that the system has booted up and the X server is running.   I haven't had a chance to look at it further.  

This system works at full resolution with Knoppix 5.1

---

