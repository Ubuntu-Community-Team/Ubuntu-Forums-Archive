---
title: "Dual-booting not working! PLEASE help!"
date: 2009-06-15
forum: Installation &amp; Upgrades
---

### Post by Dark-Star on 2009-06-15
I am at my wit's end trying to rebuild my old machine. Some time ago my IDE drive sprouted a bad spot and windoze XP refused to boot. Just recently I got a new SATA drive from a friend, reformatted/repartitioned it and tried rebuilding. 

Ubuntu, of course, installed without a fuss. XP sees the two NTFS partitions and installs just dandy...but when I reloaded the GRUB bootloader (which XP knocked out) I cannot. readd. Windows. for the life of me. 

A SS of my SATA drive:

[IMG]http://www.fileden.com/files/2009/5/9/2435913/Screenshot--dev-sda%20-%20GParted.png[/IMG]



[IMG]file:///tmp/moz-screenshot.jpg[/IMG]

---

### Post by lindsay7 on 2009-06-16
Looks like you need to set sda5 a boot flag which you can do with Gparted and you may need to make some changes in the grub menu.

Post the output of 
 Sudo fdisk -l  that is the letter l

and also the output of 

sudo gedit /boot/grub/menu.lst again this is the letter l in lst

---

### Post by Dark-Star on 2009-06-16
Righty-oh!

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           4       32098+   6  FAT16
/dev/sda2               5       38913   312536542+   f  W95 Ext'd (LBA)
/dev/sda5               5        9735    78164226    7  HPFS/NTFS
/dev/sda6            9736       26148   131837391    7  HPFS/NTFS
/dev/sda7           26149       28580    19535008+  83  Linux
/dev/sda8           28581       28945     2931831   82  Linux swap / Solaris
/dev/sda9           28946       38913    80067928+   b  W95 FAT32

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2cf22cf2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       10199    81923436    7  HPFS/NTFS
/dev/sdb2           10200       26134   127997887+   7  HPFS/NTFS
/dev/sdb3           26135       38913   102647317+   7  HPFS/NTFS

The last 3 are my old busted drive, FYI.

----


title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        f547d156-0194-4e65-bcb4-4d0ab1b10ffe
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f547d156-0194-4e65-bcb4-4d0ab1b10ffe ro splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        f547d156-0194-4e65-bcb4-4d0ab1b10ffe
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=f547d156-0194-4e65-bcb4-4d0ab1b10ffe ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        f547d156-0194-4e65-bcb4-4d0ab1b10ffe
kernel        /boot/memtest86+.bin
quiet

title        MS Windows XP
root (hd0,4) 
savedefault
makeactive
chainloader +1 

^my pitiful attempt at getting MS booting.

---

### Post by merlinus on 2009-06-16
If windows is on sda5, then set a boot flag on it.  menu.lst entry for windows is correct if sda5, but a problem may be that most often windows wants to be on a primary, not logical, partition.

---

### Post by Dark-Star on 2009-06-16
Oog. Can I delete the partitions and move the free space to a primary partition with gparted...WITHOUT wrecking my very customized Ubuntu install?

---

### Post by brncao on 2009-06-16
yep. just make sure you don't accidently format it.

---

### Post by lindsay7 on 2009-06-16
When you get done and reinstall windows on your new partition. You may have to set the grub menu up again. Type these commands in the terminal if you can not boot into Ubuntu after windows is installed.

sudo grub
find /boot/grub/stage1
(it will give a (hdx,y)
root (hdx,y)
setup (hdx)
quit

---

### Post by Dark-Star on 2009-06-16
Okay...sorry to be a pest but one last question - how do I move the free space as mentioned before? I tried several times but only made a big mess of things, thankfully changes aren't applied right away...

---

### Post by lindsay7 on 2009-06-16
I am not sure what you are asking, First delete the partitions you do not want.  Leave them all unallocated, then make a new primary partition for your windows system. You want the windows partition to be first on the drive.  You could grow the first fat32 partiton which is small to take on this space.

There are little arrows on each side of the partition and you can change the size and you can move the partitions around clicking on it and holding it.

If you go to the web site for Gparted you can find a very good tutorial on how to do everything that this program offers.

---

