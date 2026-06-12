---
title: "external hdd problems"
date: 2011-01-19
forum: Hardware
---

### Post by beew on 2011-01-19
Hello,

I have tried to reinstall Ubuntu on an external hdd but the installer keep crashing on me with an I/O error. Previously the hard disk has several Linux distro installed and somehow become unbootable. 

I ran "sudo fsck /dev/sdb" and get this message

> fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
I decided to start all over again, I used gparted to deleted all the partitions but the same error persisted.

I then used the dd command to wipe the drive and reformat it to ext2. But running fsck gives the same error. Moreover, 15G appears to be missing from the hdd. I mounted the drive and right click "properties",  it says that the 15 G is unreadable and it may be formatted as ext3/ext4.  I also noticed that when the drive is plugged into a pc running Ubuntu,  it takes a long time to mount (before it is mounted almost immediately)  there are messages like "30 G hard drive is successfully mounted" (sorry, can't remember the exact words. I can't reproduce it now as the drive is wiped again, see below) but there is no 30G partition, it existed before for one of my Linux distros but it is supposed to have been wiped!


I then deleted the ext2 partion with gparted again (now it is all unallocated) but I get the same error when running fsck and the 15 G is still missing.


I have no idea what happens or if I need to get a new one. Please help.

Thanks.

---

### Post by psusi on 2011-01-19
You forgot the partition number in the fsck command.

---

### Post by beew on 2011-01-20
The disk is not partitioned, so should it be /dev/sdb1?

---

### Post by beew on 2011-01-20
The disk is not partitioned, so should it be /dev/sdb1?

---

### Post by psusi on 2011-01-20
> **beew said:**
> The disk is not partitioned, so should it be /dev/sdb1?

Yes, it is partitioned ( even if it only has one ), and I can only guess that you want the first partition.

---

