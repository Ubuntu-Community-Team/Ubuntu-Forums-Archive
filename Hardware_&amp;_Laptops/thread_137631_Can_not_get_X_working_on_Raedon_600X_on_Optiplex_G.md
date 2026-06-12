---
title: "Can not get X working on Raedon 600X on Optiplex GLX620"
date: 2006-02-28
forum: Hardware &amp; Laptops
---

### Post by ulugeyik on 2006-02-28
I am trying to get X to start on Dell Optiplex GLX620. I believe it uses Raedon 600X. It gives me a whole bunch of errors in the log files and refuses to start. I tried both the live CD and a full installation (Breezy). I thought it may be due to lack of drivers for linux in general, so I tried a live Knoppix CD (4.0) and that worked without any problems. Only part that appears relevant from the logs is the following:
(--) PCI:*(1:0:0) ATI Technologies Inc unknown chipset (0x5b62) rev 0, Mem @ 0xf0000000/27, 0xfe9e0000/16, I/O @ 0xdc00/8, BIOS @ 0xfea00000/17
(--) PCI: (1:0:1) ATI Technologies Inc unknown chipset (0x5b72) rev 0, Mem @ 0xfe9f0000/16
Missing output drivers.  Configuration failed.

Any ideas/suggestions?

Ulugeyik

---

### Post by ulugeyik on 2006-02-28
I removed "ati" from the driver and used "vesa" and I got in. I do not quite understand why though.

---

