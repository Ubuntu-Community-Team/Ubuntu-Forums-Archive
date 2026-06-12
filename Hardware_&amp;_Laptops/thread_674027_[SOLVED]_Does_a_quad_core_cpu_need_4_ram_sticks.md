---
title: "[SOLVED] Does a quad core cpu need 4 ram sticks?"
date: 2008-01-21
forum: Hardware &amp; Laptops
---

### Post by ttiell on 2008-01-21
It's pretty well stated in the title.  But I'm updating computers.  Didn't know if a quad core cpu needs 4 sticks of ram.  I know that dual core needs 2 sticks of ram.

---

### Post by aashay on 2008-01-21
Im on a dual core and a single stick of 1GB RAM. So I dont think you do.

---

### Post by Enfenion on 2008-01-21
You do not need more than one stick. The reason that sets of two "matched" sticks are recomended is that this improves the speed of the ram in addition to the capacity.
[http://en.wikipedia.org/wiki/Dual-channel_architecture]("http://en.wikipedia.org/wiki/Dual-channel_architecture")

---

### Post by tgalati4 on 2008-01-21
You use 2 or 4 sticks to get *striping* across the ram to improve read and write speed.  This is part of the DDR2 and DDR3 specification.  That is why your memory slots (on newer motherboards are two-color.  If you use 1 or 3 memory sticks, the BIOS defaults to regular memory addressing.

Be aware that you need to rigorously test your new RAM with memtest86+ by running it overnight for 30 pass cycles.  The higher speeds of RAM striping cause the RAM sticks to heat up.  This is why the high-performance RAM has heat spreaders.  You need to verify that the RAM that you have will operate at full speed with the motherboard and processor.

The front-side-bus speeds and read/write speeds of L1, L2, and sometimes L3 cache of modern Intel processors are so fast that regular RAM speeds have not been able to keep up.  DDR2 and DDR3 is one method of coping with this speed increase.

---

### Post by ttiell on 2008-01-21
i don't understand.  you say you don't need more that one.  but the wiki page says, the more sticks that you have = the more data that can be accessed at one time.  seems to me and i could be wrong because i am a lot.  if you only have one ram stick, that means that the cpu's have to wait in line to do something until the other cpu is done using the ram.  so in a sense, you would be only using one cpu at a time, so you would only really be running a single core processor.  correct me if i'm wrong.

---

### Post by Enfenion on 2008-01-21
The CPU does not read/write from the memory on every cycle, so you get a performance boost from a single core.

I do not think you have a Quad-channel arch. anyhow, so you do not get another boost from adding two more sticks.

Hope this helps =)

---

### Post by tgalati4 on 2008-01-21
I have a Pentium D which is a dual core processor with two separate L1, L2 caches.  Newer Core 2 Duos have separate yet shared coassociative caches so that either processor can access instructions from the other's cache.  This can provide a speed up as well.  The speed difference in my testing of DDR2 RAM (2 by 1 GB sticks) running slightly overclocked at 350 MHz (700 MHz data rate) using Corsair xms2 DDR2 6400--800 MHz capable:

5-5-5-15 timing  3,199 MB/sec (at 2.94 GHz processor speed, 210 MHz Front Side Bus--slight overclock from 200 MHz)

4-4-4-12 timing 3,289 MB/sec (a modest 2.78%, nothing to write home about despite the hype)

Single RAM stick vs Dual RAM stick DDR2-dual channel mode:

At 2.4 GHz processor speed (underclocked)
859 MB/sec vs 1,450 MB/sec  (a 68.8% improvement, something to seriously consider).

So you see dual channel mode kicks butt, but latency is a much smaller contributor to performance.  This is using an AOpen Intel-based i945gm motherboard.  Your mileage will vary.

---

### Post by MoToR on 2008-01-21
**ttiell**, the answer to your question is no.

There's no connection between a single CPU's core count and a number of memory sticks in PCs. CPU doesn't even know how much sticks are installed, unless it's AMD with integrated memory controller. And even then the CPU minds his own business and works with memory through a controller of that type or another which deals with the number of sticks and their type/size. Multi CPU systems are another story.

Dual Channel RAM approach appeared long before the multi core expansion and I wouldn't call it "stripping", which is more an HDD array term, but rather I'd say in general - the bus gets twice wider, the maximum amount of data that can pass simultaneously between the RAM and the CPU raises if the RAM is working in Dual Channel mode.

The singlecore/multicore CPU "sees" dual channel RAM as a faster RAM and that's it. The memory controller (let's say motherboard) checks memory slots on system startup and decides whether to enable Dual Channel mode or not.

You can visit some hardware oriented sites like rojakpot.com, anandtech.com, tomshardware.com, etc. Lot's of info.

---

