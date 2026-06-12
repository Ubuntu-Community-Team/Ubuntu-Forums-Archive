---
title: "[SOLVED] second hard disk formated before ubuntu"
date: 2007-12-19
forum: Hardware &amp; Laptops
---

### Post by xodroolis on 2007-12-19
New to Ubuntu

I have two disk drives
1st:   40 gb
2nd: 240 gb
the 1st was formated and got installed Ubuntu (Gutsy) 7.10
The 2nd was already ntfs formated with my previous windows system and is just for file storage
It hasn't and it hadnt no operating system. Just files
I can access it. I can read the files
But!
The system doesnt see me as an administrator of this disk
so i cant write or erase files from it
The tab on its properties with the ownerships (i dont know how it is called in english ubuntu) is not accessible

Any help?

---

### Post by LaRoza on 2007-12-19
Post the contents of:

/etc/fstab

---

### Post by xodroolis on 2007-12-19
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1

UUID=314e3b90-6768-44a5-b144-0fd5224d590f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=acf8e8d7-3a8b-4fae-aa48-28d7fecba6bf none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/hdc1 /media/hdc1 ntfs nls=utf8,umask=0222 0 0

---

### Post by LaRoza on 2007-12-19
> **xodroolis said:**
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1

UUID=314e3b90-6768-44a5-b144-0fd5224d590f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=acf8e8d7-3a8b-4fae-aa48-28d7fecba6bf none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
**/dev/hdc1 /media/hdc1 ntfs nls=utf8,umask=0222 0 0**

Here is my:

```

UUID=242CF8152CF7E02A /media/ISO      ntfs    defaults,umask=007,gid=46 0 

```

It lets me do what you want to do, but don't use my UUID! (Use /dev/hdc1)

---

### Post by psusi on 2007-12-19
You can't write to it using the conventional ntfs driver, you have to install and use ntfs-3g.

---

### Post by xodroolis on 2007-12-19
actually all went wrong when i changed the line as follows
/dev/hdc1 /media/ISO      ntfs    defaults,umask=007,gid=46 0

the 2nd hard disk was vanished

only when i turned it back like this
/dev/hdc1 /media/hdc1 ntfs nls=utf8,umask=0222 0 0
i found my disk again

---

### Post by xodroolis on 2007-12-19
> **psusi said:**
> You can't write to it using the conventional ntfs driver, you have to install and use ntfs-3g.

i have it installed. what should i do next?

---

### Post by xodroolis on 2007-12-19
its ok now... i solved the problem following the guide
[https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite](https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite)
thanks anyway

---

