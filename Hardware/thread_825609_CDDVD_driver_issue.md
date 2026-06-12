---
title: "CD/DVD driver issue"
date: 2008-06-11
forum: Hardware
---

### Post by pabach on 2008-06-11
this is a problem of my own creation... i'm relatively inexperienced ubuntu user so when i upgraded i dropped my old hard drive with xubuntu into a new machine to save reconfiguring. I'm really impressed how easy this was and how well it works generally ...with only one problem: the new sata optical drive is not mounting correctly. is this a driver issue? is there a simple solution without reinstalling?

this is my /etc/fstab if that is any use:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=9632c5df-138a-4b6a-b408-d2e4cfd1cd71 /               ext3    relatime,errors=remount-ro 0       1
# /dev/hda5
UUID=3cdcf3f3-9ce0-45be-8431-e75ab9195f9d none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

