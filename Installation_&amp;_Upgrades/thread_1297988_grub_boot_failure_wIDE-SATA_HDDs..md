---
title: "grub boot failure w/IDE-SATA HDDs."
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by nss0000 on 2009-10-22
Gents:

Recently I built-out new AMD_965/MSI_790-gd70 kit containing both IDE & SATA Seagate HDDs. BIOS (v-1.4) reported the SATA, but NOT the IDE. Strange I thought.

But, I pushed ahead with a U_9.04 install from a "factory" CD. UBUNTU recognized BOTH HDDs, and I chose the SATA for UBUNTU installation. No issue appeared during install.

However, upon OS completion & reboot I got a GRUB <error> saying boot was impossible without giving details. I performed this failing sequence twice, then frustrated I removed the IDE HDD and re-installed the OS.

Success. The system now with only the SATA HDD works without issue. But, I wonder what caused the GRUB boot-error when both IDE & SATA HDDs were connected?

---

### Post by Mark Phelps on 2009-10-22
On my machine, which also has SATA and PATA (IDE) drives, whenever both are connected, the BIOS automatically selects the IDE drive as the "first" drive in the system -- which is the drive that GRUB is installed to by default.

It's very odd that Ubuntu was able to see that drive, but not your BIOS, but it probably installed GRUB there, so when you rebooted, your BIOS couldn't read it -- resulting in inability to boot.

When you removed the IDE drive, the SATA drive, now being the ONLY drive in the system, automatically becomes the "first" drive -- and once again, GRUB gets installed to the "first" drive by default.

---

### Post by dstew on 2009-10-22
Yes, there is probably a disk enumeration disconnect between the BIOS and Linux.

The Grub boot loader depends on the BIOS to access the disks. Also, it uses the BIOS disk enumeration. The Linux OS bypasses the BIOS completely, and uses its own disk detection schemes.

When you installed grub, you were running a Linux OS. The grub installer program counted all the disks *as the Linux OS saw them*, assuming that the BIOS would also recognize them and enumerate them the same way. However, the when the grub boot loader runs at start-up, it only sees what the BIOS sees. 

So at install, the Linux OS saw the IDE and SATA disks, and maybe enumerated them as 1 and 2, and installed the boot loader into the SATA disk. However, when the grub boot loader starts, with the IDE disk in place, the SATA disk might be counted as disk 1 in the BIOS. So, grub looks for disk 2, and doesn't find it, and fails.

Usually you can find some installation scheme that will work with these mixed IDE and SATA systems. For example, if you had told grub to boot disk no. 1 at installation, knowing that the SATA disk would be no. 1 in the BIOS enumeration, it probably would have worked OK.

---

### Post by nss0000 on 2009-10-22
Gents:

Appreciate your quick response. I gather that I'm "safer" not installing that 80-g HDD. Funny thing is, when I listed the "boot" sequence I picked (1st) DVD and (2nd) SATA_HDD !! 

And at the first install I DID tell UBUNTU to load into the SATA. But I see ... that SATA could have been listed as HDD#2, while on reboot there was only ONE HDD listed in BIOS.

Kinda flakey that a modern mobo like the MSI790-gd70 wouldn't grab that IDE for listing ... unless there's a BIOS command_line to enable it. Wonder if that entire IDE cable is "dead" until activated? THAT is too modern. 

Thanks again.

---

