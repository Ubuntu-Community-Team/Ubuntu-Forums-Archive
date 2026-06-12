---
title: "black screen of death"
date: 2005-09-11
forum: Hardware &amp; Laptops
---

### Post by BruceFreeburger on 2005-09-11
Folks:
  I simply cannot run Ubuntu on a PC with an nVidia card. The cards are old entry level hardware (MX 420 and 2 FX5200s). 
  Ubuntu goes through the install process until it reboots. When it switches from text mode to graphics, in three different PCs, the screen goes black.

  GNU Debian installs with a cruder driver I select from menu.
 Xandros installs fine and uses the nVidea driver.

 I thought the problem may be Gnome and the nVidea driver (Xandros uses KDE), but Kubuntu also goes black when switching out of text mode.

   Ubuntu will install if I remove the graphics card. If I then install the nVidia driver, shut down the PC and install the card, the system will still go black and freeze.

  Cheers,
  Bruce F

---

### Post by ry_ry on 2005-09-11
[QUOTE=BruceFreeburger]Ubuntu will install if I remove the graphics card. [/QUOTE]

Do you have both onboard graphics and then a graphics card in the AGP slot? If so, have you tried to turn off the onboard graphics in the BIOS?

Here's something that might help also from the Ubuntu wiki:
[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

Hope this helps. :)

---

