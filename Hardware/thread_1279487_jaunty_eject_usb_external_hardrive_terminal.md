---
title: "jaunty eject usb external hardrive terminal"
date: 2009-09-30
forum: Hardware
---

### Post by Esthellin on 2009-09-30
Trying to eject a USB external hardrive from the terminal (hence the thread name). (The external harddrive is a ntfs-3g format).
Terminal commands+output:

10:54{~} umount /media/Cerberus 
umount: /media/Cerberus is not in the fstab (and you are not root)
11:01{~} eject /media/Cerberus/
umount: /media/Cerberus is not in the fstab (and you are not root)
eject: unmount of `/media/Cerberus' failed
11:01{~}

I have no idea where to go to from here. Unmounting with the nautilus filebrowser works fine (right-click, "unmount volume"), but unmounting from terminal always gives this fstab error.

---

### Post by ezsit on 2009-10-01
Two issues going on here. First, from a terminal, you need to use sudo or be root in order to umount a drive. Second, umount and eject commands are expecting a device to work with, i.e. /dev/sda or /dev/sdb. So, first thing to do is in the terminal, type:

sudo fdisk -l 
**( -l is a lower  case L, not a 1 )**

The output will give you the /dev of your external USB hard drive, most likely: /dev/sdb1. If this is the case, type:

sudo umount /dev/sdb1

This will unmount the drive. Hope this helps.

---

### Post by Esthellin on 2010-07-03
> **ezsit said:**
> Two issues going on here. First, from a terminal, you need to use sudo or be root in order to umount a drive. Second, umount and eject commands are expecting a device to work with, i.e. /dev/sda or /dev/sdb. So, first thing to do is in the terminal, type:

sudo fdisk -l 
**( -l is a lower  case L, not a 1 )**

The output will give you the /dev of your external USB hard drive, most likely: /dev/sdb1. If this is the case, type:

sudo umount /dev/sdb1

This will unmount the drive. Hope this helps.

I have now become familiar with how mounting and the fstab file works. Thankyou for the reply, this all makes sense now :D

---

