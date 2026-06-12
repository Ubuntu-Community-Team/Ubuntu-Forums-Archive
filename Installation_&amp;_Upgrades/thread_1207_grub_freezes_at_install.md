---
title: "grub freezes at install"
date: 2004-10-19
forum: Installation &amp; Upgrades
---

### Post by pjssilva on 2004-10-19
Hello,

I am trying to help a friend to install ubuntu in his new machine based on the ASUS P4P800-E Deluxe motherboard (Intel 865PE chipset). He has two 120GB SATA drives that he wants to put in software RAID. 

We have partioned both drives with the following layout:

1 primary partition of 20Gb to be used by windows (windows will be installed using RAID 1 in this first partition on both disks).
1 primary partition of 2GB for /boot on disk 1 and for swap on disk 2.
1 primary partirion of ~20Gb for / (Software RAID 1 on both disks)
1 primary partirion of ~100Gb for /home (Software RAID 1 on both disks)

The installation goes fine (base system installed) until the moment it tries to install grub. At that moment grub installation freezes at 50%. The same happens if you try to install LILO. If one move to console 2 and try to acess the root directory the console 2 freezes.

Any hints?

---

