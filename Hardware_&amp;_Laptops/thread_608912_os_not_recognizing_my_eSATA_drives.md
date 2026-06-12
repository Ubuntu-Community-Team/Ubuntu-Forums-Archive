---
title: "os not recognizing my eSATA drives"
date: 2007-11-10
forum: Hardware &amp; Laptops
---

### Post by operand on 2007-11-10
Hi all,

I'm a complete beginner with linux/ubuntu but I wasn't sure if this fit in the beginner forum. 

I have an external enclosure with 4 sata drives in it that are connected to my pc via an eSATA pci card(SIL3124). Incase it helps, the product page for the enclosure is here: [http://www.norcotek.com/DS-500.php](http://www.norcotek.com/DS-500.php).

I can't see these drives anywhere through ubuntu. /dev doesn't list any sd* or scsi* devices(i'm not sure which would be the right one). 

I'm really clueless about how to go about diagnosing the problem. If it helps at all my fstab file has the following:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=3d27833c-8529-47e1-9672-64e20fc86559 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=29a50fc2-185f-4639-a150-7991e9f28c0d none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```



Any help at all is GREATLY appreciated. This is the last thing i need to get working :(

---

### Post by seraph47 on 2008-01-30
Hey, were you able to solve your problem? Please let me know, because I am considering purchasing the same enclosure.

---

