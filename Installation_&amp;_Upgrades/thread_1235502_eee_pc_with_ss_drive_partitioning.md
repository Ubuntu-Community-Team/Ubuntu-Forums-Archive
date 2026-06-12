---
title: "eee pc with ss drive partitioning"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by ulrith on 2009-08-09
Hello all!

I just want to continue [this thread]("http://ubuntuforums.org/showthread.php?t=750526") because I have question of partitioning of my Asus Eee PC 901 with state solid drive for Ubuntu OS (Easy Peasy).

I have selected non-journaling ext2 file system for /root (first 4Gb drive) and /home (second 16Gb drive) partitions and no swap partition (as [adviced]("http://ubuntuforums.org/showpost.php?p=4685788&postcount=5") by **bradwilliamson**).

My fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=662ef4ed-0cfe-408a-96c4-df5e8f893eaa /               ext2    noatime,errors=remount-ro 0       1
# /dev/sdb1
UUID=7e789437-a2e9-4bec-9ebc-feaa4447e9ca /home           ext2    noatime        0       2
# settings added by eeepc-tweaks
tmpfs        /tmp        tmpfs    defaults,noatime,mode=1777    0 0
tmpfs        /var/tmp    tmpfs    defaults,noatime,mode=1777    0 0
tmpfs        /var/log    tmpfs    defaults,noatime,mode=0755    0 0
```

I wonder should I add 'noatime' to *proc* file system also and, may be, 'nodiratime' to all entries as **dcstar** [adviced]("http://ubuntuforums.org/showpost.php?p=4706074&postcount=21")?

Thank you!

---

