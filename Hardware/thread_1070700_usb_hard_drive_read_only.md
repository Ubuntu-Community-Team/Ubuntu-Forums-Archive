---
title: "usb hard drive read only"
date: 2009-02-15
forum: Hardware
---

### Post by Yvon on 2009-02-15
I have a USB external hard drive(Iomega) that I formated in fat 32 witn my Mac in leopard. 
I want to use it with my xbox360, my mac and my linux box. 
I can see it with linux Ubuntu 8.04 but I can't write on it. 
I've been looking here and on google but I can't find anything. 
Any help is apreciated. 


Thank you

---

### Post by HunkirDowne on 2009-02-15
> **Yvon said:**
> I have a USB external hard drive(Iomega) that I formated in fat 32 witn my Mac in leopard. 
I want to use it with my xbox360, my mac and my linux box. 
I can see it with linux Ubuntu 8.04 but I can't write on it. 
I've been looking here and on google but I can't find anything. 
Any help is apreciated. 


Thank you

What does 'sudo fdisk -l' report?

Let's assume that it tells you that you have a 250 GB external hdd with one primary partition formatted 'vfat' but you have a bunch of hdds so this one gets 'x' as in /dev/sdx1.

First, make sure you have a place to mount it and let's assume for a moment that you don't, so from the command line:

sudo mkdir /media/iomega250

Now you want to mount it, again, from the command line:

sudo mount -t vfat /dev/sdx1 /media/iomega250 -o rw

That should pretty much do it unless you want to add it to 'fstab'.  I'm not going to put you through the pain of editing 'fstab' because it shouldn't be painful but I did something that I neither understand nor remember (but I recovered) so I'm not going to make the same mistake on your 'fstab'.  ;-)

(If I recall, I put some stuff out of order and it locked up Xorg <ruh-roh>)

---

### Post by Yvon on 2009-02-15
this is what I got:

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2               9        1967    15728640    7  HPFS/NTFS
/dev/sda3   *        1967       17272   122937344    7  HPFS/NTFS
/dev/sda4           17273       77826   486393094    f  W95 Ext'd (LBA)
/dev/sda5           21096       77826   455677952    7  HPFS/NTFS
/dev/sda6           17273       21095    30708184+  83  Linux

Partition table entries are not in disk order

WARNING: GPT (GUID Partition Table) detected on '/dev/sdf'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1      121602   976762583+  ee  GPT


My usb hard drive seem to be this one::
Disk /dev/sdf


My main problem is that I have windows 7 on this computer but I use linux most of the time. I have a macbook with osx and I also have an Xbox 360, I want my hard drive to be compatible with all of them... 

So far it's not a succes! 
Windows 7 can't see it all. 
Only my mac so far can read and write on it! 

The Xbox see it also.

---

### Post by tommcd on 2009-02-16
> **Yvon said:**
> 
WARNING: GPT (GUID Partition Table) detected on '/dev/sdf'! The util fdisk doesn't support GPT. Use GNU Parted.


I think that is the problem. Have you tried using gparted to format the drive? Windows can read-write to a drive formatted by linux in fat32. I don't know about the Mac OS. It wouldn't hurt to try reformatting the drive with gparted. You will need to backup any data on the drive before formatting it.
Use the GParted or Parted Magic live CD to make it easy.

---

### Post by pgb47 on 2009-08-04
This has been driving me crazy also, but I have just notice that I don't get the problem if I copying into a "less" full folder.  I have movie folder where I try to save current movies, but after awhile I can not longer add a movie.   I can not move large folders on the USB drive.  The drive has 80GB free space.  If I create smaller folders, I can do the copy. Not a solution but a work-around.

---

