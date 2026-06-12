---
title: "broadcom 4318 802.11b/g wireless lan and ndiswrapper...."
date: 2008-10-11
forum: Hardware
---

### Post by superyyhking on 2008-10-11
hello,i get the Trouble........
my ndiswrapper is "ndiswrapper 1.8 i386"
my Wireless card is "broadcom 4318 802.11b/g"
but i get the trouble when i used ndiswrapper install .inf
>sudo ndiswrapper -i bcmwl5.inf 
but it reply:
>"couldn't copy bcmwl5.inf at /usr/sbin/ndiswrapper line 135"
what can me do? help me please!thank you

---

### Post by sergiom99 on 2008-10-11
try following the instructions posted here: [http://ubuntuforums.org/showthread.php?t=575750](http://ubuntuforums.org/showthread.php?t=575750)

they worked perfectly well in mine.
good luck!

---

### Post by sgreene59 on 2008-10-13
Assuming you are blacklisting bcs, bcm43xxx, etc per the HOWTO, depending on the specific vendor, you may have to try several drivers to find one that will drive your specific wlan implementation.  If you are running 64-bit, make sure you are loading a 64-bit win driver.

---

### Post by MrSootentai on 2008-10-13
IDK If you've tried it yet but you can use the 'Broadcom STA Wireless Driver' from the Hardware Drivers menu under System>Administration.
I'm using it now, and have already noticed a significant boost in my speed and wireless internet's signal strength.
I've tried ndiswrapper and b43 drivers before, but so far this one is working great.

---

