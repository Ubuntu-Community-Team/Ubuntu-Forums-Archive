---
title: "Cannot mount volume (External NTFS Hard Drive)"
date: 2009-02-23
forum: Hardware
---

### Post by nmargo17 on 2009-02-23
Hey everyone

Been trying to get my desktop to access an external WD Hard Drive via USB.  However, I get the error "**Cannot mount volume.**  You are not privileged to mount the volume 'drive name'."

My buddy and I have gone through any points to get it to where it is a solid error with only this statement and no additional details.  Below you can find my fstab:

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=6aa3188c-2cac-4144-b623-9dc238ea1fcf / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=2062b44d-56a2-4c30-b285-ff2f754dcd5d none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sdb1 /media/KHTKE480 ntfs-3g defaults 0 0

In addition, I'm using Ubuntu Intrepid 8.10.  I have already tried forcing it, turning off automount in Nautilis, install usbmount and seeing if that would work, etc...  I did at one point get a FUSE error but I have seemed to fixed that to the point I previously stated above.

This is getting very frustrating.  If anyone could give me any input it is appreciated.  If you need more info please ask!  Thanks!

---

### Post by brandon88tube on 2009-02-23
Do you by any chance have the drive protected in any way? Like a password or encryption etc.

---

### Post by nmargo17 on 2009-02-23
> **brandon88tube said:**
> Do you by any chance have the drive protected in any way? Like a password or encryption etc.

nope...just your basic NTFS external hard drive....

---

### Post by caljohnsmith on 2009-02-23
You can probably mount the partition manually, so how about opening a terminal (Applications > Accessories > Terminal) and do:
```
sudo fdisk -lu
```
Find which is the partition on the WD USB drive you want to mount, for example sdb1, then do:
```
sudo mount /dev/[COLOR="Blue"]sdb1[/COLOR] /mnt && nautilus /mnt &
```
Please post the output of all the above commands, and let me know how it goes.

---

### Post by dylanads on 2009-02-25
I followed your instructions to manually mount the partition but, when I put it in a terminal window I got the following:   

 mount: you must specify the filesystem type

Any help please?  I'm a completely new to linux and quite an amateur with computers period.

---

### Post by colau on 2009-06-27
> **dylanads said:**
> I followed your instructions to manually mount the partition but, when I put it in a terminal window I got the following:   

 mount: you must specify the filesystem type

Any help please?  I'm a completely new to linux and quite an amateur with computers period.
What type of partition are you trying to mount?
ntfs or vfat?

---

