---
title: "how to get ServeRAID 6i to work in Ubuntu5.10"
date: 2005-12-08
forum: Hardware &amp; Laptops
---

### Post by Mart.Verburg@c2i.net on 2005-12-08
Installastion works fine, but after reboot there is a message
[4294169.311000] PCI: Cannot allocate recource region 1 of device 0000:03:04.0
Loading, please wait....
After that there is some activity on the drives (a RAID1 logical array which i set up using the ServeRAID support CD, v7.10b that came with the card) and the machine hangs completely.

The server i'm installing is a IBM xSeries 306.

I've been trying with Debian before, but never got past the installer loading the IPS module for the ServeRAID 6i.  I've been wondering if there is a driver conflict with the driver for the on-board AIC7901 SCSI U320 controller.  

Any help appreciated
Mart

---

