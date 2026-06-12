---
title: "hard drive setup - 4096B sectors, WD EARS"
date: 2011-02-18
forum: Hardware
---

### Post by Zenze on 2011-02-18
I'm trying to install a new hard drive into my Ubuntu machine, however apparently the automatic methods do not work as it uses 4096B sectors instead of 512B sectors. Instead, in order to get it set up correctly the partitions must be aligned manually.

I did a lot of googling and have been following a few guides regarding the subject, but I don't think I got it right.

Here is what "fdisk -lu /dev/sdc" gives me:

```
Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004956b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63  3907024064  1953512001   83  Linux
```

From my understanding, in order for the partitions to be aligned correctly the start and end sectors must be divisible by 8, which mine are not. Why this is necessary or how it aligns the partitions I don't really know (although I would like to). I have tried a couple different methods/guides but have not gotten the right result, or maybe I have and I just don't know how to tell if everything is set up correctly.

So does anyone know how to set up these 4096B sector drives in linux, or be able to inform me what to do from here?

---

### Post by Zenze on 2011-02-18
Ok so I have been messing with it some more following [this]("http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html?ca=dgr-lnxw074KB-Disksdth-LX") guide.

This is what I now get from "fdisk -lu /dev/sdc":

```
Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004956b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              64  3907029167  1953514552   83  Linux
```

The starting sector starts on 64, which is a multiple of 8 so that seems ok. The ending sector is not, but I don't know if that even matters.

Is my drive set up correctly now?

---

