---
title: "Radeon X300 card - x server fails to start"
date: 2006-01-15
forum: Installation &amp; Upgrades
---

### Post by bhsf on 2006-01-15
hi all, i'm trying to test ubuntu on a gateway mx7118, i get the "failed to start... x server not set up correctly" error when trying to boot from the live cd.  i have found a couple related posts like the following from kook44:

[I]When trying to boot from the live CD, I get:
"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the the X server output to diagnose the problem?"

then I edited /etc/X11/xorg.conf. had to find the "device" section & change the Driver from "ati" to "radeon" [/I]

however i'm new to linux and am a little lost.  any assistance would be greatly appreciated!

---

### Post by Kieffer87 on 2006-01-15
Im having the same exact problem only Im running a x800. Ive been dicking with it for about 3 hours no with no luck. Let me know if you find anything out.

---

### Post by Kieffer87 on 2006-01-15
Your gonna hate me :) but I put my old x300 card in and it booted up just fine :)  so I donno what to tell you.

---

### Post by christhemonkey on 2006-01-15
try running 
sudo dpkg-reconfigure xserver-xorg
and setting up your graphics card an monitor with that!

---

### Post by fireonyx on 2006-01-15
The ATI driver has been recently updated, and you have to install the driver, which you can find out here somewhere.  In the meantime, edit the /etc/X11/xorg.conf and under the graphics card, put the option "noaccel".  Here is the code : 
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
        Driver          "ati"
        BusID           "PCI:1:5:0"
        Option          "NoAccel"
EndSection

---

