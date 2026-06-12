---
title: "[SOLVED] Cant Mount new HDD"
date: 2008-06-27
forum: Hardware
---

### Post by kouakou on 2008-06-27
I bought a new HDD (1 Terabyte SATA by western Digital) it is connected to the computer but my ubuntu reads it as an scsi drive and will not mount it. My question is ....is there something I am missing or is there something else I need to do to mount it.
Please Help.....

---

### Post by kpkeerthi on 2008-06-27
Might help if you give us more info...

Is it a USB drive?
Is it formatted? What format?

What is the output of below commands?
```
sudo fdisk -l
```

```
cat /etc/fstab
```

---

### Post by kouakou on 2008-06-27
No it is not usb.....it is connected to the mother board. I have a 40 gb which is what I am using now

 sudo fdisk -l
=================================================Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 40.9 GB, 40981118976 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6c286c28

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4772    38331058+  83  Linux
/dev/sdb2            4773        4982     1686825    5  Extended
/dev/sdb5            4773        4982     1686793+  82  Linux swap / Solaris

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        7176    57641188+   c  W95 FAT32 (LBA)
/dev/sdc2            7177        9729    20506972+   f  W95 Ext'd (LBA)
/dev/sdc5            7177        9729    20506941    7  HPFS/NTFS

 cat /etc/fstab
================================================================
 /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=5c44feee-56f0-4f2f-980b-06ba81f78cfc /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=8cecfa96-78d2-4ade-af01-b10d0727dd91 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by kouakou on 2008-06-27
now that I look at the output of what you sent me....it brings me to another question. How do I format that drive?
Thanks for you Help

---

### Post by logos34 on 2008-06-27
Use [Gparted]("http://gparted.sourceforge.net/larry/generalities/gparted.htm") (system>admin>partition editor) to create and format new ext3 partition

then it will have a partition table

to mount it:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

make sure to use the UUID # format like the others (note how the letters changed when you connected the terabyte drive)

sudo blkid

or 

sudo vol_id /dev/sda

---

### Post by kouakou on 2008-06-27
Just wanted to say Thank you Gentlemen or ladies if you be ladies...I am up and running ....Again Thank you

---

### Post by ukripper on 2008-06-27
> **kouakou said:**
> Just wanted to say Thank you Gentlemen or ladies if you be ladies...I am up and running ....Again Thank you

Pelase mark this thread as solved from thread tools.

Cheers

---

