---
title: "Lost capacity of USB memory stick"
date: 2007-01-17
forum: Hardware &amp; Laptops
---

### Post by guy.murray on 2007-01-17
Hi,
   a friend recently gave me a nominal 4Gb USB stick on which he had installed some proprietary secure partition which had gone banana shaped. The device now only shows 2Mb capacity. My task was to try and get rid of this partition.

I figured that 

dd if=/dev/zero of=/dev/hdg

would blow away any partitions on the stick and allow me to cfdisk it, but no, dd could only see the 2Mb.

Is there anything else I can try before tossing it into the skip?

Guy

---

### Post by CameronCalver on 2007-01-17
Have you tried Gparted

---

### Post by guy.murray on 2007-01-18
Gave Gparted a try, but still could only see 2 Mib.

G

---

### Post by dannyboy79 on 2007-01-18
is there data on this drive anywhere? if not than just reformat it! if gparted is only seeing 2mb, than delete this partition and create a new one which should allow to create the entire 4gb and the format it. also, sometimes you'll get readings which aren't correct even though the drive does have all 4gb still there.

---

