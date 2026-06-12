---
title: "Missing DVD Drive"
date: 2007-02-01
forum: Hardware &amp; Laptops
---

### Post by Mithrilhall on 2007-02-01
I'm trying to follow this DVDShrink howto ([http://ubuntuforums.org/showthread.php?t=27369)](http://ubuntuforums.org/showthread.php?t=27369)).

I see my DVD drive listed below but shouldn't I see it in the /dev directory as hdc? 

I have no hdc located in my /dev directory.


```

x@debian:/dev$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=4357660b-12d3-419d-a07f-c9795a91ad99 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=2d97e222-9117-4a46-8c03-658343f9fdcf none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1    /media/windows_c ntfs  nls=utf8,umask=0222 0    0
/dev/sda5    /media/windows_d ntfs  nls=utf8,umask=0222 0    0
/dev/sda6    /media/windows_e ntfs  nls=utf8,umask=0222 0    0
x@debian:/dev$                      

```

---

