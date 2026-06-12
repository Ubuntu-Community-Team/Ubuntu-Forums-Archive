---
title: "Dual Boot EeePC 900"
date: 2008-07-10
forum: Hardware
---

### Post by nigelenki on 2008-07-10
Is it possible to dual boot the EeePC 900 16G solid state with Ubuntu and the default OS?

Also the Atheros chipset should work out of the box, or do I need to rebuild the driver still?

The wear leveling on EeePC should pretty much fine right?  I figure there should be fewer than 2^16 writes per day even with swap and a journaling file system like ext3; with 2^16 64k blocks, the 4G SSD should last one day for each write cycle it can survive (so the crappiest available NAND on a 100,000 write cycle lifespan will last some 80-90 years).

I wonder about running /home on an SD card...

---

### Post by CheeseEatingBulldog on 2008-07-11
I installed Ubuntu on my boss' eeepc 900 last week, works like a charm, even the compiz effects work out of the box. Only thing is to check google as there are some hardware fixes for the wifi, sound and fonts. Overall I was done in under 45 mins. Dual boot should work, repartition drive and install on new partition then set grub to load both.

But to be honest, you could just load ubuntu and leave the xandros restore partition, as you could then restore to factory setup very simply.

---

