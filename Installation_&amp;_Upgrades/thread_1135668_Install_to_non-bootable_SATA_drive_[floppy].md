---
title: "Install to non-bootable SATA drive [floppy?]"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by happyface_0 on 2009-04-24
I want to install 9.04 x86 on a PC with a non-bootable SATA drive. Before I had the /boot partition on a small PATA drive, but that failed.
Is it possible to install the /boot partition on a floppy disk? Or USB device? Or is there an easier way to boot up a non-bootable HDD.

Thanks! :-s

---

### Post by ChronoSphere on 2009-04-24
What do you mean by "non-bootable SATA drive"? Is it not detected? You can try to install to the SATA, and install GRUB to a bootable drive, which will then boot any other drive.

---

### Post by happyface_0 on 2009-04-24
> **ChronoSphere said:**
> What do you mean by "non-bootable SATA drive"? Is it not detected? You can try to install to the SATA, and install GRUB to a bootable drive, which will then boot any other drive.

It's a SATA PCI card that the BIOS doesn't see as a bootable device.
How can I install GRUB to a floppy disk?

---

### Post by ChronoSphere on 2009-04-24
Start grub, then:

grub> root (fd0)
grub> setup (fd0)
grub> quit

---

