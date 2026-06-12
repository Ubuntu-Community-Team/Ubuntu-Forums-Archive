---
title: "CD/DVD works sometimes??"
date: 2009-02-08
forum: Hardware
---

### Post by osurshaney on 2009-02-08
I am experimenting with different flavours of ubuntu. I was using Intrepid Ibex 8.10 and I went to Linux mint Felicia. I backed up all my documents pics and such on disks' and reformatted with Mint. I transfered all of my music just fine but when I try to transfer my documents the disk will not mount. I have tried :

mount /dev/scd0
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

Here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=b95eb4bd-52a7-4068-a2ed-e44427521ab2 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda5
UUID=e5c1c143-4d7c-4459-9dc0-31df049d0e31 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

Any ideas??

---

