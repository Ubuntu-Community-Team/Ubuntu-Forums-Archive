---
title: "Problem with terrible disk access speed"
date: 2010-08-07
forum: Hardware
---

### Post by kainalu on 2010-08-07
Hello All,

I have a EEEPC901, with the SSD's. I noticed my processor stays in IOWAIT a lot, as well as disk access of any kind being slow. I didn't track the problem down specifically to the disk until recently, but I'm sure thats the problem. I benchmarked the drives, and saw this:

Root Drive:
ASUS-PHISON SSD

FDISK -lu results:
Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders, total 7880544 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfb38fb38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     7871849     3935893+  83  Linux

Disk utility benchmark:
Min Read: 1.2MB/s
Max Read: 33.5MB/s
Avg Read: 31.4MB/s
Avg Seek: 0.7ms


Home Drive:
ASUS-PHISON SSD
Disk /dev/sdb: 16.1 GB, 16139354112 bytes
255 heads, 63 sectors/track, 1962 cylinders, total 31522176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf26d47c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    31519529    15759733+  83  Linux

Min Read: 7.3MB/s
Max Read: 30.9MB/s
Avg Read: 30.5MB/s
Avg Seek: 0.8ms


Any ideas on why its so slow?

---

