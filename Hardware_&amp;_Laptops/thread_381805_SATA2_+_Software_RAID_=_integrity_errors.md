---
title: "SATA2 + Software RAID = integrity errors"
date: 2007-03-11
forum: Hardware &amp; Laptops
---

### Post by NullPointerException on 2007-03-11
Hi,

I have 2 identical servers Dell PowerEdge 850 with integrated SATA2 controller. Each one has 2 SATA2 HDD which I mounted in one software RAID-1. I installed Linux Ubuntu Edgy. The system started up and worked. But then I found any strange behavior of data in my HDD: some files start to disappear and fsck shows integrity faults. This behavior take place in both servers and happens especially after short writes (like change attributes, file name, etc...).

What may be the cause of these data-lost? A software RAID or incompatibility of my SATA2 controller with linux kernel? I've ordered 3ware RAID controllers to create a hardware RAID, I hope it will resolve my problem.

Saludos,
Antón

---

