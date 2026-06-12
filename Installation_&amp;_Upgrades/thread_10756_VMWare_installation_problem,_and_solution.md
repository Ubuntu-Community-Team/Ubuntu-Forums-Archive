---
title: "VMWare installation problem, and solution"
date: 2005-01-11
forum: Installation &amp; Upgrades
---

### Post by Martin Atkins on 2005-01-11
Hi all,

I had a lot of trouble installing Ubuntu in a VMWare guest VM - the installer
looped forever, refreshing the screen at "19% done" while loading the
installer's modules.
(I think it got stuck at libc_udev, or somesuch)

I tried VMWare 4.1.0 (I think it was), and 4.5.2 - no difference.

The solution was to use a different physical CDROM drive as the virtual
machine's CDROM.

I don't know why this helped, but it did: after that - no problems.

BTW the CDROM which didn't work was an ATAPI CDR,
and the CDROM which did work was an ATAPI DVDROM.
I was using official Ubuntu CDs - for which, many thanks to Canonical.

Thus it **may** be that the problem is the combination of a
CDR drive and VMware.

I have not been able to try installing the physical machine from the
CDR drive, but it did boot the live disk OK, in that drive.

Sorry, I can't characterize the problem beyond that, only speculate (which
doesn't help much)!

I hope this saves someone else some time, and head scratching!

Martin

---

### Post by SnoZ on 2005-01-11
I use Virtual PC 2004, dunno if you know it, but it's similar, i think it is Microsoft's version of VMWare, anyways, my problem isnt installing (i think) because everything goes on without any error.
I tried it on my portable only yet, and my problem is after the instalation, when the log in screen appears, it appears with a weird resolution, larger than mine (<-->) but smaller (up/down) and with very few colors, like the screen had some problems... i dunno why this happens, please tell me if it ever happened to you...  ](*,) 
my portable is/has:
Pentium 4 2.40GHz
Windows XP SP2 Pro Eng
ATI Radeon M6
27,9 Gb Hard-Disk (12.5 Gb free)
512 Mb Ram DDR

---

