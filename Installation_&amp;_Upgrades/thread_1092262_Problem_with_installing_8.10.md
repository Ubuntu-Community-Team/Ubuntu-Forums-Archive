---
title: "Problem with installing 8.10"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by 41214 on 2009-03-10
Hello (: I have a HP 6735 series laptop running Windows Vista basic. I have been trying to install Ubuntu 8.10 from CD with little success.

All goes well until I reach the partitioning part of the installation. I only have two options: guided, which would use the whole of my hard disk, and manual.

I want to dual boot, so should I do my partitioning in Windows prior to installing Ubuntu? When I try and do this using the built in program in Vista, I get "access is denied", even though I am logged into the administrator account etc and I can't seem to find a solution to this problem either. Would it be advisable to use a third party programme to do this?

---

### Post by logos34 on 2009-03-10
hmm, not sure why it won't let you resize if you're administrator.

The general rule is to use Vista's own in-built Disk Management tools to resize whenever possible.  You can try using Gparted on the ubuntu live cd (system>admin>partition editor), but you'll have to fix a few things afterward to make vista bootable again.  Either that or use a non-free utility like Partition Mangic.

Read this:
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

good luck

---

### Post by jtu on 2009-03-13
> **41214 said:**
> Hello (: I have a HP 6735 series laptop running Windows Vista basic. I have been trying to install Ubuntu 8.10 from CD with little success.

All goes well until I reach the partitioning part of the installation. I only have two options: guided, which would use the whole of my hard disk, and manual.


You are using the alternate 8.10 CD, aren't you?  The live CD doesn't play nice with existing partitions on the HD

---

