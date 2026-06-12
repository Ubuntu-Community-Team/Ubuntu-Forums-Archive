---
title: "PC6400 weierdness."
date: 2010-03-12
forum: Hardware
---

### Post by Merovius on 2010-03-12
I recently replaced my MB, CPU, RAM and video card. The system runs but does not seem any different speed wise so I thought I would try to get some stats on the performance.

One thing I did was run Memtest86 to get some info on the RAM. These are the numbers it reported. Seem a bit odd to me. Am I wrong?

Ram Settings
452 mhz
DDR904
cas 3-5-5-0
DDR-1 128
1024 mb
2366 mbs

This is PC6400 800 mhz OCZ dual channel ram. (512 x 2)

MB ECS Geforce6100M-M2
AMD Athlon II  64 X2 215

More info on request. 

TIA

---

### Post by Fafler on 2010-03-12
That is odd. Looks to me as if you've overclocked your RAM. Is the system stable? Have you tried loading the default BIOS settings?

---

### Post by Merovius on 2010-03-12
Sorry so slow.Work gets in the way..

Overclock. Thats what I thought when I saw it. The way it is setup now is the only way it will even boot. It is as stable as can be. But, it doesn't seem any faster then before I upgraded virtually the whole system.

I had an AMD Athlon 64 3200+ with 1 gb of PC3200 ram in an Asus board with a Geforce 7300 GT.

I replaced the board with an ECS Geforce 6100M-M2, the CPU with an Athlon II 64 X2 215 and the ram with 1 gb of PC6400 OCZ 800 mhz (2 x 512mb) The video card was replaced with a Geforce 8600 GTS. 

I expected to notice quite a difference in responsiveness. Seems like exactly the same system. If I hadn't done it I wouldn't have noticed. And now Memtest says I'm overclocked??

---

### Post by Merovius on 2010-03-13
This is what I get from sudo lshw


 description: DIMM DDR2 Synchronous 200 MHz (5.0 ns)
             product: OCZ2P800512
             vendor: Manufacturer00
             physical id: 0
             serial: FFFFFFFF
             slot: DIMM0
             size: 512MiB
             width: 64 bits
             clock: 200MHz (5.0ns)

This is the ram in question.

[http://www.xpcgear.com/oczd2512800.html]("http://www.xpcgear.com/oczd2512800.html")

The timings I am showing and what the web site quotes are just a bit different. Or am I missing something. I'm thinking it's a voltage thing. Guess I should have done more research on the board. Guess this is the way it's going to have to run. At least it's stable. Wish I could run CPU-Z. Wonder if it works in Virtualbox?

---

