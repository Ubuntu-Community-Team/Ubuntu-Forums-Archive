---
title: "No SATA showing for HP a1610n"
date: 2008-09-14
forum: Hardware
---

### Post by jem199 on 2008-09-14
Recently many outlets have this desktop selling for about $200. I bought it specifically to try Ubuntu. I'm not a hardware-OS whiz by any means, but I've built quite a few desktops out of spare parts.

I can't get the SATA hard drive to be recognized even in BIOS. Any help you can provide would be appreciated. Here are the specs:

Athlon 64 X2 (W) 4200+ 2.2 GHz
2000 MT/s (mega transfers/second)
Socket AM2
Chipset GeForce 6150 LE 
MOBO Manufacturer: Asus
Motherboard Name: A8M2N-LA
HP/Compaq motherboard name: NodusM3-GL8E
Samsung P120S SP2X04C Series Hard Disk Drive  
1 GB 240 pin, DDR2 SDRAM
250 GB SATA
16X DVD(+/-)R/RW RAM (+/-)R DL LightScribe drive 

HP has a whole page of updates for drivers. I used another pc to make floppies for the BIOS and DVD-RW firmware updates and only the dvd drive one worked.
[http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&dlc=en&cc=us&lang=en&product=3239117](http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&dlc=en&cc=us&lang=en&product=3239117)


Thanks from a n00b,

Janet

---

### Post by tomthumb99 on 2009-01-11
Janet,

I have the same box. The live CD bootup work fine, buth installing Ubuntu on the actual PC is rought lession.  Make sure you have the recovery disks before an attempt install.  Select the manual option when choosing partitions during the install.  Key on this model is that an additional IDE drive can be installed off the mobo w/ current IDE/SATA chips set.  Go with the IDE drive, make GRUB install goes smoother.  

The HP support page is worthless there are NO drivers there for Linux.  It should become public knowledge the HP does not offer help or any guidance on a Linux install here. I think the 3.10 BIOS has some major shortfalls in Linux, apparent other vendors sell more recent BISO upgrades for this mobo. 

Regards,

TH

---

