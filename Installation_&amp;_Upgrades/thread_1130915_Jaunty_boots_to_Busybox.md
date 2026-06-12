---
title: "Jaunty boots to Busybox"
date: 2009-04-20
forum: Installation &amp; Upgrades
---

### Post by Mobiesque on 2009-04-20
Hello all. 

Updated to jaunty last night and when I rebooted it hung when trying to find root then dropped me into an (initramfs) busybox shell. As far as I can tell from reading other posts / the release notes this caused by it changing the label it looks for in fstab.

That much I gather, and think it *may* be to do with my hdd now being called 'disk' when I already had an external labeled 'Disk'. Possibly. The problem is I don't have the foggiest on how to fix it.

Here is my fstab - any help MUCH appreciated.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=42e5f94c-9500-4ea3-9543-02a40b651d70 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=2c00b52d-7ff9-4916-b3c9-24c1b53e6fcc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

---

### Post by Mobiesque on 2009-04-20
Bump?

---

