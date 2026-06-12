---
title: "UDF Volume won't mount"
date: 2009-05-12
forum: Hardware
---

### Post by potatoehead64 on 2009-05-12
Having upgraded to 9.04 Jaunty, it seems I'm unable to mount any CD's or DVD's. The error message reads "Invalid mount option when attempting to mount the volume 'UDF Volume'."

I've noticed that disks even fail to mount if I try to boot the PC directly from a CD/DVD (i.e. putting a iso disk in the drive and setting BIOS to read it first). 
I no longer run MS windows on my PC, so I can't check it via that option. 

Having searched various forums, I can't find anything specific on this matter other than advice on obtaining output (I think this is right)

> marty@marty-desktop:/$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=70136923-508a-4018-b875-55c21b620033 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=235f458f-ff90-4acb-bfb4-f6c5ef964751 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
> 

Is this a "Jaunty" bug or do you think I simply have a problem generically with the hardware (CDRW/DVD drive) ???

Please advise.

---

