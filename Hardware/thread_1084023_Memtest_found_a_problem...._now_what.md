---
title: "Memtest found a problem.... now what?"
date: 2009-03-01
forum: Hardware
---

### Post by castlefox on 2009-03-01
I was having some random problems in Ubuntu 8.04 and windows xp so I decided to run Memtest. 

The version of Memtest I used was the + version I think.  It was v1.70


The error it gave me is as follows:

Tst - 6
Pass - 0
Failing Address - 000acd7554    -   172.4MB
Good = 00200000
Bad = 00000800
Count = 9
Chan =



Can I just remove the bad RAM stick to fix my problems???
How would I know what RAM stick is the bad one?

Is there any way to address the error that memtest found ?

---

### Post by martino2k8 on 2009-03-01
I think the easiest way (albeit probably slowest) to check which stick exactly is bad is to run memtest with a single stick in, so everytime you run it you replace the stick with the next one.

And yes, removing the bad stick should fix those problems. Provided they were RAM related...

---

### Post by tgalati4 on 2009-03-01
Sometimes cleaning your memory slots with compressed air and reseating the cards a few times can clear up the problem.  If not, then try one stick at a time with memtest to isolate the bad memory stick.

It's probably best to replace them with a matched pair, but if different brands pass memtest for 30 complete cycles (likely running overnight) then you should be OK.

If you know what you are doing, you can go into the BIOS and play with the memory timings.  Adding a wait state or slowing the memory bus speed can help recover from a memory/motherboard problem.

---

