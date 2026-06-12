---
title: "HD Sector Size of 512 bytes sounds awfully small"
date: 2010-08-01
forum: Hardware
---

### Post by qQChtIhpk1 on 2010-08-01
10.04 says my logical & physical sector size is 512 bytes - this sounds awfully small.  Since i am going to re-partition my HD (for / and /home) Can or Should i increase the sector size?  Is the Sector size the blocksize of the HD?

root@ccb:/home/ccb# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001aacc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            1049        4695    29294527+  83  Linux
/dev/sda2             262        1048     6321577+   5  Extended
/dev/sda5             527         787     2096451    b  W95 FAT32

Partition table entries are not in disk order

Thanks to All that make Ubuntu a reality.  i know how youall do it - 
Simple Hard Work - THANK YOU!

Chazbo

---

### Post by mikewhatever on 2010-08-03
'Sounds awfully small' is not the brightest argument one could think of for messing with partitions. I think you should leave it be, and for the difference between sectors and block, check out the link below.
[http://help.filemaker.com/app/answers/detail/a_id/3815/~/drive-blocks-vs.-sectors---explained](http://help.filemaker.com/app/answers/detail/a_id/3815/~/drive-blocks-vs.-sectors---explained)

---

