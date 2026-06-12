---
title: "Can't get the partition of pendrive in windows after using gparted"
date: 2009-08-27
forum: Installation &amp; Upgrades
---

### Post by colau on 2009-08-27
Hi,

To install ubuntu from pendrive i partitioned the pendrive using gparted.
After partitioning i can't get the 2.9 gb partition in windows.
If i select the partition from Right click mycomputer>Manage>Disk Management and select it to format it(2.9gb) prompts me to restart the windows to enable the partition(2.9gb).
Same result if i restart the windows.

I get only the 1gb partition.

But in linux i get both partitions.
```

Disk /dev/sdb: 4016 MB, 4016046080 bytes
255 heads, 63 sectors/track, 488 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004464d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         140     1124518+   b  W95 FAT32
/dev/sdb2             141         488     2795310    b  W95 FAT32

```

---

