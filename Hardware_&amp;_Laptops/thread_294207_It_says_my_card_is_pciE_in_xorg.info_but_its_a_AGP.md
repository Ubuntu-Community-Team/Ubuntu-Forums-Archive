---
title: "It says my card is pciE in xorg.info but its a AGP"
date: 2006-11-06
forum: Hardware &amp; Laptops
---

### Post by Karlsson534 on 2006-11-06
Hello.
First of all i must say that im new to Linux and have spent many hours this last weekend to set up my computer with Ubuntu.

i must say im sorry i purchased a ATI card for my comp because it hasnt been easy to set up the Linux drivers for it.
I tried lots of guides and failed untill i stumbled on a guide that was written about how to play World of Warcraft on Linux :).

I have now installed the packages from [www.ati.com](www.ati.com) and have get rid of that Mesa 3d thing from fglrxinfo and now it correctly states Radeon Ati etc..

So far so good.
The problem starts here, i try to run "fgl_glxgears" and i only get about 200FPS, i think that is pretty slow for my card comparing to others that have about the same cards getting 600< FPS.
I cant run XGL either it yust lock up random when loaded (yeah i have read about that problem and it seems to be related to the ATI x*** cards).

Now to my question: Can the poor output of my card be related to the fact that its stated to be a PCI Express card in xorg.info?

Section "Device"
Identifier 
"ATI Technologies, Inc. R430 UM [Radeon X800 XL](PCIe)"
Driver "fglrx"
BusID "PCI:1:0:0"
EndSection

---

