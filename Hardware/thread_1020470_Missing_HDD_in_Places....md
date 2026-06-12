---
title: "Missing HDD in Places..."
date: 2008-12-24
forum: Hardware
---

### Post by bertles86 on 2008-12-24
Hi folks I installed Ubuntu Hardy Heron last night on an old Dell system, and all went swimmingly. Now I thought I got the partitioning right but maybe not:

1 x 10.2GB HDD
1 x 13.7GB HDD

I installed on the 10gb, but still partitioned the 13gb, but I can find neither on the installed system now...

In Computer it shows:

1.5GB Media
SCSI Drive
Filesystem

And the output from sudo fdisk -l is:

```
Disk /dev/sda: 10.2 GB, 10262568960 bytes
255 heads, 63 sectors/track, 1247 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea1aa9c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         187     1502046   82  Linux swap / Solaris
/dev/sda2             188         373     1494045   83  Linux
/dev/sda3             374        1247     7020405    5  Extended
/dev/sda5             374        1203     6666943+  83  Linux
/dev/sda6            1204        1247      353398+  82  Linux swap / Solaris

Disk /dev/sdb: 13.7 GB, 13702348800 bytes
255 heads, 63 sectors/track, 1665 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00240024

   Device Boot      Start         End      Blocks   Id  System

```

Can someone please help me find my missing HDD space?!

Thank you and Merry Christmas!

---

### Post by taurus on 2008-12-24
You need to use gparted (if you don't have it in System -> Administration, install it) and create a partition, /dev/sdb1, and format it to ext3.  Then, add an entry in /etc/fstab for it so it would mount automatically each time you boot.

```
/dev/sdb1   /media/sdb1   ext3   defaults   0   2
```
Of course, make sure you create that new mount point, /media/sdb1, or it won't be able to mount.

```
sudo mkdir /media/sdb1
```

---

### Post by bertles86 on 2008-12-24
Hi taurus thanks for the quick reply:

1 - I've installed Gparted
2 - I've created partition sdb1
3 - I've formatted it to ext3
4 - I've added the entry into fstab
5 - I've made the new mount point

It still doesn't appear! Any help would be grand.

[COLOR="Red"]Edit: I'm think as two short planks, restarted and all is good! Cheers taurus.[/COLOR]

---

### Post by taurus on 2008-12-24
And if you want to be able to write to it without using sudo or gksudo, then you can change the ownership of that new mount point, assuming it's /media/sdb1, from root to your login name.

```
sudo chown -R **bertles**:**bertles** /media/sdb1
ls -la /media
```
Replace **bertles** with your username.

---

### Post by bertles86 on 2008-12-24
That was my next questions cheers pal. Merry Christmas!

---

