---
title: "External HD is missing free space mysteriously..."
date: 2007-10-12
forum: Hardware &amp; Laptops
---

### Post by agiamba on 2007-10-12
Hi,

It's been discussed a bit before, but nothing resolved.

My external HD for some reason is missing space, it's 120gb capacity, about 85gb full, yet Ubuntu says I only have 125mb free! Help?

---

### Post by voided3 on 2007-10-12
Did you recently delete a lot of files from it? If that is the case, it may have left the trash on the drive full. I had a jump drive to this once, so I made a new text document, saved it, stuck it in the trash, and then emptied the trash while the drive was connected and it emptied the trash on the jump drive too.

---

### Post by dfreer on 2007-10-12
As for checking for trash, go to the folder where it is mounted and show hidden files. If you see a .trash folder, try deleting it :)
Beyond that, if you are still having issues, post the results from the command: sudo fdisk -l

---

### Post by agiamba on 2007-10-13
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            6516        9729    25816455    b  W95 FAT32
/dev/sda2   *           9        4852    38909430    7  HPFS/NTFS
/dev/sda3            4853        6254    11261565   83  Linux
/dev/sda4            6255        6515     2096482+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14593   117218241    c  W95 FAT32 (LBA)

Disk /dev/mmcblk0: 255 MB, 255852544 bytes
16 heads, 32 sectors/track, 976 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1         976      249805+   6  FAT16


I should note that it switched sometime recently, it used to work fine. Sdb1 is the drive that is not displaying correctly.

Thanks!

---

### Post by taurus on 2007-10-13
Did you mount /dev/sdb1 and where did you mount it to?  Assuming it's mounted to /media/sdb1, what's the output of this command from a terminal?

```
sudo df -h /media/sdb1
```

---

### Post by agiamba on 2007-10-13
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             112G  112G  126M 100% /media/sdb1

Generally it's just mounted when I boot up the computer, but if I do change places or something I mount it to there.

---

### Post by vanadium on 2007-10-13
The last command suggests that 112 G is used, not about 85 Gb as you mentioned in your first post. You might want to use the graphical "Disk Usage Analyzer" to take a look at that drive and see what is taking the space, then do some house keeping.

---

### Post by taurus on 2007-10-13
Try

```
sudo du -h /media/sdb1
```

---

