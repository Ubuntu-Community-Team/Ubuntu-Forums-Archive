---
title: "Memtest Results"
date: 2009-05-29
forum: Hardware
---

### Post by gordon3913 on 2009-05-29
I had trouble installing Ubuntu with the computer freezing.
When I took out 1 of the memory sticks it was able to install.

When I ran a memtest over the 518mb DDR2 bad stick I found a lot of errors

What would be the acceptable number of errors before you should discard the memory stick?:)

---

### Post by kidders on 2009-05-31
Hi there,
> **gordon3913 said:**
> What would be the acceptable number of errors before you should discard the memory stick?:)Zero, surely. A stick of RAM with even one reproducible fault is useless.

You should test the module in another machine first though ... the slot itself could be broken.

---

### Post by mcduck on 2009-05-31
> **gordon3913 said:**
> I had trouble installing Ubuntu with the computer freezing.
When I took out 1 of the memory sticks it was able to install.

When I ran a memtest over the 518mb DDR2 bad stick I found a lot of errors

What would be the acceptable number of errors before you should discard the memory stick?:)

Even a single error is a definite sign of faulty memory, memory slot, or compatibility problem with the memory chips and your motherboard's chipset. And that means a single error over long testing times (memtest should be ran for hours, at least over night, or until the first error occurs).

You can try swapping your memory sticks to different slots and testing again to check if the memory slot itself is broken.

---

