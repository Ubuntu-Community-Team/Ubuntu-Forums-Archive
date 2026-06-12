---
title: "Ubuntu doesn't have all memory available"
date: 2012-10-27
forum: Hardware
---

### Post by fmsismo on 2012-10-27
I bought a new computer a few days ago, and the system is not seen the 16gb of ram.

On /proc/meminfo the kernel get the 16gb but the free command report only 8gb.  

I'm using the 64 bit installation.

Has someone the same problem?


cat /proc/meminfo
     *-memory
          description: System Memory
          physical id: 27
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: DIMM Synchronous [empty]
             product: Array1_PartNumber0
             vendor: A1_Manufacturer0
             physical id: 0
             serial: A1_SerNum0
             slot: A1_DIMM0
        *-bank:1
             description: DIMM DDR3 Synchronous 667 MHz (1.5 ns)
             product: Array1_PartNumber1
             vendor: A1_Manufacturer1
             physical id: 1
             serial: A1_SerNum1
             slot: A1_DIMM1
             size: 8GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:2
             description: DIMM Synchronous [empty]
             product: Array1_PartNumber2
             vendor: A1_Manufacturer2
             physical id: 2
             serial: A1_SerNum2
             slot: A1_DIMM2
        *-bank:3
             description: DIMM DDR3 Synchronous 667 MHz (1.5 ns)
             product: Array1_PartNumber3
             vendor: A1_Manufacturer3
             physical id: 3
             serial: A1_SerNum3
             slot: A1_DIMM3
             size: 8GiB
             width: 64 bits
             clock: 667MHz (1.5ns)


cat /proc/meminfo 
MemTotal:        8148280 kB

uname -a -> Linux alphaprime 3.2.0-32-generic #51-Ubuntu SMP Wed Sep 26 21:33:09 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

Thanks.

---

### Post by mardybear on 2012-10-27
Hi fmsismo.


Similar problem but no solution i'm aware of:

[http://ubuntuforums.org/showthread.php?t=2074898](http://ubuntuforums.org/showthread.php?t=2074898)

mardybear

---

### Post by 2F4U on 2012-10-28
Did you run memtest to verify that the RAM is working correct? It may be physically installed, but that doesn't mean that it couldn't be damaged. When running memtest, let it run for at least two complete iterations.
Can you post the output from the free command?

---

### Post by fmsismo on 2012-10-28
free
             total       used       free     shared    buffers     cached
Mem:       8148252    8006592     141660          0      95924    5023336
-/+ buffers/cache:    2887332    5260920
Swap:     17571836          0   17571836


Already chequed the memory seems to be ok.

---

### Post by Yellow Pasque on 2012-10-28
Things to try:
- Check dmesg
- Try the RAM in different slots
- Try a newer kernel

If the RAM was faulty, it would probably still be recognized, but the problem would show up as random freezing (or not show up at all).

---

### Post by fmsismo on 2012-10-28
If I use the ram in slots without dual channel the systems see and can use the 16gb, if I set the system to use the dualchannel it's only get 8 gb to use.  I test all banks with both memories, all of them ok.

Thanks for your time!

---

