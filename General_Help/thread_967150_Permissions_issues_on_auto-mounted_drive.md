---
title: "Permissions issues on auto-mounted drive"
date: 2008-11-01
forum: General Help
---

### Post by Forlornity on 2008-11-01
Hello all, simple question I'm sure, but one I can't solve right now:
I have two ntfs partitions on Hard drives I'm using to store my media and suchlike. During the Intrepid Install, I chose manual partitioning and told it to use these drives as ntfs and to mount them within /media on folders I'd specified. They work fine in general, I can access everything, edit everything and execute everything, the problem arises when I try to access the files via my apache server: I have certain files symlinked in from the drives (to avoid redundancy and prevent me from having to change two files for updates) but the permissions on the files allow only the owner and group of the files to do anything to them. Normally this'd be fine for me, I just change the group to include the server, but when I try a chown, chmod or chgrp command, it does nothing, the files remaining as they were:
owner: root, group: plugdev
permissions: 770

My fstab looks like this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=01d017b6-4135-4f05-9c20-db2a25594092 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=8a650180-2542-4d9b-a410-7ed5c55097eb /home           ext3    relatime        0       2
# /dev/sdb1
UUID=D6B42902B428E6A9 /media/Chipper  ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=BA54AA5F54AA1E5F /media/Media    ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=289CCBFF9CCBC612 /media/Windows1 ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=4084E3F884E3EE7A /media/Windows2 ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda8
UUID=0068c567-f2b9-4002-a74a-15ca22d67758 /var            ext3    relatime        0       2
# /dev/sda4
UUID=27102d61-2213-4532-8a4d-84614242b434 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Thanks in advance!

- Forlornity - KitB

---

