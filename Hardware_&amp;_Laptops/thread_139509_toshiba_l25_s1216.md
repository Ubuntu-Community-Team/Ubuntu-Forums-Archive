---
title: "toshiba l25 s1216"
date: 2006-03-04
forum: Hardware &amp; Laptops
---

### Post by sfarr on 2006-03-04
ok i have a toshiba l25 s1216 and it has a phonix bios i have issues with the ACPI, am i fighting a loosing battle to try to have linux on this laptop, i want to have the power of linux but can not get the ACPI to show power level, or sleep.

please help if you can

---

### Post by webdr on 2007-11-23
Modify your kernel config line in /boot/grub/menu.lst file by appending 'noapic' to the kernel line.

-MW

---

