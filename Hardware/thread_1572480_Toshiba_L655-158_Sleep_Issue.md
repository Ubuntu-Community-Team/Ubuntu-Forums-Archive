---
title: "Toshiba L655-158 Sleep Issue"
date: 2010-09-11
forum: Hardware
---

### Post by gareththered on 2010-09-11
I've noticed that my Toshiba L655-158 hangs for about 10-15 seconds (and sometimes forever) when I sleep or wake the laptop.

Preliminary investigations suggest it's the AC8152 Ethernet causing the issue because if I remove the atl1c or atl1e driver after initial boot then the laptop switches in and out of sleep mode quite happily.

Has anyone else noticed this?  Or even better, has anyone resolved it?

It's not a major problem as I don't normally use an Ethernet connection.  But still, I'd rather have a fix than disabling the driver.

Thanks,

Gareth

---

### Post by canucked on 2010-12-09
I just wanted to mention that a Toshiba Satellite L655-S5115 laptop, updated to the most recent BIOS (1.70), and running Ubuntu 10.10 Maverick 64-bit is able to sleep and hibernate properly.  If sleep is not already fixed on your machine, perhaps a BIOS update would do the trick?

---

