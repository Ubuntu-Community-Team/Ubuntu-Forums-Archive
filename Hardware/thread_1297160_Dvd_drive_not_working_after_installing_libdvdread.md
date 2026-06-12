---
title: "Dvd drive not working after installing libdvdread"
date: 2009-10-21
forum: Hardware
---

### Post by inorganicangel on 2009-10-21
I cant seem to find anything that will help, here is my fstab 
```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=6dfe3558-1693-4ac0-a8d5-0d93f1181890 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d2113d2a-9157-419c-964f-6ada59bba0f3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 
```

---

