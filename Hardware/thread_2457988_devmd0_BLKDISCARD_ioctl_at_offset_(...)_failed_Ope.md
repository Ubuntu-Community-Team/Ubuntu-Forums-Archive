---
title: "/dev/md0: BLKDISCARD ioctl at offset (...) failed: Operation not supported"
date: 2021-02-13
forum: Hardware
---

### Post by Mona on 2021-02-13
Ubuntu 18.04 
Kernel: 4.15.0-36-generic

Hardware: 
3 x SSD 2 TB
Device Model: CT2000MX500SSD1
Firmware Version: M3CR033

hdparm -I /dev/sda | grep TRIM
	   *	Data Set Management TRIM supported (limit 8 blocks)
hdparm -I /dev/sdb | grep TRIM
	   *	Data Set Management TRIM supported (limit 8 blocks)
hdparm -I /dev/sdc | grep TRIM
	   *	Data Set Management TRIM supported (limit 8 blocks)

I created a RAID5-System using the 3 SSDs:

sudo cat /proc/mdstat
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sda1[3] sdb1[1] sdc1[0]
      3906754560 blocks super 1.2 level 5, 512k chunk, algorithm 2 [3/3] [UUU]
      bitmap: 0/15 pages [0KB], 65536KB chunk

On top of the RAID5 I created LVM

sudo pvs
  PV         VG      Fmt  Attr PSize    PFree
  /dev/md0   vg0 lvm2 a--    <3,64t  <1,95t


Whenever I remove a LVM snapshot, I get the error/warning message:

/dev/md0: BLKDISCARD ioctl at offset 18575744096 size 10737418240 failed: Operation is not supported.
  Logical volume "test" successfully removed

---

### Post by docescher on 2021-02-21
I get exactly the same warning / error message. I also could not solve why the error is triggered, although the firmware is up to date and according to manufactor trim is also supported.

It is not a solution, but to disable the warning message, simply edit /etc/lvm/lvm.conf:

```
issue_discards = 1
```

change to

```
issue_discards = 0
```

---

