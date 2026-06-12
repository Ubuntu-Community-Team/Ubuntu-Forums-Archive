---
title: "Nvidia AGP disabled issue"
date: 2005-07-26
forum: Hardware &amp; Laptops
---

### Post by esmein on 2005-07-26
Hi!
First of all, I'd like to state that I've been googling around for 6 hours now about this stuff and still no solution.

Here's the problem: I installed ubuntu, then a kde and then kdm. I have geforce 4 ti 4200 128mb card in a sis 760gx chipset asrock board. Integrated video disabled in bios. nvidia-glx successfully installed and is working. But I cant get agp mode enabled, anything I do it stays just disabled. Ive tried xorg.conf and NvAGP 1,2,3 and 4. Ive tried blacklisting sis_agp, Ive tried editing /boot/configure  file with no success. All i managed to do is avoiding black window. When I had gdm as default and NvAGP @2 or 3 it crashed with black window. Kdm starts fine but agp is disabled.

glxgears give me 2700 and I think its lowish for this vga.

Anyone has any idea for enabling the agp ?
Ah I have 7174 driver installed.

---

