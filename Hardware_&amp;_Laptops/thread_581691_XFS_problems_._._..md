---
title: "XFS problems . . ."
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by integr8e on 2007-10-19
I am fairly new to the Linux world and have been learning all I could for the last 2 months or so, and I decided to reformat my hard drive in the XFS format;  I found instructions on creating a separate partition for Grub as ext2, and have done that, and everything for the most part seems to be running well, except it's very picky about what I can save to my partitions (I have two separate XFS partitions, a root and home directory).  I tried to use the same fstab configuration I had with my old ext3 partition, and it didn't work, I'm guessing because I only had one primary directory at that time and I'm also using a different format.  I've posted my fstab in the likely event the problem's located there (this is not my old configuration):

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a6fc1d6b-f278-4e50-be8f-ca6963beb566 /               xfs     defaults        0       1
# /dev/sda4
UUID=efd7850f-3a2b-47e1-8604-1b8ef01c2545 /boot           ext2    defaults        0       2
# /dev/sda2
UUID=7ac60c05-a504-4698-bd57-a970711f510c /home           xfs     defaults        0       2
# /dev/sda3
UUID=2c68f5d8-15c6-4c41-ae4a-c00be196b768 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0



If anybody can, please help me.

Thanks,
integr8e

Edit: I may have found the problem, please correct me if I'm wrong.  I think I had my /boot partition set too low.  I reinstalled and reformatted my HD, this time expanding my /boot partition from 50MB to 2GB and converting it from ext2 to ext3; that seems to have fixed the problem, at least for the moment.  I'll be back if it doesn't work :)

---

