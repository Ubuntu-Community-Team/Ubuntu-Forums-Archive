---
title: "[SOLVED] nvRaid and Multi-Path IO"
date: 2007-08-16
forum: Hardware &amp; Laptops
---

### Post by raijinsetsu on 2007-08-16
My question is: will Ubuntu(and linux in general) use both channels of my nvraid (nvraid = bios backed software raid) simultaneously to get the speed increase? Or is there no benefit to software raid on the nvraid other than data redundancy? Alienware (the manufacturer of my laptop) say that you get a performance boost when using raid-0, but is that true for this type of software raid?
The answers I get will help me when making the decision to go raid-0 or raid-1.

---

### Post by psusi on 2007-08-16
Wait... a laptop with raid?  

You might want to read [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto)

---

### Post by raijinsetsu on 2007-08-16
I know about fake raid... It's software raid...
But my question goes to the performance increase. If the software raid is functioning correctly, and using both SATA channels, then I should get extra performance out of raid-0. Not as much as hardware raid, but more than standard disks. If the software does not use both channels, then there is no point to raid-0 (I don't need the space, I need speed OR data-redundancy).

---

### Post by psusi on 2007-08-16
Yes, it uses both channels ( unless you are talking ide with two disks on the same ribbon ), and the performance difference between software and hardware raid0 is imperceptible.  Hardware raid really only matters for LARGE raid configurations... like a raid-5 of 4 raid-5s of 6 disks ( 24 disks total ).

---

