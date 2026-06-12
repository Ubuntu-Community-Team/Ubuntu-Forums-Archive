---
title: "Unsupported PM cap regs version (7) - Toshiba L300"
date: 2009-08-09
forum: Hardware
---

### Post by kirillius on 2009-08-09
Hello, guys. 
This message appeared on boot: "... pci 0000:02:00.0: unsupported PM cap regs version (7)" .. 
I think something is wrong with my wifi card. lspci -vvv says the following:

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
   Subsystem: Toshiba America Info Systems Device ff64
   Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
   Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
   Latency: 0, Cache Line Size: 32 bytes
   Interrupt: pin A routed to IRQ 16
   Region 0: I/O ports at 3000 [size=256]
   Region 2: Memory at 90010000 (64-bit, prefetchable) [size=4K]
   Region 4: Memory at 90000000 (64-bit, prefetchable) [size=64K]
   Capabilities: [40] Power Management version 7

The wifi signal strong when it's near the wireless point. in the next room it's really low and not stable. 
Does anyone know how it could be solved?

---

### Post by Deadite on 2009-09-04
Don't know if you are still looking for an answer but I found this thread

[http://ubuntuforums.org/archive/index.php/t-977074.html](http://ubuntuforums.org/archive/index.php/t-977074.html)

while searching for the same error on my Toshiba 305. Looks like its a problem with the wake-on-Lan/hibernation feature of the ethernet card. Got rid of it by turning the Lan card off from the bios (as I only use wifi). Don't know about the weak wifi problem you are having though.

Hope it helps.

---

