---
title: "Mounting Problems"
date: 2007-11-10
forum: Hardware &amp; Laptops
---

### Post by ryanlhjess on 2007-11-10
Good day,

Below is my current fstab,  i would like to have all of my windows partitions mounted by default in ubuntu 7.10.   Help! 

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=e9cffe97-9528-42f4-b827-450b7a81f079 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=9894B97A94B95C06 /media/hda1     ntfs    defaults,umask=007,gid=1002 0       1
# /dev/hda5
UUID=74CCFD95CCFD523A /media/hda5     ntfs    defaults,umask=007,gid=1002 0       1
# /dev/hda6
UUID=f92b282c-28a2-4e37-b811-12c7cb7a35bc /media/hda6     ext3    defaults        0       2
# /dev/hdb2
UUID=C48427DC8427CFAA /media/hdb2     ntfs    defaults,umask=007,gid=1002 0       1
# /dev/hda7
UUID=3ca302f6-9ef2-4c52-9204-4e7aed1daea6 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

---

### Post by ofb on 2007-11-11
It looks like they are mounted as,

 /media/hda1
 /media/hda5
 /media/hdb2 

Are they not there? Or are you asking how to mount them somewhere else?

---

### Post by ryanlhjess on 2007-11-11
so....um they ARE mounted?

Well, i can't see them in my file manager....


ok wait, i can see them in /media  but it says that i don't have permission to access them.

Any ideas?

---

### Post by taurus on 2007-11-11
Try installing and using ntfs-3g to mount your ntfs filesystems.

```
sudo apt-get update
sudo apt-get install ntfs-3g ntfs-config
sudo ntfs-config
```

---

### Post by ryanlhjess on 2007-11-11
that worked thank you

---

