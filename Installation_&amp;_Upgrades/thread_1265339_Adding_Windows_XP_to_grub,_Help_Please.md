---
title: "Adding Windows XP to grub, Help Please"
date: 2009-09-13
forum: Installation &amp; Upgrades
---

### Post by yusuo85 on 2009-09-13
IM having a bit of trouble adding windows xp to my grub loader, I tried manually and it said error on it, can someone help me with this

**_FDISK_**

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38913   312568641   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb753b753

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3283    26370666   83  Linux
/dev/sdb2            3284       30401   217825335    5  Extended
/dev/sdb5            3284        3407      995998+  82  Linux swap / Solaris
/dev/sdb6            3408       30401   216829273+  83  Linux

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x255a85bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9728    78140128+   7  HPFS/NTFS


_**GRUB**_

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		ce38dd8e-b495-4c63-8120-e7f767e22d1c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=ce38dd8e-b495-4c63-8120-e7f767e22d1c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		ce38dd8e-b495-4c63-8120-e7f767e22d1c
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=ce38dd8e-b495-4c63-8120-e7f767e22d1c ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		ce38dd8e-b495-4c63-8120-e7f767e22d1c
kernel		/boot/memtest86+.bin
quiet

title Windows XP
rootnoverify (hd1,0)
makeactive
chainloader +1


Any help appreciated

---

### Post by danielsonl on 2009-09-13
so I'm new to this but was having similar problems trying to set up dual-boot (Mint & XP) on two separate HDDs. I did not want to mess up my XP HDD with partitions with Grub or various bootloader complications so I set up my master HDD with Grub/Linux, slave drive with XP, and entered the following into the GRUB boot menu :

___________________________________
title		Windows XP 
map		(hd0) (hd1)
map		(hd1) (hd0)
rootnoverify	(hd1,0)
makeactive
chainloader	+1
____________________________

I had tried tons of options and that's the one that worked for me - hope it helps!

---

### Post by yusuo85 on 2009-09-13
thanks for your help had to change the numbers as I have 3 hard drives but done the job

---

