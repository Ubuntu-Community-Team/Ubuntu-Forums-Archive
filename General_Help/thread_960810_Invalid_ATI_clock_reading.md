---
title: "Invalid ATI clock reading"
date: 2008-10-27
forum: General Help
---

### Post by flav0rl3ss on 2008-10-27
I am trying to get my current clock information in hopes to underclock slightly to see if it could fix an artifact issue... 

Ubuntu 8.10
ATI Radeon x1650pro
latest proprietary ati drivers (have tried others with same results)

ati has a built in 'overdrive' clocking utility which does not seem to work... 

"aticonfig --list-adapters" gives this output:

  * 0. 05:00.0 Radeon X1650 Series
  * - Default adapter

so to check the clock... "aticonfig --adapter=0 --odgc" outputs:

  ERROR - Get clocks failed for Adapter 0 - Radeon X1650 Series

well, i got no information from there so i installed rovclock

"rovclock -i"
  Found ATI card on 05:00, device id: 0x71c6
  I/O base address: 0x6c00
  Video BIOS shadow found @ 0xc0000
  Invalid reference clock from BIOS: 0.0 MHz
  Memory size: 262144 kB
  Memory channels: 0, CD,CH only: 0
  tRcdRD:   3
  tRcdWR:   1
  tRP:      3
  tRAS:     6
  tRRD:     1
  tR2W-CL:  1
  tWR:      1
  tW2R:     0
  tW2Rsb:   0
  tR2R:     1
  tRFC:     13
  tWL(0.5): 0
  tCAS:     0
  tCMD:     0
  tSTR:     0
  XTAL: 27.0 MHz, RefDiv: 13

  Core: 1.17 MHz, Mem: 0.0 MHz

Any help resolving this issue would be greatly appreciated, thanks in advance.

---

