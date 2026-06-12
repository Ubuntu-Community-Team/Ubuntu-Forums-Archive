---
title: "fix suspend when using ATI Radeon video driver?"
date: 2007-03-12
forum: Hardware &amp; Laptops
---

### Post by taiko on 2007-03-12
When using the fglrx ATI video driver or the standard ATI Radeon video driver I am unable to return from a suspend (i.e. the laptop suspends, but pressing the power key to turn it back on never powers on the screen).  I tried using  a non 3D graphics card video driver and I was able to suspend to ram and return successfully so I think there's probably something that isn't getting turned back on correctly when I try to return from a suspended state using the 3D accellerated drivers.  Does anyone have any suggested fixes?  Thanks.

NOTE:
I'm using a 128MB ATI Mobility Radeon 9700.

---

### Post by vespo on 2007-03-23
Hi

suspend is just not supported by ATI fglrx. You should write AMD to put pressure on them to get better linux support.

---

