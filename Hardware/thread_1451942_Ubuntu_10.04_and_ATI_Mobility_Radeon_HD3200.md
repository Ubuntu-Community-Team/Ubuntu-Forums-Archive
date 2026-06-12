---
title: "Ubuntu 10.04 and ATI Mobility Radeon HD3200"
date: 2010-04-11
forum: Hardware
---

### Post by jairus_antonia on 2010-04-11
Hey All,

I've been a member to this forum for over 2 years now but never posted b4...
I have a HP laptop type: TX2550ED, i haven't succeeded yet to enable the "eyecandy". Everyting else works fine including x server.
If I go to Appearance Preferences => Visual Effects and try to enable normal or Extra I get an error: Desktop effects could not be loaded.
So i downloaded the latest drivers (ati-driver-installer-10-3-x86.x86_64.run) with CCC and installed it without any problems.... 
But when i go to System=> Preferences => ATI Catalyst Control Center or ATI Catalyst Control Center (Administrative) i get an error saying:

Initialization error

There was a problem initializing Catalyst Control Center Linux edition.
It could be caused by the following.

No ATI graphics driver is installed, or the ATI driver is not functioning properly.
Please install the ATI driver appropriate for your ATI hardware, or configure using aticonfig.

But if i try to configure it using aticonfig, i get a list with alot of attributes. But i cant figure out which one i need to fix the problem.

If anyone could help me with this problem it would be much appreciated! Thnx in advance

HP TX2550ED specs: 

Processor  	AMD Turion 64 X2
RAM	 	3 GB
RAM Type 	SO-DIMM DDR2
HDD		250 GB
Resolotion 	1280 x 800 Pixels
Screen 		Touchscreen
Videocard 	ATI Mobility Radeon HD 3200
Videomemory 	512 MB
etc.

---

### Post by Ayuthia on 2010-04-11
The 10.3 version does not work with Lucid because of the new xorg server.  Right now, the newer fglrx driver is still being tested and has not been officially released.  You might check out this [thread]("http://ubuntuforums.org/showthread.php?t=1434064") for more information on how to use it.

---

### Post by zinadork on 2010-06-19
My laptop is unable to hibernate or wake from a sleep.  I am running the ati radeon 3200 graphics card on an acer aspire 5535.  When I try to wake it the motor starts, but the screen stays black.  I am dual booting with win7 without wubi.

---

