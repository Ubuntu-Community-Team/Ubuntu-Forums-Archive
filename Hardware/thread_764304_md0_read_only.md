---
title: "md0 read only"
date: 2008-04-23
forum: Hardware
---

### Post by rpsibew110 on 2008-04-23
I set up two 250 gig seagates in raid1 they can be mount (md0) the drive and see it but can't write to it as a user.

It can be written to in root. here is my fstab. Can someone help me set md0 so they can be read/write to all users? 

I apologize if this is somewhere else I have been looking on the internet and here for a couple of days.

please and thanks


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=cb85308c-2af6-4253-acb3-6eaa86d41c7b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=FEC09A2FC099EDE1 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=6c4d9e96-f092-4fd2-ac07-e8474112471e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto      0       0
/dev/md0        /back           auto    rw,users,auto        0       0
# /dev/md0        /back           auto    defaults        0       0

---

