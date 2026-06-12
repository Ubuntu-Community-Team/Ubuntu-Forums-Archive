---
title: "Disk partition Problem during UBUNTU startup"
date: 2007-08-21
forum: Hardware &amp; Laptops
---

### Post by andrea_wwubuforum on 2007-08-21
Hi to all,
I've always used Gnome Partition Editor without problems but today I've get a big problem:

My system is UBUNTU dapper drake on laptop, on my hard disk are installed two partitions, the first is NTFS with original WinXP, the second is extended EXT3 and includes all linux paritions.

My goal was enlarge the partition at the end of the disk, using available free space before the partition.

File moving has been performed right but during the partition re-definition the Gnome partition manager has thrown an error and now it is not able to recognize any of the existent partitions.

Partition that I try to enlarge is the /dev/sda12, now during UBUNTU startup the following error message is shown:

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

If I press ctrl D ubuntu start right, mounts all the others partitions and works without problems.

Executing the following command by terminal
    e2fsck -b 8193 /dev/sda12

the same error will be shown.


Looking the disk partitions with system>administration>disks all the mounted partition are shown with the correct dimension . Also the partition sda12 is visible but it is not available and its dimension is not correct.

I've tried also to list the partitions with the command:

andrea@andreamain:~$ fdisk -l /dev/sda

but the result was:

Cannot open /dev/sda

Any ideas?

I can loose the partition /dev/sda12 (I've a backup) but i would repair my disk...

Tanks in advance...

---

