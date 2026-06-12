---
title: "Missing disk partition numbers"
date: 2008-05-15
forum: Hardware
---

### Post by Crossroads on 2008-05-15
When I plug in my external FireWire drive, the log files show, for example:
May 15 21:46:51 ubuntu kernel: [  580.210629]  sda: sda2 sda3 < sda5 sda6 >

GPartEd shows a similar view of the disk. It has 1 primary partition and 2 logical partitions.

But where are the partitions sda1 and sda4?

Attached are the GPartEd and Windows Disk magagement views of the disk.

[Hope this is the right forum, if not, please move it.]

---

### Post by Oldsoldier2003 on 2008-05-16
> **Crossroads said:**
> When I plug in my external FireWire drive, the log files show, for example:
May 15 21:46:51 ubuntu kernel: [  580.210629]  sda: sda2 sda3 < sda5 sda6 >

GPartEd shows a similar view of the disk. It has 1 primary partition and 2 logical partitions.

But where are the partitions sda1 and sda4?

Attached are the GPartEd and Windows Disk magagement views of the disk.

[Hope this is the right forum, if not, please move it.]

i don't know what the deal is with sda1, but sda4 is traditionally reserved for zipdrives.

---

