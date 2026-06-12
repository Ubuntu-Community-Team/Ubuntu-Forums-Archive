---
title: "[solved] Netgear GA511 PCMCIA"
date: 2007-05-17
forum: Hardware &amp; Laptops
---

### Post by moxen93 on 2007-05-17
Hello everyone,

whoever has problems with a Netgear GA511 PC Card (cardbus): I managed to install that card with ndiswrapper in ubuntu edgy and the Windows drivers from Netgear version 6.1. The win98 and win2000 didnt work but the winxp driver work (NETGA511.INF).
Maybe this is a relevant google hit to anybody some day.
greetings
moxen93

---

### Post by runokiab on 2007-07-13
For me the Netgear GA511 worked on Ubuntu 7.04 out of the box. It uses the "r8169 Gigabit Ethernet driver 2.2LK". There is no need for ndiswrapper in my opinion. See the entry for the [GA511 in the Hardware Compatibility List](http://www.linuxquestions.org/hcl/showproduct.php/product/3671) of LinuxQuestions.org for comparison.

lspci output:
```
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
        Subsystem: Netgear Unknown device 5200
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (8000ns min, 16000ns max), Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 11
        Region 0: I/O ports at 1c00 [size=256]
        Region 1: Memory at 2c000000 (32-bit, non-prefetchable) [size=512]
        Expansion ROM at 28000000 [disabled] [size=128K]
        Capabilities: [dc] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1+,D2+,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
```

---

