---
title: "Ubuntu with Vortex86 arch ?"
date: 2007-10-14
forum: Hardware &amp; Laptops
---

### Post by Steel98 on 2007-10-14
Hello! I have eBox-2300, this  is Thin Client. 
Hardware specifications.
CPU: Vortex86 (System-On-Chip)
System mem: 128MB SDRAM
Flash memory: 32Mb, but I up this parameter to 2GB Horizontal type Disk On Module.
VGA: 8MB
Enhanced IDE interface, 44 pin 
RS-232, RJ-45 Ethernet connector
3 USB
PS/2 mouse, keyboard

Can I install Ubuntu on this system? I don't know how install, only if load image on in Flash and try boot. But how configure image, and does support Ubuntu Vortex86 processor?

---

### Post by kunilkuda on 2008-01-08
I have microclient ([http://www.norhtec.com/products/mcr/index.html](http://www.norhtec.com/products/mcr/index.html)) which using Vortex68 SoC. I've replaced its IDE with 40GB Notebook HDD.

I have tried installing Ubuntu 6.06 desktop, Ubuntu 7.10 (Gutsy) server, 7.10 (Gutsy) desktop, Fedora 8, openSUSE 10.3..and none of them working.

It seems like the installer cannot find the correct kernel to be installed (I think because Vortex86 doesn't give the "standard" x86 signature). 

One way to fix this, is by download and install the kernel manually (using the installer DVD as the temporary OS -- use Rescue mode). But I haven't gone to that path yet.

I'll let you know if I've found the solution.

Btw, other than Ubuntu, Knoppix, Slax, and X-Linux ([http://www.dmp.com.tw/tech/os-xlinux/](http://www.dmp.com.tw/tech/os-xlinux/)) can be used in Vortex86. But they lack of softwares as in Ubuntu / Debian.

---

### Post by Steel98 on 2008-01-09
It's work! DamnSmallLinux start on my thinclient!

---

