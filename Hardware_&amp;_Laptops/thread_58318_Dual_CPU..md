---
title: "Dual CPU."
date: 2005-08-19
forum: Hardware &amp; Laptops
---

### Post by oblivian on 2005-08-19
Hi,

How do I enable dual cpu support in ubuntu?

Thanks.

---

### Post by tseliot on 2005-08-19
You have to install a SMP kernel in synaptic. It will be called like "linux-image-2.6.10-5-[COLOR=Red]smp[/COLOR]" (this is just an example, just make sure the name has "smp").

---

### Post by oblivian on 2005-08-19
Great, thanks!

EDIT: OK, I have applied the 686 smp image. Shall I keep the other image (386 non smp) or should I uninstall it? (I am a bit worried waht happens too the GRUB loader etc...)

---

### Post by Brad wilkinson on 2005-08-20
using synaptic you should have no problems.

I upgraded from the CD (i386) to the i386-smp and K7-smp on two different machines, just reboot when synaptic is all done and away you go.

---

### Post by oblivian on 2005-08-20
Yes, it worked. Thanks a lot guys!

---

### Post by oblivian on 2005-08-20
One thing, does this apply to hyper threading too? And the Pentium D CPU's?

---

