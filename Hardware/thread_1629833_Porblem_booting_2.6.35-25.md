---
title: "Porblem booting 2.6.35-25"
date: 2010-11-24
forum: Hardware
---

### Post by limited00 on 2010-11-24
I recently upgraded from Lucid using 2.6.32-25 to Maverick with 2.6.35-25. With the new kernel, I can no longer boot into Ubuntu with the new kernel. The Lucid kernel still works, but I'd like to get 2.6.35 working.   I wish I could provide an error message, but my computer restarts during the boot. The kernel messages disappear immediately. I think the last messages I can see relate to ehci. (I tried turning USB off, didn't help).   Hardware is an MSI X58 w/ Core i7-930 and 6GB of RAM with a Kingston SSD and 1TB WD Hard Drive. The graphics card is an EVGA GT240 PCI-E card.    I have two questions: 1) Is there any way to prevent the reboot from happening so any error messages are saved? 2) Any other ways of debugging this problem? The log messages don't appear in the /var/log/ files.      --Eric  UPDATE: Adding acpi=off to my grub config allows me to boot, but CPU Frequency scaling is now disabled

---

