---
title: "can't mount my floppy"
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by keslimmer on 2009-02-19
For some reason I can't get my floppy to mount.  I have tried everything that I can find in the forums, so far I haven't found the answer.

The error I get when I try to mount using right click in a GUI format is:

CAN NOT MOUNT VOLUME
You are not privileged to mount the volume DISK 1

This is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=14e85f52-c506-4fb0-86c5-a30d3e70189e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=e7efc49c-3609-4111-b0e3-5c8500dea683 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/fd0
/dev/fd0 /media/floppy-disk rw,user 0 0

Thanks!

Ken

---

