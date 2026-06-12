---
title: "Memory compatibility."
date: 2011-08-15
forum: Hardware
---

### Post by A Traveller on 2011-08-15
Hi.

I would like to use 4 x 2GB DDR3 RAM sticks with my GA-890GPA-UD3H motherboard. I've already got 2 x 2GB DDR3 sticks, which are double-sided. What would be the better/safer option to take in terms of compatibility/performance with Ubuntu? Purchase a further 2 x 2GB single-sided or double-sided sticks? The motherboard manual states "Dual channel memory architecture". Is that the same as double-sided?

Thanks.

---

### Post by .... on 2011-08-15
> The motherboard manual states "Dual channel memory architecture". Is that the same as double-sided?No. Double-sided means RAM chips on both sides of the stick for more capacity. Dual-channel means 2 read/write channels between the RAM and the mem controller for accessing more date per clock. Neither one matters for the OS.

The safest bet is always something on the mobo manufacturer's approved RAM modules list, but other RAM modules should work fine if they follow the JEDEC standard [http://en.wikipedia.org/wiki/DDR3_SDRAM#JEDEC_standard_modules](http://en.wikipedia.org/wiki/DDR3_SDRAM#JEDEC_standard_modules)

> Purchase a further 2 x 2GB single-sided or double-sided sticks?It doesn't matter. What does matter is that you're using a 64-bit OS to take advantage of the extra RAM, or using PAE kernel for 32-bit.

---

### Post by A Traveller on 2011-08-15
Ok, thanks for the helpful reply, .....

---

