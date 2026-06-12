---
title: "Cannot mount desired partition"
date: 2005-01-07
forum: Installation &amp; Upgrades
---

### Post by andrewski on 2005-01-07
I'm trying to install Ubuntu on my /dev/hda3 (an IDE HD).  However, when I try to format and mount it, I get an error (copied from the console in Alt+F3):
```
/sbin/tune2fs: No such file or directory while trying to open /dev/ide/host0/bus0/target0/lun0/part3
Couldn't find valid filesystem superblock
mke2fs 1.3.5
Could not stat /dev/ide/host0/bus0/target0/lun0/part3 --- No such file or directory

The device apparently does not exist; did you specify it correctly?
```
Well, the device DOES exist; I can format, mount, and use it in Gentoo (currently).

Here is my fdisk for the drive, in case there's an unseen problem:
```
Disk /dev/hda: 81.9 GB, 81964302336 bytes
16 heads, 63 sectors/track, 158816 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       20815    10490413+   7  HPFS/NTFS
/dev/hda2           20816       39546     9440424    5  Extended
/dev/hda3          139441      158816     9765504   83  Linux
/dev/hda5           20816       21020      103288+  83  Linux
/dev/hda6           21021       27263     3146440+  83  Linux
/dev/hda7           27264       37667     5243584+  83  Linux
/dev/hda8           37668       39546      946984+  83  Linux
```

Thanks in advance for any help you can provide. :D

---

### Post by andrewski on 2005-01-08
To be clear, I can create, mount, and fsck this partition without problems in Gentoo.  Also, FWIW, this partition used to be a FreeBSD slice, but I've deleted it and formatted it so many times now that only you and I know that. :)

---

### Post by andrewski on 2005-01-10
I'm assuming, at this point, that I should file a bugreport on this?

---

### Post by andrewski on 2005-01-15
[https://bugzilla.ubuntu.com/show_bug.cgi?id=5549](https://bugzilla.ubuntu.com/show_bug.cgi?id=5549)

---

