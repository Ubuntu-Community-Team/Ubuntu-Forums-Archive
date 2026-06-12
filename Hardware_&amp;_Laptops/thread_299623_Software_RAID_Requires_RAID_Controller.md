---
title: "Software RAID Requires RAID Controller?"
date: 2006-11-14
forum: Hardware &amp; Laptops
---

### Post by Hase on 2006-11-14
I'm trying to get my file sever moved over to linux and need now get my RAID 1 setup.  I have the two identical drives on a SI 680 that can be configured during the boot.  I have been having trouble mkfsing or fdisking any array that has been setup by the card on boot.  When the card is configured to separate the drives (i.e. act as an IDE controller, not a RAID controller), no problem, read, write, whatever.

Using mdadm, do I need to set the SI 680 to leave the cards separate and just merge them through mdadm? Isn't this much less efficient than using the chipset on the controller to... well, "control" the drives/array?

Anyone had any luck with this card and RAID 1 or 0?

Thanks and Prost!

---

