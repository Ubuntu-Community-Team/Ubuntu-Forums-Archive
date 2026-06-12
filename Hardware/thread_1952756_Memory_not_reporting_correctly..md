---
title: "Memory not reporting correctly."
date: 2012-04-04
forum: Hardware
---

### Post by mogristle on 2012-04-04
Hello everyone,
I just installed Ubuntu 11.10 64bit, this is the  first Linux installation on my own PC, but I've used live discs in the  past.  Almost everything is great so far except for this memory problem  I'm having.

I got this Dell Inspiron 530 for free because it was  broken (just had to reset CMOS) I added some RAM to it to take the total  to 4GB (2GB + 1GB + 512MB + 512MB)  The 2GB was installed already, and I  got the others from other computers.  My problem is that System Info  and free both report 3.2GB of RAM, while BIOS reports the total of 4GB.   lshw reported 3.5GB in 3 DIMM slots, and didn't show anything for the  4th slot.  I rearranged the DIMMs in the slots with the 1GB in the 4th  slot.  BIOS still reports 4GB, System and free still report 3.2, lshw  now reports 4GB. Is this a problem with the motherboard?  I've read  some other similar posts and upgraded to the 64bit version from the  32bit, but that didn't solve the problem.  Any help is greatly  appreciated.  

System Specs:
Intel Core 2 Duo E4500
4GB DDR2
Foxconn g33m02 motherboard

Output of free and lshw (relevant portion) follows:
Before rearranging memory
free -m
             total       used       free     shared    buffers     cached
Mem:          3259        730       2529          0         28        327
-/+ buffers/cache:        373       2886
Swap:         3315          0       3315

lshw
     *-memory
          description: System Memory
          physical id: 24
          slot: System board or motherboard
          size: 3584Mib
        *-bank:0
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: AET860UD00-30DC08X
             vendor: 7F7F7F7F7F570000
             physical id: 0
             serial: 13021606
             slot: DIMM1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: M3 78T6553EZS-CE6
             vendor: Samsung
             physical id: 1
             serial: 792F7E14
             slot: DIMM2
             size: 512MiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:2
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             vendor: 7F7F7F7F7F9B0000
             physical id: 2
             serial: FFFFFFFF
             slot: DIMM3
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)

After rearranging memory
free -m
             total       used       free     shared    buffers     cached
Mem:          3259        846       2413          0         39        391
-/+ buffers/cache:        415       2844
Swap:         3315          0       3315

lshw
     *-memory
          description: System Memory
          physical id: 24
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: AET860UD00-30DC08X
             vendor: 7F7F7F7F7F570000
             physical id: 0
             serial: 13021606
             slot: DIMM1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: M3 78T6553EZS-CE6
             vendor: Samsung
             physical id: 1
             serial: 792F7E14
             slot: DIMM2
             size: 512MiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:2
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             product: M3 78T6553EZS-CE6
             vendor: Samsung
             physical id: 2
             serial: 792F7DDD
             slot: DIMM3
             size: 512MiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:3
             description: DIMM DDR2 Synchronous 667 MHz (1.5 ns)
             vendor: 7F7F7F7F7F9B0000
             physical id: 3
             serial: FFFFFFFF
             slot: DIMM4
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)

---

### Post by recluce on 2012-04-05
Having a wild mix of RAM like this is never a good idea, even less so with different vendors mixed. At current RAM prices, I would just throw away the smaller modules and either find a 2GB module that matches the existing one as close as possible - or just buy a matching set and replace all memory modules.

---

