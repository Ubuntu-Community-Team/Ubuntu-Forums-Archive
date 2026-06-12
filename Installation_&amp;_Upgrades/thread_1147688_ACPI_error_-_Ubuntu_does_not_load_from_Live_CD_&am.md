---
title: "ACPI error - Ubuntu does not load from Live CD &amp; Wubi installation error"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by anirbanb_007 on 2009-05-03
I am trying to install Ubuntu 9.04.

Processor: AMD Athlon 64 3000+ System
Motherboard: MSI RS482M-F
Graphics: NVIDIA 7300GT
Hard Disk: 160 GB SATA and 200 GB SATA

When I try to install from Windows via WUBI, I get an error. I have attached the log file.

When I try to run the live CD I get this message before the LIVE CD starts booting
[    5.588175] ACPI: Unable to Dock!
[    7.788369] ACPI: Unable to Dock!
[    7.788461] ACPI: Unable to Dock!
Loading, please wait...

The LIVE CD does not start successfully and the keyboard and the mouse freeze.

The CD is ok as it works fine on other computers.

Please suggest me a solution, I am totally new to using Ubuntu!

Thanks

---

### Post by 123456789123456789123456 on 2009-05-03
Check in your BIOS settings, to see if Power management is turned on.
If it is turned on, it may be uncompatable with ACPI from Ubuntu, which sounds like the problem, it is falling back on other methods to try and get it to work, but is failing, the last entry was not listed, because it thinks it suceeded.  Obviously it did not.
If it is turned on, try turning it off, and restarting
if that does not work, go through the temp option, and edit GRUB, to turn ACPI=off

---

### Post by anirbanb_007 on 2009-05-04
Disabling ACPI seems to solve that problem.

Trying to run the live CD after that gives the following error:
MP-BIOS bug: 8254 timer not connected to IO-APIC

Disabling APIC removes all error messages, however the end result is the same Ubuntu freezes during loading of the Live CD, keyboard and mouse are unresponsive.

What should I do after this?

---

