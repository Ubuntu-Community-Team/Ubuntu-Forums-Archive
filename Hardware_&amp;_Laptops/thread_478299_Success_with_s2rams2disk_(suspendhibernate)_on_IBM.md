---
title: "Success with s2ram/s2disk (suspend/hibernate) on IBM T60"
date: 2007-06-19
forum: Hardware &amp; Laptops
---

### Post by frigaut on 2007-06-19
Most threads on these forums are to report problems. This one will be to report a success story, for once.

I have a thinkpad T60 (core2duo 2GHz, 15.4" screen, intel graphic chip 945GM). Suspend kind of worked out of the box, but the video was slightly corrupted (few lines close to the bottom of the screen) when brought back to life after a suspend. I solved the problem using the intel video drivers instead of the i810 ones (xserver-xorg-video-intel instead of xserver-xorg-video-i810). Then I had problems with randomly loosing video when switching virtual consoles (vt 7->1 for instance, which happens when you log out and during the suspend process). These were solved by : (1) using uswsusp (s2ram and s2disk) as s2ram -f -a 3 (forces s3_bios and s3_mode), appending acpi_sleep=s3_bios,s3_mode vga=0 to the kernel boot parameters (/boot/grub/menu.lst) and removing splash from the same kernel options. I have done that 8 days ago, and gone through 3 countries, around 50 s2ram and 4-5 s2disk without a hinch (note: I'm still using the intel video drivers)

In summary:
my config:
- thinkpad T60
- core 2 Duo 2GHz
- intel graphic chip 945GM
- 1680x1050 screen 15.4"
- atheros wireless card

What I have done to properly suspend/hibernate:
- installed xserver-xorg-video-intel instead of xserver-xorg-video-i810 (synaptic/apt-get)
- installed uswsusp (s2ram and s2disk, also installed with synaptic/apt-get)
- modified the kernel boot parameters to include acpi_sleep=s3_bios,s3_mode vga=0 and removed splash (in /boot/grub/menu.lst)
- use s2ram -f -a 3 to suspend to RAM
- use s2disk to suspend to disk

works like a charm. I am even suspending with the following on: beryl, mysql, apache2.

---

