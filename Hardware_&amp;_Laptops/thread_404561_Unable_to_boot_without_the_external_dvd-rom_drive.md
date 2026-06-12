---
title: "Unable to boot without the external dvd-rom drive"
date: 2007-04-08
forum: Hardware &amp; Laptops
---

### Post by rekotc on 2007-04-08
Hi! I have installed ubuntu 6.10 on my toshiba portege 3490 ct...and i have a big problem with my external dvd - rom drive , during the installation it seems to work properly but now i cannot boot the linux partition without this drive!!..it gives me the "ubuntu waiting for root file system" error...this is my /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hde1
UUID=3511d036-7d17-4aae-b07c-884ff1810939 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hde2
UUID=802acc1e-4273-4558-a586-df5b856cb510 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda        /media/floppy0  auto    rw,user,noauto  0       0

I tried to comment the line of the cdrom drive 

##/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
 
but it doesn't work...can you help me?

---

### Post by red_five on 2007-04-10
First thing I would do is replace the 2 UUID=XXX entries with /dev/whatever entries. If you ever ghost those partitions to a new drive, those UUIDs will most likely change, which'll give you fits trying to boot if you ever replace/upgrade the drive. That change will probably clear it up.

---

