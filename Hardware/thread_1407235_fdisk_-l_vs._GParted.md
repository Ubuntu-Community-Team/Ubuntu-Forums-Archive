---
title: "fdisk -l vs. GParted"
date: 2010-02-15
forum: Hardware
---

### Post by yawnmoth on 2010-02-15
According to "sudo fdisk -1", /dev/sdc is described thusly:

```
Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *       14267       14594     2620416    c  W95 FAT32 (LBA)
/dev/sdc2              11        1316    10485760    7  HPFS/NTFS
/dev/sdc3   *        1316       14267   104031232    7  HPFS/NTFS
/dev/sdc4           14267       14594     2621440    f  W95 Ext'd (LBA)
/dev/sdc5           14267       14594     2620416    0  Empty

Partition table entries are not in disk order
```
According to GParted, however, it only has one partition - an unallocated one with an unallocated filesystem.  My question is...  why the difference?

Also, GParted took a very long time to come up, whereas "sudo fdisk -l" took no time at all.  Any ideas as to why?

---

### Post by yawnmoth on 2010-02-17
bump

---

