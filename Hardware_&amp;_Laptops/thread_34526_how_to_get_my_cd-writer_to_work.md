---
title: "how to get my cd-writer to work?"
date: 2005-05-15
forum: Hardware &amp; Laptops
---

### Post by boebel on 2005-05-15
Hi,
In the past I've tried a lot of different distros and they all recognized my cd-writer but unfortunately kubuntu only shows the device as a cdrom reader. K3B says "can't find a suitable writer". Can anyone point me in the right direction please of how I can fix this? I've been searching with google and I've seen stories about /etc/fstab and about adding users to certain groups but I really don't know which is applicable to my situation. Here's my fstab: ```
     $ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>          <options>               <dump>  <pass>
proc            /proc           proc            defaults                0       0
/dev/hda4       /               reiserfs        notail                  0       1
/dev/hda2       /storage        ext3            defaults                0       2
/dev/hda3       none            swap            sw                      0       0
/dev/hdc        /media/cdrom0   udf,iso9660     ro,user,noauto          0       0
/dev/sda1       /mnt/sda1       vfat            rw,user,noauto          0       0
```

Any help very much appreciated!

---

### Post by boebel on 2005-05-16
"kdesu k3b" showed me that the cd-writer is recognized as root
Editing /etc/group and adding myself to the "cdrom" group did the trick, yay :-)

---

