---
title: "Help with my Wacom Intuos 4"
date: 2011-04-13
forum: Hardware
---

### Post by Aewawa on 2011-04-13
Hi, I'm new in Ubuntu, and Im trying to get my USB Intuos 4 work with Ubuntu 10.10.

I managed to make it work without OLEDs, but I've just formated it because I messed around a little with my OS, and this time I want it working with OLEds.

I've read a lot of tutorials in this forum but since I'm a completely noob in linux, I couldn't understand them (don't know which driver I should use, how do I use those downloadable scripts, and other things), could someone post a step by step tutorial for dummies?


I'm using Ubuntu 10.10 64

---

### Post by Favux on 2011-04-13
Hi Aewawa,

Welcome to Ubuntu forums!

For help on configuring your tablet see the linux wacom project's mediawiki: [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO)
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Wacom_Tablet_Set_Up](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Wacom_Tablet_Set_Up)
[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Rotation](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Rotation)

You can also find a sample script for the Intuos4 attached to the bottom of post #2 on the Bamboo Pen and Touch HOW TO. See part IV. in the first post for instructions.  [http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)

You have to pay attention to what version of xf86-input-wacom you have. Changes have been fast and furious. The Maverick default is 0.10.8, and not everything works with it.

OLED's are working thanks to Christoph Karg's userland app. Sanette has his modification of it with profiles on this Ubunutu forums thread:  [http://ubuntuforums.org/showpost.php?p=10527977&postcount=174](http://ubuntuforums.org/showpost.php?p=10527977&postcount=174)  Have you looked at the README file in it after you download it?  It has the install instructions.  You probably be better off posting questions about OLEDs on that thread so Sanette or one of the other posters can find you.

And Christoph just posted an update to his version on linuxwacom-devel with profiles. Be warned though, there is a bug in xf86-input-wacom that causes X crashes when using the app. That was fixed around 0.10.11.

Hope this helps.

---

