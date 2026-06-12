---
title: "PATA on libata nForce 939 (CK8S) strange issues - non standard kernel"
date: 2008-01-09
forum: Hardware &amp; Laptops
---

### Post by Jonie on 2008-01-09
I recompiled 2.6.22 kernel and enabled libata support for the Nvidia ATA controller (now seen as 'SCSI'). There is about 10 per cent performance improvement and the system feels just a bit snappier, there are, however, two strange issues using this driver (no longer marked as experimental, but not enabled by default on Ubuntu Gutsy). 
First of those is that, during startup (about time gdm is starting) and about 2 seconds before final halt when shutting down a click can heard indicating that disk head parks. There is no spin down (motor is still powered) and drive instantly resumes its normal operation. It does not cause any error nor data corruption.
Second is that with this setup computer cannot power off. Disk spins down and ...that's it. In fact it does sometimes power off, but very seldomly.
Maybe it's an ACPI problem? Did anyone try libata on similar hardware? I tried some 2.6.23 live cds and it seems to work without a glitch.
Or maybe there is a way to setup libata and enjoy it's full bells and whistles just now.

---

