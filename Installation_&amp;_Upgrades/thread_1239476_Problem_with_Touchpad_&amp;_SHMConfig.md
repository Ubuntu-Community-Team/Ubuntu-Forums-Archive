---
title: "Problem with Touchpad &amp; SHMConfig"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by unihiekka on 2009-08-13
I just upgraded from 7.10 to 8.04 but now my synaptics touchpad stopped working. Everything else is fine. I've tried adding lines as described in different posts in xorg.conf and adding an fdi file, but nothing seems to work. Setting "SHMConfig" to "on" or "true" in xorg.conf doesn't do anything. 

```
$ synclient -l
Can't access shared memory area. SHMConfig disabled?
```

Somehow I cannot get SHMConfig to be enabled... I even tried:

```
$ cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0b22ce51-8e72-466c-8247-426d0c26c212 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=aaa10e10-3d84-4119-8cff-996b3a77a0e6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
tmpfs           /dev/shm        tmpfs   defaults        0       0
```

Does anyone have any ideas, because a laptop without a working touchpad is quite useless on the road?! Thanks in advance...

---

### Post by unihiekka on 2009-08-14
Anyone?

---

