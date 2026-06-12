---
title: "lacie edmini hard disk"
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by SKOGGERS on 2009-05-17
Hi a newbie to ubuntu but i was told it may help me solve a problem so i thought i would give it a go and to be honest i am currently impressed

heres my problem

i have a lacie 300 gig ethernet edmini external hard disk that has failed. the hard disk is fine and i would like to retrieve my backup data off the drive if possible. I am under the impression that a linux install is the only was to see the contents of the drive and retrieve the data onto another hard disk. Is it possible. i have dont a ubuntu install witht the drive attached 

below is a copy of the terminal window showing how the drives are connected

skoggers@KOONSKAU-PC:~$ sudo fdisk -l

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4d4d4445

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          31      248976    5  Extended
/dev/sda2              32          48      136552+   c  W95 FAT32 (LBA)
/dev/sda3              49       36482   292650624    c  W95 FAT32 (LBA)
/dev/sda5               1          16      128457   82  Linux swap / Solaris
/dev/sda6              17          17        8001   83  Linux
/dev/sda7              18          30      104391   83  Linux
/dev/sda8              31          31        8001   83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x555e7b7d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9327    74919096   83  Linux
/dev/sdb2            9328        9729     3229065    5  Extended
/dev/sdb5            9328        9729     3229033+  82  Linux swap / Solaris

the information i want is on sda3 can someone please tell me if / how i can retrieve it

thanks in advance

---

### Post by Mark Phelps on 2009-05-17
I'm presuming that you're running from a liveCD since you say you don't have an Ubuntu install with the drives attached, so the simplest way is to do the following:
1) plugin an external drive.  Should get a desktop icon showing the drive, and a Nautilus file window as well.
2) Go into Places on the top menu, and under Removable Media, click the drive you want to read.  You may have to experiment to find the correct drive.
3) Copy the files and folders from the mounted drive to the external drive.
4) When done, close the Nautilus windows, right-click on each of the drive icons on the desktop, and select Unmount Volume.

---

### Post by SKOGGERS on 2009-05-18
hi

im not running from a live cd i have installed ubuntu on the 80 gig hard disk shown above. i then connected the drive i have taken out of the lacie edmini ethernet disk. i can not see the attached drive moutned anywhere to copy the files from

the information i want to keep i would think is on one of the two fat32 partitions SDA2 or more likely SDA3. all 8 are from the one 300 gig drive i connected

i  tried this in terminal window

sudo mount -t vfat -o umask=000 /dev/sda3 /osshare

this is what happens when i do 

wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or s


i cant get ubuntu to mount the drive so that i can take the information off it

hope this helps you help me :-)

---

