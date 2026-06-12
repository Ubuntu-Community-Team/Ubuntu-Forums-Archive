---
title: "Diagnosing an AMD Hardware Error"
date: 2012-06-25
forum: Hardware
---

### Post by CharlesT423 on 2012-06-25
Hi Everyone,

  I just got a new box for a client from Tiger Direct, and it's throwing up errors that seem to be related to the CPU Cache, but it also fails Memtest 86 test 6 (Moving Inversion, random patterns)  I'm not really familiar with AMD systems, so I'm hoping someone can help me diagnose what is actually bad: CPU, RAM, or motherboard.  It's an AMD FX-8120 in an MSI 760GM-E51 motherboard with two Corsair XMS3 4GB PC10666 DDR3 1333MHZ sticks of RAM, running on 12.04 AMD64.

  Here are the logs that show up intermittently in dmesg and syslog:


[Hardware Error]: CPU:2    MC2_STATUS[Over|CE|MiscV|-|-|-|-|CECC]: 0xd8484000010c0176
[Hardware Error]: Combined Unit Error: VB Data/ECC error.
[Hardware Error]: cache level: L2, tx: DATA, mem-tx: EV
[Hardware Error]: CPU:3    MC2_STATUS[-|CE|MiscV|-|AddrV|-|-|CECC]: 0x9c4840f001040136
[Hardware Error]:     MC2_ADDR: 0x000000020dbd7248
[Hardware Error]: Combined Unit Error: Fill ECC error on data fills.
[Hardware Error]: cache level: L2, tx: DATA, mem-tx: DRD
[Hardware Error]: CPU:2    MC2_STATUS[-|CE|MiscV|-|-|-|-|CECC]: 0x98484000010c0176
[Hardware Error]: Combined Unit Error: VB Data/ECC error.
[Hardware Error]: cache level: L2, tx: DATA, mem-tx: EV
[Hardware Error]: CPU:3    MC2_STATUS[Over|CE|MiscV|-|AddrV|-|-|CECC]: 0xdc48402001040135
[Hardware Error]:     MC2_ADDR: 0x000000020dbd7008
[Hardware Error]: Combined Unit Error: Fill ECC error on data fills.
[Hardware Error]: cache level: L1, tx: DATA, mem-tx: DRD
[Hardware Error]: CPU:2    MC2_STATUS[Over|CE|MiscV|-|-|-|-|CECC]: 0xd8484000010c0176
[Hardware Error]: Combined Unit Error: VB Data/ECC error.
[Hardware Error]: cache level: L2, tx: DATA, mem-tx: EV
[Hardware Error]: CPU:3    MC2_STATUS[Over|CE|MiscV|-|-|-|-]: 0xd800000000050152
[Hardware Error]: Combined Unit Error: Fill parity error on insn fills.
[Hardware Error]: cache level: L2, tx: INSN, mem-tx: IRD
[Hardware Error]: CPU:2    MC2_STATUS[Over|CE|MiscV|-|-|-|-]: 0xd800000000050152
[Hardware Error]: Combined Unit Error: Fill parity error on insn fills.
[Hardware Error]: cache level: L2, tx: INSN, mem-tx: IRD
[Hardware Error]: CPU:3    MC2_STATUS[Over|CE|MiscV|-|-|-|-]: 0xd800000000050152
[Hardware Error]: Combined Unit Error: Fill parity error on insn fills.
[Hardware Error]: cache level: L2, tx: INSN, mem-tx: IRD
[Hardware Error]: CPU:2    MC2_STATUS[Over|CE|MiscV|-|AddrV|-|-|CECC]: 0xdc4840f001040136
[Hardware Error]:     MC2_ADDR: 0x0000000215657548
[Hardware Error]: Combined Unit Error: Fill ECC error on data fills.
[Hardware Error]: cache level: L2, tx: DATA, mem-tx: DRD
[Hardware Error]: CPU:3    MC2_STATUS[Over|CE|MiscV|-|AddrV|-|-|CECC]: 0xdc4840f001040136
[Hardware Error]:     MC2_ADDR: 0x000000020dbd7248
[Hardware Error]: Combined Unit Error: Fill ECC error on data fills.
[Hardware Error]: cache level: L2, tx: DATA, mem-tx: DRD
[Hardware Error]: CPU:2    MC2_STATUS[Over|CE|MiscV|-|-|-|-]: 0xd800000000050152
[Hardware Error]: Combined Unit Error: Fill parity error on insn fills.
[Hardware Error]: cache level: L2, tx: INSN, mem-tx: IRD
[Hardware Error]: CPU:3    MC2_STATUS[Over|CE|MiscV|-|-|-|-]: 0xd800000000050152
[Hardware Error]: Combined Unit Error: Fill parity error on insn fills.
[Hardware Error]: cache level: L2, tx: INSN, mem-tx: IRD
[Hardware Error]: CPU:2    MC2_STATUS[Over|CE|MiscV|-|-|-|-]: 0xd800000000050152
[Hardware Error]: Combined Unit Error: Fill parity error on insn fills.
[Hardware Error]: cache level: L2, tx: INSN, mem-tx: IRD
[Hardware Error]: CPU:3    MC2_STATUS[Over|CE|MiscV|-|-|-|-]: 0xd800000000050152
[Hardware Error]: Combined Unit Error: Fill parity error on insn fills.
[Hardware Error]: cache level: L2, tx: INSN, mem-tx: IRD
[Hardware Error]: CPU:2    MC2_STATUS[Over|CE|MiscV|-|AddrV|-|-|CECC]: 0xdc4840f001040136
[Hardware Error]:     MC2_ADDR: 0x000000020c077448
[Hardware Error]: Combined Unit Error: Fill ECC error on data fills.
[Hardware Error]: cache level: L2, tx: DATA, mem-tx: DRD
[Hardware Error]: CPU:3    MC2_STATUS[-|CE|MiscV|-|-|-|-]: 0x9800000000050152
[Hardware Error]: Combined Unit Error: Fill parity error on insn fills.
[Hardware Error]: cache level: L2, tx: INSN, mem-tx: IRD
[Hardware Error]: CPU:2    MC2_STATUS[Over|CE|MiscV|-|-|-|-|CECC]: 0xd8484000010c0176
[Hardware Error]: Combined Unit Error: VB Data/ECC error.
[Hardware Error]: cache level: L2, tx: DATA, mem-tx: EV
[Hardware Error]: CPU:3    MC2_STATUS[-|CE|MiscV|-|-|-|-]: 0x9800000000050152
[Hardware Error]: Combined Unit Error: Fill parity error on insn fills.
[Hardware Error]: cache level: L2, tx: INSN, mem-tx: IRD
[Hardware Error]: CPU:2    MC2_STATUS[Over|CE|MiscV|-|-|-|-]: 0xd800000000050152
[Hardware Error]: Combined Unit Error: Fill parity error on insn fills.
[Hardware Error]: cache level: L2, tx: INSN, mem-tx: IRD

