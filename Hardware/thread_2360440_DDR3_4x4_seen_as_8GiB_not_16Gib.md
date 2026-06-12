---
title: "DDR3 4x4 seen as 8GiB not 16Gib"
date: 2017-05-04
forum: Hardware
---

### Post by Torxbit on 2017-05-04
I have an MSI 970A-G45 (MS-7693) motherboard.  In it are 4 DIMMS of 4G memory.  All are Corsair 1333Mhz 9-9-9-24 modules.  The BIOS sees 16G, memtest sees all 4 DIMMs but only sees 8G of memory.  Strangly enough it thinks it is in XMP mode.  The motherboard is an AMD board, not Intell.

Linux <redacted> 4.4.0-75-generic #96-Ubuntu SMP Thu Apr 20 09:56:33 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

lshw sees 16G
 *-memory
       description: System Memory
       physical id: 27
       slot: System board or motherboard
       size: 16GiB
     *-bank:0
          description: DIMM DDR3 Synchronous 667 MHz (1.5 ns)
          product: Array1_PartNumber0
          vendor: A1_Manufacturer0
          physical id: 0
          serial: A1_SerNum0
          slot: A1_DIMM0
          size: 4GiB
          width: 64 bits
          clock: 667MHz (1.5ns)
     *-bank:1
          description: DIMM DDR3 Synchronous 667 MHz (1.5 ns)
          product: Array1_PartNumber1
          vendor: A1_Manufacturer1
          physical id: 1
          serial: A1_SerNum1
          slot: A1_DIMM1
          size: 4GiB
          width: 64 bits
          clock: 667MHz (1.5ns)
     *-bank:2
          description: DIMM DDR3 Synchronous 667 MHz (1.5 ns)
          product: Array1_PartNumber2
          vendor: A1_Manufacturer2
          physical id: 2
          serial: A1_SerNum2
          slot: A1_DIMM2
          size: 4GiB
          width: 64 bits
          clock: 667MHz (1.5ns)
     *-bank:3
          description: DIMM DDR3 Synchronous 667 MHz (1.5 ns)
          product: Array1_PartNumber3
          vendor: A1_Manufacturer3
          physical id: 3
          serial: A1_SerNum3
          slot: A1_DIMM3
          size: 4GiB
          width: 64 bits
          clock: 667MHz (1.5ns)


free sees 8 
              total        used        free      shared  buff/cache   available
Mem:           7953         608        6909          17         435        7059
Swap:         16352           0       16352


And /proc/meminfo sees 8G
MemTotal:        8144764 kB
MemFree:         7075888 kB
MemAvailable:    7228616 kB
Buffers:           39852 kB
Cached:           328452 kB
SwapCached:           36 kB


I have gone over the BIOS settings, reset the CMOS and even tried manual timings per above.  I have even removed the DIMMs and cleaned the contacts. Still only 8G is seen.  dmesg has no memory errors. 

Has anyone ran across this before?

---

### Post by Bucky Ball on 2017-05-04
Is it a new board? It could be the pair of RAM slots. It can happen. Hard to imagine both sticks of RAM are dead. Have you swapped them into the two slots you know are working and the two that are currently in there into the slots that aren't, if you follow me? ;)

Try all four a pair at a time in the two working slots and see what happens.

And yes, I have had two slots die, which is why I mention it. ;)

---

### Post by Yellow Pasque on 2017-05-04
Are you using the latest BIOS? Changelog for 2.7 says something about memory size not identified properly. [https://us.msi.com/Motherboard/support/970AG45.html#down-bios](https://us.msi.com/Motherboard/support/970AG45.html#down-bios)

---

### Post by Torxbit on 2017-05-05
Yes, I change the BIOS from the 1.X version to the 2.X version.  This added EFI, which I really do not care for.  As for switching the memory the board has two matched slots.  Ubuntu only recognizes one of the DIMMs from each slot.  Each DIMM works independently, and checks out with memtest86+.  And even when the option for XMP is disabled in BIOS memtest still thinks it is in XMP configuration.

---

### Post by Bucky Ball on 2017-05-05
Still confused. So each DIMM works independently in both slots when inserted on its own?

---

### Post by Torxbit on 2017-05-08
Yes, but not exactly.  The board has dual channel memory.  The DIMMs much match and are paired in DIMM1 with DIMM3 and DIMM2 with DIMM4.  And if you put in only one DIMM you have to start with DIMM2.  But yes, each DIMM tests fine in the slot.  But Ubuntu fails to see the second DIMM in the paired slot.

---

### Post by sp40140 on 2017-05-10
What do other OS / distro see?
I mean if you boot it with live env of other distro (or even windows), do they detect 16 gigs or 8?

---

