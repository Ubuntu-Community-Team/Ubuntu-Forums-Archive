---
title: "LG DVD Drive Not mounting CD-ROM"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by stuber79 on 2007-07-29
Hi, 

             My LG DVD drive doesnt seem to like CD-ROMs. DVDs mount ok, but not CDs. My FSTAB goes like this:

                    
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/hda1
UUID=35a0c371-4872-4ab1-b168-aabf8cd900a4 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,s$
# /dev/hda5
UUID=57ff4aa8-0780-4c95-84c7-878cf019d6ed none swap sw 0 0
#/dev/hdb /media/cdrom0 auto users,atime,auto,rw,dev,exec,suid 0 0
/dev/hdb /media/cdrom0 auto  noauto,owner,users,rw 0 0
/dev/fd0 /media/floppy0 auto user,atime,noauto,rw,dev,exec,suid 0 0

Stud

---

