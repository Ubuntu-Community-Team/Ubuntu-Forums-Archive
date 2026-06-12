---
title: "Onboard sata mode for dual boot setup"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by Cold-Gin on 2009-10-17
Hi. I just bought a new machine and a secondary hard drive. Both drives are SATA drives. In the BIOS, the onboard sata mode is set to RAID.

I would like to set up a dual boot configuration; one drive for Linux, the second drive for Windoze. What is the proper onboard sata mode setting for this? The available options are RAID, AHCI, IDE.

Thank you for your time.

---

### Post by tosk on 2009-10-17
You'll want either AHCI or IDE.

AHCI will provide better performance, but may require special drivers during Windows setup. Linux should be fine.

IDE provides more compatibility. In a nutshell, the BIOS translates IDE commands to SATA commands before sending them on to the drive.

I'd go with AHCI. That way you can use full SATA2 speed.

---

