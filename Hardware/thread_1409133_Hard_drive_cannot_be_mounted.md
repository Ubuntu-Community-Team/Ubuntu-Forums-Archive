---
title: "Hard drive cannot be mounted"
date: 2010-02-17
forum: Hardware
---

### Post by fabecool on 2010-02-17
Hi there, 

I've had some GRUB issues that have now been fixed (see [http://ubuntuforums.org/showthread.php?t=1408199](http://ubuntuforums.org/showthread.php?t=1408199)), but since then, my second hard drive (which is actually an array of two HD) can no longer be found from the "places". 

However, I still find both disks as well as the array in the disk manager.

I also checked from WinXP, and no problem: it's still there. So I booted from the live CD, and there it is as well.

Is there something that can be done to fix this?

Thank you!

Fa

---

### Post by fabecool on 2010-02-17
Okay,

I've now even tried to re-install Ubuntu so that I would get my drives back, but that does not help. So they can only be found from the live CD (and from Windows). 

However, they do appear in Palimpsest Disk Utility. 

I have no idea what the command to mount a disk is, but by looking around, I've found this that I tried:

```
sudo mount /dev/sda1
```

and it gives me this:

```
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab
```

Any help would be really appreciated!

Thank you

Fa

---

### Post by fabecool on 2010-02-17
Now I ran a 

```
sudo fdisk -l
```

and here's the result:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x50ecca38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38914   312576673+  42  SFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbc2ebc2e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        6079    48829536    7  HPFS/NTFS
/dev/sdc2            6080        9964    31206262+   5  Extended
/dev/sdc5   *        6080        9798    29872836   83  Linux
/dev/sdc6            9799        9964     1333363+  82  Linux swap / Solaris

```

disk sdb is probably said not to contain a valid partition because it is mounted in sda as part of a RAID.

Fa

---

### Post by fabecool on 2010-02-19
Bump

I'm still stuck with this issue, and I really don't get it. If I connect an USB drive, it is automatically detected and Ubuntu automatically mounts it for me. I can also see my windows partition from the "Places". 

But I still haven't figure out how to get my raid drives recognized and mounted.

Anyone's got an idea? 

A nice week-end to you all!

Fa

---

