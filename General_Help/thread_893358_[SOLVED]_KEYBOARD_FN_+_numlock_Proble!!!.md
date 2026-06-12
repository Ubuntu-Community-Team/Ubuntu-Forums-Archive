---
title: "[SOLVED] KEYBOARD FN + numlock Proble!!!"
date: 2008-08-18
forum: General Help
---

### Post by scu-ba-de-buntu on 2008-08-18
AHH! Half my keyboard will not work without me holding the f***ing ¨fn¨ key. I use a laptop, DE33 Inspiron 1501. never had a problem until recent (couple of days ago)  software upgrade, running 8.04. randomly turns on hand then unfixable even by pressing numlock, unless reboot. when i try to fix it, if i press numlock, then those keys do nothing. so, i can either type holding fn, use the numbers it out puts, or reboot every couple of mins.

---

### Post by guttingfish on 2008-08-18
If it's the same problem as happened to me with my mac keyboard then hitting F6 twice should turn off the numlock thingy...

also check the value of /sys/module/hid/parameters/pb_fnmode

if it's at 1 then try changing it to 2. You can do that by sudo copying a file containing only 2 over it.

---

### Post by scu-ba-de-buntu on 2008-08-18
Than2s for the response, but no go, unfortunately. f6 twice does nothing. and /sys/module/hid/parameters/pb_fnmode d6esn´t exist. /sys/module/* d6s though. :( it is not the keyboard-mouse control thing that is discussed in other threads either.um, break ca4ses them to turn into arrows. note that this is not totally an FN problem, as other fn buttons such as volume (END) and dim (arrows) are not misbehaving.

SOLVED: UNINSTALL mouseemu regression problem.

---

