---
title: "How to find out about my RAM-specifications"
date: 2007-05-02
forum: Hardware &amp; Laptops
---

### Post by asdir on 2007-05-02
I'd like to know if there is any easy way to look up the specifications of my RAM-chips that are in my Desktop-PC without actualy opening the box.
The hardware information in the panel menu does not give me anything, not the vendor name nor anything else that is useful.

Thx

---

### Post by asdir on 2007-05-11
Afer intense search the only thing I found was the terminal command
> sudo lshw
which shows a detailed list of hardware, even including vendor names for most pieces.
Unfortunately not for my RAM-chips.

---

### Post by zursch on 2008-07-15
Thats weird it didn't show up, mine looked like this:
        *-bank:0
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             vendor: xxxxxxxx (blocked out)
             physical id: 0
             serial: xxxxxxxx (blocked out)
             slot: DIMM_A
             size: 512MiB
             width: 64 bits
             clock: 533MHz (1.9ns)
        *-bank:1
             description: DIMM DDR Synchronous 533 MHz (1.9 ns)
             vendor: xxxxxxxx (blocked out)
             physical id: 1
             serial: xxxxxxxx (blocked out)
             slot: DIMM_B
             size: 512MiB
             width: 64 bits
             clock: 533MHz (1.9ns)

---

