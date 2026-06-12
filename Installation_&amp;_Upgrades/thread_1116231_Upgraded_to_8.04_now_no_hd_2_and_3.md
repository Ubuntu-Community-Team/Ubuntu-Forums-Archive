---
title: "Upgraded to 8.04 now no hd 2 and 3"
date: 2009-04-04
forum: Installation &amp; Upgrades
---

### Post by leesway on 2009-04-04
I just upgraded to 8.04 I have 3 hd in the system. #1 is for sys files and 2,3 are for data. After the upgrade drives 2 and 3 are missing. Here is my fstab file contents.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=0ce55381-c7e0-4c1d-84b7-5c42bcfbba61 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=68f72d5d-169e-427a-89d1-3984f261e390 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd1 /media/HDD_2 ext3 defaults
/dev/hdc1 /media/HDD_3 ext3 defaults
# /dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by lswb on 2009-04-04
Hardy uses sdxx instead of hdxx to identify drives. Run the command

sudo fdisk -l

to see what your partitions are. The device names /dev/hdxx in /etc/fstab can be changed to /dev/sdxx as required, or even better, switch to mounting by the UUID instead. The command "sudo blkid" will return the UUIDs of your system, and you can edit your /etc/fstab, using the form of the existing lines that begin "UUID=...."

The advantage of using UUID (labels can be used as well) is that for various reasons, some systems will not consistently assign device names to the same disks at boot. Using UUID or label in /etc/fstab makes this not matter.

---

### Post by leesway on 2009-04-04
Thanks so much, that did the trick. Now the kids can get to their files.

---

