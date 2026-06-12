---
title: "Ubuntu 2004 can only detect 2disks"
date: 2021-08-27
forum: Hardware
---

### Post by piupiuisland on 2021-08-27
Hi guys,  I'm looking for your help on my disk problems..

Now I have a m2 Sdd(1TB) and a Hdd(4TB).  I bought a new m2 sdd(1TB), and installed it. 

However,  the system can only detect two Sdd, and seems the previous folder links point to the new sdd. $ sudo fdisk -l cannot detect Hdd.  
If I unplug the new sdd, Hdd works as normal. If plug all three disks,  only two ssd can be detected.. How can I solve the problem?

---

### Post by oldfred on 2021-08-27
Check your manual.
Many motherboards disable a SATA port if you use M.2 port.

---

### Post by piupiuisland on 2021-08-27
Thanks ! you saved me!!  The m2 port blocked SATA. change another SATA, it works now! thanks

---

