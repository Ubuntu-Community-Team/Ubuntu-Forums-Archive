---
title: "See All hard drive parameters"
date: 2007-02-19
forum: Hardware &amp; Laptops
---

### Post by alimovz on 2007-02-19
Hey guys,

I am trying to figure out my hard drive vendor. I am logged in remotely and cannot pull it out. Can anyone give a command to do it? 

Thanks.

---

### Post by 1aB on 2007-02-19
$ dmesg | grep <hd-device>


example from my laptop:

$ dmesg | grep hda
hda: FUJITSU MHU2100AT, ATA DISK drive
hda: max request size: 128KiB
hda: 195371568 sectors (100030 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
hda: cache flushes supported
hda: hda1 hda2
EXT3 FS on hda2, internal journal

And if you want even more information about your HD:
$ sudo hdparm -i /dev/hda

---

