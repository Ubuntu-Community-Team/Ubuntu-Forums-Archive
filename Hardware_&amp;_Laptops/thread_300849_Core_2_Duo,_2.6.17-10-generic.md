---
title: "Core 2 Duo, 2.6.17-10-generic"
date: 2006-11-16
forum: Hardware &amp; Laptops
---

### Post by newguy1950 on 2006-11-16
Hello everyone,

I'm having problems with my recently assembled Core 2 Duo system with edgy. First, depending on the BIOS settings, I can either boot Windows or Linux, but not both with the same configuration. The central option in my Phoenix BIOS is "IOAPIC" - if I disable it, the Linux kernel boots, otherwise it will hang once it starts initializing the hardware. Windows, however, will not run without it.

If I boot into Windows, both CPU cores show up and work fine. Linux, however (according to /proc/cpustat) only shows one CPU. Does anyone else have experience with Core 2 Duo and Linux? If so, please share.

Also, any help in solving the IOAPIC issue would be appreciated. I can post any "diagnostics" requested.

**SOLUTION: I've found some hints on the ubuntu wiki that my mainboard may be the problem (MSI P965 Neo-F) - disabling the legacy USB support (according to the wiki) did the trick - to do that, turn off "USB Mouse Support" and "USE Keyboard Support" in the BIOS.**

---

