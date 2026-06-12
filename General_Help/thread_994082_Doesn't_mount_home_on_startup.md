---
title: "Doesn't mount /home on startup"
date: 2008-11-26
forum: General Help
---

### Post by MenZa on 2008-11-26
Hey everyone,

I'm having some issues with my box---it doesn't mount my /home partition when I boot it, and it doesn't start gdm.

fsck complains about not being able to check the partitions, then asks me to fix my problem myself. It then dumps me into a root shell, from where I can *mount /home ; exit* with no problems.

This is my partition setup:

```
Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007c7c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14946   120053713+  83  Linux
/dev/sda4   *           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a42bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1945    15623181   83  Linux
/dev/sdb2            1946       23617   174080340    5  Extended
/dev/sdb3   *       23618       30401    54492480    7  HPFS/NTFS
/dev/sdb5            1946       23617   174080308+  83  Linux

```

My root partition is /dev/sdb1, and my /home partition is /dev/sdb5.

I attempted to substitute the UUID for the device name in /etc/fstab, which now looks like this:

```

UUID=1fc1fdee-484b-47c2-aa78-076fad06dac9 /               ext3    relatime,errors=remount-ro 0       1
/dev/sdb5 /home           ext3   auto,relatime        0       2
UUID=3965b869-64ee-43cc-9f26-c827ab94d588 /media/backups  ext3    relatime        0       2
UUID=67ea3ab1-c9c4-402f-b203-2ea29f0b729d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

# external drive
/dev/sdc1	/media/external	ext3	rw,user,auto,relatime	0	0

# backup drive
/dev/sda6	/media/backup	ext3	rw,user,auto,relatime	0	0

# media drive
/dev/sda1	/media/ackbar	ext3	rw,user,auto,relatime	0	0

```

What gives?

---

### Post by Titan8990 on 2008-11-26
First off, you should never use the logical names of the drive in /etc/fstab.


This is because the logical names are dynamic, and can change at any time. The exception is when udev rules are in place.


Is your /home partition a USB drive?


Also, having the same drives in your /etc/fstab more than once probably isn't helping.

---

### Post by MenZa on 2008-11-27
> **Titan8990 said:**
> First off, you should never use the logical names of the drive in /etc/fstab.


This is because the logical names are dynamic, and can change at any time. The exception is when udev rules are in place.


Is your /home partition a USB drive?


Also, having the same drives in your /etc/fstab more than once probably isn't helping.

My /home partition is a logical partition on my /dev/sdb hard-drive. I'm not sure how to get the UUID for it to put it back in.

---

### Post by wesley_of_course on 2008-12-01
Ran across this and maybe it'll help , use a live cd and then try
 sudo fdisk -lu  . Hope it helps.

---

