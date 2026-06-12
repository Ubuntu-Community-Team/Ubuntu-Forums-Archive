---
title: "Windows Raid0 , Ubuntu seperate disk"
date: 2009-09-20
forum: Installation &amp; Upgrades
---

### Post by encinoman on 2009-09-20
I installed Vista on a RAID0 array of two 320Gb disks. I then installed Ubuntu on a separate 160 Gb hard drive. Right now, GRUB will only let me boot into Ubuntu.  I understand all the problems with linux and hard/soft RAIDs but can't figure out how to get GRUB to boot into windows OR Ubuntu. I really never fooled around with grub so I am a little bit of a beginner here. Here is my Fdisk and grub file, thanks:

Fdisk:---------------------------------

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3be1172f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   471042047   235520000    7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0e85cb4c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   307098539   153549238+  83  Linux
/dev/sdc2       307098540   320159384     6530422+   5  Extended
/dev/sdc5       307098603   320159384     6530391   82  Linux swap / Solaris

grub : /boot/grub/menu.lst

title           Ubuntu 9.04, kernel 2.6.28-15-generic
uuid            9c3fd79b-d34d-4bf3-83f5-3f58eb19c022
kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=9c3fd79b-d34d-4bf3-83f5-3f58eb19c022 ro quiet splash
initrd          /boot/initrd.img-2.6.28-15-generic
quiet

title           Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid            9c3fd79b-d34d-4bf3-83f5-3f58eb19c022
kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=9c3fd79b-d34d-4bf3-83f5-3f58eb19c022 ro  single
initrd          /boot/initrd.img-2.6.28-15-generic

title           Ubuntu 9.04, kernel 2.6.28-11-generic
uuid            9c3fd79b-d34d-4bf3-83f5-3f58eb19c022
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=9c3fd79b-d34d-4bf3-83f5-3f58eb19c022 ro quiet splash
initrd          /boot/initrd.img-2.6.28-11-generic
quiet

title           Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid            9c3fd79b-d34d-4bf3-83f5-3f58eb19c022
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=9c3fd79b-d34d-4bf3-83f5-3f58eb19c022 ro  single
initrd          /boot/initrd.img-2.6.28-11-generic

---

