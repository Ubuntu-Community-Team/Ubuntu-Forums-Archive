---
title: "DDR400 shows up as DDR333"
date: 2005-11-01
forum: Hardware &amp; Laptops
---

### Post by Joh_ on 2005-11-01
Not exactly related to Ubuntu but I just noticed and have to ask somewhere. :p

I've got an [ASRock K7S8X motherboard](http://www.asrock.com/product/product_k7s8x.htm) and at the same time I bought that, I also bought 256 MB DDR333 (PC2700) memory. As time went by however, I noticed I needed more memory, and since memory had decreased in price, I got myself 512 MB DDR400 (PC3100) just as my motherboard supports. This was about 3 months ago. I just noticed now however in the BIOS that the 512 one is detected as a DDR333 and not a DDR400 as it's supposed to. That's when I've got the memory frequency set to Auto. I can of course change it manually, but if I set it to DDR400, the 256 one gets set to DDR400 too, which isn't all too good. So how do I solve this? All I want to do is run my 256 MB memory as a DDR333 and the 512 one as DDR400.

Thanks in advance

---

### Post by Xentex on 2005-11-01
Well.... to put it simply:  you can't.

The memory must be running at the same speed as the other module(s) installed. They will all run at the fastest speed the slowest module can run (if that makes sense..)

If you put a DDR266 alongside the DDR333, both would run at DDR266.

What speed does your FSB run at? I assume 166MHz, as you had DDR333 installed first.  In that case, unless you're overclocking you won't ever hit DDR400 speeds (200MHz).

In general - especially AMD's, the FSB must run at a 1:1 ratio with the memory. Intel's can perform better at a ratio of 4:5 or something (Don't know exactly, never owned an Intel).

Don't worry about the DDR400 running at DDR333 - it's not going to hurt it - and it sure ain't gonna go any faster :-)

---

### Post by Joh_ on 2005-11-01
I just thought it was strange that I bought a DDR400 memory and it runs at the same speed as a cheaper DDR333. My friend had the same problem with another motherboard with only one memory (DDR400) running as a DDR333.

I went on and set it to DDR400 though to run both on 200 MHz since I figured the DDR333 sits right next to the CPU fan and gets cooler by that. I've had it like that for 3 hours now and no smoke yet. :p

Also, my FSB is at 133 MHz (AMD Duron 1.6 GHz) so I guess it shouldn't matter all too much what my memory uses, but it's the point that matters. :p

---

