---
title: "Ubuntu 9.10 Karmic No DVI Detection"
date: 2010-04-17
forum: Hardware
---

### Post by Jazzmaster94 on 2010-04-17
I just installed Karmic on my Dell Dimension E521 computer in a Dual Boot with Windows Vista.  My graphics card is an ATI Radeon X1350 Pro with 256MB GDDR2.  My Vista partition displays to both VGA and DVI just fine.  However, if I boot into Ubuntu with DVI, I have no picture what so ever.  I just rebooted with VGA and I have my Acer X203h running at full 1600 X 900 resolution.  Running VGA isn't much of a problem as far as picture quality, but I have an XP netbook (which I am writing on) that I use VGA out on to do homework.  I cannot download anything for my Dual Boot Dell since I do not have ethernet running to my room yet.  If you have any configuration solutions for me to try I can do those.  I just need a little help here :confused:.  By the way, I am a little new to actually natively running Linux (although I did use Linux Mint in Virtualbox), so it is alright to treat me as a relative n00b. Thanks!

---

### Post by lidex on 2010-04-18
What driver are you using?
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")
[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by Jazzmaster94 on 2010-04-18
I did a diagnostic after installing Ubuntu to make sure all of my drivers were working by going to System > Administration > System Testing, and looking through the logs there are several entries for the opensource radeon driver.  One is under information about my graphics card: Kernel Module: radeon.  So I most likely am running the open source radeon driver. If you have anymore questions about my system I could look through the log file it created in FireFox.

---

