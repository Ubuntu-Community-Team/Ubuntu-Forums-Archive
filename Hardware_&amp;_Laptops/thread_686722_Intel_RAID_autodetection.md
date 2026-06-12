---
title: "Intel RAID autodetection"
date: 2008-02-03
forum: Hardware &amp; Laptops
---

### Post by glalejos on 2008-02-03
Hi everyone!,

I'm new to Ubuntu Forums, and this is my first post :)

I have an Intel DP35DP with two SATA disk drives configured to work in RAID mode. I run Ubuntu Live CD and the disks were recognized correctly, but not the RAID partition. Googling around I found that it was possible to install the DMRAID package in order to have the RAID partition detected.

Sadly this package is not supported by Ubuntu at this moment, what makes it quite "dangerous" to use it as base of an Ubuntu installation (I guess there will be problems at boot time since Ubuntu is not prepared to configure the boot loader appropriatelly for this case).

Does anyone know if there are plans to include the DMRAID package in the supported packages repository?

Thanks,

---

### Post by huard on 2008-03-05
Hi,

I'm looking for the same information for the same problem. Did you figure it out?

Thanks.

---

### Post by CNLiberal on 2008-03-05
Why not just run mdadm?  The RAID that your mobo is essentially no different than the DMRAID.  Many mobos use proprietary software that uses the main CPU to do the XOR calcs on the hard drives.  MDADM does the same thing.  So you really don't need the DM drivers.  That's how I'd run it.  However, MDADM will only allow you to run RAID 1 (mirroring the drives) on bootable hard drives (last I heard).  I hope that's what you're asking for.  I've not really given advice on this forum yet!  Good Luck!

Jim

---

