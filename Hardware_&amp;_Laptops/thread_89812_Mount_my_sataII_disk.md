---
title: "Mount my sataII disk"
date: 2005-11-13
forum: Hardware &amp; Laptops
---

### Post by janbanan on 2005-11-13
I've been trying to mount my sataII disk by following the ubuntuguide:

In terminal i ran:
~$ sudo mount /dev/sda5 /media/windows/ -t ntfs -o nls=utf8,unmask=0222

getting the following message:

mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

What's wrong?

---

