---
title: "Problems with fglrx driver"
date: 2005-12-06
forum: General Help
---

### Post by MetalHannes on 2005-12-06
Hello
I have got a ATI Technologies, Inc. 3D Rage IIC (AGP). 
The ATI Driver works fine but i want to play ET :p As youve guessed Signal 11 and so on. Seraching gave i should use fglrx as Driver. Again Searching got me to the wiki/BinaryHowTo... so i followed the instructions installed xorg-driver-flgrx and said on the terminal:
> sudo gpkg-reconfigure xserver-xorg
Selected fglrx instead of ATI as Driver. Reboot.
X Server screwed up. Error logs told me some probs with lbGl.so(?). Then i installed xorg-driver-fglrx-dev(?) and nothing changed.

Any ideas?? Thx

Hannes

P.S. I know that ATi is not very popular in the Linux-support-team but i got it from an old pc. My other Grakifcs-card was a Texas Instruments and i was so happy i got a ATI and could have a chance of playing ET :( :( :(

---

### Post by Hezekiah on 2005-12-06
Sadly, the fglrx drivers don't support those cards.   They only support Radeon-family cards 85xx, 9xxx and newer.

Your best/only hope is with the standard xorg ATI drivers, which may not be of much help.

---

### Post by MetalHannes on 2005-12-07
To bad but anyway thx

---

