---
title: "Very Important data lost Please help"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by naqvisat on 2009-10-27
Hi Dear Friends
I had initially installed xp then I wanted to install ubuntu 9.04 while installation I selected side by side. I selected to install ubuntu in C where already there was xp. now the problem is that for drive D the file system was ntfs but while installation I selected EXT3. so what it did is that it formatted my drive and I can not see any single file which I had in C or D drive. even windows xp has also deleted I don't know how... but the point is that I want to recover my D drive data please help me what to do... it is very urgent.

thanks

---

### Post by fancypiper on 2009-10-27
Sorry, I am afraid that you have erased it and it's gone forever.

---

### Post by howefield on 2009-10-27
> **fancypiper said:**
> Sorry, I am afraid that you have erased it and it's gone forever.

Possibly, maybe even likely. But it is worth checking first before bringing in the doom and gloom merchants.

> **naqvisat said:**
> please help me what to do... it is very urgent.

Can you open a terminal (Applications > Accessories > Terminal) and post the output of

```
fdisk -l
```

If you have over written your files, it may be possible to recover some of the data.

---

### Post by ShapeShiftme on 2009-10-27
How mean to make it sound worse than it is.
Data is 95 % of the time recoverable. The main problems are how to do it/ how long will it take and 3rd would be / how much will it cost.

Your main problem is that you formated over NTFS with EXT. so that makes things harded my first step as a sugestion is for you to install testdisk. use a software manager.

Then from console run

testdisk /dev/sda 

Cinsidering testdisk /dev/sda is the hard drive in question. The scan the disk for files.
It is a awsome program but it take s a LONG LONG time. But hopefully that will help
Regards

---

### Post by fancypiper on 2009-10-27
> **ShapeShiftme said:**
> How mean to make it sound worse than it is.
Data is 95 % of the time recoverable.:redface:
I didn't intend to sound mean, but I did something similar in 1999 and tried everything I could find in forums and suggestions in user mailing lists.  I had lost it all.

I hope he isn't one of the 5 percent club.:)

---

### Post by naqvisat on 2009-10-27
fdisk -l did not show any output not even any message.

when i tried testdisk /dev/sda it showed
unable to open the file/device /dev/sda
I also tried for sda1 and sda2 but it did not work... please any other way???
I will be very thankful

---

### Post by alphaniner on 2009-10-27
You need to use sudo with those commands:

```
sudo fdisk -l
```

```
sudo testdisk /dev/sda
```

---

### Post by naqvisat on 2009-10-27
Hi thank you all and the result of sudo fdisk -l is as follows[]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=5")
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x77777777

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       14593    86501992+   f  W95 Ext'd (LBA)
/dev/sda5            3825       14267    83883366   83  Linux
/dev/sda6           14268       14571     2441848+  83  Linux

---

### Post by fancypiper on 2009-10-27
Great! there is still hope, I think, at least for your C drive.

Try mounting the filesystem and see if you can see anything.

sudo mkdir /mnt/win
sudo mount /dev/sda1 /mnt/win
sudo ls/mnt/win

---

### Post by naqvisat on 2009-10-27
thank you and also please mention how to mount the file system as i am not an expert in ubuntu.

thank you very much

---

### Post by fancypiper on 2009-10-27
Basically, create a mount directory
Mount the device on the mount directory
list the files in the directory

In a terminal, paste these commands:
sudo mkdir /mnt/win
sudo mount /dev/sda1 /mnt/win
sudo ls /mnt/win

---

### Post by naqvisat on 2009-10-27
Hi there is no results founds like this
fuse: failed to access mountpoint /mnt/win: No such file or directory

---

### Post by naqvisat on 2009-10-27
Hi
I think instead of midir it should be mkdir???  for make directory the very first command.
Am i right or wrong?

---

### Post by fancypiper on 2009-10-27
You're right.  I am a lousy typist!

---

