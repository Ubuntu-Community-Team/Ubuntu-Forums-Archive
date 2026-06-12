---
title: "Cannot see files in a CD!!!"
date: 2006-01-29
forum: Hardware &amp; Laptops
---

### Post by barisurum on 2006-01-29
Hi. 
    Its weird but I cannot see some of the files in CDs!
   The drive is mounted but does not open in nautilus automatically.
   And when I open it in nautilus I cant see all files I only see some of them!!
   It happened after I installed the automatix and did the CDROM drive auto eject thing.
    Please help I have to reach some files. S - O - S!

   fstab:

   # <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/extraswap      none            swap    sw              0       0  
/dev/hda1       /media/hda1     ntfs    ro,users,gid=users,umask=0002,        0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

     mount output

/dev/hdc on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=maniac)
/dev/hdd on /media/cdrom1 type iso9660 (ro,noexec,nosuid,nodev,user=maniac)

---

### Post by towsonu2003 on 2006-01-29
this won't be the solution... to see and get the files (as it's an emergency):
open a terminal,
```
cd /media/cdrom0 (this will take you to cdrom0)
ls (this will list all files or folders in cdrom)

```
use cd to go into a folder (cd somefolderwithincurrentplace or cd /media/cdrom0/somefolder)
use cp to copy a file (cp /file/in/cd /copy/to/here)
use cp -r to copy a folder (cp -r /somefolder/tocopy /copy/thefolder/here)
best place to copy them is the desktop (~/Desktop)
use your tab button (in your keyboard) to complete the names of folders/files you are writing.

other than this workaround, no idea... try View>Show Hidden Files in nautilus?? maybe posting/moving this to the automatix forum? sorry, very clueless...

---