---

### Post by Redblade20XX on 2012-06-25
Try running a memtest with each stick alone. From your kernel output it seems as if the cpu is getting some cache errors from performing operation on memory addresses that might be corrupt and that are stored in L2 cache.  -Red

---

### Post by BeenLikeFlynn on 2012-06-26
I feel as though there is a component missing or one cuplink is off by a hair.

---

### Post by CharlesT423 on 2012-06-26
Hmm, I reseated the RAM and ran memtest with each stick in by itself with no difference in the results when I originally setup the server.  It didn't have any crashes during the initial testing (probably because it wasn't getting enough load) so I put it into production, which was probably a mistake.

We've ordered a replacement box, but I'm curious as to what is actually wrong.  I'd rather not have to RMA the whole server to fix a single component.

> **BeenLikeFlynn said:**
> I feel as though there is a component missing or one cuplink is off by a hair.

---

### Post by Redblade20XX on 2012-06-26
> **CharlesT423 said:**
> Hmm, I reseated the RAM and ran memtest with each stick in by itself with no difference in the results when I originally setup the server.  It didn't have any crashes during the initial testing (probably because it wasn't getting enough load) so I put it into production, which was probably a mistake.

We've ordered a replacement box, but I'm curious as to what is actually wrong.  I'd rather not have to RMA the whole server to fix a single component.

If you can, recheck the memory modules on another board just in case the orginal board is corrupted. In saying that, your problem might linked to the cpu and a faulty mmu thats corrupting the cache and making the cpu throw errors.

-Red

---

