---
title: "X windows with AMD64 and Radeon 9200SE"
date: 2005-10-08
forum: Hardware &amp; Laptops
---

### Post by Stupid on 2005-10-08
Greetings denizens of the Ubuntu forums,

I have a system with an AMD 64 processor, and for some time I've been running 32 bit Debian Sarge on it.  I wanted to switch to a 64 bit distro, and I've heard good things about Ubuntu, so I decided to give it a try and wiped my Debian system, but unfortunately things haven't gone too well with the new Ubuntu 5.10 system and now I'm Linuxless (except for console mode).

When I finish the Ubuntu installation process and the system reboots I get the nice Ubuntu logo with the brown progress stuff printed below it, and then when X starts I get a window full of what looks like random noise.  The mouse looks like an X windows mouse, and I can move it and everything, but other than that the system doesn't respond.  I can't kill X with ctrl-alt-backspace, and I can't switch to a console with ctrl-alt-fx, I basically just have to hard reboot.   

I have a Radeon 9200SE video card that I think is probably the culprit.  I've tried doing a "dpkg-reconfigure xserver-xorg" and manually selecting the correct horz and vert refresh rates for my monitor, and also selecting the generic "ati" option for my vodeo card, but I get the same screen of random colors.  I tried manually setting up my xorg-config file, but nothing I've tried there has made any difference.  

I also tried getting the driver from the video card's manufacturer, but they only offer the driver for AMD64 as an rpm.  I got that and converted it with alien and attempted to install it, but it complains about the version of libc available in Ubuntu.  If I try to install it with ignore depencies set then it fails with all kinds of errors.  So it seems that that driver is no good for this situation.

Has anybody had success with a similar setup?  I would really like to try Ubuntu, but if my hardware makes it impossible then I guess I'll start looking for some other distro that might work.

Thanks in advance.

---

### Post by PsyberOneZero on 2005-10-09
Try this How-to, it should be exactly what you're looking for:

HOW-TO: ATI Radeon driver install - mlomker
[http://ubuntuforums.org/showthread.php?p=348911](http://ubuntuforums.org/showthread.php?p=348911)

---

### Post by Stupid on 2005-10-09
Thanks for the advice.  I've just tried the howto listed above, but I got the same problems I had before.  Maybe I did something wrong though.  I'll try again in the morning when I've had some rest and haven't been drinking.

---

### Post by Stupid on 2005-10-09
Ok, I cleaned out the remains of my previous attempts at getting this to work, and retried the  howto you linked to.  I can now log into X at least.

Thanks again for your help.

---

