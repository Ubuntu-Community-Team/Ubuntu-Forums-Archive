---
title: "Problems with getting the live CD to boot."
date: 2007-06-05
forum: Hardware &amp; Laptops
---

### Post by MKenney on 2007-06-05
I've tried quite a few different methods, but none have worked. 

Video: GeForce MX 4000
Processor: Intel Celeron 1300 MHz
Ram: 512 Megs
(It's an old HP Pavilion 520n with a spare PCI graphics card I had lying around)
Monitor: Widescreen 1440x900
The disc: Ubuntu 7.04 32bit.

When I use "safe graphics" boot, it will actually give me an error message--"X Server Error... Fatal Error: No Screens Found".
When I use the regular method, it hangs at a black screen.
When I use "vga=771" or "vga=900" it hangs exactly like before.
When I use "noapic" and/or "nolapic" it hangs.
When I use "no splash" and "pci=noapic"... ditto.

As Ubuntu loads drivers, it tells me that the system doesn't possess a reboot flag. If that is helpful in your diagnosis. 

I've never had good luck with ubuntu, and that's a pity...

---

### Post by mahiyar on 2007-06-05
Try these various options.
1)try another cd.
2)try same cd on another comp.
3)try some other distro

---

### Post by MKenney on 2007-06-05
I tried the same CD on my main computer and it worked fine.


After using the alternate CD to install it on the other computer, I'm stuck again. Same problem, only now I have the proper drivers.

---

