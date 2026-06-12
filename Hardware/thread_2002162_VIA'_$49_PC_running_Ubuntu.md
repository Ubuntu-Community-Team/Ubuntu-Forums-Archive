---
title: "VIA' $49 PC running Ubuntu?"
date: 2012-06-12
forum: Hardware
---

### Post by MadsRH on 2012-06-12
Hi

Does anyone know if I'll be able to install Ubuntu on VIA Technologies' $49 Android barebones PC ? That would be _SO_ nice :P

[http://www.engadget.com/2012/06/12/via-technologies-apc-up-for-pre-order-ships-in-july/](http://www.engadget.com/2012/06/12/via-technologies-apc-up-for-pre-order-ships-in-july/)

[IMG]http://apc.io/media/apc/img/apc-banana.jpg[/IMG]

---

### Post by sanderj on 2012-06-12
Nope:

The VIA APC has a ARM11, which has a ARMv6 architecture (see [http://en.wikipedia.org/wiki/ARM_architecture#ARM_cores](http://en.wikipedia.org/wiki/ARM_architecture#ARM_cores)).


The current Ubuntu targets the ARMv7 and above Application Processor family (Cortex A8, A9 and above). See [https://wiki.ubuntu.com/ARM#ARM_Processor](https://wiki.ubuntu.com/ARM#ARM_Processor)

So that is a No Go.

Remarks:
Old Ubuntu versions supported older ARM architectures.
Debian does run on ARMv6 (like the RasPi).

HTH

---

### Post by MadsRH on 2012-06-12
sanderj -> Thank you! That's kind of sad. I also didn't know the Rasbery Pie can't run Ubuntu :-/

---

### Post by mastablasta on 2012-06-12
why sad? debian can do all the same stuff Ubuntu can. it's just maybe a bit more difficult to install.

---

### Post by sanderj on 2012-06-12
> **MadsRH said:**
> sanderj -> Thank you! That's kind of sad. I also didn't know the Rasbery Pie can't run Ubuntu :-/

Indeed. FWIW: I think Ubuntu/Canonical's focus is on a great user experience, thus requiring better CPU/GPU/RAM hardware.

However, it's strange and possibly questionable that VIA has chosen the ARMv6 CPU architecture for its APC. Why not an ARMv7 like the Cortex-A? 

It's also strange and possibly questionable VIA has chosen Android 2.3 (designed for mobile phones) and not Android 4.0 (designed for phones and tablets / computers).

I really wonder whether the ARM11/ARMv6 can run Android 4.0 at all.

The VIA APC also has got only 512MB, which I consider too little for Ubuntu 12.04.


So I'm looking forward to an ARMv7 system with at least 1GB RAM. And especially a laptop (13 inch) would be very nice.

---

