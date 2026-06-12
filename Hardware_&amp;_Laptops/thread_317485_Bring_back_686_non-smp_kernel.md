---
title: "Bring back 686 non-smp kernel?"
date: 2006-12-12
forum: Hardware &amp; Laptops
---

### Post by hardyn on 2006-12-12
what are the odds of this happening? there are few cases that the inclusive SMP kernels cause problems with a few Pentium M notebooks, mine included; and i have not been able to rebuild a kernel from ubuntu source yet has worked with all the hardware support of the OEM SMP kernel. (i keep losing networking).

Thanks.

---

### Post by adaptr on 2006-12-12
This points out an interesting discrepancy: you are using Feisty, yet do not know how to compile a kernel.
Compiling a kernel without SMP is simple: copy the config of the Feisty 686 SMP kernel and open it with "[FONT="Courier New"]make (menu|X)config[/FONT]".
Then simply de-select the SMP support and build it.
You also have to build the initrd for it, but I'm sure that is documented somewhere.

---

### Post by hardyn on 2006-12-12
nope, using edgy, i just don't exect the ubuntu guys/gals to put more work into edgy... im looking forward in time on this one.

It would be nice to not have to keep building kernels though, and i seem to keep losing hardware support after a kernel rebuild, which i may be able to correct; havent tried yet, but they are building there fancy 586/smp kernels, and the plain 386 kernel, it would be nice if they would do a 686/uni at the same time.

just a thought.

---

### Post by hardyn on 2006-12-13
apparently the 386 kernel, is just that, a generic processor uni-proc. kernel. go figure.

---

