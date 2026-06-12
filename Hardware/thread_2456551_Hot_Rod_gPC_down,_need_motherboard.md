---
title: "Hot Rod gPC down, need motherboard"
date: 2021-01-13
forum: Hardware
---

### Post by bcschmerker on 2021-01-13
**The GIGABYTE® GA-MA78-S2HP in my ubuntu® 20.04-LTS mini-tower is no longer recognizing i8042 keyboards!**  Stops POST at "Keyboard error or no keyboard present" always.  Does anybody have a recommendation for a µ-ATX Advance Micro Devices® RS780G/SB700 (AM2+) planar that meets the following requirements?

Necessary:  At least one E-IDE, five to six SATA (including eSATA), IEEE 1284 (mini-36 preferred/DB-25 acceptable), IEEE 1394 (6-pin FW), at least one EIA/TIA-578 serial (DE-9), i8042 KDB/MSE port(s) (mini-DIN6).
Desirable:  One disquette header (34-pin), up to six USB 2.0 host adapters total, 4 x 4 GiB (viz., 16 GiB) DDR3 max memory provision.

---

### Post by Yellow Pasque on 2021-01-16
Have you tried a USB keyboard? Maybe your keyboard went south?

---

### Post by bcschmerker on 2021-01-16
@[Yellow Pasque](https://ubuntuforums.org/member.php?u=327594)  **The GA-MA78GM-S2HP has *always* been finicky with i8042 keyboards,** never did accept an *e*machines®/ac*e*r® unit that works consistently on my ASUS® CM1630 as upgraded under Win 10.  The last one that worked was a 1990's-vintage D&#9830;LL®.  The Used Computer Store (Berkeley, CA, USA) is shut down into April 2021, so I couldn't even see whether they even *have* a PS/2 keyboard (and by PS/2 keyboard I mean the genuine article from International Business Machines).

---

### Post by Yellow Pasque on 2021-01-17
You can try an adapter (USB->PS/2). You can also control what errors will stop booting in your BIOS.(Standard CMOS Features Menu, Halt on)

---

