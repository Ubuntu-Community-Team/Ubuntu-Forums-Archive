---
title: "Old PCI modem on kernel 3.x"
date: 2013-08-29
forum: Hardware
---

### Post by Tulainas on 2013-08-29
Hi everyone, I've been trying to use my old pci modem as a caller ID, but i've found that the instructions i have from: [https://help.ubuntu.com/community/DialupModemHowto/Lucent/Agere](https://help.ubuntu.com/community/DialupModemHowto/Lucent/Agere) are not supposed to be used in Kernel above 2.6

 So, the quwestion is precisely that one: has anyone successfully activated an old pci modem using the later kernel?

FYI:

lspci -vvv:


Communication controller: LSI Corporation V.92 56K WinModem (rev 02)
        Subsystem: LSI Corporation Device 044c
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr-
Stepping- SERR+ FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort-
<TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 64 (63000ns min, 3500ns max)
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at dffffc00 (32-bit, non-prefetchable) [size=256]
        Region 1: I/O ports at ec00 [size=8]
        Region 2: I/O ports at e800 [size=256]
        Capabilities: [f8] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2+ AuxCurrent=0mA PME(D0-,D1-,D2+,D3hot+,D3cold-)
                Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-


So... I kinda need a little help here please.


 Thanks

---

### Post by adfelippe on 2013-08-30
Maybe [this]("http://linmodems.technion.ac.il/packages/ltmodem/11c11040/HOWTO-Agere-11c11040-HDA.html") can help you?

---

