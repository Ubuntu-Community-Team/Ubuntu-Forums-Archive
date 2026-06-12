---
title: "Not entirely sure if Im adding new hdd properly"
date: 2009-12-18
forum: Hardware
---

### Post by cackles on 2009-12-18
Hi, Im adding a new HDD using this tutorial - [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

Seems all is well, seems.

My drive was sdc so I used that, which is fine.

When it came to using this this line in the tutorial:

```
sudo mkfs -t ext3 /dev/sdc1
```

I just dont get it. I used:

```
sudo mkfs -t ext3 /dev/sdc
```

Because I have no idea where the '1' comes from.

It gave me a warning about it using the whole device. When I went to 

```
sudo lshw -C disk
```

again, there was still no '1' showing on it. Can someone please tell me the relevance of the '1' and what I can type in to actually see it labelled as that. Should I do it again and use the '1'?

---

### Post by lunaparadox on 2009-12-18
the one is just to say the first partition on the drive I believe. yes use the 1.

---

### Post by Some Penguin on 2009-12-18
Yes.

/dev/sdX is a whole device.
/dev/sdXn is partition n on drive sdX.

What you want to do is ensure that your partition table on /dev/sdc looks how you want it to, and THEN build filesystems on the partition(s).  What you've already done has probably already scrambled the partition table, so you might have to use something like 'cfdisk -z' to ignore the scrambled one.

---

### Post by cackles on 2009-12-18
Are there any commands I can use to see the disks I have with their partitions?

---

### Post by Some Penguin on 2009-12-18
sudo fdisk -l

should list partition tables for each drive.


sudo fdisk /dev/sdc

for that particular drive (and 'p' to show partition table, etc).

---

### Post by cackles on 2009-12-18
OK, I can see the differences in them now, I really appreciate the help on this.

Disk /dev/sda: 30.7 GB, 30738677760 bytes
255 heads, 63 sectors/track, 3737 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a2d0e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3577    28732221   83  Linux
/dev/sda2            3578        3737     1285200    5  Extended
/dev/sda5            3578        3737     1285168+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe38e7838

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    5  Extended
/dev/sdb5               1       30401   244195969+  83  Linux

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000


First disk is the OS, second where I download to and share and 3rd is going to be where I backup everything. I'll be sharing that too.

Just going back through the steps now I can see whats going on.


I went to go and mount it and I get this for my current config in fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=aa29596c-f8fa-4815-8760-4e5c9085f5c6 /               ext3    relatime,erro$
# /dev/sda5
UUID=6b280dbc-b787-44e6-987f-fd76c92e6986 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


/dev/sdb5       /shared         ext3    defaults        0       0
```

Why have I mounted sdb5 instead of sdb1 for my second hdd? Its been a year or so since I done it and I lost all my notes when I killed my other hdd ... so I have no idea why ...

---

