---
title: "Toshiba M55-S1001 Suspend/hibernate"
date: 2006-06-05
forum: Hardware &amp; Laptops
---

### Post by remusus on 2006-06-05
Hi, I'm trying to install Dapper on a new Toshiba M55-S1001 (special Office Depot off-the-shelf model).  Everything works perfectly except for suspend and hibernate, unfortunately for this thing having those working is critical. I've tried a bunch of tweaks to the kernel boot parameters and the acpi-support file, but so far nothing works.  When I suspend-to-ram, it appears to work fine but on resume the backlight does not turn on and it appears to be hardlocked.  When I use standby, it does nothing (comes back to locked screen without standing by), and when I hibernate it appears to be writing ram to disk but then comes back to locked screen without shutting down.

Anyone have any idea?  If I can get just one or the other working that will probably be sufficient.

Toshiba Satellite M55-S1001
Celeron M 1.6GHz
ATI m200 (fglrx and ati both have same behavior)

---

