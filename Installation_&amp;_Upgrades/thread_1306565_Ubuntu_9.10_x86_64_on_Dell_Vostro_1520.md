---
title: "Ubuntu 9.10 x86_64 on Dell Vostro 1520"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by grover66 on 2009-10-30
Installation of Ubuntu 9.10 x86_64 on a Dell Vostro 1520 Laptop;

Do a standard installation. After reboot;

Need to add the following to the end of the following line in /etc/default/grub;

from:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.reset i8042.nomux i8042.nopnp i8042.noloop"

This seems to cause a problem with randomly losing keyboard and mouse control.

Then run the following command to update grub;

update-grub

Mike

---

