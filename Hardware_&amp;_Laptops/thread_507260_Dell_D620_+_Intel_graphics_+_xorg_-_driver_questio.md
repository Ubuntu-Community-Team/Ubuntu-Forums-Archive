---
title: "Dell D620 + Intel graphics + xorg - driver question"
date: 2007-07-22
forum: Hardware &amp; Laptops
---

### Post by docvalde on 2007-07-22
Hi there,

I'm new here so I hope this is the appropriate area for my question. In medias res:

I have a Dell D620 with the Intel 945(GM?) graphics chipset. This works like a charm with the intel-driver (no 915resolution necessary, 3d acceleration etc.).

Unfortunately, the intel driver does not support Xinerama, which is absolutely needed by me. Therefore, I switched back to the i810-driver (and got Xinerama working without much trouble).

Now the question: 

Why can I only have installed the i810 driver XOR the intel driver? I would like to use i810 for my Xinerama configs and intel for the mobile, single screen config. synaptic wants just one of them.

TIA && regards,

Doc.

---

### Post by shakyone on 2007-07-30
I am afraid you are out of luck.  I have the D620 and an extra monitor  Xinerama is designed for desktops with two identical displays.  You have to do some shoehorning to make it work with a laptop.  I gave up on this effort once I realized it was not a practical option.  It may work better if you have a flat panel with the same resolution set as on your laptop.  But otherwise I couldn't venture a guess.

     You can check out Synergy, if you have the monitor connected to a different desktop on the same network.  (It doesn't have to be the same OS).  It is a pretty snazzy application.  [http://synergy2.sourceforge.net/](http://synergy2.sourceforge.net/)

Shaky

---

