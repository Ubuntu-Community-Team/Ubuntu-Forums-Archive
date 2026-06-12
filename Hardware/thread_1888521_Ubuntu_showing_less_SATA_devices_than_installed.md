---
title: "Ubuntu showing less SATA devices than installed"
date: 2011-11-29
forum: Hardware
---

### Post by Sith Lord Kyle on 2011-11-29
So I have a large tower with ten SATA devices installed to it.  One harddrive and nine optical drives.  The harddrive and seven optical drives are hooked into the motherboards SATA ports, the other two SATA drives are hooked into a SATA controller card via PCI-e.

Oddly, all the devices seem to show up in the BIOS and POST, but when Ubuntu starts, only seven of the drives seem to exist.  I can't figure out how to make the other two optical drives active.

All of them have power and all open manually.  I have Google'd around, but can't seem to find any information on this.  Hoping someone has an idea.

---

### Post by MoreOrLess on 2011-11-29
So the two drives attached to the add-in card are inactive? It sounds like the controller card isn't being recognized by the kernel. Post the output of lspci (the part pertaining to the SATA card):
```
lspci -vv
```

---

### Post by Sith Lord Kyle on 2011-11-29
Actually the SATA controller works fine.  It is two of the drives plugged into the motherboard itself through the SATA ports.

---

### Post by Sith Lord Kyle on 2011-11-29
Here is the lspci -vv for that SATA controller:

08:00.0 RAID bus controller: Silicon Image, Inc. SiI 3132 Serial ATA Raid II Controller (rev 01)
	Subsystem: Silicon Image, Inc. Device 7132
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at fd4ff000 (64-bit, non-prefetchable) [size=128]
	Region 2: Memory at fd4f8000 (64-bit, non-prefetchable) [size=16K]
	Region 4: I/O ports at 7f00 [size=128]
	[virtual] Expansion ROM at fd300000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: sata_sil24
	Kernel modules: sata_sil24

Though, again, both drives connected to that SATA controller work fine and show up.

---

### Post by Sith Lord Kyle on 2011-11-29
Solved it!

Apparently the motherboard's SATA controllers had to be set to AHCI instead of IDE.  This allowed all drives to become recognized and active in Ubuntu.

---

### Post by JPZ on 2011-12-18
> **Sith Lord Kyle said:**
> Solved it!

Apparently the motherboard's SATA controllers had to be set to AHCI instead of IDE.  This allowed all drives to become recognized and active in Ubuntu.

Thanks for posting the solution. The Gigabyte Z68X-UD3H-B3 motherboard has two separate SATA controllers and I had only changed the first to AHCI.

-Jeff

---

