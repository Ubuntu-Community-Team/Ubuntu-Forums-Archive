---
title: "Can't have a partition outside the disk!"
date: 2010-02-21
forum: Hardware
---

### Post by Fixman on 2010-02-21
Each time I open gParted, this message appears:
```
martin@Laptop:~$ gksu gparted
======================
libparted : 1.8.8.1.159-1e0e
======================
Can't have a partition outside the disk!
```

And gParted shows my hard drive totally unallocated. This is my fdisk -l:

```
martin@Laptop:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05b8ef9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19099   153412684   83  Linux
/dev/sda2   *       19100       27363    66380580    7  HPFS/NTFS
/dev/sda3           27364       30402    24410767+   f  W95 Ext'd (LBA)
/dev/sda5           27364       29275    15358076   83  Linux
/dev/sda6           29276       30401     9044552   82  Linux swap / Solaris

```

---

### Post by falconindy on 2010-02-22
> **Fixman said:**
> ```
martin@Laptop:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, **30401** cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05b8ef9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19099   153412684   83  Linux
/dev/sda2   *       19100       27363    66380580    7  HPFS/NTFS
/dev/sda3           27364       **30402**    24410767+   f  W95 Ext'd (LBA)
/dev/sda5           27364       29275    15358076   83  Linux
/dev/sda6           29276       30401     9044552   82  Linux swap / Solaris

```
That doesn't seem right... I don't have an extended partition nearby to confirm though...

---

### Post by Fixman on 2010-02-23
Any actual help?

---

### Post by Fixman on 2010-02-24
Help!

---

### Post by SecretCode on 2010-02-24
The bit that falconindy highlighted is almost certainly the problem. I have a disk which is also 30401 cylinders, and the extended partition ends at 30401. 
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x656d4f17

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3264    26218048+   7  HPFS/NTFS
/dev/sda2            3265       30401   217977952+   f  W95 Ext'd (LBA)
/dev/sda5            3265        6249    23976981   83  Linux
/dev/sda6            6529        9792    26218048+   7  HPFS/NTFS
/dev/sda7            9793       17625    62918541    7  HPFS/NTFS
/dev/sda8           17626       30401   102623188+   7  HPFS/NTFS
/dev/sda9            6250        6528     2241036   82  Linux swap / Solaris
```

The last logical partition also ends at 30401, and so does yours, so it *may* just be a matter of editing the MBR partition table, changing one byte. Unfortunately I need to go offline now but I could help with this tomorrow...

---

### Post by Fixman on 2010-02-26
I don't need the Windows partition anymore, will the problem be solved if I delete it? Since I can't use Parted, what other tool do you recommend?

---

### Post by dabl on 2010-02-26
> **Fixman said:**
> 

 Since I can't use Parted, what other tool do you recommend?


It's still Parted, but I really like the Parted Magic Live CD, from here:

[http://partedmagic.com/download.html](http://partedmagic.com/download.html)

There's also Hiren's from here:  [http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

If you were in position to "start all over" with that hard drive, you could "dd" it and start with a new partition table, as per:  [http://ubuntuforums.org/showthread.php?p=8882137](http://ubuntuforums.org/showthread.php?p=8882137)

---

### Post by SecretCode on 2010-02-27
I think regular partitioning tools are likely to object because the current partitioning is inconsistent. Bare-metal editing of the MBR would be my recommendation! - Yes, done this before. 

First back up your MBR. Run this from a live CD, and attach a USB stick to save to.
```
sudo dd if=/dev/sda of=/media/usbstick/backup-mbr bs=1 skip=0 count=512
```
Note _if_ is /dev/sda, the raw hard drive. Change _of_ to point to your actual USB stick or other location, but don't change anything else in the command!

Make a copy of the partition table (64 bytes within the MBR):
```
sudo dd if=/dev/sda of=/media/usbstick/backup-pt bs=1 skip=446 count=64
```

Post here the output of 
```
hexdump -C /media/usbstick/backup-pt
```
substituting whatever filename you used above.

---

### Post by ahui132 on 2010-11-07
```
[ahui@ahui-host ~]$ hexdump -C backup-pt 
00000000  80 01 01 00 0c ef ff ff  3f 00 00 00 01 78 19 01  |........?....x..|
00000010  00 fe ff ff 0f fe ff ff  7d 78 19 01 83 97 4f 0e  |........}x....O.|
00000020  00 ef ff ff 06 ef ff ff  c0 30 69 0f 50 56 38 03  |.........0i.PV8.|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  55 aa                                             |U.|
00000042

[ahui@ahui-host ~]$ sudo fdisk /dev/sda
Warning: extra link pointer in partition table 18

Unable to seek on /dev/sda
[ahui@ahui-host ~]$ sudo parted /dev/sda print
Error: Can't have a partition outside the disk!  

```
my god!what should I do??:confused:
it's the hateful diskpart under the XP,which do not support my Ext4 partition and delete my  incorrectly&#65281;
Any help will be appreciated!

---

### Post by srs5694 on 2010-11-07
Please post the output of the following command:

```

sudo fdisk -lu /dev/sda

```

---

