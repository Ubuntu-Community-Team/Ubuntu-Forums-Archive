---
title: "Mounting an External HFS+ drive on Ubuntu"
date: 2012-11-04
forum: Hardware
---

### Post by M477H145 on 2012-11-04
Hello,

I'm running Ubuntu 12.10 in a dual-boot on my MacBook Pro 8.2.
I'm trying to mount an external hfs+ drive but it doenst seem to be working at all. 

I tried several things like hfsprogs, hfsutil, etc..

Ive got the following message when I try to mount from the finder:

Error mounting /dev/sdb2 at /media/matthias/Iomega_HDD: Command-line `mount -t "hfsplus" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdb2" "/media/matthias/Iomega_HDD"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Can someone help me with this one?

Greetings

---

### Post by M477H145 on 2012-11-06
Nobody that can help me with this problem? :(

---

