---
title: "Formating and Partitioning Drives"
date: 2008-09-09
forum: General Help
---

### Post by Mr.Macdonald on 2008-09-09
I need a utility to format and partition my drives that is command line(and/or interactive). FDisk won't work because (i may be wrong), it doesn't support EXT3.

Also I couldn't choose a format for an extended partition??

Now i could have no clue what i am talking about so please help me

---

### Post by bodhi.zazen on 2008-09-09
fdisk will make partitions.

you then format a partition from the command line as wall 

mkfs.ext3 /dev/sda1

See these links :

[http://ubuntuforums.org/showthread.php?&t=282018](http://ubuntuforums.org/showthread.php?&t=282018)

[http://tldp.org/HOWTO/Partition/fdisk_partitioning.html](http://tldp.org/HOWTO/Partition/fdisk_partitioning.html)

[http://tldp.org/HOWTO/Partition/formatting.html](http://tldp.org/HOWTO/Partition/formatting.html)

[http://linux.die.net/man/8/mkfs](http://linux.die.net/man/8/mkfs)

---

### Post by cdtech on 2008-09-09
Using your Live CD and "gparted" would work for ya....

---

