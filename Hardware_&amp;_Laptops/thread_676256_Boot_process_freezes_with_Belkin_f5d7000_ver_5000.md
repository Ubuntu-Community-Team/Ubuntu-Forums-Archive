---
title: "Boot process freezes with Belkin f5d7000 ver 5000"
date: 2008-01-23
forum: Hardware &amp; Laptops
---

### Post by cdaaawg on 2008-01-23
:confused:I have a working Ubuntu 7.10 installation to which I would like to add a Belkin Wireless G Desktop Card model # f5d7000 ver. 5000. Prior to adding the card, the system functions well with two wired ethernet cards, one for internet connectivity, and one for my trusted home network.  Inserting the card and powering up causes the boot process to freeze just after this boot message:

Starting up . . .
[0.000000] ACPI: DMI BIOS year = 0, assuming ACPI-capable machine

_



Removing the card allows the system to boot and function as before. This card functions well with windoze but I have not tried it with any other Linux distro. The chipset is Atheros, marked AR2413A-00. This is an older machine used for a testbed. Chaintech mobo with PII 400MHz, 384MB RAM.

Is there a boot option from grub that I can use to skip hardware detection and attempt to install the driver from a terminal? Any suggestions are appreciated.

---

### Post by cdaaawg on 2008-01-23
I have found a workaround to the kernel hang I experienced with the Belkin desktop wireless card. Using the *acpi=off* kernel boot option allows the system to boot and install the driver for this card. However, there are no native drivers for the chipset and therefore, the proprietary restricted drivers are loaded.

My next course of action will be to test the wireless connection functionality. I will then test the boot process by removing the *acpi=off* boot option. Will post results of my testing when complete.

---

