---
title: "Acer Aspire 5504WXMi"
date: 2006-04-14
forum: Hardware &amp; Laptops
---

### Post by nolongerlivecd on 2006-04-14
I'm using an Acer Aspire 5504WXMi, which contains:

Intel Pentium M 760 2GHz
1GB DDR2 SDRAM
ATi Mobility Radeon X700 64MB VRAM
100GB Ultra ATA/100
Some Broadcom Gigabit chipset
Intel PRO/Wireless 2200BG
14.1" WXGA CrystalBrite LCD (Widescreen)

My questions are:

[LIST=1]
[*]My max configurable resolution is like 1024x768, not 1280x800 as in my screen. How do I configure Ubuntu's fglrx to do widescreen?
[*]ipw2200 can't seem to work. I can't find it under /etc/modprobe.d, and I can't install acer_acpi (can't compile, output is:

awk: cannot open /lib/modules/2.6.12-10-686/build/include/linux/version.h (No such file or directory)
gcc -I/lib/modules/`uname -r`/build/include -c -Wall -Wstrict-prototypes -Wno-trigraphs -O2 -fomit-frame-pointer -fno-strict-aliasing -fno-common -pipe -DMODVERSIONS -DMODULE -D__KERNEL__ -o acer_acpi.o acer_acpi.c
/bin/sh: gcc: command not found
make: *** [acer_acpi.o] Error 127

Wi-Fi Radar also can't seem to work. Anybody help?](*,) 
[/LIST]

---

