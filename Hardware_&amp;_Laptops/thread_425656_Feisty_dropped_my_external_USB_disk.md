---
title: "Feisty dropped my external USB disk"
date: 2007-04-27
forum: Hardware &amp; Laptops
---

### Post by SteveHoffmanUK on 2007-04-27
Upgraded today from Edgy to Feisty. All seemed to go OK, but I have discovered that it hasn't picked up my Freecom FHD-2 Pro USB 2.0 external hard drive. Dapper and Edgy picked it up straight away and I have been using it for my external backups.

How can I get it back on line, other than going back to Edgy? Not an option I'd want to take if I can avoid it.

---

### Post by SteveHoffmanUK on 2007-04-28
Hmmm

Rebooted this morning, and ....

1. After Grub started to load, screen went completely blank, nothing at all happened, didn't even get the Ubuntu splash screen. Eventually I pulled the plug on the system and turned it on again, and ...

2. This time got the splash screen, login and now the USB external disk is there and everything OK.

Doesn't exactly build confidence. Just how stable IS Feisty, I wonder? Ah, now I see some new updates. Maybe they will help. OTOH, maybe they will bork the whole system. Here we go ...

ON EDIT: Results appear to be completely random:
1. After two complete closedowns of Feisty, the USB disk appeared once, was absent the other time.
2. After two restarts of Feisty, the USB disk appeared once, was absent the other time.

---

### Post by SteveHoffmanUK on 2007-04-29
Here is my /etc/fstab contents:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=2dde783c-8b00-47df-9e29-899b55941f7f / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=bbafafdb-80cd-40e4-8b78-13ca7f70ef13 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
#LABEL=fhd2-pro  /media/fhd2-pro  vfat    defaults,users  0  2
```

Newbie here: don't really understand fstab contents. The external hdd is the last entry (fhd2-pro). 

Can someone look at that entry and say if they see anything that might cause the disk sometimes to be picked up by Feisty and sometimes not?
Does the "vfat" mean that it's a FAT32 file? It shouldn't be - it should be ext3.

Thanks for your help.

---

