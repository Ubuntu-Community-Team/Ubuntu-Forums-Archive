---
title: "I my SSD correctly aligned?"
date: 2010-10-05
forum: Hardware
---

### Post by Glaucous on 2010-10-05
Sitting on Ubuntu 10.04 x64 (no TRIM).

I'm using a Corsair SandForce 60 G2. I'm getting good performance, which should be as good as it gets, but I'm still curious if my partitioning was successful.

fdisk -lu
```
Disk /dev/sdc: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ebfa7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   117226304    58612128+  83  Linux

```

I formated using gparted, and added a 1 MB (2048 sectors) space at the start (was recommended). Although I don't think the block size is correct.

Input appreciated.

---

