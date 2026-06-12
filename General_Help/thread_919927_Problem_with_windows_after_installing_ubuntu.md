---
title: "Problem with windows after installing ubuntu"
date: 2008-09-14
forum: General Help
---

### Post by mcfroger3 on 2008-09-14
So this is what happened.  I was installing ubuntu on my friends computer.  so i partitioned some space on his hdd and went with the install.  the first time it was at teh end and grub failed to install, and when it restarted windows was saying that hall.dll was coruppt and needed to be reinstalled, so we installed ubuntu again and grub worked, so we have linux but we cant get windows working, also we dont know his xp admin password.  any way we could fix this from linux?

We are using ubuntu 8.04

---

### Post by Sef on 2008-09-14
Let's check the partitions:

Applications > Accessories > Terminal

then paste or type this command:

```
sudo fdisk -l
``` Small L; paste the results here.

---

### Post by mcfroger3 on 2008-09-14
Heres what i get

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            8902        9729     6650910   83  Linux
/dev/sda2   *           1        8901    71497251    7  HPFS/NTFS

Partition table entries are not in disk order

```

---

### Post by mcfroger3 on 2008-09-14
anything? am i going to have to reinstall windows?

---

