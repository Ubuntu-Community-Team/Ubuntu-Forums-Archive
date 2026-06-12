---
title: "ATI RADEON x300 on Ubuntu 9.10"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by n4q on 2009-11-02
Hey guys my graphic card is an ATI RADEON x300, I went on the ATI website and I found a driver for x300 in the Linux section. When I download the file the extension is .run, when I double click it I get an error and it doesn't work. Can someone please tell me how to install my graphic card? I want the special effect thing to work with my dual screens.

Ubuntu 9.10

---

### Post by Mark Phelps on 2009-11-02
You can't install that driver in Ubuntu 9.04 or newer.  It conflicts with the version of the XServer.

Your only recourse is the open source driver -- which is installed by default.  If you're seeing a desktop, you already have that driver installed and there is no other version you can use.

If you force the installation of the driver you got from ATI, you will have to boot into a console to manually remove the ATI driver and replace it with the open source driver.

---

### Post by OmegaAI on 2010-04-10
Well that sucks... I am having the same issues... I install the ATI drivers (9.3) on Karmic and brings up a screen when I reboot saying that they have failed to load D:

---

### Post by Fenris_rising on 2010-04-10
I have an ATI Radeon x300 to. Dual screen with compiz works OOTB with no proprietary drivers. No tricks were required to get it going other than unticking the mirror screens option in the display control window and installing CCSM, simple CCSM, Compiz fusion icon and emerald.

regards

Fenris

---

