---
title: "No CD or DVD in Feisty"
date: 2007-04-21
forum: Hardware &amp; Laptops
---

### Post by am_pcguy on 2007-04-21
When I click on the CDROM in Nautilus I get the following error:
mount: block device /dev/cdrom is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/cdrom,
       missing codepage or other error
       in some cases useful info is found in syslog - try
       dmesg | tail  or so

Here is my /etc/fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=138b0e9c-e59d-4364-a9ce-4f30d629367f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=427fc544-8787-439b-b5a5-5b39da064041 none            swap    sw              0       0
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto     0       0


I've found this bug report in Launchpad I think it's related:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94119](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/94119)

---

