---
title: "how to get AHCI for SSD"
date: 2013-06-29
forum: Hardware
---

### Post by ub9876 on 2013-06-29
How can I get my Toshiba BIOS to turn on AHCI    it doesnt show in my BIOS

---

### Post by dino99 on 2013-06-30
here is an old howto (grub1) and is a bit techy, but it can give idea to dig a bit more: [http://rants.atmurray.net/2009/06/sata-ahci-mode-on-systems-without-bios.html](http://rants.atmurray.net/2009/06/sata-ahci-mode-on-systems-without-bios.html)
but with actual kernels maybe its possible to force that setting (need to search about) like that other one: [https://wiki.ubuntu.com/Kernel/PowerManagementALPM](https://wiki.ubuntu.com/Kernel/PowerManagementALPM)

as the bios does not propose AHCI, that might also mean that the chipset(s) are too old to support ahci : see the chipset doc of your tosh

---

