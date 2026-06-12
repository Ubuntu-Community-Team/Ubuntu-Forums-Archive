---
title: "Harddrive repartition"
date: 2006-01-17
forum: Hardware &amp; Laptops
---

### Post by arjun on 2006-01-17
Hi. I want to make my root partition 10 GB smaller and add that disk space to my /home partition.  Can I do this without formatting my drive?

---

### Post by heimo on 2006-01-18
[quote=arjun]Hi. I want to make my root partition 10 GB smaller and add that disk space to my /home partition.  Can I do this without formatting my drive?[/quote]

It may be quite easy, or quite hard to accomplish, depending on the current partitioning. Basicly, you A) **BACKUP **everything and B) boot from live CD (Knoppix, Ubuntu Live CD or such) and use qtparted or gparted to resize your partitions. If those partitions are next to each other, this should be quite easy to do.

---

