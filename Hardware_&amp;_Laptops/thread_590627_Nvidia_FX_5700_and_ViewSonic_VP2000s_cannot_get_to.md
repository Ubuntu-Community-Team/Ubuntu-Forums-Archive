---
title: "Nvidia FX 5700 and ViewSonic VP2000s: cannot get to 1600x1200"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by sbalea on 2007-10-24
Hi all,

I've just installed ubuntu 7.10 and I am having some problems setting up my monitor to its native 1600x1200 resolution.  Maximum I can get is 1280x1024. My monitor is a ViewSonic VP2000s (the Costco version of the VP201s).  My video card is a Nvidia GeForce FX 5700 manufactured by BFG.  

The problem appears with both the open source and the restricted NVidia drivers.  I've ran nvidia-settings and it appears that the monitor is not detected properly, since it claims that the native resolution is 1280x1024.  The xorg logs show that all 1600x1200 modes are rejected because they require a pixel clock that is higher than 150Mhz, which is the (autodetected) maximum supported on this monitor. 

Now this problem has always happened with the open source nv drivers, but I could fix it by simply installing the NVidia-provided driver package.  However, I was hoping that the restricted driver in Gutsy, which appear to be fairly recent, would work out of the box.

Any advice?  Thanks in advance...

Mihai

---

### Post by sbalea on 2007-10-25
Bump...

---

