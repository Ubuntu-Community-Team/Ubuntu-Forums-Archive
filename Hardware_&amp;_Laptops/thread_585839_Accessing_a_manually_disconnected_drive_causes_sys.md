---
title: "Accessing a manually disconnected drive causes system hang (edgy)"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by GeneralNMX on 2007-10-21
If I manually disconnect a drive's power then try to access it, I get an "ata 5: command timeout" error which hangs the system. I've waited up to 30 minutes and the system doesn't come back. All my hdd activity indicator lights on the system itself are solid, making it seem like the bus is being flooded with requests. The same problem occurs even if I reconnect the power before attempting the access the drive -- just disconnecting the power once causes the problem.

While these are PATA drives in this case, the PCI Controller card they're on causes Linux to detect them as SCSI devices.

I want to be able to hotswap drives out of removable hdd bays for storage and backups reasons without needing to reboot the machine.

---

