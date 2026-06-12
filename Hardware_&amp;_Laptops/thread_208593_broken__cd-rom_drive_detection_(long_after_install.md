---
title: "broken *** cd-rom drive detection (long after install)"
date: 2006-07-03
forum: Hardware &amp; Laptops
---

### Post by rmg on 2006-07-03
word up, linux people. i've had this computer that'd been running ubuntu for a year and a half. at some point, the cd-rom drive stopped working -- it may be that the old one just kicked off during a move a while back. having been a linux user for some seven years, i knew that fixing the cd-rom thing wouldn't be worth the substantial piece of my youth i'd spend on it, so i just let it go. anyway, this machine was in a seriously bad way and it finally just broke down entirely a few weeks ago, so i got a new one that sucks even more than the old one.

the old hard drive was fine, so i just took it out of the old broken machine and put in the new one. now the operating system has done admirably in detecting things, except it doesn't see the cd-rom or zip drives (i suspect the zip drive would actually need media loaded to be detectable, but i'm not so interested in that). the cd-rom (from the new machine, not transplanted) has become mission critical, so i really must have it working. i believe the cd-rom drive is the secondary ide device. /dev has some devices that would seem to match the description (to wit, /dev/hdd and what looks like about thirty partions thereof), but linking /dev/cdrom to them doesn't do the job.

so what am i supposed to do to get this thing to recognize the cd-rom drive? in fact, if there's some way to get it to figure out all the new hardware for me, that'd be great. i don't want to have to recompile my kernel or anything. oh, and does anyone have any tips for speeding things up? i'm going from 1g of memory to 198m and the transition is making me want to commit ritual suicide. (and no, i can't get any more memory into this thing.)

thx.

---

