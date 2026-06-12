---
title: "hub overcurrent"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by DrysdaleAE on 2007-10-19
Hi:  in a terminal or on dmesg I get a bunch of messages saying  "hub 4-0:1.0: over-current change on port 1", alternating with the same thing for port 2.  There does not seem to be anything wrong with my usb ports, and I remember this is due to some oddity of a VIA chipset. I remember that there was some simple way to disable usb 2, but I can't find it any more in the forums.  Does this ring a bell with anybody, and can you point me to the way this was done?  I had done this, but it went away when I upgraded to Gutsy.

Alan

---

### Post by DrysdaleAE on 2007-10-21
Disabling USB 2 in the BIOS fixes the message problem.

---

### Post by Shane10101 on 2008-02-15
I've done Google searches on this, and keep seeing something about "uhci" (or something like that) and "oc_ignore" -- something about setting this parameter when the kernel boots.  

Does anyone have any idea how to use this fix, and what the exact module/parameter is?

Sorry for the vague question  :(  

Shane

---

