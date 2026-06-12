---
title: "TOSHIBA Satellite A60-332"
date: 2008-11-19
forum: Hardware
---

### Post by crik91 on 2008-11-19
Hi,
I'm sorry, I'm Italian and I don't speak English very well.
I have this laptop: TOSHIBA Satellite A60-332 (Intel Pentium 4 2800 MHz L2 Cache 512K, 704 MB RAM, 160 GB HDD, ATI RadeON Mobility 7000 IGP, ATI Technologies Inc. IGP AC'97 is audio card, Proprietary ACPI BIOS 1.90)

I have tried many times to install Ubuntu 8.10 on my laptop but I was unable to start the LiveCD for an error APIC...I was not able to even start with:
```
noapic nolapic acpi=off
```
I installed from a CD Alternate even if the system has never started a GRUB Error 18, I tried to LiveCD KNOPPIX reinstalling GRUB without success.
I managed to install Ubuntu 8.04, then I upgrading to version 8.10 .
Almost in all sessions during use is blocking everything including touchpad and combinations CTRL+ALT+DELETE and CTRL+ALT+Bksp had no effect.Worked only with:
```
noapic nolapic acpi=off
```
in menu.lst GRUB. Unfortunately, with:
```
acpi = off
```
not working turn off, standby and USB ports that Ubuntu saw no more but had not even fired.

I removed acpi=off in menu.lst and returned the problems:
* Splash at the screening sometimes loading stops almost immediately;
* The audio is not working;
* When using everything hangs very often

I hope to have been understandable.I ask for help and I thank you!

---

### Post by crik91 on 2008-11-19
I have dual-boot ubuntu-windowsxp.Memtest results: for 7 hours running: 11 Pass 0 Errors.
Someone can help me please?

---

### Post by lisati on 2008-11-19
Maybe using the "alternate" installation disk is an option for you.

I have a Toshiba A100 with specifications more modest than your laptop.
When I first installed Ubuntu on it a year ago, with version 7.04, I found that using the "alternate" disk was easier - the installation was faster.
My experience with version 8.10 was that my machine works better with Xubuntu, again installed using the "alternate" disk.

---

### Post by crik91 on 2008-11-19
I've the same problems with both installation CDs(LiveCD and AlternateCD).
I don't like Xubuntu...Thank you...
Other ideas?

---

