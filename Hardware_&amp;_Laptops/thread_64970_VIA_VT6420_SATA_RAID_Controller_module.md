---
title: "VIA VT6420 SATA RAID Controller module?"
date: 2005-09-12
forum: Hardware &amp; Laptops
---

### Post by Klakier on 2005-09-12
Hello. I want to turn on DMA SATA drive with this controller

**VIA VT6420 SATA RAID Controller (rev 80)**


Which module should I add in **/etc/modules** to get it working with DMA

Now I get that when I'm trying to turn on DMA:

[B]mc@ubuntu:~$ sudo hdparm -d1 /dev/sda

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
[/B]

---

