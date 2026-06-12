---
title: "Unable to install ATI Catalyst drivers for Mobility Radeon 5000"
date: 2010-11-02
forum: Hardware
---

### Post by diplo.monstarr on 2010-11-02
Hello everyone. I just installed Ubuntu 10.10 on my Dell Studio 1550. This is my first time using Linux as a 100% OS replacement, not emulation or live cd so I'm a bit lost. 

My first step was to enable the ATI proprietary FGLRX drivers in Hardware Drivers, but that didn't allow me to turn on Desktop effects. I have an ATI Radeon Mobility 5470, btw. 

I went to the documentation and read that the 5xxx series has problems with the drivers and I need to install ATI Catalyst. I followed the Binary download tutorial for ATI cards. I looked to see if there were compatible Linux 64 Catalyst drivers for my card, and the ATI website said there were. I downloaded it and followed the steps in the tutorial, with each step producing the expected result. On the last step, however, the terminal outputted:
Unable to open /etc/ati/control, please reinstall the driver
aticonfig: No supported adapters detected. 

What to do? Thanks in advance for help!

Also, so I don't start another topic, is there a reason my fan is spinning really fast whereas under Windows its pretty quiet?

---

### Post by diplo.monstarr on 2010-11-03
I am unsure of the forum etiquette here but I will bump for now. I know on some forums threads are ignored because of perceived laziness on the part of the OP. I think I've done everything I I'm aware of, especially being a a newb.

The documentation specifically mentions my card as problematic and needing Catalyst drivers. Also, the binary driver tutorial says that the ATI website will determine if your card supports Linux 64 bit drivers, and it did. On the incompatibility sticky, one user with the same exact card reported fuzzy images, but didn't have the same installation issue I did. Another user said that performance in Lucid improved with ATI drivers, but I don't have his Radeon 3xxx or Lucid. Sorry for text wall. G'nite folks.

---

### Post by mastablasta on 2010-11-03
wait 2 days before bump.
 
what catalyst drivers did you download (version)? also if you enabled ATI drivers first it means you already installed certain version (i think that's how it works) and you need to turn it off and clean/remove it before installing the new one you just downloaded and trying to install.

---

### Post by archithcr on 2010-11-03
Hi everyone  I have similar problems with my radeon 5650 drivers not working on my HP DV6 3143 laptop running ubuntu 10.10 64bit . When i activate the default ubuntu drivers, i am unable to boot into my desktop at all, even in recovery mode. if i reinstall my OS, and install the linux drivers 64 bit from AMD's website, i run into the same problems and i get a low memory corrupt message. I read somewhere that the presence of both Intel HD and AMD graphics adapters causes problems for ubuntu. Since there is no option in the BIOS to turn either one off, for the time being, i am running my ubuntu desktop on intel HD.  The switchable graphics run without problem on Windows 7. Hope someone can help us out.  thanks

---

