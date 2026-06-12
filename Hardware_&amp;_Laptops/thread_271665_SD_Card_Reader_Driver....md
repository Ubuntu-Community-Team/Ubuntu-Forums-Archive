---
title: "SD Card Reader Driver..."
date: 2006-10-05
forum: Hardware &amp; Laptops
---

### Post by ghstzr0 on 2006-10-05
I have a Fujitsu Lifebook T4010 with Ubuntu Dapper installed on it.  The SD Card Reader DOES NOT WORK!!  Nothing happens if I put a SD in the slot, and if I leave it in there during boot, the system hangs during booting on the step "loading hardware drivers...".  I surmised that I had the wrong drivers and have ever since been trying to get the correct ones installed.  I contacted the company directly (when I failed to find the right drivers after much googling) and they sent me some source to compile the drivers, but the source is all screwed up, badly commented, brief instructions, some files missing, yadda yadda...

I thne came upon this page: [http://mmc.drzeus.cx/wiki/Controllers/O2/OZ711Mx]("http://mmc.drzeus.cx/wiki/Controllers/O2/OZ711Mx"), which describes the EXACT model of notebook I have, and describes THE EXACT model of SD card reader I have.  First, it mentions:

> 
Company representatives have claimed they are working on a proprietary kernel module that will be made available to users. The driver has so far failed to materialize. There are no other alternative drivers as of 2006-09-04.


...which make me think that I am just screwed and my sd card reader won't work as of right now.  But then it mentions:

> 
Please do not confuse this controller for any other o2Micro controller, it is stacked together with the o2Micro MemoryCardBus OZ711M3/MC3 with PCI ID 1217:7223 **which has a working driver**...


...which sounds like there IS a driver that would work, but I cannot find it anywhere...  Does anyone have any idea here.  Am I cooked?  Or is there a driver out there?

---

