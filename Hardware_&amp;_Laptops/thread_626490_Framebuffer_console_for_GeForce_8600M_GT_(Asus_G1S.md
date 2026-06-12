---
title: "Framebuffer console for GeForce 8600M GT (Asus G1S)"
date: 2007-11-29
forum: Hardware &amp; Laptops
---

### Post by uqbar on 2007-11-29
Hi all.
I installed KUbuntu Gutsy on a fresh new G1S that never booted Windows :-)
Susequently I've installed the nvidia-glx-new driver and everything under X is fine and fast.
The only point now is that there's no visible console during the boot.
Once the kernel is started by GrUB I can see just a couple of lines, then the LCD goes black until X gets the control of the display.
I'd prefer to see the boot diagnostics, possibly with hi-res console, but even an 80x25 is better than 0x0 :-)

 I've tried different vga=... and video=nvidiafb:... kernel parameters. But got no luck.
 Any hint?
 Thanks,

---

### Post by uqbar on 2007-11-29
Well, you can start getting an 80x25 boot output by changing the "splash" with "nosplash" in the /boot/grub/menu.lst file or by changing it by hand during the boot.

---

