---
title: "Very high (and increasing) UDMA CRC Errors in SMART report"
date: 2016-03-29
forum: Hardware
---

### Post by Chris_Shelton on 2016-03-29
Hi,

I have recently built a new NAS with 6 new 2TB WD Red disks for zfs data, and I am using 2 older 320GB Toshiba disks for Ubuntu in Raid 1.

The OS disks are not new, but have been used a little bit in some laptops before being ripped out.

Ever since I set up SMART monitoring, I keep getting a huge number in the UDMA CRC Errors column of the report for both disks.

As of today for disk 1 and 2 read: 54068696 and 25632701 respectively, and these numbers are increasing by about 400,000 every day...

I have read online that this generally means there is some kind of cable connection issue, rather than something to do with the disks themselves.

All parts, except for the 2 320GB OS disks are brand new (will post build specs if needs be).

My mobo only has 6 SATA ports, so the OS disks are plugged into a PCI Express Sata Controller, maybe this could be the cause of the issue?

I'm just not sure. Anyone able to shed any light on this?

Thanks, Chris.

---

### Post by weatherman2 on 2016-03-29
Yeah, a cabling issue is what I've read is a likely cause of CRC errors as well.  I've rarely seen it and not persistently.

I suspect it is something to do with the controller card.  Obviously you could swap cables and see if that makes a difference.  Or swap ports temporarily with one of your data disks and see if the disk now attached to the SATA port starts getting CRC errors or the Toshiba disk stops getting them.  There's also some chance it's a Toshiba S.M.A.R.T. thing.  It may even be a false error.

Or it could be a real issue with the card.  But as the CRC errors would be fixed, could be the worst problem you will have is reduced performance on the OS disks because some data must be re-transmitted.

---

