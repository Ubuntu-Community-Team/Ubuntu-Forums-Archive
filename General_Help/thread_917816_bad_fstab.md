---
title: "bad fstab"
date: 2008-09-12
forum: General Help
---

### Post by LittleKoy on 2008-09-12
Hello, when I boot up, when loading the various kernel modules, it says:

```
[mntent]: line 6 in /etc/fstab is bad
```

Here's my fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=d8f71c01-ce28-4a61-b031-646b397ee49b /               ext3    defaults,errors=remount-ro noatime,data=writeback 0 1
# /dev/hda5
UUID=19d95d50-95e2-4696-9d75-4816ef8c0133 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

---

### Post by soxs on 2008-09-12
type ```
sudo blkid
``` to get wether the UUIDs are orrect. If the UUID in /etc/fstab doesn't exist, replace it with the pending one for that partition you get by sudo blkid

---

### Post by LittleKoy on 2008-09-12
```
/dev/sda1: UUID="d8f71c01-ce28-4a61-b031-646b397ee49b" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="19d95d50-95e2-4696-9d75-4816ef8c0133" 
```

Looks like it's correct...

---

### Post by sisco311 on 2008-09-12
```
UUID=d8f71c01-ce28-4a61-b031-646b397ee49b /               ext3    defaults,errors=remount-ro noatime,data=writeback 0 1
```-->[FONT=monospace]
[/FONT]```
UUID=d8f71c01-ce28-4a61-b031-646b397ee49b /               ext3    defaults,errors=remount-ro**,**noatime,data=writeback 0 1

```

---

### Post by LittleKoy on 2008-09-12
Wow, it solved!

Just for curiosity, I have had that problem for quite a long time (maybe some months) but I decided to solve it only today, since it didn't seem to give big problems... So, what problem could have given?

---

### Post by soxs on 2008-09-13
PLx mark the thread as *SOLVED*

---

