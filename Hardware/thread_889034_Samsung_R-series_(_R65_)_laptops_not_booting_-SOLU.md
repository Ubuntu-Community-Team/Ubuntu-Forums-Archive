---
title: "Samsung R-series ( R65 ) laptops not booting -SOLUTION"
date: 2008-08-13
forum: Hardware
---

### Post by Submatrix on 2008-08-13
Hello, this is a post for the benefit of other people googling for a fix who may have the same trouble as me with samsung R series laptops. I managed to find a handy fix that doesn't involve disabling ACPI

First you can install install ubuntu from the live cd with the bootcode:

acpi=off

the above works on my R65 but may be model-specific, so if it doesn't work try:

acpi=off noapic pci=bios

After the install is complete and you boot for the fist time you will still need to type these bootcodes into GRUB (on the line that says 'ro quiet splash' at the end), otherwise the boot process will hang. These bootcodes will eventually get you into a working system, but with ACPI disabled. However, obviously want our hibernate functions, battery meter and auto poweroff at shutdown to work. To achieve this:

Edit /etc/modprobe.d/blacklist and add the line 'blacklist video' at the end.

reboot without the ACPI bootcodes and enjoy your fully working system :)

Keywords so people find this on google:

"Samsung R65 Ubuntu" "Samsung R65 linux" fix solution

---

