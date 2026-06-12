---
title: "Rebuild RAID 5 on Adaptec 5805 v.5.2.0 build 15738"
date: 2013-01-25
forum: Hardware
---

### Post by pasaico on 2013-01-25
Hi, I have a problem.
On my array 5TB broke a hard disk,
I changed it and rebuild the procedure went ok at 100%

Now the array is not mounted.
Can you help me?

list of command and results;

> fdisk /dev/sdb1
Unable to open /dev/sdb1

> e2fsck /dev/sdb
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdb
Could this be a zero-length partition?

> e2fsck /dev/sdb1
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: No such file or directory while trying to open /dev/sdb1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>

> sudo sfdisk -l /dev/sdb
Disk /dev/sdb: 607670 cylinders, 255 heads, 63 sectors/track
read: Input/output error

sfdisk: read error on /dev/sdb - cannot read sector 0
 /dev/sdb: unrecognized partition table type
No partitions found

I also launched the comand testdrive but did not find partitions.

this is my line in fstab: /dev/sdb1               /node2_data             ext3    defaults

---

