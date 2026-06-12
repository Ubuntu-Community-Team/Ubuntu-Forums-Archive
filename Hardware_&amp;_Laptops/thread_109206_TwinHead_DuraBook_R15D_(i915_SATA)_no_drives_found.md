---
title: "TwinHead DuraBook R15D (i915 SATA) no drives found"
date: 2005-12-28
forum: Hardware &amp; Laptops
---

### Post by leonbrooks on 2005-12-28
If I boot the installer, it freezes after unpacking the kernel.

If I use noapic, acpi=off or acpi=ht it passes that point, but aha_piix reports controllers found sans "device", which presumably means no detectable drives.

I tried the Mandriva 2006.0 (and 2006.1 0.3) installer, and they work with an option "noauto" -- which is not supposed to make it just work, it's supposed to prompt for driver modules instead of autodetecting them -- but the resulting system exhibits the same symptoms (and "noauto" there doesn't help).

The chipset is Intel 915; sundry PCI listings etc live at [http://durabook-r15d.cyberknights.com.au/](http://durabook-r15d.cyberknights.com.au/) for the curious.

MS-Windows-XP works on it, but the wireless (ipw2200) is dodgy and the CPU fan doesn't spin up even if the case is at egg-frying temperatures.

---

