---
title: "Can't mount Fat32 partition rw at boot"
date: 2005-06-13
forum: Hardware &amp; Laptops
---

### Post by greenstar on 2005-06-13
I need some help getting my Fat32 partition to mount with read & write permissions for all users, so I went to the Ubuntu Guide and followed instructions at 

[http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat)

Just so you can see that I did it as the guide proscribed, here is the contents of my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdd6       /               reiserfs notail          0       1
/dev/hdc3       none            swap    sw              0       0
/dev/hdd1       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hde        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdc4       /mnt/Storage1   reiserfs rw,user,auto   0       0 
/dev/hdc5       /mnt/120GB      ntfs    ro,user,umask=0222  0       0 
/dev/hda5       /mnt/OS-Share   vfat    rw,user,auto,umask=000    0       0 
/dev/hdd4       /mnt/Storage2   reiserfs rw,user,auto   0       0 
/dev/hdd5       /mnt/160GB      ntfs    ro,user,umask=0222  0       0 

on the ntfs & fat32 partitions, if I remove all options except for umask value, as the guide shows, the partitions do not automount. So, I split the difference as far as the options go, and the only thing I'm missing is user write support on the Fat32 partition. I can't seem to get past this... HELP!

Thanks for your time,

greenstar

---

### Post by greenstar on 2005-06-14
I found my own answer in a couple of other forums.  Here are the links:

[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=331409&highlight=mount+fat3+read+write](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=331409&highlight=mount+fat3+read+write)

[http://my.opera.com/forums/showthread.php?s=&threadid=83440](http://my.opera.com/forums/showthread.php?s=&threadid=83440)

And here's the fstab line in question:

[COLOR=Blue]/dev/hd??       /wherever  vfat    nodev,noexec,nosuid,gid=users,umask=0007    0       0[/COLOR]

just modify:

[COLOR=Blue]/dev/hd??[/COLOR] to the appropriate partition & 

[COLOR=Blue]/wherever[/COLOR] to the mount point you prefer

[COLOR=Blue]gid=[/COLOR]your user group

edit: fix typo & add gid option tip

---

### Post by greenstar on 2005-06-15
The fstab line I finally got working for me is:

[COLOR=Red]/dev/hda5       /mnt/OS-Share   vfat    rw,auto,users,gid=users,umask=0007   0       0 [/COLOR]

I hope this helps others get write permissions on Fat32 partitions.

greenstar

---

