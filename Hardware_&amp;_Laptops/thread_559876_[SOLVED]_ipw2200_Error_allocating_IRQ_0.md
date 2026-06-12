---
title: "[SOLVED] ipw2200: Error allocating IRQ 0"
date: 2007-09-25
forum: Hardware &amp; Laptops
---

### Post by ylg91 on 2007-09-25
Hi , i use a laptop Medion MIM 2080 with a wifi card Intel 2915ABG.
When i use options _noapic nolapic pci=noacpi_ in /boot/grub/menu.lst , the card is not working.
With no options , the card work well but USB devices work very slow and sometimes the comtuper freeze .

> juju@juju-laptop:~$ dmesg | grep ipw
[   19.276000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2
[   19.276000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   19.276000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[   19.276000]  [<dcace360>] ipw_isr+0x0/0xc0 [ipw2200]
[   19.276000]  [<dcacf0cc>] ipw_pci_probe+0x5ac/0x7b0 [ipw2200]
[   19.276000]  [<dcaceb20>] ipw_pci_probe+0x0/0x7b0 [ipw2200]
[   19.276000]  [<dc87202b>] ipw_init+0x2b/0x76 [ipw2200]
[   19.276000] ipw2200: Error allocating IRQ 0
[   19.276000] ipw2200: probe of 0000:00:06.0 failed with error -16

---

### Post by ylg91 on 2007-09-26
:confused:

---

### Post by ylg91 on 2007-10-08
DSDT is the answer

yannis.lg :guitar:

---

