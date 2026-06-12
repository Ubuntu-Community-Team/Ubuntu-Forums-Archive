---
title: "Disk label problem?"
date: 2010-04-07
forum: Hardware
---

### Post by awhy on 2010-04-07
Hello All, 

I have Kubuntu Lucid Lynx booting from sde3 and Open SuSE 11.2 booting from sde5.

Disks sda sdb sdc sdd sde are SATA, sdf and sdd - PATA (IDE) on a separate 2-channel 
PCI controller. Both IDE disks are perfectly visible, fdisk-able in SuSE,  but in Kubuntu 
fdisk, parted and cfdisk refuse to recognize these PATA disks (unable to read /dev/sdf), 
although mkfs happily creates a filesystem on /dev/sdf1 and /dev/sdd1 (partitioned in SuSE) 

I dont't think it's a hardware incompatibility problem, but rather suspect some disk label 
screwup (disks were used in Solaris before, including ZFS pool), but I tried to scratch and 
re-create fresh msdos label with many different tools - still Kubuntu doesnt like it, 
while SuSE does. 

Please advice
Thanks!

---

