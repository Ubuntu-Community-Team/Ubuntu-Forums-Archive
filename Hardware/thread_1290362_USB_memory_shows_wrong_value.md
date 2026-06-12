---
title: "USB memory shows wrong value"
date: 2009-10-13
forum: Hardware
---

### Post by Biopyro on 2009-10-13
I recently tried to partition my usb drive using Gparted and it went wrong, it said neither operation could be completed (I was making 2 partitions; 800MB and the rest to fill the 3.7GB drive). Now both windows and ubuntu see the drive as being 838.9MB. I've tried formatting in windows but it only gives the option to format size: 800MB. 

I know it's still there because $ sudo fdisk -l shows the drive 
```
Disk /dev/sdb: 4009 MB, 4009754624 bytes
255 heads, 63 sectors/track, 487 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6f20736b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         102      819283+   b  W95 FAT32

```

Restarted and tried again, despite having a few errored runs before, I am now the owner of a happily partitioned drive

---

