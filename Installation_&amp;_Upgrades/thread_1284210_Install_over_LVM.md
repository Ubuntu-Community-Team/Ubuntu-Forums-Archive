---
title: "Install over LVM"
date: 2009-10-06
forum: Installation &amp; Upgrades
---

### Post by awhogan on 2009-10-06
Hi - 

I need to install Ubuntu on a machine that is currently running SUSE 10.0. The system is setup using LVM (and possibly RAID, I'm not sure how to tell). 

The /home directory is a LVM partition. I would like to install Ubuntu and keep the drive set up, specifically, recognizing the home paritition without having to format it. 

Is this possible? I've been a Ubuntu Desktop user for years, but am not familiar with this raid/lvm stuff.

Here is the partition list from fdisk:
```

/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2               8        1052     8388608   8e  Linux LVM
/dev/sda3   *        1053        1078      208845   83  Linux
/dev/sda4            1079       72809   576179257+   f  W95 Ext'd (LBA)
/dev/sda5            1079        1340     2104483+  82  Linux swap / Solaris
/dev/sda6            1341       72809   574074711   8e  Linux LVM

Disk /dev/dm-0: 10.7 GB, 10737418240 bytes
255 heads, 63 sectors/track, 1305 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/dm-1: 4294 MB, 4294967296 bytes
255 heads, 63 sectors/track, 522 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/dm-1 doesn't contain a valid partition table

Disk /dev/dm-2: 3221 MB, 3221225472 bytes
255 heads, 63 sectors/track, 391 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/dm-2 doesn't contain a valid partition table

Disk /dev/dm-3: 3221 MB, 3221225472 bytes
255 heads, 63 sectors/track, 391 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/dm-3 doesn't contain a valid partition table

Disk /dev/dm-4: 7516 MB, 7516192768 bytes
255 heads, 63 sectors/track, 913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/dm-4 doesn't contain a valid partition table

Disk /dev/dm-5: 10.7 GB, 10737418240 bytes
255 heads, 63 sectors/track, 1305 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/dm-5 doesn't contain a valid partition table

Disk /dev/dm-6: 107.3 GB, 107374182400 bytes
255 heads, 63 sectors/track, 13054 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/dm-6 doesn't contain a valid partition table

Disk /dev/dm-7: 214.7 GB, 214748364800 bytes
255 heads, 63 sectors/track, 26108 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/dm-7 doesn't contain a valid partition table
```

---

