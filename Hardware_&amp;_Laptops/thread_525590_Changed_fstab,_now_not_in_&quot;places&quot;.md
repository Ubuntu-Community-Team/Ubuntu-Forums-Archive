---
title: "Changed fstab, now not in &quot;places&quot;"
date: 2007-08-14
forum: Hardware &amp; Laptops
---

### Post by lsutiger on 2007-08-14
I changed my fstab so my mounted hard drives would not show on the desktop. But now the mounted drives do not show up in nautilus.
Here is my fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1
UUID=1136b0da-f3fe-4c13-9e36-90ce12e16c1d /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc2
UUID=0054796F54796874 /mnt/hdc2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdc3
UUID=C818DD1218DCFFFC /mnt/hdc3     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdc4
UUID=5f9d0e5e-fad8-4217-96d6-34fd283a1e5c none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
//192.168.1.15/ftp.affordablerto.net    /mnt/server        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.1.15/brian    /mnt/brian-serv        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```
I want all of these to show up in nautilus. I can get to them by navigating to /mnt/DRIVE, but that is a pain.
Thanx in advance!

---

### Post by merlinus on 2007-08-14
Wonder why you edited the drives out of /etc/fstab, when you could have simply disabled the icons from showing on your desktop with the gconf tool?

-merlin

---

### Post by lsutiger on 2007-08-14
I still want removable media to show up

---

### Post by merlinus on 2007-08-14
Looks like you cannot have it both ways....

-merlin

---

