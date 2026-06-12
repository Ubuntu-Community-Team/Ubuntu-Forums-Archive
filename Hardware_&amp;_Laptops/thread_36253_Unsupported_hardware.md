---
title: "Unsupported hardware?"
date: 2005-05-22
forum: Hardware &amp; Laptops
---

### Post by discrepant on 2005-05-22
I am attempting to install Ubuntu 5.04 on a Compaq Presario SR1111NX. Here are some basic hardware specifications...

Chipset: Intel 845GV
Video: Intel Extreme 82845G/GL/GE/PE/GV
Processor: Intel Celeron 2.53 ghz
HDD: 40gb Seagate
RAM: 768mb PC2700

I load the installation CD at startup and the machine boots to the CD as expected. I attempt to boot the kernel with the default installation (pressing enter) and as soon as the kernel begins to load, the machine restarts. This is an ongoing process that I am unable to work around. Does this mean the hardware is simply not supported? And if not, could an administrator report this hardware configuration to the developers? Or could I do this? I'll also mention I've tried booting other Linux distributions on this machine with no luck. Gentoo, Knoppix, Mepis, and of course; Ubuntu. So then, this is a problem with the Kernel. Hm, what can be done about this?!

---

### Post by codejunkie on 2005-05-22
had/have the same problem myself just type linux acpi=off at the boot prompt this should fix the rebooting issue if you are using live cd change that to live acpi=off hope this helps.

---

### Post by discrepant on 2005-05-22
Wonderful! It works! Thank-you!

---

### Post by codejunkie on 2005-05-22
happy to help! :)

---

