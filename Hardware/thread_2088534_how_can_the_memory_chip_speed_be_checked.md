---
title: "how can the memory chip speed be checked?"
date: 2012-11-26
forum: Hardware
---

### Post by s1baker on 2012-11-26
hi,

I have a old desktop box that is running xubuntu with xfce  ( 12.04.01 ).

It has two memory slots in it and the specs for the
motherboard show that it can max 2 gigs and run DDR up to PC3200 (400mhz).

I now have one slot filled with PC3200 , 1/2 gig.

I would like to verify that this chip is running at 400 mhz. I think it may be clocking back down to PC2700.

Is there anyway to do that from the terminal?

thanks

---

### Post by ahallubuntu on 2012-11-26
The motherboard BIOS should be set to clock the RAM at the rated speed or as fast as the motherboard can support, unless you have manually set the RAM timings in BIOS.  (Not possible in every BIOS setup.)

If there is no way to change RAM timings in BIOS, don't worry about it.  If the motherboard can't support 400MHZ and is running it at 333MHZ, your only option is to try overclocking the FSB, if your motherboard supports that.  I really don't recommend that unless you are desperate for more performance and willing to risk instability.

---

