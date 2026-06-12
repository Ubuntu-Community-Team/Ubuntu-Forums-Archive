---
title: "Can't write to mounted partition"
date: 2007-06-29
forum: Hardware &amp; Laptops
---

### Post by PopcornEaterMan on 2007-06-29
I have a 20 gb ext3 partition  and a 50 gb ext2 partition.  
I've added the last line to mount the 50 gb partition as "storage".  After booting up, there is a new icon on the desktop called "storage".  However, when I attempt to write to it, by right clicking and attempting to create a new file, the OS tells me I do not have write privs.  This appears to be some kind of permissions issue.  I've made media/storage readable / writable (chmod 777 /media/storage).  I'm not sure what I did wrong.  If I change the line to be ext3, then the partition doesn't mount at all.

Here is my fstab file: 

# [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=845239d9-a7c1-44df-9d5d-301fe223fdbf /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=b8d80958-78fd-424c-a88c-143daae3db69 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
tmpfs        /dev/shm    tmpfs    defaults,ro    0    0
/dev/hda3    /media/storage    ext2    auto,user,exec,rw,async    0    0

---

### Post by merlinus on 2007-06-29
Try this:

```

    sudo chown -R username:username /media/storage

```

username is your login id.

-merlin

---

### Post by PopcornEaterMan on 2007-06-29
what's the default ownership?

---

### Post by merlinus on 2007-06-29
Right-click on Files System /media/storage, select Properties, then Permissions.

The default varies on how you set it up, or how ubuntu detected the partition during installation.

-merlin

---

