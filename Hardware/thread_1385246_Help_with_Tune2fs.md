---
title: "Help with Tune2fs"
date: 2010-01-19
forum: Hardware
---

### Post by completeidiot on 2010-01-19
I have a 1tb external that i just repartitioned and changed file systems with using gparted. It's only giving me 931.51 usable space. I need more.
It's external and only contains media, no programs of any sort.

I tried doing this before and received various errors. mostly 

tune2fs: Bad magic number in super-block while trying to open /dev/sdb
Couldn't find valid filesystem superblock

also tried /dev/sdb1
and i just noticed in gparted that the drive is referred to as sdb in the top right drop down menu but it's called sdb1 everywhere else on the screen.

i'm new so don't assume i know anything

Thanks

---

### Post by completeidiot on 2010-01-20
i have officially stumped the forum

---

### Post by louieb on 2010-01-20
NTFS is a Microsoft file system - tune2fs only works with Linux - ext2-ext4 - file systems.  

There are some tools in Linux for working with NTFS - but its best to fix or check a NTFS file-system using a PC running windows.

BTW: sd@ refers to a drive 
sd@# refers to partition on the drive.

---

