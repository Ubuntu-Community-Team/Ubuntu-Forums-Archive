---
title: "cds read but do not write"
date: 2006-11-01
forum: Hardware &amp; Laptops
---

### Post by Will Breathe on 2006-11-01
[SIZE="3"][SIZE="3"]Greetings, 
          I have two cd drives which read but will not 
write to disk. I have tried various things to no avail
so far. If you know what to do I'd appreciate a solution.

Thanks,
Will Breathe
 
current fstab is : 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 rw,user,noauto     0       0
/dev/hdd        /media/cdrom-1   udf,iso9660 rw,user,noauto     0       0

Tried to mount in sudo

Got : [mntent]: warning: no final newline at the end of /etc/fstab


original fstab :

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

ls /media :

cdrom  cdrom0  cdrom-1  usbdisk


Thanks[/SIZE][/SIZE]

---

