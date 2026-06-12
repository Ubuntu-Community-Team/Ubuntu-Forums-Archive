---
title: "Adding media drive"
date: 2008-10-21
forum: General Help
---

### Post by zetagirl on 2008-10-21
I have an hp personal media drive...In theory all i would have to do is hook it up and it would work..well when I did that I get an error msg saying  You are not privileged to mount the volume 'HP Personal Media Drive'.   

Any suggestions?


here is my fstab results

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=489be023-9ba0-4dac-81ff-cb717e6e656f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=50fb6460-8719-4e47-8295-c5877fe678bf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb5      /media/HP ntfs-3g force 0 0
/dev/sdb1     /media/MMCSD     auto     user,auto,exec,rw     0     0

---

### Post by freelinuxhelp on 2008-10-21
This link might help you: [https://answers.launchpad.net/ubuntu/+question/19865](https://answers.launchpad.net/ubuntu/+question/19865)

---

