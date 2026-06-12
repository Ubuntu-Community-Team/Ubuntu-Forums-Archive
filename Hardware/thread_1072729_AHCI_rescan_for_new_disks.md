---
title: "AHCI rescan for new disks?"
date: 2009-02-17
forum: Hardware
---

### Post by Cracauer on 2009-02-17
I have a machine with the SATA onboard controller from the Intel 5100 chipset here. I run it as AHCI devices (as opposed to piix).

That works great, but there's a problem: it does not detect newly added hot-plugged drives on ports that did not have a disk at boot time.

If you have a disk connected at boot you can remove it and plug in a different one and all is fine. But if the port didn't have anything at boot time it just slacks off and never detects a new disk.

Is there a way to force AHCI to re-scan all ports?

---

### Post by dcstar on 2010-11-05
> **Cracauer said:**
> I have a machine with the SATA onboard controller from the Intel 5100 chipset here. I run it as AHCI devices (as opposed to piix).

That works great, but there's a problem: it does not detect newly added hot-plugged drives on ports that did not have a disk at boot time.

If you have a disk connected at boot you can remove it and plug in a different one and all is fine. But if the port didn't have anything at boot time it just slacks off and never detects a new disk.

Is there a way to force AHCI to re-scan all ports?

Old thread ressurection but I had the same issue with an eSATA drive that I only power on for backups and I think that this will work:

```
sudo partprobe
```

---

