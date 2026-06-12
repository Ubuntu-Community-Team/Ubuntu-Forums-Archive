---
title: "Ubuntu USB Install - Partitioning"
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by robbyc on 2009-04-19
I have downloaded Ubuntu 9.04 RC. I have successfully installed Ubuntu to my 16GB USB drive. I tried to repartition my USB drive using gparted live cd so I had ~8.5GB as a Primary ext3 partition (mounted to /), 1GB as swap at the end of the drive in a logical parition and then the rest as another logical partition as NTFS. 

I was trying to do this so that when the USB key was inserted into a computer running windows I could still use it as a regular USB drive. This did not work. The NTFS partition did not appear under Windows just the ext3 partition.

How can I partition my USB key correctly so I can use it as both a standard USB key and a bootable OS.

Any help will be gratefully appreciated.

---

### Post by wirechief on 2009-04-19
Windows ?
Windows XP or Vista ?
If Vista you need to use Vista to partition the ntfs (it uses a unique ntfs)

---

### Post by robbyc on 2009-04-19
Yes Vista but when I try and format the logical partition within windows it gives me an error. So I m presumming I have done my partitioning incorrectly.

---

### Post by wirechief on 2009-04-19
This is what mine looks like....
sudo fdisk -l

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x52df0fb1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14243   114406866    7  HPFS/NTFS
/dev/sdb2           14244       19457    41881455   83  Linux


note the Id

---

### Post by robbyc on 2009-04-19
Ok so I format my USB drive as below:

Disk /dev/sdf: 16.0 GB, 16039018496 bytes
255 heads, 63 sectors/track, 1949 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004f0d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1        1087     8731296   83  Linux
/dev/sdf2            1088        1822     5903887+   7  HPFS/NTFS
/dev/sdf3            1823        1949     1020127+   5  Extended
/dev/sdf5            1823        1949     1020096   82  Linux swap / Solaris

This works but I cannot access the NTFS partition from windows. It asks me to format it but after I do I still cannot access it and it also formats /dev/sdf1 as NTFS.

This gives the following.

Disk /dev/sdf: 16.0 GB, 16039018496 bytes
255 heads, 63 sectors/track, 1949 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004f0d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1        1087     8731296    7  HPFS/NTFS
/dev/sdf2            1088        1822     5903887+   7  HPFS/NTFS
/dev/sdf3            1823        1949     1020127+   5  Extended
/dev/sdf5            1823        1949     1020096   82  Linux swap / Solaris

What am I doing wrong? 

Thanks

---

### Post by arubislander on 2009-04-19
I doubt you're doing anything wrong. It appears Windows can only see the first partition of your USB key. So if you want to use it in both Linux and Windows you'll have to format that as the NTFS.

Just out of curiousity. Why did you not use the "Creat USB startup disk" option in System->Administration?

---

### Post by robbyc on 2009-04-19
Thanks for the response. I originally used the "Create USB Startup disk" but it appeared to give me a USB version of the LiveCD. Will this function just as well as a full linux installation?

As for the NTFS partition being at the start of the drive will this mean I won't be able to boot linux from this USB drive in this way. I thought for some reason that Ubuntu had to be at the start of the drive in order to be bootable?

Thanks again

---

### Post by arubislander on 2009-04-19
> **robbyc said:**
> Thanks for the response. I originally used the "Create USB Startup disk" but it appeared to give me a USB version of the LiveCD. Will this function just as well as a full linux installation?
Not entirely, but it will function all right, provided you tell the program you want to store your changes in reserved extra space. (Be careful with updates though...) And it will probably prolong the life of your USB key as well.

> **robbyc said:**
> As for the NTFS partition being at the start of the drive will this mean I won't be able to boot linux from this USB drive in this way. I thought for some reason that Ubuntu had to be at the start of the drive in order to be bootable?
You could get Ubuntu to boot off a FAT32 partition. Not sure about an NTFS partition, but I guess it could be done too. Just afraid I wouldn't be of much help in that area.

---

### Post by robbyc on 2009-04-19
Thank you for your help I have now achieved what I desired.

I formatted my USB drive as shown below. This allows it to be used as a standard USB drive as well as a portable version of Ubuntu I can run on any of my computers with all my apps and config as I like it. 



Disk /dev/sdb: 16.0 GB, 16039018496 bytes
255 heads, 63 sectors/track, 1949 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004f0d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         503     4040316    7  HPFS/NTFS
/dev/sdb2   *         504        1755    10056690   83  Linux
/dev/sdb3            1756        1949     1558305   82  Linux swap / Solaris

---

### Post by wirechief on 2009-04-19
I just remembered something basic. I think Windows always wants to be the
first person on the HD, in your case you have linux because you used the usb
startup and I think Windows is balking about the mbr of that stick.
In my case i formated the USB HD completely ntfs using windows vista then
I resized it using gparted (with ntfsresize installed) gparted must of used that to resize the partition and i created a linux partition and am using it with my linux as a backup drive while using the vista partition when under vista as backup. I doubt you can make it bootable (linux partition that is) I haven not heard of this being done actually. Not that it can't
i just dont know. Really need grub to manage the booting. I have tested a usbstick that when you use grub you can select it to boot from or if dual boot with vista but that stick doesnt have persistence and i think you are looking to do that.
As a side note the Jaunty 9.04 usb-creator aka usb startup disk has been broken but allegedly will be fixed with the final release (according to those in the process) it drops users to a initramfs busy box currently and there have been various pita work arounds but it will worth the wait for the final....

---

### Post by arubislander on 2009-04-19
Great to hear you got it working!

---

### Post by arubislander on 2009-04-20
> **wirechief said:**
> As a side note the Jaunty 9.04 usb-creator aka usb startup disk has been broken but allegedly will be fixed with the final release (according to those in the process) it drops users to a initramfs busy box currently and there have been various pita work arounds but it will worth the wait for the final....

It is often the case that the usb startup disk gets broken in the process of going to a new version. It is also always the case that the developers aim to fix it for the final release. It is sadly not always the case that this is achieved.

---

### Post by wirechief on 2009-04-20
looks like new files casper lupin-casper and ubiquity-casper got added to the latest daily build, not sure they are the ones needed to make usb-creator work but it is working now on with the latest build.

---

### Post by tamas305 on 2009-04-20
Check the third post on this [thread]("http://ubuntuforums.org/showthread.php?t=1116206").

Hope it works.
-tamas

---

