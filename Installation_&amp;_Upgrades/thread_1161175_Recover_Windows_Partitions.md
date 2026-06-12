---
title: "Recover Windows Partitions"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by rzumbado on 2009-05-16
Hi guys,

I'm having a hard time trying to recover a partition from a friend's computer.

What i'm trying to do? recover the partition so i can rescue all the files in there.

My Issues?
- Windows does not start at all.
- When running ubunto from the CD and running this command from the shell i get:

```

ubunto@ubunto:-$ sudo fdisk -l

Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0x518b of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/tracks, 14593 cylinders
Units = cilynders of 16065 * 512 = 8225280 bytes

Device     Boot Start     End        Blocks   id  System
/dev/sda1           1        8       64228+    6  FAT16
/dev/sda2    *      9     4186     33559785    c  W95 FAT32 (LBA)
/dev/sda3        6383    14594     65961819    f  W95 Ext'd (LBA)
/dev/sda5    ? 250909   143383  1283776687+   84  OS/2 hidden c:

```

The one im trynig to recover is /dev/sda3

I have tried searching from all the forums with no luck.
I'm desperate here! 
plz help!!!!!

---

