---
title: "Solved! External HD on front USB"
date: 2005-08-15
forum: Hardware &amp; Laptops
---

### Post by LeadFoot on 2005-08-15
My external HD would not auto-mount when attached to the front USB ports, but will to the back USB ports.  It would just blink, spin up, then spin down.  Other USB devices -- media card, flash drives -- would work fine whether at the back or front.  There are some tell-tale lines from dmesg that says something like over-current at port x.  After googling for a couple of hours, I finally found the solution.  I have a MSI motherboard and Antec case.

The gist of the problem is pin 10 on the motherboard USB header should be unconnected.  Since the Antec case comes with a 10-pin block that (conveniently) plugs into the mobo header, I had no idea it would cause a conflict.  What I had to do was to pull the pin 10 socket out of the front panel USB connector block, fold it back against the wire and wrap it in electrical tape.  Now all my USB 2.0 devices auto-mount and work at the front USB ports.

More information at [this thread](http://www.techsupportforum.com/computer/topic/60768-1.html)

---

