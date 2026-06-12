---
title: "CD/DVD ROM not working/recognized, please help!"
date: 2009-01-23
forum: Hardware
---

### Post by Aluvian on 2009-01-23
I'm new to ubuntu having just recently installed it a couple of days ago.
The thing is, I'm running Ubuntu 8.10 on a HP Pavilion DV6500 laptop, everything is working fine except that my cd-rom/dvd-rom is not working or not recognised. I'm clueless as to what the cause is and I've already tried searching around for possible solutions with no success. Any help would be greatly appreciated.

---

### Post by Aluvian on 2009-01-23
BTW, doing:

```
sudo cat /etc/fstab
```

gets me:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=657d5aaf-1ae5-4017-acde-fc235b76be69 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=a7f51d02-2c95-416e-9348-47c8abe6fe46 /home           ext3    relatime        0       2
# /dev/sda5
UUID=e15986ba-77b5-4b02-9503-3c99c6a2b75e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by Brad_au on 2009-03-16
I had a similar problem where udev linked my drive to /dev/dvd2 rather than /dev/dvd. Once corrected everything worked perfectly.

What is the output of lshw?

---

