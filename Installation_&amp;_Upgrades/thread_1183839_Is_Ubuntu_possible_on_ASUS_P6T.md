---
title: "Is Ubuntu possible on ASUS P6T?"
date: 2009-06-10
forum: Installation &amp; Upgrades
---

### Post by jpbrowning on 2009-06-10
Jaunty Jackalope install fails to see SATA Raid on my ASUS P6T motherboard system. Contacted ASUS, they say the Raid chip manufacturer (Marvell) should supply Linux driver. Contacted Marvell, they say ASUS should supply the Linux driver. (Who's on first?) Any solution?

---

### Post by wkulecz on 2009-06-10
Read up on "fake raid" and/or DM raid.  I'd suggest you not use it, unless you need both Windows and Linux on the same partitioned array (IMHO way more trouble than its worth give how cheap hard drives are these days).

You should be able to see the Marvel controller as seperate SATA channels and create a software raid 1 (can't boot Linux from raid 5) using mdadm.  Although you may have to change the BIOS to put the controller in non-raid mode.

--wally.

---

### Post by jpbrowning on 2009-06-10
Thanks, Wally. Was hoping to use the RAID for that operating systems (dual boot Win 7 and Ubuntu) and use the other drive(s) for data, but having Ubuntu installed on a separate hard drive will do.

---

