---
title: "Ubuntu can't find the mx-100 external drive"
date: 2009-07-22
forum: Hardware
---

### Post by Jon_kanon on 2009-07-22
Hello everyone..

First let me say that I'm a newbee with ubuntu.

I have Install version 9.04 32 bit, on a asrock ION 330. I have also bought a ANTEC hard drive cabinet, where my old windows OC system where. At first when I put the drive in, ubuntu found it. But I was unable to delete windows from it. 

Then I proberbly did something stupid, I ran the command mount -a from a shell, and the ANTEC drive disappeared from ubuntu. 

fdisk -l 
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0e8a14fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3656    29366788+  83  Linux
/dev/sda2            3657       38183   277338127+  83  Linux
/dev/sda3           38184       38913     5863725   82  Linux swap / Solaris

I have tried it on a windows machine, and there it works fine..

Please help!!

---

### Post by bryonak on 2009-07-22
Could you please specify a bit more?
You have 2 hard drives, one with Ubuntu, the other with Windows, both connected via IDE or SATA (not USB)?
Does logging out and back in help?

Please post the output of ```
cat /etc/fstab
```
This file keeps track of all the "unmovable" drives in your computer, and your Windows drive probably isn't there if you plugged it in after installing Ubuntu.
"mount -a" simply mounts all drives listed in this file.

---

### Post by Jon_kanon on 2009-07-22
Output from cat /etc/fstab

proc /proc proc defaults 0 0
UUID=f63ef028-6da3-4cf5-b85c-aa8706003b64 / ext3 relatime,errors=remount-ro 0 1
UUID=7c0599e8-afea-4bef-90a0-75da022b0ccc /home ext3 relatime 0 2
UUID=ef997c6a-c50b-4754-8b52-f7a850dfe63d none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

I have two disks, one connected(sata) in the new Computer. They other one is also a sata harddisk, but connected via a USB stick in a harddisk cabinet.

---

### Post by Jon_kanon on 2009-07-22
The cabinet or enclosure is of the type:[http://www.antec.com/Believe_it/index.php?page=support_productInfo_details&ProdID=77152](http://www.antec.com/Believe_it/index.php?page=support_productInfo_details&ProdID=77152)

It dosn't seem to help to login/out but I have got it to start one time, but now its not working again..

Will borrow another harddisk tomorrow and test it with that!

---

### Post by Jon_kanon on 2009-07-23
Okay, the problem seems to be fix with a new harddisk.

---

