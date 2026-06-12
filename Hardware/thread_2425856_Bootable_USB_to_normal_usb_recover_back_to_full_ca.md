---
title: "Bootable USB to normal usb recover back to full capacity"
date: 2019-08-31
forum: Hardware
---

### Post by kcgoli on 2019-08-31
my 32 GB usb drive created with 4 GB of bootable image
after succesful use of bootable drive
now i tried to format usb
but it only formatted upto 4 GB not upto its full capacity 32 GB
I have tried following methods but its still fail
1. terminal by using fdisk -l,umount , mkfs and wipefs all
2 Gparted 
3 windows normal format

---

### Post by yancek on 2019-08-31
Use GParted and create a new partition table for the drive and take care that you get the correct drive as you will delete anything on it.

---

### Post by C.S.Cameron on 2019-09-01
Use Disks to unmount the ISO9660 flash drive before using GParted to reformat it.

---

