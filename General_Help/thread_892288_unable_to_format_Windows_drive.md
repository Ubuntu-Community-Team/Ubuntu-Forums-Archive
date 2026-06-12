---
title: "unable to format Windows drive"
date: 2008-08-17
forum: General Help
---

### Post by slickuser on 2008-08-17
I was unable to format my Windows partition. Any ideas why?

Thanks. Error detail below.


GParted 0.3.5

Libparted 1.7.1

Format /dev/sda1 as ext2  00:01    ( ERROR )
     	
calibrate /dev/sda1  00:00    ( SUCCES )
     	
path: /dev/sda1
start: 63
end: 78140159
size: 78140097 (37.26 GiB)
set partitiontype on /dev/sda1  00:00    ( SUCCES )
     	
new partitiontype: ext2
create new ext2 filesystem  00:00    ( ERROR )
     	
mkfs.ext2 /dev/sda1
     	
mke2fs 1.40.8 (13-Mar-2008)
Could not stat /dev/sda1 --- No such file or directory

The device apparently does not exist; did you specify it correctly?
libparted messages    ( INFO )
     	
Error informing the kernel about modifications to partition /dev/sda1 -- Device or resource busy. This means Linux won't know about any changes you made to /dev/sda1 until you reboot -- so you shouldn't mount it or use it in any way before rebooting.
The kernel was unable to re-read the partition table on /dev/sda (Device or resource busy). This means Linux won't know anything about the modifications you made until you reboot. You should reboot your computer before doing anything with /dev/sda.

========================================

---

