---
title: "HDD add and mount to /usr problems"
date: 2006-06-27
forum: Hardware &amp; Laptops
---

### Post by benny@linux on 2006-06-27
hi all , i add new HDD to my computer ,format it to be ext3, copy /usr files to it

and change fstab so its look like this :

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda1       /usr            ext3    defaults,errors=remount-ro 0       2
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

and after change my /usr to /usr2
ubuntu not loading :( 
so i came back to livecd and change the folder name back to /usr
-its back again - but how can i make ubuntu mount my HDD and use /usr from there while loading ??

---

### Post by BoneKracker on 2006-06-27
What is the mount command you used to manually mount the new drive when you copied the files over onto it.

That same command should work in the fstab.

I assume you got the device name right (and that it's not sdb).

---

### Post by benny@linux on 2006-06-28
i dident mount it manualy i use gnome disk utility .. 
and i posted my fstab file before - the drive name is hda1

if i dont delete the usr folder ubuntu is loading prfectly and then mount hda1 into /usr , but i dont want that - i want thet hda1 will replace /usr complitly and for that ubuntu neet to mount it before its accessing /usr

---

### Post by BoneKracker on 2006-06-28
How did you determine the device name to be hda?

---

### Post by benny@linux on 2006-07-03
in the graphic tool this the name it shown , is there a better way to know?

---

### Post by BoneKracker on 2006-07-03
Provided you are using the correct mount command in fstab, I do not know why you have this problem.  Sorry.  If you can mount it manually, you should be able to mount it from fstab.

fdisk is another tool you can use to verify the device and partition name.

fdisk /dev/hda

---

