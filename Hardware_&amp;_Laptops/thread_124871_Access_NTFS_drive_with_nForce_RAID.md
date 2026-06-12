---
title: "Access NTFS drive with nForce RAID"
date: 2006-02-02
forum: Hardware &amp; Laptops
---

### Post by bousquf on 2006-02-02
Hello,

I was using Windows XP and switched to Ubuntu Linux 5.10 x64.

Everything is working fine (nVidia graphic and nForce drivers are installed), except that I am not able to access my data hard drive (160 GB S-ATA) formatted in NTFS. fdisk is displaying a SFS file system format ? Secure File System ?

I think that it may be related to nForce RAID driver that was installed on my old XP installation where, at a time, I played with RAID configs. However, the drive was not in a RAID configuration.

To test, I installed XP aside Linux and I needed to install nForce drivers to see that hard disk.

Now how can I access data under Linux?



root@copernic:~# fdisk -l

Disk /dev/sda: 164.6 GB, 164696555520 bytes
16 heads, 63 sectors/track, 319120 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

Device Boot Start End Blocks Id System
/dev/sda1 1 319120 160836448+ 42 SFS

Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 4314 34652173+ 83 Linux
/dev/sdb2 4315 4500 1494045 5 Extended
/dev/sdb5 4315 4500 1494013+ 82 Linux swap / Solaris
root@copernic:~# ls -l /dev/sda1
ls: /dev/sda1: No such file or directory
root@copernic:~# ls -l /dev/sda1
ls: /dev/sda1: No such file or directory
root@copernic:~# mount -t ntfs -o ro /dev/sda1 /a
mount: special device /dev/sda1 does not exist
root@copernic:~# uname -a
Linux copernic 2.6.12-10-amd64-generic #1 Mon Jan 16 17:16:24 UTC 2006 x86_64 GNU/Linux
root@copernic:~#

---

### Post by madmetal on 2006-02-02
you can read files from a NTFS hdd but not write (but still may face problems)
so try to make a FAT32 partition to have your files there and access to them from both winxp and ubuntu.

---

### Post by bousquf on 2006-02-02
Euh...  I know that, the problem is that I can't even access the partition, /dev/sda1 doesnt exists !

---

