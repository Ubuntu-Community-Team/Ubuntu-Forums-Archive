---
title: "How to use multiple Hard Drives?"
date: 2007-12-26
forum: Hardware &amp; Laptops
---

### Post by SomeStupidHippie on 2007-12-26
I am assuming this is a pretty easy fix. I recently built a computer that I set up with two hard drives; one 10,000 RPM 72 GB raptor and anothe 7200 RPMr 160 GB caviar (both Western Digital)

I intended to have the raptor serve as a boot drive and have the caviar for all of my files, and so during the install I selected to install to the raptor. However, now that everything is up and running i realize that i cannot find any way to save to the other hard drive (caviar)

Yes, both drives are recognized under the hardware information and they both seem to be running just fine.... Is there anyway to access my other drive? I am running Gutsy, thank you in advance for your help :)

---

### Post by LaRoza on 2007-12-26
> **SomeStupidHippie said:**
> I am assuming this is a pretty easy fix. I recently built a computer that I set up with two hard drives; one 10,000 RPM 72 GB raptor and anothe 7200 RPMr 160 GB caviar (both Western Digital)

I intended to have the raptor serve as a boot drive and have the caviar for all of my files, and so during the install I selected to install to the raptor. However, now that everything is up and running i realize that i cannot find any way to save to the other hard drive (caviar)

Yes, both drives are recognized under the hardware information and they both seem to be running just fine.... Is there anyway to access my other drive? I am running Gutsy, thank you in advance for your help :)

Post the output of:

```

less /etc/fstab

```

and 

```

sudo fdisk -l

```

---

### Post by SomeStupidHippie on 2007-12-26
**fstab output:**

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b855572f-5f5d-4672-97d1-2a2495f646f4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=278faed9-5cec-4297-848f-fee6a3082ad7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
~
~
~
~
~
~



~
~
~
~
~
(END) 


[B]
fdisk output:[/B]


Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b3b33

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8666    69609613+  83  Linux
/dev/sda2            8667        9039     2996122+   5  Extended
/dev/sda5            8667        9039     2996091   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

---

### Post by SomeStupidHippie on 2007-12-27
little bump, sorry not trying to be impatient this is just a little urgent :)

---

### Post by taurus on 2007-12-27
There doesn't seem to be any partition/filesystem on your second harddrive.

```

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

```
Therefore, you need to create it first.  The easiest way is to install gparted and use it to recreate a partition, /dev/sdb1, and format it to ext3 if you want to use it with Ubuntu.

```
sudo apt-get update
sudo apt-get install gparted
```
Gparted is now in System -> Administration.

---

### Post by SomeStupidHippie on 2007-12-27
great, thanks a lot! i already have a gparted live CD lying around, Ill let you know if i run up against any issues

---

### Post by SomeStupidHippie on 2007-12-27
Sorry, one last quick question. I got it mounted and I can now see the hard drive, however it says I dont have permission to use it. How to I edit the settings to allow me to access it?

---

### Post by taurus on 2007-12-27
Where do you mount it to, mountpoint, and how do you mount it, through /etc/fstab?  You can change the ownership of the mountpoint from root to your login name, assuming you have formatted it to ext3.

```
sudo chown -R **username**:**username** /mountpoint_of_that_second_drive
```

---

### Post by SomeStupidHippie on 2007-12-27
Sorry, nevermind I got it figured out on my own. Thanks so much for your help!

---

