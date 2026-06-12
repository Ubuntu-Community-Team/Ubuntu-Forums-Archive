---
title: "raid5 software"
date: 2006-01-30
forum: Installation &amp; Upgrades
---

### Post by ivan.virtuale on 2006-01-30
Hi,
I' ve got a big problem; my system (Ubuntu 5.10) is composed of 4 HD ata in raid software (boot ->raid1, / ->raid5).
When I've installed the server ,I done a mistake because I forgot to set a spare disk for my root partition (md2).
Now... if I wanna resolve this problem... have I to repeat the procedure of installation or can I do some operation on my mdadm.conf?
Help me please...

My mdadm.conf is:
DEVICE partitions
ARRAY /dev/md2 level=raid5 num-devices=4 UUID=5e2dfcde:768ac5a0:02824bf0:4dac06f6
   devices=/dev/sda6,/dev/sdc6,/dev/sdb6,/dev/sdd6
ARRAY /dev/md1 level=raid5 num-devices=4 UUID=e2f8e4cd:3ee31e4d:7c7f4ad3:d6a2a2ff
   devices=/dev/sda5,/dev/sdc5,/dev/sdb5,/dev/sdd5
ARRAY /dev/md0 level=raid1 num-devices=4 UUID=fff0cbce:98817369:67ae0fdb:815f87d6
   devices=/dev/sda1,/dev/sdc1,/dev/sdb1,/dev/sdd1

My fstab is:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/md2        /               ext3    defaults,errors=remount-ro 0       1
/dev/md0        /boot           ext3    defaults        0       2
/dev/md1        none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

