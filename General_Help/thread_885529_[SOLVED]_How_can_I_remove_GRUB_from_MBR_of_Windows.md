---
title: "[SOLVED] How can I remove GRUB from MBR of Windows disk?"
date: 2008-08-10
forum: General Help
---

### Post by MaxSommerfeld on 2008-08-10
Hello,

I've tried to install Ubuntu on an external HDD. Because of a GRUB error I have reinstalled GRUB using 
```
sudo grub
find /boot/grubstage1
root (hd1,5)
setup (hd0)
```

(hd1,5) is the partition which I installed Ubuntu to and this was also the output of the find command (as expected).

Windows XP is installed on the internal HDD. When I try to boot from this HDD (without the external HDD plugged in) GRUB is loading and returns ERROR 21. 

It seems to me that I've unintentionally installed GRUB to the MBR of the internal disk (and the ERROR 21 appears due to the fact that GRUB stage2 is on the external and cannot be found).

How can I remove GRUB from the internal's MBR and let it boot into Windows XP by default as it did before?

Thanks in advance for any help you can give me!

-Max

P.S.: The output of fdisk -l (from the live CD, external HDD plugged in):

ubuntu@ubuntu:~$ sudo fdisk -l

Platte /dev/sda: 120.0 GByte, 120034123776 Byte
255 Köpfe, 63 Sektoren/Spuren, 14593 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0xfa26fa26

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1               1         510     4096543+  1b  Verst. W95 FAT32
/dev/sda2   *         511        8962    67890690    7  HPFS/NTFS
/dev/sda3            8963       14593    45231007+   f  W95 Erw. (LBA)
/dev/sda5            8963       14593    45230976    7  HPFS/NTFS

Platte /dev/sdb: 500.1 GByte, 500107862016 Byte
255 Köpfe, 63 Sektoren/Spuren, 60801 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x000eaf9f

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1   *           1       25496   204796588+   7  HPFS/NTFS
/dev/sdb2           25497       60801   283587412+   f  W95 Erw. (LBA)
/dev/sdb5           25497       38244   102398278+   7  HPFS/NTFS
/dev/sdb6           38245       59846   173518033+  83  Linux
/dev/sdb7           59847       60801     7671006   82  Linux Swap / Solaris

---

### Post by Mgiacchetti on 2008-08-10
grab your xp disk and pop it in the cd rom.

Restart your computer and hit whatever key you use to boot from cd.

whilst in the cd install process, hit "R" at some time to enter 'recovery console'

It will now scan and ask you to log in to your windows installation.

At this point (after you have logged in to the installation) enter 'fixmbr'
and press enter.

when thats done, go ahead and restart your pc.

Now you may use NTLDR as your bootloader, go download Bootpart, its made by the same people that make winimage.

Now Whilst in windows:

Make a folder called bootpart in c:\
put bootpart.exe in this folder

now open a command prompt

start > run > cmd

here you're going to want to go cd c:\bootpart

now, type bootpart and hit enter

it is going to show your partition table which should look *something like this*
```

Boot Partition 2.60 for WinNT/2K/XP (c)1995-2005 G. Vollant (info@winimage.com) 
WEB : [http://www.winimage.com]("http://www.winimage.com/") and [http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm) 
Add partition in the Windows NT/2000/XP Multi-boot loader 
Run "c:\bootpart /?" for more information 
 
Physical number of disk 0 : 89108910 
 0 : C:* type=7  (HPFS/NTFS), size= 24781648 KB, Lba Pos=63 
Physical number of disk 1 : b0953c74 
 1 : D:* type=83  (Linux native), size= 8185086 KB, Lba Pos=63 
 2 : D:  type=5  (Extended), size= 11823840 KB, Lba Pos=16370235 
 3 : D:  type=82   (Linux swap), size= 2923798 KB, Lba Pos=16370298 
 4 : D:  type=5   (Extended), size= 8900010 KB, Lba Pos=22217895 
 5 : D:  type=83    (Linux native), size= 8899978 KB, Lba Pos=22217958 
Physical number of disk 2 : 5f68687 
 6 : E:  type=f  (Win95 XInt 13 extended), size= 103193527 KB, Lba Pos=16065 
 7 : E:  type=7   (HPFS/NTFS), size= 34587913 KB, Lba Pos=16128 
 8 : E:  type=5   (Extended), size= 26627737 KB, Lba Pos=69191955 
 9 : E:  type=7    (HPFS/NTFS), size= 26627706 KB, Lba Pos=69192018 
10 : E:  type=5    (Extended), size= 41977845 KB, Lba Pos=122447430 
11 : E:  type=7     (HPFS/NTFS), size= 41977813 KB, Lba Pos=122447493 
12 : E:  type=7  (HPFS/NTFS), size= 20474842 KB, Lba Pos=206403120 
13 : E:  type=7  (HPFS/NTFS), size= 53247442 KB, Lba Pos=247352805 
14 : E:  type=7  (HPFS/NTFS), size= 18434587 KB, Lba Pos=353847690 

```make note of the number of the partition that is your linux native/ubuntu partition (in the above it would be 1) and enter the following:


bootpart X C:\btubuntu.lnx LBA Ubuntu
where X = the partition number from above

Basically what this does, is takes the boot info from x partition and saves it to the file btubuntu.lnx, in LBA mode, and updates your BOOT.INI file to add the line Ubuntu with the path to the file c:\btubuntu.lnx.

Now when you boot, windows asks which os you want to enter, and grub asks which kernel you would like to load.

---

### Post by issih on 2008-08-10
The last line where you typed setup hd0 was the error. That line installed grub into the mbr of the internal windows drive.
Had you put hd1 instead it would be in the mbr of the external one.

The error is indeed as you surmised that grub is looking for the external disc, but its not there.

Use a windows disc or a supergrub disc to repair the mbr of the internal disc so that windows can boot again. After that do as you did before but install grub onto the mbr of the external disc.

Then to boot ubuntu just plug in the external drive and select to boot from it (usually doable from a simple keypress in most modern bioses)

---

### Post by MaxSommerfeld on 2008-08-10
Hi,

thanks a lot for your answers. 
I've solved the issue using the SuperGRUB disk as described here and at many other places in the forum.

I should have done a little more research before posting. Sorry for the unnecessary thread.

Marked as solved.

Again, thank you very much!

-Max

---

