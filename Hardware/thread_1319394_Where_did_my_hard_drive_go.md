---
title: "Where did my hard drive go?"
date: 2009-11-08
forum: Hardware
---

### Post by sschafer on 2009-11-08
I have a 60g Western Digital IDE drive attached to a PCI controller that was working fine until I upgraded to 9.10 and then it disappeared.   Here are the interesting facts:

[LIST]
[*]If I boot into the 2.6.24-24 kernel I can see the partition and mount it, no problem.
[*]If I boot into the current kernel (2.6.31-14) it seems to be gone
[LIST]
[*]It does appear in /proc/partitions (both the drive and the partition)
[*]It does not appear in /dev (the drive does but not the partition)
[*]There's nothing in /dev/mapper that points to it that I can tell
[*]In gparted, the partition appears to exist.
[*]In palimpsest, it looks like the drive is unpartitioned.  If I attempt to create the partion and format, I get an error saying it's in-use.
[/LIST]
 
[/LIST]
This is an AMD/64 machine.  The boot partition is also on the same PCI controller and is working fine.  The primary IDE drive on the motherboard controller is also working fine.

Any thoughts?

---

