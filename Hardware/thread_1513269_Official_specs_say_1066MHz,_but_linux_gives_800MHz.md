---
title: "Official specs say 1066MHz, but linux gives 800MHz. Please help."
date: 2010-06-19
forum: Hardware
---

### Post by AlexZaim on 2010-06-19
I am using a Toshiba T135-S1309 laptop.
The official specs say:
Memory*
    3GB DDR3 1066MHz memory
sudo lshw say:```
*-memory
          description: System Memory
          physical id: c
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: SODIMM Synchronous 800 MHz (1.2 ns)
             product: 16JSF25664HZ-1G1F1
             vendor: 802C
             physical id: 0
             serial: E636DBFB
             slot: M1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
        *-bank:1
             description: SODIMM Synchronous 800 MHz (1.2 ns)
             product: M471B2873EH1-CF8
             vendor: 80CE
             physical id: 1
             serial: 9379FA70
             slot: M2
             size: 1GiB
             width: 64 bits
             clock: 800MHz (1.2ns)
```
Why so?

---

