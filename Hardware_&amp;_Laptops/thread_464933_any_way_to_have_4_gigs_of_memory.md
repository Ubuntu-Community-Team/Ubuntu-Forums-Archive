---
title: "any way to have 4 gigs of memory?"
date: 2007-06-05
forum: Hardware &amp; Laptops
---

### Post by redneckracin on 2007-06-05
hey is it possible to make my 32-bit version of feisty to recognize the fact that i have 4 gigs of ram in my system?

Or does a guy have to migrate over to the 64-bit? My concern about this is driver compatibility with my 8600GT.

---

### Post by Cappy on 2007-06-05
4GB and over you must use a 64-bit OS. Your video card will work fine with 64-bit (you could use envy unstable)

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by patrickfromspain on 2007-06-05
4 gigs or ram should be fine with 32bit.. in fact, it's the maximum that a 32bits OS can address:

2^32 = 4294967296bytes = 4096Mbytes = 4 gbytes

---

### Post by Ken_Lewis81 on 2007-06-05
But x86 has always done daft things with its memory addressing.  One of which is to map PCI-connected peripherals that need memory access into the 32-bit memory address space, at the cost of being able to use 4 GiB of RAM.  AMD64 doesn't have this problem.

take care.
Ken.

---

