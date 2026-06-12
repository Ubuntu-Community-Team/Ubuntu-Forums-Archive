---
title: "Ubuntu 10.04 memory values different"
date: 2012-05-03
forum: Hardware
---

### Post by snash on 2012-05-03
I have two x 2GB DDR3 sticks in my machine, as confirmed by lshw below.
Why does sysinfo and meminfo show 3GB?
This is x86_64. 10.04 LTS

sysinfo shows:
3018MiB

=============
cat /proc/meminfo | grep MemTotal
MemTotal:        3090800 kB


======
lshw 
 *-memory
          description: System Memory
          physical id: 2d
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM Synchronous 1333 MHz (0.8 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: DIMM Synchronous 1333 MHz (0.8 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)

---

