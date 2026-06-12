---
title: "Lenovo intergrated graphics card wont work"
date: 2007-11-29
forum: Hardware &amp; Laptops
---

### Post by xitdedragon on 2007-11-29
I have a Lenovo 3000 N200 T7100 with an intel integrated graphics card. Copy and paste from lspci:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

The one Gusty choose for me doesn't allow me to use any special compiz stuff. Also, the website for the card said that Linux made their own, so that was no use. Anyway, I know there are plenty to try, but I was wondering what you guys suggest.

---

### Post by xitdedragon on 2007-12-06
Bump.

---

### Post by victorgreen on 2007-12-07
If thats the intel 3100gma that they have in T61's and X61's [which Im on now, great machine], then there is a flaw in the intel driver that makes compiz do some weird stuff, as in you cant play video files with compiz enabled. Thus that card is blacklisted from using compiz, You can override this obviously :), but you wont be able to play videos while you have it enabled. 

RUN:
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

 reboot

get the compiz settings manager through synaptics

and then go to system ==> appearance 

esktop effects tab

enable custom and go into settings and enable your cube

---

### Post by staib on 2007-12-17
This worked for me - thanks.

---

### Post by SorryGoFish on 2008-03-23
Do either of you have external, non mirrored monitor working?

---

