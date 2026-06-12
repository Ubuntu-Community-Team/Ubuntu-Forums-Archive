---
title: "Hardware monitor seems to report incorrect memory size."
date: 2010-06-30
forum: Hardware
---

### Post by BeauKpad on 2010-06-30
I pulled up hardware monitor to check my hdd access, and noticed that it was reporting that I had 3.2 gigs of memory. I was pretty sure that I had 6. I ran lshw, and it reported 6 also. VirtualBox reports 3.2. I'm running ubuntu 10.04 x64. The system has 4 banks, three have 2 gigs each, the third is empty.
   Any ideas?

---

### Post by mikewhatever on 2010-06-30
The output of **free -m** please.

---

### Post by BeauKpad on 2010-06-30
Here is the output of free -m:


             total       used       free     shared    buffers     cached
Mem:          3276       3146        129          0        258       2214
-/+ buffers/cache:        674       2602
Swap:            0          0          0

Here is the memory stanza of lshw:

     *-memory
          description: System Memory
          physical id: 33
          slot: System board or motherboard
          size: 6GiB
        *-bank:0
             description: DIMM DDR2 Synchronous 333 MHz (3.0 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM_A1
             size: 2GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM DDR2 Synchronous 333 MHz (3.0 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM_B1
             size: 2GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:2
             description: DIMM DDR2 Synchronous 333 MHz (3.0 ns)
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM_A2
             size: 2GiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:3
             description: [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM_B2

Thanks for taking a look!

---

### Post by mikewhatever on 2010-07-01
That's bizarre. :confused:

---

### Post by BeauKpad on 2010-07-19
Little update/clarification:

   The mis-reporting ubuntu install reports a 'uname -a' as :


Linux elbeau-desktop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux


   A separate, correctly reporting ubuntu install on the same computer (it's 10.04 upgraded from 9.10) reports:


Linux lebeau-desktop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 x86_64 GNU/Linux

   The correctly reporting OS is 64 bit. The incorrect is 32 bit. It lacks the address space to handle 6 gigs of memory.

---

