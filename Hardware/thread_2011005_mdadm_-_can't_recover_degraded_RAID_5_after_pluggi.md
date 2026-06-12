---
title: "mdadm - can't recover degraded RAID 5 after plugging of SATA cable"
date: 2012-06-26
forum: Hardware
---

### Post by dom2 on 2012-06-26
Hello,

I've software RAID 5 with mdadm (3 identical disks, 3partitions sdb1, sdc1, sdd1).

Yesterday for testing purposes I've plugged off SATA connection from sdb.
As it should happen, RAID became degraded, after reboot I've got only access to shell.

I've booted live cd to join sdb1 back to /dev/md0, but:

[PHP]root@ubuntu:/media# mdadm --manage /dev/md0 --add /dev/sdb1 
 mdadm: /dev/sdb1 not large enough to join array
root@ubuntu:/# sfdisk -s /dev/sdb1; sfdisk -s /dev/sdc1; sfdisk -s /dev/sdd1
1953514552
1953514552
1953514552
root@ubuntu:/# cat /proc/mdstat 
Personalities : [raid6] [raid5] [raid4] 
md0 : active raid5 sdc1[1] sdd1[3]
      3907024896 blocks super 1.2 level 5, 1024k chunk, algorithm 2 [3/2] [_UU]
unused devices: <none>

Fdisk:
Disk /dev/sdb1: 2000.4 GB, 2000398901248 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x9d39af9c

Disk /dev/sdc1: 2000.4 GB, 2000398901248 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xac63d3db

Disk /dev/sdd1: 2000.4 GB, 2000398901248 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x49c3c27c
[/PHP]I've not changed anything to sdb1 partition, why it's now 'too small'? Metadata is 1.2.
Has anyone of you got this issue?

Thank you in advance for any help,

cheers

---

### Post by TheFu on 2012-06-26
I haven't seen this specific issue. Mine were always a loose cable inside the array.

$ sudo mdadm --assemble /dev/md0 -v

This command should put the array back based on the /etc/mdadm settings.

---

### Post by dom2 on 2012-06-26
Have tried that, no way. :-)

I've tried to add whole /dev/sdb instead of partition, it worked.

Have found I've got mess with align, was set from 2048 instead of 64 (on WD disks).

recovery in progress. :-)!

Thank you for you help!


One more question:
active raid5 sdb1[4] sdc1[1] sdd1[3]

can those numbers in [ ] be changed to 0, 1, 2 or something that is in order? How they are generated?

cheers

---

### Post by TheFu on 2012-06-26
I assume those numbers are significant to the internals of mdadm in your RAID set.  Perhaps it means something about the specific stripes? I dunno. When you dropped a drive from the RAID set, the stripe changed.

Mine are:
> md0 : active raid5 sdf1[1] sde1[2] sdd1[3] sdc1[0]since sdf used to have a bad cable and dropped from the RAID set  ... er ... multiple times.

I do not know how to change the order. I would assume either of these methods could work:
a) being selective and forcing failures
b) doing a complete backup, destroying the RAID set and rebuilding it from scratch.

If you really want to know, take a look at the mdadm source code. ;)

BTW, a 1M chunk seems really large. I thought 256K was the best practice these days. [https://raid.wiki.kernel.org/index.php/RAID_setup#RAID-5](https://raid.wiki.kernel.org/index.php/RAID_setup#RAID-5) Perhaps not.

---

