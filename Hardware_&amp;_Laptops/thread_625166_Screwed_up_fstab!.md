---
title: "Screwed up fstab!"
date: 2007-11-27
forum: Hardware &amp; Laptops
---

### Post by nathanhillinbl on 2007-11-27
I was trying the "tweaks" found here:
[http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed)

and i think i royally screwed up my fstab. When i go and try the last step of the instructions on that page
 ```
sudo tune2fs -o journal_data_writeback /dev/hdc
```

i get:
```
 sudo tune2fs -o journal_data_writeback /dev/hdc
tune2fs 1.40.2 (12-Jul-2007)
tune2fs: Bad magic number in super-block while trying to open /dev/hdc
Couldn't find valid filesystem superblock.
nate@natesmonster:~$ 

```

I made a boneheadded move by not backing up my fstab which now looks like this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1
UUID=afb2c748-1184-4ff2-856d-26d894bcd630 /               ext3    defaults,errors=remount-ro,data=writeback,noatime 0 0       1
# /dev/hdd1
UUID=0ca97d67-fbf8-4748-9635-1554b45df1e9 /home           ext3    defaults,errors=remount-ro,data=writeback,noatime 0 0       2
# /dev/hdc5
UUID=2603e989-af08-41c7-8cf6-5a31bb993dac none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```


I'm guessing that if i restarted, i would have serious issues, so any help offered that would resolve this issue would be greatly appreciated.

--Nate

---

### Post by nathanhillinbl on 2007-11-27
Is there any way to auto-repair a fstab?

---

### Post by nathanhillinbl on 2007-11-27
bump..:)

---

