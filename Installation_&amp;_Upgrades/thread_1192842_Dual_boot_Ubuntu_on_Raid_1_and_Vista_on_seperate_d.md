---
title: "Dual boot: Ubuntu on Raid 1 and Vista on seperate drive"
date: 2009-06-20
forum: Installation &amp; Upgrades
---

### Post by dfc106 on 2009-06-20
I'm running 9.04 on a Raid 1 (fake raid) drive.  I want to dual boot Vista on another drive which is not part of the array.  To get Vista to install I had to disconnect my raid drives and disable raid in my bios.  So Vista thinks its installed on the only HD in my system.  After reconnecting all my drive and enabling the array, I can boot back into Ubuntu with no problems.  To enable dual boot I've added the following to my menu.lst:

title Vista
rootnoverify (hd1,0)
makeactive
chainloader +1

This all seems to work, however after Vista starts to load it blue screens and reboots my PC.  I've tried adding:

map (hd0)(hd1)
map (hd1)(hd0)

But then Grub gives me an invalid device string error.
Any way to fix this?

---

### Post by dfc106 on 2009-06-20
I don't care if Windows can see the raid array.  And i don't really care if Ubuntu can see the Windows disk, though it already can.

Maybe this helps:

david@server:~$ cat /boot/grub/menu.lst |grep -e^[^#]
default		0
timeout		5
title		Ubuntu 9.04, kernel 2.6.28-13-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=/dev/mapper/isw_caihjeeidi_Volume01 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-13-generic root=/dev/mapper/isw_caihjeeidi_Volume01 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic
title		Ubuntu 9.04, kernel 2.6.28-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=/dev/mapper/isw_caihjeeidi_Volume01 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.28-11-generic root=/dev/mapper/isw_caihjeeidi_Volume01 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic
title		Ubuntu 9.04, kernel 2.6.27-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=/dev/mapper/isw_caihjeeidi_Volume01 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=/dev/mapper/isw_caihjeeidi_Volume01 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic
title		Ubuntu 9.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
title		Vista
root		(hd1,0)
savedefault
makeactive
map		(hd0)(hd1)
map		(hd1)(hd0)
chainloader	+1


david@server:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001fe71

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       29164   234259798+  83  Linux
/dev/sda2           29165       30400     9928170    5  Extended
/dev/sda5           29165       30400     9928138+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001fe71

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       29164   234259798+  83  Linux
/dev/sdb2           29165       30400     9928170    5  Extended
/dev/sdb5           29165       30400     9928138+  82  Linux swap / Solaris

Disk /dev/sdc: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9e12d6dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       19452   156247040    7  HPFS/NTFS

---

### Post by basementgeek on 2009-11-10
Did you ever find a solution to this problem?  I have a similar issue with Ubuntu in raid1 and Vista on a separate disk.  I haven't tried to play with grub too much, but have tried easybcd, with no success...

---

