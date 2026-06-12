---
title: "USB plug Problem"
date: 2008-08-10
forum: General Help
---

### Post by greenco on 2008-08-10
Does anyone know if there is a module available, that fixes the USB connections? Right now, in order for me to use my CH Yoke and Pedals, I have to unplug them, after I shut down the operating system. The next time I start up the operating and am at the desktop, I have to plug them back in. I am running Ubuntu v2.22.1 on my computer. As long as I follow this procedure I can use them and I can calibrate them. If I leave them plugged in and then start Ubuntu, the game can not use (find) them. 
Thanks

---

### Post by Sycron on 2008-08-10
please post the output of 
```
$ cat /etc/fstab
```

---

### Post by greenco on 2008-08-10
Here are the results.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=27617bf9-d6c2-403e-bfc5-23ba4685b4d5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=3dfd545a-0a0e-43af-a9d2-d92630900627 /home           ext3    relatime        0       2
# /dev/sda3
UUID=3ab89527-46fd-47ba-9150-e029080af56f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

