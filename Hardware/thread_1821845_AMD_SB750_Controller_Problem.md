---
title: "AMD SB750 Controller Problem"
date: 2011-08-09
forum: Hardware
---

### Post by lister171254 on 2011-08-09
I have a Gigabyte motherboard (GA-MA790FXT-UD5P) with two controllers (AMD SB750, JMB322).

I'm running a RAID1 software array and the disks are plugged into the SB750 controller.

My problem is that during heavy disk I/O (ie. full backup of +400GB, full mdadm check of array) the system sometimes hangs.

With 'hangs' I mean that nothing is logged to the the logs, there is absolutely no disk activity, etc. Only way to recover is a reboot.

This does not happen every time during heavy disk I/O, but far to often for my liking.

Question is if this could be related to the controller. I have not tried the other controller as it has problems with SMART.

I have seen this problem on my current version of Ubuntu 11.04 and the previous version

---

### Post by .... on 2011-08-10
I would feel the southbridge heatsink when this happens (WARNING: it could be very hot). Gigabyte may not have tested the board with that much I/O. All too often, I find NB/SB cooling solutions inadequate, especially on cheaper boards, but even with good boards.
If you suspect SB temp might be the problem, you could try a bigger heatsink or more airflow.

---

### Post by lister171254 on 2011-08-10
Interesting point. My rig (CPU, GPU) is water cooled (but not overclocked)

---

### Post by .... on 2011-08-10
If you don't have air moving inside the case, SB temp could definitely be an issue. My suggestion is to use a quiet 120mm fan pointed at the SB. You could probably sit it on the bottom of your case if you don't move your system often, or you could zip tie it to the drive cage.

---

### Post by lister171254 on 2011-08-10
There is some airflow (ie. disks are cooled ok), but will follow your suggestion and let you know.

I think you may be on to something here as most of the time the system just hangs during unattended I/Os (ie overnight backup), but I have seen this at least twice when working and the system initially is that the mouse cursor slows down until it eventuall freezes completely.

Cheers

---

### Post by lister171254 on 2011-08-19
I've put a small fan on top the controller (separate on my motherboard) and have had not freezes since. Have completed big file operations (copy, backup, move) and everything stayed up.

Thanks for you help.

---

