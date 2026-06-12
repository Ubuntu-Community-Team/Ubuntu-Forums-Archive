---
title: "nVidia / AGP and slow performance"
date: 2008-12-03
forum: Installation &amp; Upgrades
---

### Post by IgD on 2008-12-03
I'm running Intrepid 8.10.  I've got an nVidia 6800 GT AGP video card.  I installed the 180.06 drivers from the nVidia website.  I also tried installing the 177 drivers that come bundled with Ubuntu.

After installing the video drivers, I was getting a black screen.  I edited xorg.conf and added this option:

Option         "NvAGP" "1"

Now I'm able to boot into Ubuntu just fine.  GLXGEARS also runs.  The problem is the performance is slow.  For example, if I run Savage on Windows I get 120 FPS.  Running the Linux port of the game, I'm only getting 20-30 FPS.

Looking at DMESG I see:

[   12.931179] agpgart-amd64 0000:00:00.0: AGP bridge [1106/3188]
[   12.932892] agpgart-amd64 0000:00:00.0: AGP aperture is 32M @ 0xe0000000
[   27.181520] NVRM: not using NVAGP, an AGPGART backend is loaded!

Searching through the threads on this forum, it looks like I need to find a way to disable agpgart-amd64 so I can use the NVAGP interface.  My assessment is the FPS is slow because Ubuntu is not using the AGP interface to its fullest capacity.

Can anyone help me out?  I'm in over my head.  Thanks!

---

### Post by IgD on 2008-12-04
Somebody mentioned:

[http://us.download.nvidia.com/XFree86/Linux-x86/177.82/README/chapter-12.html](http://us.download.nvidia.com/XFree86/Linux-x86/177.82/README/chapter-12.html)

If you are using a recent Linux 2.6 kernel that has the Linux AGPGART driver statically linked in (some distribution kernels do), you can pass the

agp=off

parameter to the kernel (via LILO or GRUB, for example) to disable AGPGART support. As of Linux 2.6.11, most AGPGART backend drivers should respect this parameter.

---

### Post by IgD on 2008-12-04
I solved the problem by replacing Ubuntu 8.10 i386 with AMD 64.  FPS is back over 100.  The other thing is Ubuntu didn't black screen after I installed the NVIDIA drivers.  I didn't even need to mess with the AGP stuff this time.

---

