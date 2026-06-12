---
title: "problem to calibrate stylus on a tablet PC"
date: 2008-04-09
forum: Hardware &amp; Laptops
---

### Post by roy.nico on 2008-04-09
Hello, 

I have a Tablet PC Fujitsu T4220, with Ubuntu 7.10. My stylus is not well calibrated, and i read somewhere taht there is a tool called xsetwacom to do it. But when i start the command  xsetwacom  i obtain the following message : 

>> xsetwacom 
xsetwacom: error while loading shared libraries: libxcb-xlib.so.0: cannot open shared object file: No such file or directory

Any idea about what it means ? Does it exist another way to calibrate le stylus ? 

Thank you in advance for any help

nicolas

---

### Post by Magnes on 2008-04-09
Search for libxcb in synaptic and install it.
Also -  try this (Tablet Apps) - [http://alexmac.cc/tablet-apps/](http://alexmac.cc/tablet-apps/)

---

### Post by roy.nico on 2008-04-09
Thanks a lot for the hints !

I installed the package libxcb-lib in synaptic and now the xsetwacom command works... but i don't know how to use it :-( 
The program "Tablet Apps" ([http://alexmac.cc/tablet-apps/](http://alexmac.cc/tablet-apps/)) seems to be interesting, but the cursors "device tilts" (which are precisely those i need to calibrate, as far as i understand) are fixed at 0 and i can't move them.

nicolas

---

