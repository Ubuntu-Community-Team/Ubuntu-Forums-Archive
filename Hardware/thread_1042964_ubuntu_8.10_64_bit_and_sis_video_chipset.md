---
title: "ubuntu 8.10 64 bit and sis video chipset"
date: 2009-01-18
forum: Hardware
---

### Post by giorsat on 2009-01-18
Hi. I installed ubuntu 8.10 64 bit on a fujitsu esprimo mobile 5535 with a sis video card
I put the following lines in the monitor section of xorg.conf 
option "DPMS"
HorizSync 28-72
VertRefresh 43-70

after reboot I got a 1280x800 instead of a 800x600

now
- how can I know if the system is using a sis driver or a vesa one? xorg.conf is almost empty
- how can I get a 2d sis driver working in case it's a vesa? I found some threads on ubuntu 804 but now in 8.10 xorg is different..

anyone with the same problem?

---

