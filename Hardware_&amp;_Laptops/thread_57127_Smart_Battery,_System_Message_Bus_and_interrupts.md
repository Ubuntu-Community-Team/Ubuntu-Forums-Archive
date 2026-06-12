---
title: "Smart Battery, System Message Bus and interrupts"
date: 2005-08-15
forum: Hardware &amp; Laptops
---

### Post by jimbz on 2005-08-15
Hi,

I own an Acer Travelmate 3201 and like most Acer laptops it has a Smart Battery.

I downloaded the latest package from [https://sourceforge.net/projects/sbs-linux/](https://sourceforge.net/projects/sbs-linux/) ( 20050328 ) and I easily managed to patch my DSDT and add it to the initrd (thanks to all the good doc I found)...

But as the project guys say in the README:
> The SBS-CM stuff has one notable drawback: it accesses the SBS via the
System Management Bus found within the laptop's embedded controller
(EC). At the moment, the Linux driver for the EC suffers from the
problem that repeated EC transactions can lead to lost
interrupts. What this means in layman's terms is that keypresses and
other important events are lost; and this is not a small problem when
the battery is being polled once every few seconds.
and it's extremely annoying!

There is a patch provided in the sbs package but I can't apply it over the Ubuntu ones...

Do you know if a next version of the kernel will fix this problem or how I can patch this one conserving the ubuntu patches?

Thank you by advance

Jim

PS Please forgive a little frenchy for his english ;)

---

