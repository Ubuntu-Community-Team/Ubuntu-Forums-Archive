---
title: "Unable to mount external iomega 500gb device"
date: 2009-02-20
forum: Hardware
---

### Post by cdshamwell on 2009-02-20
I've recently switched my lenovo s10 ideapad from windows xp to ubuntu hardy.  i have a slew of music and video files i'd like to pull off my drive and place on my laptop, but when i plug in i get this error: invalid mount option when attempting to mount the volume 'MediaDrive' (media drive is my external of course).  i've searched to blogs for a while and did all the ntfs stuff, any ideas?;)

---

### Post by taurus on 2009-02-20
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -**l**
```
That would be a lower case letter L, not number 1.

---

### Post by cdshamwell on 2009-02-20
studio@soundroctrine:~$ sudo fdisk -1
[sudo] password for studio: 
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
studio@soundroctrine:~$

---

