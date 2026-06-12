---
title: "USB devices not working on 32-bit Ubuntu brand new PC"
date: 2018-06-10
forum: Hardware
---

### Post by sherrrock on 2018-06-10
Hi, I have just purchased a new desktop pc with Asrock mobo and found that the keyboard and mouse attached not working once I boot up with Ubuntu 16.04 LTS i386 (32-bit). I have tried to upgrade the BIOS version from 1.2 to 1.6 but the issue still persists.
However, the Ubuntu 16.04 AMD64 is working perfectly fine on the same PC. In the BIOS setting, I have tried to enable Legacy USB Support, PS/2 Simulator and XHCI Hand-off but there's no difference.

Here's the specs:
MotherBoard: ASRock X299 Killer sli ac
Processor: Intel Core i7-7800X Skylake-X 8-Core 3.6 GHz
Graphics Card: GEFORCE GTX 1050 (2GB)

Thanks in advance for the help!

---

### Post by sudodus on 2018-06-11
Why are you not happy with Ubuntu 16.04 AMD64 which is working perfectly fine?

---

### Post by sherrrock on 2018-06-11
Unfortunately I have to use some applications for work purposes which requires a 32-bit OS.

---

### Post by sudodus on 2018-06-11
I see. Have you tried a **32-bit version** of an Ubuntu community flavour, Kubuntu, Lubuntu, ... Xubuntu of the new release **18.04 LTS**? It might work with your computer's hardware. A new version is more likely to work with new hardware.

You find them via this link: [releases.ubuntu.com](http://releases.ubuntu.com/)

Try them live to check that things work as they should, and if they do, select the desktop environment that you like best for installation.

---

### Post by mörgæs on 2018-06-11
Also Ubuntu 18.04 is still available as a 32 bit version. You just have to begin installing from the minimal ISO.

By the way, which applications require a 32 bit OS? Sounds strange to me.

---

### Post by sherrrock on 2018-06-13
I have tried installing minimal ISO of Ubuntu 18.04 as well as the other Ubuntu community flavours but the issue still persists. Until Asrock has finally replied my email with a solution. All I need to do was to disable the "Above 4GB MMIOBIOS assignment".

BIOS path: Advanced > Chipset Configuration > Above 4GB MMIOBIOS assignment

Thanks a lot for the help!

---

### Post by sudodus on 2018-06-13
Thanks for sharing your solution :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

