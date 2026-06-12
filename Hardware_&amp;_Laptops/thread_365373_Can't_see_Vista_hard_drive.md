---
title: "Can't see Vista hard drive"
date: 2007-02-19
forum: Hardware &amp; Laptops
---

### Post by dvgrhl on 2007-02-19
I have Ubuntu installed on its own hard drive, and Windows on another hard drive.  Ubuntu found and mounted all hard drives just fine, and I was able to browse files on my Windows drive from Ubuntu.  But that was when I had XP Pro installed on my Windows hard drive.

I have since upgraded to Vista on my Windows hard drive, and I can now no longer see that drive from Ubuntu.  It just doesn't show up.  Any ideas on what could be causing this or what I could do to attempt to resolve it?

---

### Post by taurus on 2007-02-19
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by dvgrhl on 2007-02-19
Sorry, I should have included this.  I have 3 hard drives in my computer.  2 160gb drives, and 1 120gb drive.  Ubuntu is on the 120gb drive.

```


Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       13291   106759926    7  HPFS/NTFS
/dev/hda2           13292       14593    10458315    f  W95 Ext'd (LBA)
/dev/hda5           13292       13422     1052226   82  Linux swap / Solaris
/dev/hda6           13423       14593     9406026   83  Linux

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19458   156289024    7  HPFS/NTFS

Disk /dev/sdb: 2079 MB, 2079350784 bytes
64 heads, 63 sectors/track, 1007 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1006     2028064+   6  FAT16

Disk /dev/sdd: 495 MB, 495452160 bytes
16 heads, 63 sectors/track, 960 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         960      483719+   b  W95 FAT32



```

---

### Post by Ptero-4 on 2007-02-19
Is Linblocker (a.k.a bitlocker) running. If it is, I`m sorry to say this but it`s gonna take a S76 to pluck your data off that ¨Vista¨ HD. If linblocker isn`t running you`ll need to install ntfs-3g and you`ll be able to access your data (at least until linblocker activates, which happens in the least expected moment).

---

### Post by Resurrection on 2007-02-19
Which hard drive is the Vista one?

Is it hdb or sda?

Also can you output the result of 

```
sudo gedit /etc/fstab
```

Edit:  Ptero is right.  I was working you through the way to check how your system is attempting to mount the Vista drive (or if its trying to mount it at all).  But if you have Bitlocker turned on, it won't work.  So here's how to turn it off:

[http://technet2.microsoft.com/WindowsVista/en/library/c61f2a12-8ae6-4957-b031-97b4d762cf311033.mspx?mfr=true]("http://technet2.microsoft.com/WindowsVista/en/library/c61f2a12-8ae6-4957-b031-97b4d762cf311033.mspx?mfr=true")

---

### Post by dvgrhl on 2007-02-19
> **Resurrection said:**
> Which hard drive is the Vista one?

Is it hdb or sda?

Also can you output the result of 

```
sudo gedit /etc/fstab
```

Vista is on the sda one.

Here is that output:

```


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
UUID=52df442b-a9f5-4e0c-9757-2861cc15abbb /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=26AC629AAC626471 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=08F4159CF4158CD6 /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=6670184D701825F9 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=f5b26b21-157c-49fc-9efb-ef2e694d4841 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0



```

Edit:  I didn't realize bitlocker was something that was enabled by default.  I'll turn it off and see if that corrects the issue.  Thanks.

---

### Post by Resurrection on 2007-02-19
Someone else can confirm but fstab looks good to me.  It should mount with the same commands as any other NTFS drive as Vista NTFS is pretty much the same as XP NTFS, just some added features.

---

### Post by dvgrhl on 2007-02-19
I have the Business version of Vista, so I don't think that has Bitlocker with it.  Maybe I am missing something, but Bitlocker seems to be only part of Ultimate.

Ptero-4:  I'll try installing the ntfs-3g thing and see if that fixes it.  Thanks.

---

### Post by taurus on 2007-02-19
I would replace the UUID with the actual partition device like /dev/hda1 (/dev/hdb1 & /dev/sda1) and whatnot in /etc/fstab.

---

### Post by dvgrhl on 2007-02-19
> **taurus said:**
> I would replace the UUID with the actual partition device like /dev/hda1 (/dev/hdb1 & /dev/sda1) and whatnot in /etc/fstab.

This fixed it, thanks!

---

### Post by konohamarusan on 2008-02-05
Hi,
I am very new to ubuntu, and I have the same problem. I did change the UUID to the actual device as taurus said, but It didn't work.

:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+  de  Dell Utility
/dev/sda2              11        1316    10485760    7  HPFS/NTFS
/dev/sda3   *        1316        5518    33751040    7  HPFS/NTFS
/dev/sda4            5519       14593    72894937+   f  W95 Ext'd (LBA)
/dev/sda5            6538       14312    62442496    7  HPFS/NTFS
/dev/sda6            5519        6537     8185054+  83  Linux
/dev/sda7           14313       14593     2257101   82  Linux swap / Solaris

Partition table entries are not in disk order

sudo gedit /etc/fstab


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=8845247a-b1b8-4983-89e1-13600a90cc0a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
/media/sda1=07D7-090B  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
/media/sda2=307A48C07A488496 /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
/media/sda3=D0804D00804CEF12 /media/sda3     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
/dev/sda5=C62252C02252B561 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda7
UUID=bc786a1b-98e9-48be-ba8e-fb4b1a4559b3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0



Please help!!

---

### Post by cdtech on 2008-02-05
```
blkid
```
used to get the disk id for the partitions on the disks. Normally /dev/sda# or /dev/hda# is fine in /etc/fstab. However, Ubuntu prefers using the blkid number, I'm not sure why.

---

