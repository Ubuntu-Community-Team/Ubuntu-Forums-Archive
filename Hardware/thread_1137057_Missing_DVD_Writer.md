---
title: "Missing DVD Writer"
date: 2009-04-25
forum: Hardware
---

### Post by kahping on 2009-04-25
As simple as that. My DVD writer (Philips DVD+/-RW DVD8631) on a Dell Dimension 8400 is missing from the system. I tried a bootable CD & it works so it should be fine.

Anybody else got this problem with Jaunty?

---

### Post by kahping on 2009-04-25
Nobody at all?

The log file viewer doesn't seem to list this which I found in dmesg:

[ 3.926592] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[ 4.200051] ata5.00: NODEV after polling detection

Looks like Ubuntu doesn't detect the drive at all :(

---

### Post by kahping on 2009-04-25
Nevermind. There's a bug report that sounds like my problem: [https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/335968/](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/335968/)

---

