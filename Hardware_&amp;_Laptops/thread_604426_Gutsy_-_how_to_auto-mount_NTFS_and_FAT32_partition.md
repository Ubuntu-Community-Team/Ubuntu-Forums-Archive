---
title: "Gutsy - how to auto-mount NTFS and FAT32 partitions?"
date: 2007-11-06
forum: Hardware &amp; Laptops
---

### Post by weird_c00kie on 2007-11-06
'Ello :)

I've just had a relatively painless installation of Gutsy and I'm trying to get my other drives to auto-mount

here's what *sudo fdisk -l* gives me

```
Disk /dev/hda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cf911

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       13986   112342513+  83  Linux
/dev/hda2           14362       38913   197213940    b  W95 FAT32
/dev/hda3           13987       14361     3012187+   5  Extended
/dev/hda5           13987       14361     3012156   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7b5a08df

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9561    76798701    7  HPFS/NTFS
/dev/hdb2            9562       24321   118559700    b  W95 FAT32

```

How do I make them auto-mount? In Feisty I got Automatix to do it for me and it worked beautifully, but I've been hearing bad things about Automatix as of late, so I thought I'd do it the more difficult way.
I also have an external hard disk which is also FAT32 and I'd like that one to automatically mount as well whenever I connect it.

Oh yeah, and my fstab looks like this if anyone needs it

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=f01b34ba-108e-4341-9943-f9122317c4c2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=44fde93e-aae0-4ff9-99db-a80fdfe21f22 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
```

Many thanks in advance for any help provided :)

---

### Post by ROBarber on 2007-11-06
[http://www.psychocats.net/ubuntu/mountwindows]("http://www.psychocats.net/ubuntu/mountwindows")

good luck

---

### Post by weird_c00kie on 2007-11-06
trying to read that makes my brain hurt. i'll have to have a go at it tomorrow after i've had some rest. it really shouldn't be this difficult. for a novice user, this is a VERY un-user-friendly way of mounting partitions that should load by default

but that's hardly your fault. thanks for the link :)

---

