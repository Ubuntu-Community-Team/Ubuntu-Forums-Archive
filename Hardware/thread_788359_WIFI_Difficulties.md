---
title: "WIFI Difficulties"
date: 2008-05-09
forum: Hardware
---

### Post by stephenobe on 2008-05-09
I have an Acer Aspire 5520, Model # ICW50
Dual Core Turion 64 Bit
160 Gigabyte Hard drive,2 Gigabyte RAM
Windows Vista Or Ubuntu 8.04
Nvidia 7000m Graphics Accelerator
Atheros AR5007EG Wireless Network Adapter

When running Ubuntu 8.04, it says under hardware manager that I have the Atheros HAL and Atheros support for 802.11 Wifi. I have tried numerous things, but none seem to work. I can get on using my CAT5 cord plug up, but thats it. Any help would be appreciated.:confused::mad:

---

### Post by loserboy on 2008-05-09
follow this, but read the whole thing before starting

[http://ubuntuforums.org/showthread.php?t=766529&highlight=AR5007EG](http://ubuntuforums.org/showthread.php?t=766529&highlight=AR5007EG)

hope it helps

---

### Post by stephenobe on 2008-05-10
no, it still dosnt seem to work.

---

### Post by loserboy on 2008-05-12
ive seen other threads mentioning problems with that chipset, but the thread I linked had the best description of a fix, did it work in 7.10 or have you used 7.10 at all?

---

### Post by fissionmailed on 2008-05-12
Blacklist madwifi
Use ndiswrapper
You might have to connect via command line, like I do.

that should get you started, if you search on the forums you can find info on it.  Some times you have to do more or less with those AR5007EG, so it might be a breeze or it could take some working.  

Although, if you're running a 32-bit OS madwifi has a patch for it.  Although if didn't work for me, you might want to try it.

---

### Post by stephenobe on 2008-05-13
I'm running the 64-bit version,on 8.04, what do you recommend?

---

