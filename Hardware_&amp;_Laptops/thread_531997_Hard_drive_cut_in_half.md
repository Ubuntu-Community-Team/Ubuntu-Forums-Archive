---
title: "Hard drive cut in half?"
date: 2007-08-22
forum: Hardware &amp; Laptops
---

### Post by Kemrin on 2007-08-22
We have a 60 GB hard drive here. It was NTFS, but before the easy NTFS access tool was out, in 6.something. Ubuntu. We struggled with it for a little bit, and it didn't work right, and then the space in the hard drive randomly halfed in size, Now, for all purposes, it's 30GB, and all computers recognize it as a 30 Gb hard drive. This happened almost a year ago, so details beyond these may not be available. I would really appreciate help restoring this hard drive if someone knows what to do. Thanks.

---

### Post by Kemrin on 2007-08-22
Can someone help me?

---

### Post by merlinus on 2007-08-22
Try gparted live cd:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Also you might post results of:

```

sudo fdisk -l
df -h

```

-merlin

---

### Post by Kemrin on 2007-08-23
Here are the results

> sudo fdisk -l

Disk /dev/sda: 58.5 GB, 58506416640 bytes
255 heads, 63 sectors/track, 7113 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         637     5116671    7  HPFS/NTFS
/dev/sda2             638        1245     4883760   83  Linux
/dev/sda3            1246        1306      489982+  82  Linux swap / Solaris
/dev/sda4            1307        7113    46644727+  83  Linux

Disk /dev/sdb: 33.8 GB, 33820286976 bytes
255 heads, 63 sectors/track, 4111 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4111    33021576    7  HPFS/NTFS

>df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             4.6G  2.9G  1.6G  66% /
varrun                502M  108K  501M   1% /var/run
varlock               502M     0  502M   0% /var/lock
procbususb            502M  112K  501M   1% /proc/bus/usb
udev                  502M  112K  501M   1% /dev
devshm                502M     0  502M   0% /dev/shm
lrm                   502M   33M  469M   7% /lib/modules/2.6.20-16-generic/volatile
/dev/sda4              44G   42G  463M  99% /home
/dev/disk/by-uuid/04DC69AADC6996A8
                      4.9G  4.6G  332M  94% /media/sda1
/dev/sdb1              32G  764M   31G   3% /media/Black


I'll try the gparted once it finishes downloading

---

### Post by jacob01 on 2007-08-23
does ubuntu recognize the drive as having 30 gig or is it windows that recognizes the 30 gig

---

