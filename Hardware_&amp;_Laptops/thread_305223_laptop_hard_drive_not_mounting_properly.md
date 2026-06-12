---
title: "laptop hard drive not mounting properly"
date: 2006-11-23
forum: Hardware &amp; Laptops
---

### Post by afbase on 2006-11-23
I installed an old laptop hard drive into my server with a 44 pin laptop to 40 pin IDE connector.  I am curious as whether that prevents me from writing files onto the hard drive.  If so, then I think i know my problem.

Anyways, If that isn't the case I am have difficulties changing /dev/hdc1 as a read, write drive.
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdd1       /home/clinton/hdd1 ext3 suid,dev,exec 0 0
/dev/hdc1       /home/clinton/mysql ext3 suid,dev,exec 0 0


```

I am trying to figure out as to why i get this error message after i type:```
root@Condor:/home/clinton# mount -t ext2 -o rw,remount /dev/hdc1 /home/clinton/mysql


mount: block device /dev/hdc1 is write-protected, mounting read-only


```

---

### Post by xyz on 2006-11-23
You'll probably find answers here:
[Psychocats]("http://www.psychocats.net/ubuntu/")

---

