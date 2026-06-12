---
title: "I can't mount a ntfs partition"
date: 2007-11-06
forum: Hardware &amp; Laptops
---

### Post by tuxilico on 2007-11-06
Hi friends, my problem is that i have Gutsy and Windows (two partitons ntfs), and Gutsy correctly recognized both partitions (hda1, hda3) and put tow acces on the Desktop... before... but now, i don't know why, it only mount just hda1, but not hda3... i've tried to mount manually but i can't do it because the system refuses... I checked fstab but i don't see nothing wrong , this is the file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda5
UUID=e1b88b73-7726-45cf-9c64-35017ca6875d /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=181C8F651C8F3D2E /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda3
UUID=7C28FF1828FECFDE /media/hda3     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda6
UUID=12860bbb-a8a4-4e53-8b93-fcd2f4bac578 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0


as you can see both, hda1 and hda3, have same configuration, but system mounts just hda1!! this situation begins after i connected an external USB hd. 

if anybody know how to fix this... please tell me :( 

(Please excuse my english...;))

---

### Post by ROBarber on 2007-11-06
use this link
[http://www.psychocats.net/ubuntu/mountwindows]("http://www.psychocats.net/ubuntu/mountwindows")

good luck

---

