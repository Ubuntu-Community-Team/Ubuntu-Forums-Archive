---
title: "Server Edition - Can't See Raid Drives"
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by MR-808 on 2007-04-23
Hi All,

I'm a Linux newbie who's only been playing around with it for a couple of weeks.  I've run into a hitch in trying to setup a NAS box using Server Ed. 7.04.

When I type fdisk -l, it shows my boot/swap drive and my SATA drive, but not my RAID drive(s).  I originally had the RAID card & drives in a different box running S.E. 6.10, and they worked fine.  At that time I formatted the drive as an ext2  partition.  I have a copy of the 6.10 desktop version of Ubuntu, and if I boot the live cd, I can mount the RAID drive just fine.  So I don't think it's a hardware problem.

I used lspci -n and the Debian [device driver check page]("http://kmuto.jp/debian/hcl/") to confirm that my install of S.E. 7.04  included the driver for the RAID card (IT/ITE8212).

What do I do next?

Thanks!
Jeffrey

---

### Post by MR-808 on 2007-04-26
Nevermind.  I downloaded Debian 4.0, and it installed just fine.

---

