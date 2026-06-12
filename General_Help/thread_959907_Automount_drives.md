---
title: "Automount drives"
date: 2008-10-26
forum: General Help
---

### Post by ChazZeromus on 2008-10-26
How do I automount my drives?  I have to always click on them in the computer window for them to mounted. And when I click on them they mount but I get an error saying "Unable to mount to location".  I'm running 64-bit ubuntu.

---

### Post by reality1011 on 2008-10-27
You want to modify /etc/fstab...


The last 3 were manually added to my fstab.  You can test fstab by using the mount command.  If you have an error then fstab is not configured correctly.  If it mounts then you are good to go.


```
cappetta@Linux-Box:/var/www/c_sharp$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1 -- converted during upgrade to edgy
UUID=7cabe776-d82e-409b-8f53-dee811c2d77d / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=bb3bfcb3-cbb5-4071-ada2-d9de314f445d none swap sw 0 0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb1       /backups        ext3    defaults,exec  0 0
/dev/sdb2       /data           ext3    defaults,exec 0 0
/dev/sdb3       /PROJROOT       ext3    defaults,exec 0 0

```

---

### Post by _sAm_ on 2008-10-27
Here is a nice guide on how to mount a partition/harddrive on Ubuntu; [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

