---
title: "hdparm fun."
date: 2008-11-22
forum: Hardware
---

### Post by kooldino on 2008-11-22
So I was following a guide for hdparm to attempt to speed up my hard disks:

[http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html?page=1](http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html?page=1)

However, when I run the commands, I get the following errors:

```
dino@nebula:~$ sudo hdparm /dev/sda1

/dev/sda1:
 IO_support    =  0 (default)
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 60801/255/63, sectors = 976768002, start = 63
dino@nebula:~$
```

I have a few disks in this machine, some of which are SATA and some of which are IDE.  The hardware in this box is about 6 months old.

Here's an output of fdisk -l:

```
dino@nebula:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000c5b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdb: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcd13cd13

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        8659    69553386   83  Linux
/dev/sdb3            8660        9039     3052350   82  Linux swap / Solaris

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
86 heads, 15 sectors/track, 302885 cylinders
Units = cylinders of 1290 * 512 = 660480 bytes
Disk identifier: 0x0006bdd0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              45      293498   189277830    f  W95 Ext'd (LBA)
/dev/sdc5   *          45      293498   189277822+  83  Linux

Disk /dev/sde: 1015 MB, 1015808000 bytes
5 heads, 4 sectors/track, 99200 cylinders
Units = cylinders of 20 * 512 = 10240 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1              13       99200      991875+   6  FAT16

Disk /dev/sdh: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0d109f1b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1   *           1       60801   488384001    7  HPFS/NTFS
dino@nebula:~$                                                      
```

Can anyone help?

---

### Post by kzutter on 2008-11-22
I think hdparm works with disks, not partitions.

try
```
sudo hdparm /dev/sda
```

---

### Post by sdennie on 2008-11-22
Not all drives support all functions of hdparm.  In fact, most SATA drives won't support most of the tweaks you can find in hdparm because they are either permanently enabled or don't make any sense for a SATA drive.

---

### Post by kooldino on 2008-11-23
> **kzutter said:**
> I think hdparm works with disks, not partitions.

try
```
sudo hdparm /dev/sda
```

Same error.

---

### Post by kooldino on 2008-11-23
> **vor said:**
> Not all drives support all functions of hdparm.  In fact, most SATA drives won't support most of the tweaks you can find in hdparm because they are either permanently enabled or don't make any sense for a SATA drive.

Hmmm, so they're already "natively tweaked"?

---

