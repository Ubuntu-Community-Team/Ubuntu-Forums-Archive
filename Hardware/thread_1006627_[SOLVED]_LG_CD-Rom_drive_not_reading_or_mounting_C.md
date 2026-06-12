---
title: "[SOLVED] LG CD-Rom drive not reading or mounting CDs"
date: 2008-12-09
forum: Hardware
---

### Post by asilaydyingdl on 2008-12-09
Here is my situation.  The CD-Rom drive on my Hardy install is not reading CDs.  However, it can boot from disk at starup.  I have tried terminal commands and fixing the symlink to no avail.  I think it might be a BIOS issue, since the drive worked until I tried to install another CD-Rom drive (that install failed).  The computer is old, with a Pentium III processor and I believe half a gig of RAM.  If you would like to see more system stats, please give me a command or place to look on my computer so I can get them for you.  Here is my fstab to get started with.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e3c68393-2004-4b09-9df5-cddb5fa428b1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=1bcec022-0956-45a8-84bb-ea79dc1feef7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Any help would be greatly appreciated.  Thank you!

---

### Post by asilaydyingdl on 2008-12-09
Problem solved!  I checked cables and reset the BIOS and now everything works fine!

---

