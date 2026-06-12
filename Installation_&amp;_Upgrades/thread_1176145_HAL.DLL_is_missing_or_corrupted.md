---
title: "HAL.DLL is missing or corrupted?"
date: 2009-06-02
forum: Installation &amp; Upgrades
---

### Post by fellixombc on 2009-06-02
I need some help here, after I installed ubuntu, this error kept coming up when I tried running Windows XP. I know that you have to edit boot.ini, but I need help doing so. I don't know my C drive partion is, etc, big, big mess.

Here is my boot.ini file code:
```
[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

c:\wubildr.mbr="Ubuntu"
```

my sudo fdisck -l
```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc933c933

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4865    39078081    c  W95 FAT32 (LBA)

Disk /dev/sdb: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x66236623

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4658    37415353+   7  HPFS/NTFS
/dev/sdb2            4659        4863     1646662+   5  Extended
/dev/sdb5            4659        4863     1646631   82  Linux swap / Solaris

```
My sudo fdisk
```

Usage: fdisk [-l] [-b SSZ] [-u] device
E.g.: fdisk /dev/hda  (for the first IDE disk)
  or: fdisk /dev/sdc  (for the third SCSI disk)
  or: fdisk /dev/eda  (for the first PS/2 ESDI drive)
  or: fdisk /dev/rd/c0d0  or: fdisk /dev/ida/c0d0  (for RAID devices)


```

Please help, and if you do, you are a good man or woman ;)

---

### Post by cak3 on 2009-06-02
You could try just replacing hal.dll if you have an XP disk (see [http://pcsupport.about.com/od/fixtheproblem/ht/restorehaldll.htm](http://pcsupport.about.com/od/fixtheproblem/ht/restorehaldll.htm) ).

If that is the issue, that should fix it. I don't really know anything about editing boot.ini to fix the issue, but since you appear to be using wubi, it might not just be a simple windows problem (which it usually is). I have never used wubi myself, I dual-boot the old fashion way, so I don't know what to tell you.

---

### Post by fellixombc on 2009-06-02
> **cak3 said:**
> You could try just replacing hal.dll if you have an XP disk (see [http://pcsupport.about.com/od/fixtheproblem/ht/restorehaldll.htm](http://pcsupport.about.com/od/fixtheproblem/ht/restorehaldll.htm) ).

If that is the issue, that should fix it. I don't really know anything about editing boot.ini to fix the issue, but since you appear to be using wubi, it might not just be a simple windows problem (which it usually is). I have never used wubi myself, I dual-boot the old fashion way, so I don't know what to tell you.

I was reading up information somewhere, and windows was moved on another partion, and you can easily fix it doing your method (forgot to try) or editing boot.ini to the partion windows is on. I don't know the partion windows is on.

---
I got acsess denied when i tried doing what you did =/

---

### Post by cak3 on 2009-06-02
I came across this [http://shanegfowler.wordpress.com/2007/01/10/missing-haldll-error-corrupt-bootini-file-quick-fix/](http://shanegfowler.wordpress.com/2007/01/10/missing-haldll-error-corrupt-bootini-file-quick-fix/)

Looks like it has instructions for both the method I suggested above and the boot.ini method. See if that works.

---

