---
title: "laptop memory capacity"
date: 2009-02-27
forum: Hardware
---

### Post by evrkusd on 2009-02-27
I have a compaq presario f700 and i'm tring to see what my memory capacity is. i'm getting different results from sites listing specs. I typed lshw and got back the results of:

 *-memory:0
          description: System Memory
          physical id: b
          slot: System board or motherboard
          size: 1GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM [empty]
             physical id: 0
             slot: DIMM 1
        *-bank:1
             description: DIMM 667 MHz (1.5 ns)
             physical id: 1
             slot: DIMM 2
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)

Does capacity mean 2gb total or mean 2gb per slot? i want to get maybe a 2gb x1 and a 1gb x1 setup but i'm not sure if it's possible.

---

### Post by nixscripter on 2009-02-27
It means:

1. You have 2 memory slots.
2. One slot is empty, the other slot has a 1 GB DIMM in it (running at 667 MHz clockrate, not DDR).
3. Your motherboard can support up to 2 GB of memory.

Hope this helps you know what to buy.

---

