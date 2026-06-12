---
title: "Hp Pavilion dv6130 us"
date: 2008-11-17
forum: Hardware
---

### Post by bleja on 2008-11-17
Hi 
How can i install and fix my webam to work on ubuntu 8.10 gnome?

Hp Pavilion dv6130 us

lsusb:

Bus 005 Device 005: ID 1058:1100 Western Digital Technologies, Inc.
Bus 005 Device 004: ID 05ca:1810 Ricoh Co., Ltd
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 12a7:3160 Trendchip Technologies Corp.
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 047d:1048 Kensington
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

lsmod | grep videodev:

videodev 41344 1 uvcvideo
v4l1_compat 22404 2 uvcvideo,videodev

If somebody can help...Thanks

---

