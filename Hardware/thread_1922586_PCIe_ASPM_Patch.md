---
title: "PCIe ASPM Patch"
date: 2012-02-09
forum: Hardware
---

### Post by der_hede on 2012-02-09
Hi Ubuntu users,

With Linux 3.0.20 there's some improvement with PCIe Power Savings.
 --- Rework ASPM disable code ---

Are there any patched Ubuntu Kernels out there? 

Ubuntu Oneiric has it's own Patchset for Kernel 3.0.0 (3.0.13).
So I made my own patch derived from Matthew Garretts patch for Kernel 3.0.19
for the Ubuntu 11.10 Kernel and compiled it. Works fine so far.
(Using Linux Mint 12 here))

But even if I have a line saying
"ACPI FADT declares the system doesn't support PCIe ASPM, so disable it"
in dmesg, I cannot see any improvements with my patched Kernel.
(IBM Thinkpad x60s here)


If anyone is interested in my binaries, ask for it...
###
linux-headers-3.0.0-15-generic_3.0.0-15.26_i386.deb
linux-headers-3.0.0-15-generic-pae_3.0.0-15.26_i386.deb
linux-image-3.0.0-15-generic_3.0.0-15.26_i386.deb
linux-image-3.0.0-15-generic-pae_3.0.0-15.26_i386.deb
linux-tools-3.0.0-15_3.0.0-15.26_i386.deb
###

Regards
 hede

---

