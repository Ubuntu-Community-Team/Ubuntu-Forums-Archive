---
title: "Cannot mount SFS Formatted Hard Disk"
date: 2006-06-08
forum: Hardware &amp; Laptops
---

### Post by stizzco@gmail.com on 2006-06-08
After much knashing of teeth and numerous google searches, I have succeeded in finding ou WHY my drive won't mount. But I have not yet been able to figure out how to fix the problem.

I have a fileserver box, it has 2 hard disks in it.

hda - 15 GB master
hdb - 120 GB slave

Prior to my ubuntu server insatllation, hda had windows 2000 server on it.

Now I have switched to ubuntu server, and fdisk tells me that hdb is SFS. I can't seem to mount this drive which really defeats the whole purpose. I need samba to share this drive on my network.

I read that Dynamic Drive support was problematic in earlier kernel versions. Now that we have moved beyond 2.4, is this still an issue? Do I have to recompile my kernel? I also understand that I need NFS v3 support. I have no idea what to do from this point forward short of wiping and reinstalling windows.

```


Disk /dev/hda: 15.3 GB, 15307407360 bytes
255 heads, 63 sectors/track, 1861 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1815    14578956   83  Linux
/dev/hda2            1816        1861      369495    5  Extended
/dev/hda5            1816        1861      369463+  82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       14593   117218241   42  SFS
Note: sector size is 2048 (not 512)

Disk /dev/hdc: 452 MB, 452603904 bytes
255 heads, 63 sectors/track, 13 cylinders
Units = cylinders of 16065 * 2048 = 32901120 bytes

Disk /dev/hdc doesn't contain a valid partition table
root@ubuntu:~# mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

---

### Post by mikedoth on 2006-10-18
I am going through the same thing but with Ubuntu 6.10. I think it has something to do with Simple File Sharing, which I did to the root of the drive. I believe and am going to test if I remove the sharing if it will retun to NTFS and will be accessable.

---

### Post by mikedoth on 2006-10-20
Still no luck mounting NTFS or FAT drives yet in 6.6 or 6.10. Being forced to work with fstab is a pain in the *** for the average user. I hope they bring back "disks" aka Disk Management in Windows.

---

### Post by ephie on 2006-10-31
hello,

I have the same problem with my SFS formated drive! How can I mount it in Ubuntu???

However, I got my NTFS drive working by editing the /etc/fstab file but the drive can only be accessed as read only!

eph!e

---

### Post by ephie on 2006-11-06
Hi

I got my SFS drive mounted by editing the /etc/fstab file and adding the same line I added for my NTFS drive!

The only problem is that the sfs drive is read only! But apparently  ntfs and sfs drives can only be read only under Ubuntu!

Programs exist I think to be able to write to NTSF but they are not so easy to install. I didn't have time to try it out yet! If someone has let me know

eph!e

---

### Post by Draek on 2007-02-27
Unfortunately for me, I am not as lucky as you guys. I am using SFS volume from Windows Vista now. And I cannot mount it for the life of me.

First off, I can see the /dev/sda hard disk in fdisk from linux, this is a good start:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24322   195359130+  42  SFS
/dev/sda2           24322       24322         798   42  SFS

Next, I am trying to add an entry to fstab, and mount, but i get the following:

mount: special device /dev/sda1 does not exist

Which is funny, since its listed right above there... When I installed Ubuntu 6.10, it didn't even prompt me for setting up boot sequence for Windows, GRUB just ignored it all and moved on. I found this odd. But I didn't realize the seriousness until I reached the OS and couldn't mount my NTFS, now I can't boot to windows, and I can't read the data in Linux.

I know the partition is still there, and is readable, I can read the HD on another computer, all my data is safe. But this is just silly...

Anyone have ideas?

---

