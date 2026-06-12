---
title: "hardware unknown &amp;&amp; me == noob;"
date: 2005-11-03
forum: Hardware &amp; Laptops
---

### Post by Samm3h on 2005-11-03
Hey, ive used various versions of linux before, but ive only ever installed 2. 

RH8 and now Ubuntu, RH8 was very easy and simple, there wasnt much for me to do, but over the years things have changed.

Ive managed to install Ubuntu and i can log into my account without a prob. 

As for my hardware, pretty much everything is unknown. Ive been browsing the web for afew hours now and i cant seem to find what im looking for, so either 1 - im blind or 2 - i need to recompile the kernels

If anyone knows where i can find drivers for this system :

Abit AN8 Fatality SLi ( nForce4 sli chipset )
nVidia Ethernet Controller (onboard so part of my chipset )
MSI 6600 GT PCI-E gfx card ( nVidia chip again)

I appreciate any form of comment even if its flaming :P

// ive just read the 'installing nvidia' thread, so im going to try that, but if you folks can suggest anything other than following that in the mean time :)

---

### Post by MarcDM on 2005-11-03
don't know about your setup, but I know that the command :
> lspci 
should list all your pci devices by address and manufacturer string. And 
> lsusb

does the same for Usb devices.

---

