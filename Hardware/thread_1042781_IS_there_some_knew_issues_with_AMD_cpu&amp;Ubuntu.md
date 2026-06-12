---
title: "IS there some knew issues with AMD cpu&amp;Ubuntu?"
date: 2009-01-17
forum: Hardware
---

### Post by helmetator on 2009-01-17
Hi,

I recently got this laptop based on a Sempron CPU (around 700-900 Mghz) and 448 RAM (DDR); I'm trying to install Ubuntu 8.10 on it and can't.
It seems to hang up just b4 showing the desktop after everything has been installed.

As Xp was on it, I even tried to install via WUBI. but same thing. Installation looks going well, but hanging up after reboot when 
"checking the installation". 

I dont know what to do and was wondering if sby has any idea about that?

The laptop is a Packardbell named "Easynote".

Thanks a lot.

info for this laptop are

CPU:
Mobile AMD SEMPRON 3000+
Socket 754
Instructions:MMX(+), 3Dnow(+), SSE, SSE2
Core speed:801,9 

MOTHERBOARD:
Manufacturer: Mitac
Model:Packardbell Easynote 5a
Chipset: VIA  K8M400(VT8380)  rev:0.0
         Southbridge VIA VT8235

BIOS:
Brand: Inside Software
Ver. : R1.06
Date:11/19/2004

GRAPHIC INTERFACE:
Ver.:AGP ver.3.0
Tx rate:8X   Max.supp.:8X
Side band:enabled

ok  thanks again.

---

### Post by helmetator on 2009-01-21
Just to say I realized the problem was not a CPU one but a graphic one.

After installing Ibex under safe graphic with acpi=off and noapic, I could 
get the GUI working properly.

Then, I checked the graphic interface model and was informed it s a VIA K8M800 or stmg.

I saw on Ubuntu's forum there is some issue with this kind of graphic device.

I installed openchrome as it was suggested, and, mmmagic, it's working.

Thanks a lot ubuntu community!

---

