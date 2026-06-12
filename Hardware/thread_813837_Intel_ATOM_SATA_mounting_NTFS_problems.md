---
title: "Intel ATOM SATA mounting NTFS problems"
date: 2008-05-31
forum: Hardware
---

### Post by neilneil2000 on 2008-05-31
I was running an Athlon XP system and have 3 hard drives

1xIDE - boot
2xSATA - Media

The SATA drives have been moved from a Windows PC and are formatted as NTFS.  This was working fine using ntfs-3g in fstab.

I have now moved across to the new Intel Atom platform and I can't mount the partitions.  I have a feeling this is a driver problem but maybe someone else can shed some light on it.

my fdisk -lu output is:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000663c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    48837599    24418768+  83  Linux
/dev/sda2        48837600   156296384    53729392+   5  Extended
/dev/sda5       151766118   156296384     2265133+  82  Linux swap / Solaris
/dev/sda6        48837726   151766054    51464164+  83  Linux

Partition table entries are not in disk order
```

Hope you can help!

---

