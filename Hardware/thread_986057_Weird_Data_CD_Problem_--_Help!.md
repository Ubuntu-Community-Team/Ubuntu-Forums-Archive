---
title: "Weird Data CD Problem -- Help!"
date: 2008-11-18
forum: Hardware
---

### Post by gilf on 2008-11-18
Ubuntu 7.10, all updates current, Dell GX60.

Inserting a data CD results in the system mounting it as an audio CD, and Sound Juicer claims it is some bogus audio title. Example:

1.) I insert the MS Office 97 CD to try to installl it under Crossover Office.

2.) On the desktop appears an Audio CD Icon and Sound Juicer asks if I want to play the "Richard Feinman Lectures Volume 1"

This happens with other CDs as well and the system makes up bogus titles for audio content -- symphonioes, etc.

What the heck is going on?

Here's fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=c4df93d8-e109-4460-ac61-724fc65baf0e /               reiserfs notail          0       1
# /dev/sda1
UUID=0EFCB7D0FCB7AFF7 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=bb1fb809-68ca-4d89-94af-78fcd4ee1161 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0 
```

Any help would be appreciated!

---

