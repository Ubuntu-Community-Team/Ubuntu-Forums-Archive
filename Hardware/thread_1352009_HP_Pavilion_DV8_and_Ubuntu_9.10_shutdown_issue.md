---
title: "HP Pavilion DV8 and Ubuntu 9.10 shutdown issue"
date: 2009-12-11
forum: Hardware
---

### Post by langostino on 2009-12-11
Hi, everybody. I have the last HP Pavilion DV8 with 18,4'' screen's size and i7 core. Manufacturing operating system is Windows 7 Home Premium 64 bits.

I tried last Ubuntu 9.10 Live CD (64 bits) and it boots normaly. Wifi is working. But, when I shoutdown or halt system from this Live CD, notebook is halted, but when I switch the notebook ON, BIOS shows an abnormal hibernation or shutdown process ocurred, maybe for an overheating operation.

I see this BIOS message is not displayed when I boot Ubuntu LiveCD with ACPI=off option.

Do you have the same issue? My BIOS version is F.05.

PD: Sorry for my bad english.:(

---

### Post by inoxllor on 2009-12-24
Same issue here with Ubuntu 9.10 and with Linux Mint 8 x64.
:(

Upgrading bios version to F1.20 seems to correct the problem. But now the FAN is always on.

---

### Post by paulobear on 2010-02-07
I have the same issue.  I was wondering if the BIOS didn't make some assumptions about the boot sector on the hard drive, and stick some data out there.  Then when I installed Ubuntu, maybe GRUB uses some of that same disk sector for its own purposes and the two collided.

Paul

---

