---
title: "Help merge partitions"
date: 2005-08-29
forum: Hardware &amp; Laptops
---

### Post by Morbeo on 2005-08-29
I have a lot of partitions and now I want to change that.
Here is the fdisk output
 
```
 Disk /dev/hda: 81.9 GB, 81964302336 bytes 
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
 
Device Boot Start End Blocks Id System
/dev/hda1 * 1 653 5245191 b W95 FAT32
/dev/hda2 654 9963 74782575 f W95 Ext'd (LBA)
/dev/hda5 654 1973 10602868+ b W95 FAT32
/dev/hda6 1974 1974 8001 82 Linux swap / Solaris
/dev/hda7 2612 9963 59054908+ 7 HPFS/NTFS
/dev/hda8 * 1975 2278 2441848+ 83 Linux
/dev/hda9 2279 2611 2674791 83 Linux
 
Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
 
Device Boot Start End Blocks Id System
/dev/hdb1 2 19457 156280320 f W95 Ext'd (LBA)
/dev/hdb5 2 7650 61440561 7 HPFS/NTFS
/dev/hdb6 7651 19457 94839696 7 HPFS/NTFS
``` 
 
Now, my root is hda8 and my /home is hda9. What I am trying to achieve is to merge all partitions from hda5 to hda9, make them root and make hdb5 my new home. All of them partitions are emptied from all data with the exception of hda8 (root). I suggest I'll have to backup my root on other partition in order to merge it.
I intend to do all these operations without the need to reinstall Ubuntu. My aversion of doing so is because my net connection is not the brightest star in the sky.
 
I please for advices in accomplishing this task.

---

