---
title: "GRUB is confusing"
date: 2005-08-12
forum: Hardware &amp; Laptops
---

### Post by HJB on 2005-08-12
Hi all. I have this problem with GRUB, please help.
How do I know which hard drives in GRUB's reference, refers to which ones when using fdisk -l
This sounds stupid I know, BUT the other night (using Breezy) I typed fdisk -l and it listed my SATA drive firstly:
>    Disk **/dev/sda**: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23943   192322116   83  Linux
/dev/sda2           23944       24321     3036285    5  Extended
/dev/sda5           23944       24321     3036253+  82  Linux swap / Solaris

Disk** /dev/hda**: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        3824    30716248+  17  Hidden HPFS/NTFS
/dev/hda2   *        3825        9903    48829567+  83  Linux
/dev/hda3            9904       10876     7815622+  82  Linux swap / Solaris
/dev/hda4           10877       14593    29856802+   c  W95 FAT32 (LBA)

Disk **/dev/hdb**: 30.7 GB, 30758289408 bytes
255 heads, 63 sectors/track, 3739 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3738    30025453+   c  W95 FAT32 (LBA)

just now(_ after an breezy kernel update_) it showed:
> Disk **/dev/hda**: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        3824    30716248+  17  Hidden HPFS/NTFS
/dev/hda2   *        3825        9903    48829567+  83  Linux
/dev/hda3            9904       10876     7815622+  82  Linux swap / Solaris
/dev/hda4           10877       14593    29856802+   c  W95 FAT32 (LBA)

Disk **/dev/hdb**: 30.7 GB, 30758289408 bytes
255 heads, 63 sectors/track, 3739 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3738    30025453+   c  W95 FAT32 (LBA)

Disk **/dev/sda**: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23943   192322116   83  Linux
/dev/sda2           23944       24321     3036285    5  Extended
/dev/sda5           23944       24321     3036253+  82  Linux swap / Solaris

I initially assumed that sda1 = hd(0,0) and hdb1 = hd(2,0) and configured GRUB accordingly. 


I then created a dual boot setup and referenced hd(2,0) as my XP boot partition.
Everything went well. I then upgraded breezy and GRUB was rewritten (my XP option erased)
> 
## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-6-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-6-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-6-386
savedefault
boot

 and fdisk shows like above?

How do I know which hd(X,Y) is equal to what in fdisk -l?
Whay does GRUB say hd(0,0) = sda but fdisk says its hd(2,x)
Does this make sense?
I now looks (to the n00b) that hda = hd(0,x) and sda = hd(2,x)

I first want to figure this out before trying the dual boot thingy again.


Please help!

---

### Post by amohanty on 2005-08-12
This might help:
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

Edit: sorry meant this:
[http://www.gnu.org/software/grub/manual/grub.html#Loading-an-operating-system-directly](http://www.gnu.org/software/grub/manual/grub.html#Loading-an-operating-system-directly)

---

