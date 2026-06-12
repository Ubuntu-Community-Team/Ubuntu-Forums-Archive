---
title: "[SOLVED] /dev/sdb1 won't show"
date: 2008-09-12
forum: Hardware
---

### Post by miegiel on 2008-09-12
/dev/sdb1 won't show in /dev/ but I can fdisk /dev/sdb and mkfs /dev/sdb1
Everything seems fine till I actually try to use it (mount it or use it for a raid array)

I accidentally added /dev/sdb to a raid5 array while experimenting with mdadm a bit (i should have added it as /dev/sdb1 in the 1st place). Now i removed the array to start over, all drives and partitions are showing except /dev/sdb1 (a, b, c and e are the raid experimental drives).

```
:~$ ls /dev/sd*
/dev/sda   /dev/sdc   /dev/sdd1  /dev/sdd4  /dev/sdd7
/dev/sda1  /dev/sdc1  /dev/sdd2  /dev/sdd5  /dev/sde
/dev/sdb   /dev/sdd   /dev/sdd3  /dev/sdd6  /dev/sde1
```

At 1st I thought there might be something wrong with the partition and I've fdisked and mkfsed a few times now. I even tried shocking it back into existence by installing windows on it.

At the moment fdisk gives :
```
:~$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b8ba5

   Device Boot  Start     End     Blocks   Id  System
/dev/sdb1   *       1   60800  488375968+   7  HPFS/NTFS
```
It is there! really!

By now I'm convinced it's got nothing to do with the disk, but there's a ghost in my machine shouting "don't use /dev/sdb1". Something that remained after removing that raid I was playing with. But where is it and how can i find it?

I'm in dire need for some inspiration #-o

---

### Post by IntuitiveNipple on 2008-09-12
Check if there are md arrays:
```

ls /dev/md*

```
If so, check their configuration:
```

sudo mdadm --misc --detail /dev/md0

```
It is likely /dev/sdb is part of an array which would 'hide' /dev/sdb1.

---

### Post by miegiel on 2008-09-12
```
:~$ ls /dev/md*
/dev/md0

:~$ sudo mdadm --misc --detail /dev/md0
mdadm: md device /dev/md0 does not appear to be active.
```

I also just booted to my 32bit ubuntu and the partition doesn't show there either.
I'm thinking now that i didn't remove the aray properly or maybe did something wrong and didn't remove it at all.

I'll go and read more on removing raid arays, maybe I can find what I did wrong.

When I removed the aray i used :
```
sudo mdadm -f /dev/md0
sudo mdadm -r /dev/md0
```

---

### Post by IntuitiveNipple on 2008-09-12
This might help:
```

sudo mdadm --misc --query /dev/sdb

```
And this is likely to solve the problem:
```

sudo mdadm --misc --zero-superblock /dev/sdb

```

---

### Post by miegiel on 2008-09-12
Yay ... it's working now :D

```
sudo mdadm --misc --zero-superblock /dev/sdb
```
pointed me in the right direction.

It didn't work at 1st, but starting, stopping, failing, removing, cleaning and adding and consistently trying to zero the supperblock did the trick eventually.

thanks alot

---

