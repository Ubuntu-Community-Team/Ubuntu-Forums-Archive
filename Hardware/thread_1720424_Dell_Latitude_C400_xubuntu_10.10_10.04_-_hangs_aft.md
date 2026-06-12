---
title: "Dell Latitude C400 xubuntu 10.10 10.04 - hangs after installation"
date: 2011-04-03
forum: Hardware
---

### Post by lukki on 2011-04-03
I've tried to install Xubuntu 10.10 and 10.04 on Dell Latitude C400 (Pentium III 800 MHz, 256 MB memory, 20 GB disk) with wubi installer, but it hangs every time after boot (screen blanks and laptop freezes - hard reset required).
It happens in all boot modes (safe graphics etc), except ACPI workarrounds, which boots me into text mode and no X can be run.
My graphics chipset is Intel 830M.

I couldn't find any solutions for these particular versions of X(Ubuntu).

---

### Post by SJI on 2011-04-13
I've just tried installing 10.10 on my C400.

If you use either nomodeset vga=771 vga=772 or vga=773 kernel arguments it will stop the screen going blank.

The problem sees to be with frame buffer settings, and Xorg doesn't seem to get the graphics set up right.

---

