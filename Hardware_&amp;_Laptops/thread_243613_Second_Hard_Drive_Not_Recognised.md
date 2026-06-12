---
title: "Second Hard Drive Not Recognised"
date: 2006-08-25
forum: Hardware &amp; Laptops
---

### Post by suilven222 on 2006-08-25
Hi,
I've just installed ubuntu 6.06 on my computer. It is a dual boot system with Windows XP, both OS's are on a single SATA drive. Its working great, except I have a second drive (IDE) which ubuntu is not recognising at all. Windows sees it fine. If i type fdisk -l it only lists my sata drive:

    neil@neil-desktop:~$ for i in /dev/[hs]d[a-z]; do sudo fdisk -l $i; done
    Password:

    Disk /dev/sda: 163.9 GB, 163928604672 bytes
    255 heads, 63 sectors/track, 19929 cylinders
    Units = cylinders of 16065 * 512 = 8225280 bytes

    Device Boot Start End Blocks Id System
    /dev/sda1 * 1 17389 139677111 7 HPFS/NTFS
    /dev/sda2 17390 17402 104422+ 83 Linux
    /dev/sda3 17403 19674 18249728+ 83 Linux
    /dev/sda4 19675 19929 2048287+ 82 Linux swap / Solaris

Can anyone tell me why ubuntu doesn't recognise the IDE drive? It is formatted as NTFS at the moment, I have also tried FAT32 and leaving it unallocated but it made no difference. The /etc/fstab file has no reference to the drive since I cannot identify its device name so cannot add it!

I couldn't see anything on other forums on this problem. Thanks in advance.

Neil

---

