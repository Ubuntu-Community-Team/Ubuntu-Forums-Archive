---
title: "sony memory stick"
date: 2006-02-11
forum: Hardware &amp; Laptops
---

### Post by Vega on 2006-02-11
how do I make ubuntu recognize my memory stick drive?

thanks in return.

---

### Post by houseofmore on 2006-02-20
same here!

---

### Post by abeowitz on 2006-03-23
In my Sony PCG-FRV25, I believe it's a winbond chip, (as that's what the window's calls that driver.)

I've not gotten it to work yet, but currently the wbsd module loads successfully.  I'll need to add a patch to the 2.6.15 kernel and recompile...

This site is tracking this project and has a descent how-to:

[http://mmc.drzeus.cx/wiki/Linux/Drivers/wbsd](http://mmc.drzeus.cx/wiki/Linux/Drivers/wbsd)

I just downloaded the 2.6.16 kernel, and it does include the mmc_block module, but I've not gotten 2.6.16 to boot up for me yet...

---

