---
title: "Problems after installation"
date: 2006-02-07
forum: Installation &amp; Upgrades
---

### Post by darksteel1989 on 2006-02-07
Hey, guys. I'm new here, yada yada...skip to the problem...

I have the 64-bit version of Ubuntu 5.10. I installed it with no problems. The problem came when I booted up. It goes through the checklist fine but afterwards, at the time when you're supposed to see the GUI, I get a monitor with a bunch of funky colored lines in it. I try the Live CD: same thing.

Now I think my specs are an important factor here so here they are:

2x Xeon Nocona 3.0Ghz 64-bit
nVidia GeForce 6600GT 256MB PCI-E
1024MB of RAM

The funny thing is, I tried the same Live CD on another computer equipped with only one Xeon and a built-in video card, but with the same RAM, and Ubuntu ran with no problems. I'm pretty sure its in the hardware. I just don't know if the deciding factor is the number of processors or the video card. I need a solution for this problem, or any possible workarounds. Thanks in advance.

---

### Post by BenTyreman on 2006-02-07
Strongly sounds like there's an issue with the graphics card driver. Have you tried running
```
dpkg-reconfigure xserver-xorg
```
and changing the graphics over to vesa, just to see if you can get any picture.

---

