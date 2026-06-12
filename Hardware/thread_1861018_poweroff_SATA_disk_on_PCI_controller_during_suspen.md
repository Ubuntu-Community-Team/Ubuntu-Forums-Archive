---
title: "poweroff SATA disk on PCI controller during suspend to RAM"
date: 2011-10-15
forum: Hardware
---

### Post by dimajcc on 2011-10-15
I have an old PC. Its motherboard (ASUS A7N8X2.0) doesn't have an internal SATA controller. So I put the Silicon Image 3114 SATA controller into a PCI slot. It works pretty good, but there is one inconvenience - when I switch PC into sleep mode the SATA disk doesn't power off and this prevents PC to completely disable power and go into sleep. When SATA is not connected to PC - everything is OK. I think this is because ACPI is handled in BIOS and BIOS of my PC doesn't know anything about SATA (for IDE disks there are an option in BIOS to disable power in low-power state).

The question - is there any program way to shutdown a SATA disk? For example some CLI command or maybe options for kernel module?

---

