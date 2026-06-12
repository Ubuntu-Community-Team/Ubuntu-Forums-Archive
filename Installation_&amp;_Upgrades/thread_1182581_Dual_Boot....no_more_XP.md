---
title: "Dual Boot....no more XP"
date: 2009-06-09
forum: Installation &amp; Upgrades
---

### Post by JoeShmo397 on 2009-06-09
Ok, so my plan was to install Xubuntu on my laptop (which already runs XP).  After partitioning, everything seemed fine and XP still booted no problem.  However, after installing Xubuntu (which I had to do a few times to get all of the settings right, and they're still not all the way right) XP no longer boots.  If you look at the partition on GParted, it's unreadable.  And in the grub menu on startup, you can click on XP but nothing happens.  Does anyone know a way to fix it?  Or at least know what I did wrong? (I'm hoping there's a solution that doesnt require me to have my XP disc)....thanks in advance

---

### Post by woozly on 2009-06-09
Hi,
check if winXP partition exist anymore
 
1. 
 
Check which harddrive type is in use (hda?,sda?)
#cat /prog/partitions
```
 
debtb15:~# cat /proc/partitions
 
major minor #blocks name
8 0 8388608 sda
8 1 2433816 sda1
8 2 1 sda2
8 5 329301 sda5
8 6 5622718 sda6
debtb15:~#
 

```
--> Source SDA. First SATA drive | secound will be SDB
________________________________
 
2. 
 
Check if winXP exist
```
#fdisk -l /dev/sda
```
 
On my system there is no windows partition ... 
On your system there must be a NTFS partition...
 
```
 
debtb15:~# fdisk -l /dev/sda
Disk /dev/sda: 8589 MB, 8589934592 bytes
255 heads, 63 sectors/track, 1044 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b0e22
Device Boot Start End Blocks Id System
/dev/sda1 * 1 303 2433816 83 Linux
/dev/sda2 304 1044 5952082+ 5 Extended
/dev/sda5 304 344 329301 82 Linux swap / Solaris
/dev/sda6 345 1044 5622718+ 83 Linux
debtb15:~#

```
____________________________________________
 
Get SDA[ID] like /dev/sda3 ---> NTFS...
 
3.
 
open grub config
```
 
vi /boot/grub/menu.list

``` 
GO to windows section.
Check if the (hd0,-->0<--) is the right id linke /dev/sda3 NTFS = (hd0,2)
 
NOTE: (hd0) was mapped from grub.. You can see grub mapping in 
/boot/grub/device.list
 
_____________________________________________
 
4.
Windows section in menu.list example
```
 
title Windows XP
root (hd0,2)
makeactive
chainloader +1
 

```
 
ps. Post you device.list and your fdisk -l /dev/hda (ATA Harddisk ).. oder /dev/sda (SCSI or SATA hard disk )....
 
chears
woo

---

### Post by JoeShmo397 on 2009-06-09
major minor  #blocks  name

   8        0   96213285 sda
   8        1   20988891 sda1
   8        2    8193150 sda2
   8        3    4096575 sda3
   8        4   62934637 sda4




Disk /dev/sda: 98.5 GB, 98522403840 bytes
255 heads, 63 sectors/track, 11978 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2613    20988891    7  HPFS/NTFS
/dev/sda2            2614        3633     8193150   83  Linux
/dev/sda3            3634        4143     4096575   82  Linux swap / Solaris
/dev/sda4            4144       11978    62934637+   b  W95 FAT32





title           Ubuntu 9.04, kernel 2.6.28-11-generic
uuid            80ae7213-0266-466c-bb29-ce22af333a9a
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=$
initrd          /boot/initrd.img-2.6.28-11-generic
quiet


title           Ubuntu 9.04, kernel 2.6.28-11-generic (rec$
uuid            80ae7213-0266-466c-bb29-ce22af333a9a
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=$
initrd          /boot/initrd.img-2.6.28-11-generic
title           Ubuntu 9.04, memtest86+
uuid            80ae7213-0266-466c-bb29-ce22af333a9a
kernel          /boot/memtest86+.bin
quiet



### END DEBIAN AUTOMAGIC KERNELS LIST

title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1


As far as I know, the partition is still there.  I do know that when I view the partitions in GParted, the NTFS/Windows partition has a triangle with an exclamation mark in it.  I am thinking that this is because the mbr is messed and something can't be read or loaded, but I am a complete newb and have no idea whats really going on here.

Thanks for your help.

---

### Post by dannybuntu on 2009-06-09
Sounds like a corrupted partition... So sorry man..

---

### Post by JoeShmo397 on 2009-06-09
That's what I feared.  Well, I have my re-install XP discs at school (im home from college for the summer), with that I can just reformat the hard drive and run XP like I always used to right?  Then I can try this again.  In the meantime is there a way for me to take over my entire hard drive with ubuntu?  (Or does a corrupted partition mean that my entire hard disc is f*^%ed?? ....  sorry, I'm that guy who doesnt know how too much about computers but isnt afraid to try things to learn along the way

---

### Post by dstew on 2009-06-09
I don't think the Windows system is necessarily gone altogether. It may just be that the boot loader for Windows is not working. Maybe there are disk errors that can be repaired.

The triangle with the exclamation point means that Gparted detected the "Bad Sectors" flag on the partition. NTFS can label bad sectors, isolate them, and the file system can still be useable. Gparted won't touch it though.

If your Windows CD has the ability to boot a "[Recovery Console]("http://support.microsoft.com/kb/314058")", you can run the chkdsk program on the NTFS with the **chkdsk c: /r** command. The boot sector code can be repaired with the **fixboot c:** command. The grub chainload command tries to load the boot sector code, which will then boot windows. If it is gone, the Windows menu item will not work.

Note the **fixmbr** command will remove grub from the master boot record, and replace it with the Windows boot loader. You can try it if you want to do everything to boot Windows, but then you will need to re-install grub later if you want to boot Ubuntu.

---

### Post by Pumalite on 2009-06-09
Try this and see:

title Microsoft Windows XP Professional
root (hd0,0)
makeactive
chainloader +1

---

### Post by woozly on 2009-06-10
Try to use windows install cd to reinstall the windows boorloarder.
Start rescue console and use bootsec --help
 
chears woo

---

