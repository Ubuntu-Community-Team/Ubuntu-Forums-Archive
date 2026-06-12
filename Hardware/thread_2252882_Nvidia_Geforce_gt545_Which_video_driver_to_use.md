---
title: "Nvidia Geforce gt545: Which video driver to use?"
date: 2014-11-15
forum: Hardware
---

### Post by swipisnt on 2014-11-15
hello friends.

my video card is gforce gt545 oem and in additional drivers i have 5 option to choose: 

nvidia binary driver -version 331.37 from nvidia 331 (proprietary tested)
nvidia binary driver -version 304.117 from nvidia 331 update (proprietary)
nvidia binary driver -version 331.38 from nvidia 331 update(proprietary)
nvidia legacy binary driver - version 304.117 from nvidia 304 update (proprietary)
x.org x server - nouveau display driver (**by default active this one**)

which one is the best for gaming?

thank you

---

### Post by sudodus on 2014-11-15
It is hard to tell before trying. If you are lucky, someone with exactly that card will reply and help you. (I have a GeForce GT 430/PCIe/SSE2 and run the driver 304.88 in Ubuntu 12.04.5. Nouveau works too, but cannot use advanced stuff like VDPAU, which is good for playing HD video.)

You can test all the available drivers and select the one that works best for you. If one of them does not work at all, you can boot in text mode, replace it and reboot.

---

### Post by swipisnt on 2014-11-15
thank you for reply. looks like 331.37 working good

---

