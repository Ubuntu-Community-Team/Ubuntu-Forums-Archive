---
title: "Read-Only Files Syste on SD reader"
date: 2008-03-25
forum: Hardware &amp; Laptops
---

### Post by krushr on 2008-03-25
I am having issues with my SD card reader in my eee pc, anyways when it mounts I can sometimes write, but then when i try to delete sometimes gives me a read-only fs dialog.  I hooked this up to a macbook via an usb sd reader, and it worked fine.  I think it is something to do w/ my fstab since i know its something that my ubuntu os is not doing when it mounts, it worked fine for a day after i hooked it up.  When I put dl'ed content on it and try to delete it, it almost always give me the read only dialog as well.

heres my fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d9b3cc60-6762-488a-b574-f88f0e524b12 /               ext2    defaults,noatime,errors=remount-ro 0       1
# /dev/sda2
UUID=7d904599-579f-4374-aa12-23154de974da none            swap    sw              0       0
# /dev/scd0       /media/cdrom0   udf,iso9660 user,exec 0       0

```

Thanks in advance.

It mounts by default at /media/disk btw, and btw i don't have a internal disk drive, just an external usb cdrom drive, how should i configure the scd0 if i don't have it right?

THX
THX:popcorn:

---

