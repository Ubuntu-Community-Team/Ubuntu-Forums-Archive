---
title: "USB drive not on desktop"
date: 2008-11-07
forum: General Help
---

### Post by Tex786 on 2008-11-07
Hi,

I was trying to format my USB drive in XP on my laptop and it did not go so well. It really got screwed up and I don't know what to do. The format was not finished and now when I try to plug my usb drive into my desktop that is running 8.10 its not showing up at all.

its a new drive..

Can someone help me out with this??

Thanks

---

### Post by beercz on 2008-11-07
Does it show in Places->Computer?

---

### Post by geirha on 2008-11-07
Do you see the usb drive in [apt://gparted](apt://gparted) or with "**sudo fdisk -l**" when it is inserted?

---

### Post by Tex786 on 2008-11-07
> **beercz said:**
> Does it show in Places->Computer?

it says unable to mount location.

---

### Post by Tex786 on 2008-11-07
> **geirha said:**
> Do you see the usb drive in [apt://gparted](apt://gparted) or with "**sudo fdisk -l**" when it is inserted?

home@home-desktop:~$ sudo fdisk -l
[sudo] password for home: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8fb48fb4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30025   241175781   83  Linux
/dev/sda2           30026       30401     3020220    5  Extended
/dev/sda5           30026       30401     3020188+  82  Linux swap / Solaris

Disk /dev/sdb: 8387 MB, 8387559424 bytes
64 heads, 32 sectors/track, 7999 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
home@home-desktop:~$ 

Do you see it? I don't know what to look for...

---

### Post by geirha on 2008-11-07
> **Tex786 said:**
> 
Disk /dev/sdb: 8387 MB, 8387559424 bytes
64 heads, 32 sectors/track, 7999 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table
home@home-desktop:~$ 

Do you see it? I don't know what to look for...

/dev/sdb must be it; an 8GiB disk with an invalid partition table. Install [apt://gparted](apt://gparted), run it (System -> Administration -> Partition Editor) and use it to create partitions on /dev/sdb. A fat32 partition that cover the entire drive is a common setup.

---

