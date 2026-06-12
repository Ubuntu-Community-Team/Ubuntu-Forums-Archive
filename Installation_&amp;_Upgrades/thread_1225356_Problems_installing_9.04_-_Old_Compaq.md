---
title: "Problems installing 9.04 - Old Compaq"
date: 2009-07-28
forum: Installation &amp; Upgrades
---

### Post by KingBongo on 2009-07-28
Hi. First post here, :) My brother is having problems with his PC running 8.04, so I am trying to help him out. Installing 9.04 the regular (easy) ways does not seem to work: 

1. No upgrade to 9.04 pops up automatically in the installer. Not to 8.10 either.

2. It will not install from a CD (i386, Alternate). In the middle of installation it suddenly says something like "Please insert Ubuntu 9.04 disk into drive", which does not make any sense. 

What is wrong here? It is a pretty old computer: Compaq EVO D310, Celeron 1.7 GHz (Pentium 4), 1.2gb ram.

He is also having serious issues with his brand new graphics card Sapphire 3850HD AGP, [http://www.datormagazin.se/tester/article249136.ece](http://www.datormagazin.se/tester/article249136.ece) It does not work at all, ends up frozen with a black screen at start up. I have read some about this, and no easy fix seems to exist. Any help?

---

### Post by ptn107 on 2009-07-28
Use the internet to upgrade.  Click System -> Administration -> Software Sources, click Updates tab, change "Release Upgrade 'Show new distribution releases'" to 'Normal'.  Then open up System -> Administration -> Update Manager.  Click the check button.  Install any updates that show up until the only box you see is the 'Upgrade to new distribution release', click it.

*Back up everything important before you upgrade.

---

### Post by KingBongo on 2009-07-28
ptn107:
Thank you. I'll try that, :) I will tell you if it works or not.

As a side-note. I really like Linux (I am running OS X myself). The main problem seems to be lack of good, timely (or easily installable) drivers for many graphics cards. That is a problem which I believe seriously hinders Linux success. I believe the Linux community really has to focus heavily on drivers. Non-working brand new hardware is a pita since you really want to try your new stuff. I basically convinced my brother to invest in his old computer (much cheaper than buying a new one) by upgrading the memory and buying a really good (but cheap) graphics card, and now we cannot make the card work. Not good, :(

---

### Post by KingBongo on 2009-07-31
ptn107:
Well. Thank you, trick worked great. 9.04 installed, :) There is one thing I don't understand though, 9.04 runs slow. Yes, the computer is pretty old, but shouldn't it have enough juice to run 9.04 smoothly?

Compaq EVO D310, Celeron 1.7GHz (Pentium 4), 1.2GB DDR Ram, 400Mhz (4X100MHz) FSB. As I understand it, the motherboard (MS-6541 ver. 1.0) and peripherals (sound, graphics) have been used by several manufacturers. Therefore, drivers and such should have been developed for Linux.

So why does it run slow on 9.04? Any ideas? Please help!

PS. The problem with the new AGP HD3850 graphics card still remains, but that is another issue.

---

### Post by ptn107 on 2009-08-06
You could just turn off desktop effects in System -> Preferences -> Appearance, and disable some unused startup services System -> Preferences -> Startup Applications (be careful what you disable here).

---

### Post by KingBongo on 2009-08-06
ptn107:
Well, the first "trick" I know about already, but I will try the second one too. Thank you.

I also found another processor in an old broken computer of mine (strain of luck). It's a Pentium 4 (1.8Ghz, 256kb L2 cache). The current one is a Celeron (Pentium 4, 1.7GHz, 128kb L2 Cache). They are both based on the Willamette core, 478 socket so it should slip right in and just work, :) I will replace the processor soon to get the old Compaq up to incredible speeds comparable to a modern eight-core machine, :D

---

