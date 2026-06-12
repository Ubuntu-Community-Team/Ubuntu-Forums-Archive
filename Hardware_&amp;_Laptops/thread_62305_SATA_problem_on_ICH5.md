---
title: "SATA problem on ICH5"
date: 2005-09-04
forum: Hardware &amp; Laptops
---

### Post by nilus on 2005-09-04
This is my hardware
* Epox 4PCA3+
* P4 3.0 GHz Prescott
* 2x512 MB PC3200
* Matrox G550
* 200 GB Maxtor SATA

SATA Controller is configured in Ehnanced mode, so my SATA Disk, in Linux, is sda.
I'm trying to install ubuntu but i get always a lot of errors.
The same is for Debian Sarge or Debian Sid and also Mepis. But with slackware i have no problems so I suppose this is a problem of debian and debian-based distros.
I think that a module is missing. I tryed to install with acpi and apic disabled and loading libata, ide-disk, ide-generic and ata_piix modules. But i always have the **sense key Medium Error** and the PC freezes. I read somewhere that it's a problem of 2.6.8 and 2.6.9 kernels. So I tryed with Debian Testing netinstall kernel 2.6.11. The error is different but the problem remains.

How can I do? Does Ubuntu recognize ICH5 controller?

I tryed everything, also assigning SATA to the Primary Channel of the EIDE Controller but it's always the same story.

Please help me... it's about 2 days that I'm trying to resolve the problem.

Thanks

---

