---
title: "Mount VFAT drive stopped working"
date: 2007-03-18
forum: Hardware &amp; Laptops
---

### Post by think13 on 2007-03-18
I have a VFAT partition on my hard drive to share files between Windows and Linux on the same machine.  When I booted up today, it didn't automatically mount on boot.  It is listed as /dev/sda3 and the mount point is /media/sda3.  I tried

sudo mount /dev/sda3 /media/sda3 

but it said that it could not find /dev/sda3 in /etc/fstab or /etc/mtab.  I opened fstab and it looked like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=ae8a2bd3-1404-42ff-b9bd-39318d34acff /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=20B88D5AB88D2EFA /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=45B6-8BB0  /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=9c436903-5472-408a-9fe2-966f39c24f34 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

I uncommented the /dev/sda3 line and mounted it and it worked.  What caused this problem in the first place?  How should I fix my fstab? How can I prevent this from happening again?

---

