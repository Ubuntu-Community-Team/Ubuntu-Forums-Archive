---
title: "Cannot find Ricoh xD-Picture Card Disk Device"
date: 2008-05-09
forum: Hardware
---

### Post by Tim Silver on 2008-05-09
Hi,

I'm running Hardy Heron from an external (USB) HDD on a Dell Inspiron 9400. This machine is fitted with an internal Ricoh xD-Picture Card Disk Device, but the heron is not seeing it (or if he is, I'm not! :lolflag:). Do I need to find a driver?

---

### Post by timcredible on 2008-05-09
what happens when you plug in an xd card?  does a new window pop up on your screen, or f-spot manager, or an icon on your desktop?

---

### Post by Tim Silver on 2008-05-12
Hi timcredible,

Absolutely nothing! As if card reader wasn't there, and not seen in the File Browser either.

---

### Post by ZeCagou on 2008-05-22
Got the same error on an AsusTek laptop whith the **hardy heron**
and  
Linux xxxxxx 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

Memorystick is not recognized while SDCARD is !


----8< -------------------------------------------------------------------
08:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host 
        Adapter (rev 22)
        Subsystem: ASUSTeK Computer Inc. **Unknown device 1517**

08:03.1 0805: 1180:0822 (rev 22)
	Subsystem: 1043:1517
-------------------------------------------------------------->%---------

---

### Post by inzy123 on 2009-08-28
yeah i have the same problem here
looked at a few threads, still no answer for me :(

the xD slot would work back when i was using XP, now all of a sudden its decided it wont work on ubuntu 9.04

---

### Post by Ellio-pc on 2010-08-05
I have a Dell Inspiron 1525 and the following worked for me. I got this information from: [https://bugs.launchpad.net/ubuntu/+s...2490/+activity](https://bugs.launchpad.net/ubuntu/+s...2490/+activity)

I then got the file: [http://launchpadlibrarian.net/443737...h_xd_3.tar.bz2](http://launchpadlibrarian.net/443737...h_xd_3.tar.bz2)


First, extract the file in Nautilus in your home directory (right click, select extract here)

Open a terminal then: cd ricoh_xd_3

Then to install please do: make && sudo make install && sudo make load

This work wonderfully for me!

---

### Post by IcarusR on 2010-08-05
You need to install the 'build-essential' package from the repositories to build anything from source.

Launchpad link does not work.

---

### Post by Ellio-pc on 2010-08-06
Sorry the links didn't work, try these:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/202490/+activity](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/202490/+activity)

[http://launchpadlibrarian.net/44373795/ricoh_xd_3.tar.bz2](http://launchpadlibrarian.net/44373795/ricoh_xd_3.tar.bz2)

---

### Post by tripkin on 2010-10-07
This worked quite well, thank you!

---

### Post by Ellio-pc on 2010-10-08
I'm glad it worked.

Update -- My Xd card reader on my Dell Inspiron 1525 now works fine with the beta version of Ubuntu 10.10. Didn't have to load up anything, worked straight away.

---

