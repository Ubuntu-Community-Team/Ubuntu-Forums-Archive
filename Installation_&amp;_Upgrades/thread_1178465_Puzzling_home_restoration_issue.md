---
title: "Puzzling /home restoration issue"
date: 2009-06-04
forum: Installation &amp; Upgrades
---

### Post by MaindotC on 2009-06-04
I'm trying to restore my /home partition to a clean installation - like on the psychocats.net tutorial.  For some reason, when I tell fstab to use the partition that has /home on it, it mounts it as /home/home and thus my logins don't work correctly.  /dev/sda3 is my /home partition from the previous installation.  Here's the line in my fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=517b5070-edb3-4127-91dd-f1e7311b3ea0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
/dev/sda3	 /home           ext3    relatime        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

I've also tried using the nodev and nosuid options specified in psychocats.  What gives?

---

### Post by pastalavista on 2009-06-04
You could try ```
blkid /dev/sda3
``` and replace /dev/sda3 in fstab with the UUID number.

---

