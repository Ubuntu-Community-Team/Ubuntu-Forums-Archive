---
title: "Trouble installing 3rd hard drive"
date: 2006-06-15
forum: Hardware &amp; Laptops
---

### Post by lonegranger on 2006-06-15
My PC has 3 hard drives. When I was running XP it recognised all 3 therefore the BIOS must be set ok. The one I have on IDE 3 just is not recognised by Dapper. The motherboard is a Gigabyte K7 Triton GA-7N400-Pro2

Any ideas gratefully received

---

### Post by bruce89 on 2006-06-15
What happened to the other thread in Absolute Beginners? - [http://www.ubuntuforums.org/showthread.php?t=196749](http://www.ubuntuforums.org/showthread.php?t=196749)

---

### Post by lonegranger on 2006-06-15
I had to log off before I could finish the help I was getting. Below is the what was asked before I had to log off which was what does the fstab file contain.

Appreciate further help.

/etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda3 / ext3 defaults,errors=remount-ro 0 1
/dev/hda1 /boot ext2 defaults 0 2
/dev/hdb1 /media/hdb1 ntfs user,umask=0200 0 0
/dev/hdb5 /media/hdb5 ntfs user,umask=0200 0 0
/dev/hda5 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

---

