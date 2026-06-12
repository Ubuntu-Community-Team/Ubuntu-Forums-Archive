---
title: "SanDisk USB Flash Drive Broken..."
date: 2007-08-25
forum: Hardware &amp; Laptops
---

### Post by nebriv on 2007-08-25
I have posted about this a long time ago but then gave up. 

MY PROBLEM:

I was trying to put ubuntu onto my usb flash drive 1 GB. And put simply, it didn't work. Now I am unable to write anything to my flash drive. Its in two partitions, I am unable to format it delete any of the files. I have tried to chmod it, I've tried reformatting it in windozes. 

I think I was useing something like this tutorial, [http://pendrivelinux.com/2007/01/25/usb-x-ubuntu-610](http://pendrivelinux.com/2007/01/25/usb-x-ubuntu-610)

I have tried deleteing the files in the edgy partition, I can't even get access to the casper partition...

I think I have tried everything I know how...

There is no little button on it to lock it or anything as I have searched the thing countless times...

Please help....

---

### Post by nebriv on 2007-08-25
emmm anyone have any ideas?

---

### Post by w4ett on 2007-08-26
I ran across this the other day...seem it can repair both HDD and Flash Drives....Never tried it, but it's worth a look.
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by tgalati4 on 2007-08-26
You could try the SanDisk website and look for a tool to reformat the drive.  There are also programs to recover digital photos from CF cards, perhaps one of those tools could help diagnose the problem.

Flash memory has a limited life.  They also get flexed being in pockets.  Moisture and dirt can quickly render them inoperable.

As they drop in price, the time you spend trying to recover them is more than what they are worth.  They are almost disposable.

I'm using an Emphase 4 GB industrial flash IDE module and I've had problems with them.  They are supposed to be good for 4 million write cycles.

I'm using Damn Small Linux with mini-ITX VIA pc's.  The OS is loaded from flash, runs completely in ram, then at the end of the session, dumps a snapshot back to flash.  There are no intermediate writes to flash during operation.

To get Ubuntu to do this takes some effort.  Knoppix would be a better choice, it's designed to be run from a Live CD, so presumably you could run in read-only mode, and "nest" your personal data on the flash.

---

### Post by nebriv on 2007-08-26
ok, thanks I will look on sandisks website, I don't think it would be a probelm of the flash drive dying because it was almost brand new.

---

### Post by nebriv on 2007-08-26
> **w4ett said:**
> I ran across this the other day...seem it can repair both HDD and Flash Drives....Never tried it, but it's worth a look.
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)


I think TestDisk is also in the universe repositorys

Thanks for the link anyways

---

### Post by vanadium on 2007-08-26
- I do not think there is a hardware failure of the USB stick. USB sticks are very robust
- As root, you are in charge, i.e, you can do anything you want.

You need, in my opinion, to repartition the USB drive and format the partition again. You can do this with gparted just from within your regular Ubuntu session.

* With your system ready, plug in the USB stick
* Load gparted, as root of course: press Alt+F2, then type "gksudo gparted"
* In the right corner, in the drop down, select your USB
* Your partitions should become visible
* Right-click the rightmost partition, select Unmount, then right-click again, select "Delete"
* Do the same with the left-most partition
* Now, you (should) have all empty space (if not, delete other partitions that might be there). Right-click, select "new". Have the new partition use the entire space and format it (right-click). I recommend fat32 for such small volumes, for the sake of compatibility (readable on Linux, Windows, Mac OS, ...)
* Remove the drive, wait a bit, insert it again. Ubuntu should automatically mount it as a fat32 volume read/writable by the user

---

### Post by nebriv on 2007-08-27
> **vanadium said:**
> - I do not think there is a hardware failure of the USB stick. USB sticks are very robust
- As root, you are in charge, i.e, you can do anything you want.

You need, in my opinion, to repartition the USB drive and format the partition again. You can do this with gparted just from within your regular Ubuntu session.

* With your system ready, plug in the USB stick
* Load gparted, as root of course: press Alt+F2, then type "gksudo gparted"
* In the right corner, in the drop down, select your USB
* Your partitions should become visible
* Right-click the rightmost partition, select Unmount, then right-click again, select "Delete"
* Do the same with the left-most partition
* Now, you (should) have all empty space (if not, delete other partitions that might be there). Right-click, select "new". Have the new partition use the entire space and format it (right-click). I recommend fat32 for such small volumes, for the sake of compatibility (readable on Linux, Windows, Mac OS, ...)
* Remove the drive, wait a bit, insert it again. Ubuntu should automatically mount it as a fat32 volume read/writable by the user


I have tried that before, but I just tried it again and again it didn't work... I can't delete partitions or resize them, I get this error:

The following operation could not be applied to disk:

Delete /dev/sdb1 (fat32, 714.81 MiB) from /dev/sdb

See the details for more information

sooo, yeah...

---

### Post by nebriv on 2007-08-28
oh, just to add another bit of information, in gparted the fat32 partition is flagged bootable or w/e...does that make a difference? I always thought that reformatting would just fix it, :( hmmm I really want to figure this one out... may not be possible though...

---

### Post by nebriv on 2007-08-28
I tried reformatting it with fdisk also

again that didn't work

---

### Post by nebriv on 2007-08-29
HAHA! ok oh well I think sandisk will replace it for me...Thanks anyways everyone who helped

---

