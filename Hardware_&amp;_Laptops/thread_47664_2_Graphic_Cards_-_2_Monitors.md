---
title: "2 Graphic Cards - 2 Monitors"
date: 2005-07-09
forum: Hardware &amp; Laptops
---

### Post by Cordan on 2005-07-09
Hi,

i am trying to fix my problem since some days now but i could not find any information about it anywhere =) Maybe you guys can drop me some lines.

I installed Ubuntu 4 days ago and it works perfectly =) (there are some little flaws but im getting to fix that slow but steady).

One of my problems is that in my computer are 2 gfx-cards, one pci, one agp. Ubuntu has recognize both (thats what the Devicemanager says.

XORG runs only on the pci gfx-card (GeForce MX 200), the AGP one (GeForce TS 4200)  is only used during the boot up and shut down phase (where you see if the systems and daemons are working) when the Desktop (the graphical one) starts the agp monitor keeps black.

I have installed succesfully the NVidia drivers.

Now i need help on how to use 2 gfx and 2 monitors (to extend the desktop) on my computer =) (if you need further information post and ill provided them asap).

Thank you very much in advance =)

---

### Post by blazko on 2005-07-09
Hello Cordan,

I have really no idea in such things, but the nVidia binary driver knows a parameter called BusID, where -in case of multiple cards- you can tell what device is really ment. BusID is some PCI id as retrieved by lspci (as root).
But please, I have never tried this, so better carefully read the documentation in /usr/share/doc/NVIDIA-GLX (or so) according to the BusID stuff.
If I remind correctly, BusID can be used per graphic card section, though it should work. In the layout section of the X conf, you should be able to combine the two graphic card sections.

Greetings,
Timo

---

### Post by Cordan on 2005-07-10
Thank you very much =)

After reading the NVidia file I changed my xorg.conf according the documentation and now I have both graphiccards and monitors working properly =)

---

