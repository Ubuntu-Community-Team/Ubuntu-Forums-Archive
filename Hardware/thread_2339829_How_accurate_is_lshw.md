---
title: "How accurate is lshw?"
date: 2016-10-13
forum: Hardware
---

### Post by Arunomi on 2016-10-13
This is what i get from lshw:
```
-memory
          description: System Memory
          physical id: 15
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 667 MHz (1,5 ns)
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: SerNum00
             slot: DIMM0
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM [empty]
             product: ModulePartNumber01
             vendor: Manufacturer01
             physical id: 1
             serial: SerNum01
             slot: DIMM1
```

in this it says that i have a ddr2 1gb memory with a clock of 667MHz but if i look at the hardware
its a ddr3 1333MHz 1gb.

The laptop in question is a Asus Eee pc 1015pn and in the specs it says that it is a ddr3 memory in it.

If i read on the memory slot i can read ddr3 1.5v.

So what should i believe and why do i get this print out from lshw?

And the other question is why wont my new memory work.
Its a Samsung 2BG 2Rx8 PC3-10600s-09-10-F2 / M471B5673FHO-CH9   1008.

If i read the specs it should work on this laptop but all i get is a blank screen at boot.
I read that i could be the cmos that needs to be cleard and to do that you just remove the battery for a time 
and try to start the laptop again, but dose not work in this case.

I can but back my old memory and the the laptop works just fin.

---

### Post by ian-weisser on 2016-10-13
lshw queries the hardware, and reports what the hardware replies about itself.
The Linux kernel assumes that hardware is truthful about itself.

Packaging, however, may be a different story. It's possible that your memory was intentionally or unintentionally mislabeled.

---

### Post by QLee on 2016-10-13
> **Arunomi said:**
> 

The laptop in question is a Asus Eee pc 1015pn and in the specs it says that it is a ddr3 memory in it.

If i read on the memory slot i can read ddr3 1.5v.
...
I can but back my old memory and the the laptop works just fin.
My ASUS  netbook in the 1015 series uses low power. 1.35v., memory. However, on their website ASUS makes it clear that specs can change and mine is not a "PN".

I don't know if too low a voltage would make the system misidentify like you show. I also agree with poster ian-weisser, things can be mislabeled. 

One thing you might do is try a reliable memory site (perhaps Crucial, [http://www.crucial.com](http://www.crucial.com)) and see what they recommend. If it isn't correct maybe you can return it where you bought it.

---

