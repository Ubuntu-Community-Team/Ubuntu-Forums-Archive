---
title: "Will my graphic card work on ubuntu?"
date: 2007-04-28
forum: Hardware &amp; Laptops
---

### Post by bamsee on 2007-04-28
Hi,

I've a (LINK:)  [NVIDIA GeForce 8800 GTS - ....530M 640MB DDR DUAL DVI TV XT](http://www.xfxforce.com/web/product/listConfigurationDetails.jspa?series=GeForce%26trade%3B+8800&productConfigurationId=879503), will it be any problem with drivers for this graphic card? On the offical website i don't find anything regarding to linux.

Thanks for help! :)

---

### Post by karoliina on 2007-04-28
Hi,

You just need to install the nVidia binary driver if it is not included by default. 
Other than that it should work. 

We have in our living room Geforce 8800GTX 768 MB (Club3D) + 30 inch Dell widescreen tft-monitor
running resolution 2560x1600 and it works without problems. The PC itself is AMD64 with SLI main board, but we have only one GF8800GTX installed so far. We have not yet updated this system from Suse 10.1 to Ubuntu though but we have been having plans to do so. With Suse the driver was not included by default and it required some work on command line to get it working because with the included drivers no graphics mode ever appeared, but the nVidia installer compiles the kernel module without the user required to do other than run the installer.

I am running X-plane 8.60 ([http://www.x-plane.com](http://www.x-plane.com)) with reasonable framerate with the nearly maximum details and with the full 2560x1600 resolution on the living room's Linux-PC. Unlike ATI proprietary drivers, nVidia binary drivers work. I have also tested Quake 4, Vendetta, Doom 3 etc. Everything works with stellar performance (the only game that still demands more than Geforce 8800 GTX can deliver is the X-plane). I am also using AC3D 3D modeling program and a variety of other applications which use OpenGL and everything works nicely. In general, I would like to always recommend nVidia for serious 3D in Linux. I have ATI on some laptops (IBM and Dell) and it never worked properly and then ATI discontinued supporting the chipset besides of that the performance figures the mobility radeon can offer is a faint laugh compared to the GF8800GTX supercomputer on a gfx-chip =)... 

Best Regards,
Karoliina Salminen
[http://www.karoliinasalminen.com/blog](http://www.karoliinasalminen.com/blog)

---

### Post by bamsee on 2007-04-28
Thanks for reply!
I'll install Ubuntu, then I'll come back with some information.
Thank you! :)

---

