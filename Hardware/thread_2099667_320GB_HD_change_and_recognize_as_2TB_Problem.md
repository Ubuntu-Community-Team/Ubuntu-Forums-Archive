---
title: "320GB HD change and recognize as 2TB Problem"
date: 2012-12-30
forum: Hardware
---

### Post by jao_madn on 2012-12-30
Hi, 

I would like to ask if someone experince this problem on a Hard disc. I had a 320 GB WD Blue 3.5 Hard disc. When i plug on my PC BIOS detect it for a while and dis-appear. Luckily sometimes i can check it on a bootable CD or attach on other LINUX PC but for a while it will dis-appear. As if you try to access the HD it will disappear from OS system even in  BIOS. This is the results when i check the HD on linux using Fdisk. To my surprise the 320GB detected as 2TB.. HOW come it become to 2TB.

> 
Disk /dev/sdc: 2199.0 GB, 2199023255552 bytes
255 heads, 63 sectors/track, 267349 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

# fdisk /dev/sdc
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0x92c910e4.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

WARNING: The size of this disk is 2.2 TB (2199023255552 bytes).
DOS partition table format can not be used on drives for volumes
larger than (2199023255040 bytes) for 512-byte sectors. Use parted(1) and GUID 
partition table format (GPT)


Disk /dev/sdc: 2199.0 GB, 2199023255552 bytes
255 heads, 63 sectors/track, 267349 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0993f2aa


the Disk Identifier change when i force to format it with fdisk option.. It means the disc is still accessible or something im missing..i already tried gparted or any tools related to HD or Filesystem (UBCD). But no success.

Maybe someone can give some ensights or opinion or any things that will help recover my HD or should i throw it on the garbage.

---

