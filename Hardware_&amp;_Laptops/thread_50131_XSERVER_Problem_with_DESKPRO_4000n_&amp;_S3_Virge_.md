---
title: "XSERVER Problem with DESKPRO 4000n &amp; S3 Virge Chipset"
date: 2005-07-19
forum: Hardware &amp; Laptops
---

### Post by netkit on 2005-07-19
Hello,

I installed Ubuntu on my old Deskpro 4000n (233MMX,256MB RAM, 5GB HDD).
The installation runs without Problems but after booting the installed system, the xserver crashes with "no devices found" in the log file.
I found some hints in the net that the svga driver will not work, so I configured xserver with S3 Virge but the same problem.
can anybody give me a hint... 

...console mode works fine...

thanks

netkit

---

### Post by Teroedni on 2005-07-19
Can you post some of the xorg.conf

I know you cant copy since your in console, but can you write in manually tha part of xorg conf from device and downwards


Your probably now but incase you dont here how to get xorg.conf in console

sudo nano /etc/X11/xorg.conf

---

