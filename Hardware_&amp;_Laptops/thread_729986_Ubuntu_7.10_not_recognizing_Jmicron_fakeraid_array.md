---
title: "Ubuntu 7.10 not recognizing Jmicron fakeraid array"
date: 2008-03-20
forum: Hardware &amp; Laptops
---

### Post by Metaluna on 2008-03-20
I have had Ubuntu 7.10 (32-bit) running on a Gigabyte GA-965P-S3 motherboard for several months w/ WinXP dual boot.  The other day I tried adding a pair of Maxtor 300GB drives in RAID0 to the onboard Jmicron JMB363.  I set up the array using the BIOS utility, and partitioned and formatted it as NTFS in WinXP.  In Ubuntu, however, the drives show up as individual devices (Right now they're /dev/sda and /dev/sdb), and there is nothing in the /dev/mapper directory except an entry named "control".  I've read some HOWTO's about using dmraid  to activate the array but since the drives don't show up in /dev/mapper, dmraid reports that there are no RAID arrays present, and I'm pretty much stuck at that point.

 I have the BIOS set for "RAID+IDE" and I have a PATA DVD writer plugged into the controller as well, in case that matters.  I've also done some searches and read that there may be known problems with the 363 under linux, but most people seem to at least get the drives to show up in /dev/mapper.

I do have a Sil3132-based PCIe card that I can try out as well.  Does anyone know if these work better with this kernel?

---

