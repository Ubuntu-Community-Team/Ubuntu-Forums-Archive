---
title: "Partition issues"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by javadog on 2009-04-09
Hi there. I ran the Ubuntu 8.10 installer, when it got to the partition step, I selected a partition of roughly 25GB. It began running the crashed. When I re ran the installation in picked up that I only have one partition and that should it create the desired partition it would be the complete HD (80GB) in other words it is not picking up my XP partition nor the 5 GB of recovery the my IBM has located to that.

Any help would be appreciated.

---

### Post by facefur on 2009-04-09
I'm not certain, but it sounds like your first installation may have damaged or overwritten your partition table. If you did not clearly identify each partition during the manual selection, the MBR may not have the proper pointers to each pre-existing partition, and you may have overwritten them as well.  If you have a Windows CD you could try using the Windows Rescue process and see if it can restore it.

There are also a few free partition repair programs out there that can try and find the actual partitions themselves and repair the MBR for you.  Sorry, I don't have the references handy, but you could Goggle "MBR Repair" or a similar topic.

---

