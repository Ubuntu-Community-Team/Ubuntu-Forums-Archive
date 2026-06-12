---
title: "GPE Storm Detected on Dell Mini 9"
date: 2008-10-19
forum: Hardware
---

### Post by redDEADresolve on 2008-10-19
I was trying to reinstall Ubuntu 8.10 Beta on my Dell Mini 9.

Instead of going to a LiveUSB desktop it keeps throwing me into a BusyBox Shell

I get the error:

> [    0.749487] ACPI: GC: GPE storm detected, disabling EC GPE
Loading Please wait...

BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu4) built in shell (ash)
Enter 'help' for a list of built-commands.

I tried adding acpi=off in the boot line but no luck.

---

### Post by redDEADresolve on 2008-10-21
**SOLVED**
It was an error in the usb-creator software. I used [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) and installation worked flawlessly.

---

