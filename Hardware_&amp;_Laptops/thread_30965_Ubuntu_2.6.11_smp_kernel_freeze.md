---
title: "Ubuntu 2.6.11 smp kernel freeze"
date: 2005-05-01
forum: Hardware &amp; Laptops
---

### Post by dacosta123 on 2005-05-01
Hi,

I'm trying to get the 2.6.11 smp kernel to work properly on Hoary.
After many cycles i decided to pick up Knoppix 3.8.1 to see whether its smp kernel did work ok. It did, picked it up, started X(Free86) and things were fine.

The Ubuntu version is already 'stuffed' from the very first moment it loads the kernel into memory (at grub all is fine, the moment after enter the keyboard is no longer). I'm not sure whether its significant but without specifiing it anywhere the numlock is active (not the case with a normal kernel).

Falling back on the 2.6.10-5-smp version gives me the same problem.
Short of dropping Ubuntu (which i really don't want to do) what can i try to get this thing to work properly. (acpi=off makes it fall back to 1 cpu so no option either)

So, in short knoppix has got a working version and de same kernel for Ubuntu does not. Since the problem appears right after loading it seems as if there is something funky going on at kernel level.

Any help appreciated.
tia,

Fermin DCG


HW:
P4 HT, 512M
ATI Radeon 9800 (dual thing that causes strive as well)
USB keyb
PS/2 wheelmouse

---

### Post by dacosta123 on 2005-05-01
[QUOTE=][/QUOTE]
 Solved by adding usb-handoff to the bootparameters!
Why it works? I don't know (and honestly i'm not too concerned either after many cycles ;-) )

---

