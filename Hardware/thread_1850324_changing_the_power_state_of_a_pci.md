---
title: "changing the power state of a pci"
date: 2011-09-26
forum: Hardware
---

### Post by jacnaz on 2011-09-26
Hello everybody, I'd like to change the power state of my network  adapter from D0 to any other state(D1,D2,D3hot), is that possible?

I have install and running acpid and I'm using  kernel 2.6.38...


[PHP]root@localhost jacob]# lspci -s 05:01.0 -vv
05:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
   Subsystem: Lenovo Device 2074
   Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
   Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
   Latency: 64 (8000ns min, 16000ns max)
   Interrupt: pin A routed to IRQ 21
   Region 0: I/O ports at 2000 [size=256]
   Region 1: Memory at d0100000 (32-bit, non-prefetchable) [size=256]
   Capabilities: [50] Power Management version 2
      Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0-,D1+,D2+,D3hot+,D3cold+)
      Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
   Kernel driver in use: 8139too
   Kernel modules: 8139cp, 8139too[/PHP]thank you in advanced

---

