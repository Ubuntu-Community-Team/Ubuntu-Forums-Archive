---
title: "Dual boot Windows on separate drive"
date: 2005-12-29
forum: Installation &amp; Upgrades
---

### Post by loney on 2005-12-29
I would like to consolidate a legacy Windows 2000 machine with my Ubuntu workstation.  Ubuntu currently runs on a single SATA drive. The upgrade plan is to add an IDE drive with the boot sector and a second SATA drive for RAID-0. Specifically:

o tar up all non-transient files from the current SATA drive

o add the IDE drive

o install Windows on the IDE drive

o copy legacy Windows content to the IDE drive

o add a second SATA drive

o reinstall Ubuntu partitioned as follows:

  /boot, /var/local --> IDE drive

  / --> striped RAID-0 SATA drives (erases previous content)

o untar the previous content to the new install

The SATA drives are fast and small (WD Raptor).

The IDE drive is slower and large. /var/local holds bulk data, e.g. non-critical backups and repositories.

Is this a feasible plan? Any special considerations?

More of a Windows question: can I make the SATA drives invisible to Windows? I would like to isolate the Windows Petri dish to its own drive to prevent infection of the SATA drives.

---

