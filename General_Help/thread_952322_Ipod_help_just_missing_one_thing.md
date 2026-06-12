---
title: "Ipod help just missing one thing"
date: 2008-10-19
forum: General Help
---

### Post by heatmaka on 2008-10-19
I been trying for a long time to get my ipod connected, but Ubuntu just wont regonized it. I'm using Amarok, and it does not pick it up either. When i run "/etc/mtab" in terminal, the file is empty?!?!

When is run "sudo gedit /etc/fstab" I get this : ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3f4e5eb8-c292-4c96-83e4-4ae97c64fc9d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=e51a1a46-95e8-48be-a8dd-7560d50a62e2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdc2 /media/iPod vfat nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8 0 0
```

I tried all the updates, i got all the sypnatic ipod related things. What do i do now?!?!

---

### Post by b0b138 on 2008-10-19
Try removing "/dev/sdc2 /media/iPod vfat nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8 0 0" from fstab and rebooting.

---

### Post by heatmaka on 2008-10-20
that dint change a thing some one help please

---

