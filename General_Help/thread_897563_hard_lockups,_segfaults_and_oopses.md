---
title: "hard lockups, segfaults and oopses"
date: 2008-08-22
forum: General Help
---

### Post by notyetroot on 2008-08-22
I'm running a generic 2.6.24-19, currently fglrx-tainted but the problem occurs with or without it. I get hard lockups multiple times a day, which don't always even respond to sysrq + RSEIUB.

When running applications that consume a lot of memory (compiling, firefox to a lesser degree etc) they tend to exit randomly with a segmentation fault. When I get a lockup while in the terminal, I get something like this:
BUG: CPU #0 stuck for 11s (always 11s)

I also get a paging related bug I cannot recall, at least for readahead-watch. I run the kerneloops applet and sometimes get some recoverable errors too.

It seems like a hardware problem though, since Windows XP gets a BSOD with:
IRQ_NOT_LESS_OR_EQUAL (hex codes etc)
and a random .sys file (often ntfs.sys).

I haven't run memtest86+ long enough to confirm a hardware problem though.

Does anybody know what this is? Has anybody confirmed it?

Specifications:
- Pentium D 2.8 Ghz
- Asus motherboard (will note model, was not the original motherboard that came with it, all the subsystems seem to be made by SiS)
- RAID stripe with Windows XP NTFS and Ubuntu 8.04 EXT3.
- 1GB RAM

lmsensors outputs that show an "ALARM": 
in1:        +11.83 V  (min = +13.25 V, max =  +4.38 V)   ALARM
AVCC:        +3.22 V  (min =  +2.05 V, max =  +0.06 V)   ALARM
3VCC:        +3.22 V  (min =  +3.42 V, max =  +1.10 V)   ALARM
in4:         +1.80 V  (min =  +0.22 V, max =  +0.38 V)   ALARM
in5:         +1.61 V  (min =  +1.10 V, max =  +1.34 V)   ALARM
in6:         +5.68 V  (min =  +5.79 V, max =  +2.12 V)   ALARM  
VBAT:        +3.22 V  (min =  +3.58 V, max =  +1.57 V)   ALARM
(Some non existant fans at 0 RPM)

---

### Post by kidders on 2008-08-24
Hi there,

Sounds like a hardware problem to me. The most likely candidate is faulty RAM, imo.

---

