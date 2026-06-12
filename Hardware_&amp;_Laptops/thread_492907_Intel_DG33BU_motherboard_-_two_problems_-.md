---
title: "Intel DG33BU motherboard - two problems -"
date: 2007-07-05
forum: Hardware &amp; Laptops
---

### Post by fugitivo on 2007-07-05
I have the Intel DG33BU motherboard and I'm using Ubuntu 7.04 Desktop (32bit). Installation works out of the box but I have 2 harware issues:

1- Netword card is not detected. I had to download lastest intel drivers and compile them from source.
2- Videocard is not detected (xorg is using vesa) and if I change manually my xorg conf to use intel driver, it doesn't work neither (i think this is because kernel doesn't detect the chipset maybe?)

I decided to upgrade to gutsy and kernel 2.6.22-7 seems to detect the network card and the videocard. But:

1- Network doesn't work correctly, icmp packets work (ping) but no tcp or udp packets (very weird). Module loaded by ubuntu is e1000-ich9. With kernel 2.6.20 i compiled and use without problems module e1000. Compiling again this module (e1000) in 2.6.22-7 results in the same problem as e1000-ich9.
2- Intel drivers for xorg are working, but with problems. OpenGL crashes xorg, also trying to use applications like mythtv in fullscreen crashes xorg.

This is my lspci -vvnn in kernel 2.6.20

00:00.0 Host bridge [0600]: Intel Corporation Unknown device [8086:29c0] (rev 02)
        Subsystem: Intel Corporation Unknown device [8086:5044]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
        Latency: 0
        Capabilities: [e0] Vendor Specific Information

00:02.0 VGA compatible controller [0300]: Intel Corporation Unknown device [8086:29c2] (rev 02) (prog-if 00 [VGA])
        Subsystem: Intel Corporation Unknown device [8086:5044]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at 54300000 (32-bit, non-prefetchable) [size=512K]
        Region 1: I/O ports at 2130 [size=8]
        Region 2: Memory at 40000000 (32-bit, prefetchable) [size=256M]
        Region 3: Memory at 54200000 (32-bit, non-prefetchable) [size=1M]
        Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
                Address: 00000000  Data: 0000
        Capabilities: [d0] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:03.0 Communication controller [0780]: Intel Corporation Unknown device [8086:29c4] (rev 02)
        Subsystem: Intel Corporation Unknown device [8086:5044]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at 543a6100 (64-bit, non-prefetchable) [size=16]
        Capabilities: [50] Power Management version 3
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [8c] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000

00:19.0 Ethernet controller [0200]: Intel Corporation Unknown device [8086:294c] (rev 02)
        Subsystem: Intel Corporation Unknown device [8086:0001]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 17
        Region 0: Memory at 54380000 (32-bit, non-prefetchable) [size=128K]
        Region 1: Memory at 543a4000 (32-bit, non-prefetchable) [size=4K]
        Region 2: I/O ports at 2100 [size=32]
        Capabilities: [c8] Power Management version 2
                Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=1 PME-
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000
        Capabilities: [e0] Vendor Specific Information

00:1a.0 USB Controller [0c03]: Intel Corporation Unknown device [8086:2937] (rev 02) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation Unknown device [8086:5044]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 18
        Region 4: I/O ports at 20e0 [size=32]
        Capabilities: [50] Vendor Specific Information

00:1a.1 USB Controller [0c03]: Intel Corporation Unknown device [8086:2938] (rev 02) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation Unknown device [8086:5044]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 21
        Region 4: I/O ports at 20c0 [size=32]
        Capabilities: [50] Vendor Specific Information

00:1a.2 USB Controller [0c03]: Intel Corporation Unknown device [8086:2939] (rev 02) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation Unknown device [8086:5044]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin C routed to IRQ 16
        Region 4: I/O ports at 20a0 [size=32]
        Capabilities: [50] Vendor Specific Information

00:1a.7 USB Controller [0c03]: Intel Corporation Unknown device [8086:293c] (rev 02) (prog-if 20 [EHCI])
        Subsystem: Intel Corporation Unknown device [8086:5044]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin C routed to IRQ 16
        Region 0: Memory at 543a5c00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [58] Debug port
        Capabilities: [98] Vendor Specific Information

00:1b.0 Audio device [0403]: Intel Corporation Unknown device [8086:293e] (rev 02)
        Subsystem: Intel Corporation Unknown device [8086:0001]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 22
        Region 0: Memory at 543a0000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000
        Capabilities: [70] Express Unknown type IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s <64ns, L1 <1us
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
                Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
                Link: Supported Speed unknown, Width x0, ASPM unknown, Port 0
                Link: Latency L0s <64ns, L1 <1us
                Link: ASPM Disabled CommClk- ExtSynch-
                Link: Speed unknown, Width x0

00:1c.0 PCI bridge [0604]: Intel Corporation Unknown device [8086:2940] (rev 02) (prog-if 00 [Normal decode])
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: 54400000-544fffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s <64ns, L1 <1us
                Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
                Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
                Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 1
                Link: Latency L0s <1us, L1 <4us
                Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
                Link: Speed 2.5Gb/s, Width x0
                Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug+ Surpise+
                Slot: Number 1, PowerLimit 10.000000
                Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq-
                Slot: AttnInd Unknown, PwrInd Unknown, Power-
                Root: Correctable- Non-Fatal- Fatal- PME-
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
                Address: 00000000  Data: 0000
        Capabilities: [90] Subsystem: Intel Corporation Unknown device [8086:2940]
        Capabilities: [a0] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1c.1 PCI bridge [0604]: Intel Corporation Unknown device [8086:2942] (rev 02) (prog-if 00 [Normal decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00001000-00001fff
        Memory behind bridge: 54100000-541fffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s <64ns, L1 <1us
                Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
                Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
                Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 2
                Link: Latency L0s <256ns, L1 <4us
                Link: ASPM Disabled RCB 64 bytes CommClk+ ExtSynch-
                Link: Speed 2.5Gb/s, Width x1
                Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug+ Surpise+
                Slot: Number 2, PowerLimit 10.000000
                Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq-
                Slot: AttnInd Unknown, PwrInd Unknown, Power-
                Root: Correctable- Non-Fatal- Fatal- PME-
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
                Address: 00000000  Data: 0000
        Capabilities: [90] Subsystem: Intel Corporation Unknown device [8086:2942]
        Capabilities: [a0] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1c.2 PCI bridge [0604]: Intel Corporation Unknown device [8086:2944] (rev 02) (prog-if 00 [Normal decode])
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: 54500000-545fffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s <64ns, L1 <1us
                Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
                Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
                Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 3
                Link: Latency L0s <1us, L1 <4us
                Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
                Link: Speed 2.5Gb/s, Width x0
                Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug+ Surpise+
                Slot: Number 3, PowerLimit 10.000000
                Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq-
                Slot: AttnInd Unknown, PwrInd Unknown, Power-
                Root: Correctable- Non-Fatal- Fatal- PME-
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
                Address: 00000000  Data: 0000
        Capabilities: [90] Subsystem: Intel Corporation Unknown device [8086:2944]
        Capabilities: [a0] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1c.3 PCI bridge [0604]: Intel Corporation Unknown device [8086:2946] (rev 02) (prog-if 00 [Normal decode])
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Memory behind bridge: 54600000-546fffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s <64ns, L1 <1us
                Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
                Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
                Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 4
                Link: Latency L0s <1us, L1 <4us
                Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
                Link: Speed 2.5Gb/s, Width x0
                Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug+ Surpise+
                Slot: Number 4, PowerLimit 10.000000
                Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq-
                Slot: AttnInd Unknown, PwrInd Unknown, Power-
                Root: Correctable- Non-Fatal- Fatal- PME-
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
                Address: 00000000  Data: 0000
        Capabilities: [90] Subsystem: Intel Corporation Unknown device [8086:2946]
        Capabilities: [a0] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1c.4 PCI bridge [0604]: Intel Corporation Unknown device [8086:2948] (rev 02) (prog-if 00 [Normal decode])
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        Memory behind bridge: 54700000-547fffff
        Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s <64ns, L1 <1us
                Device: Errors: Correctable+ Non-Fatal+ Fatal+ Unsupported+
                Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
                Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s L1, Port 5
                Link: Latency L0s <1us, L1 <4us
                Link: ASPM Disabled RCB 64 bytes CommClk- ExtSynch-
                Link: Speed 2.5Gb/s, Width x0
                Slot: AtnBtn- PwrCtrl- MRL- AtnInd- PwrInd- HotPlug+ Surpise+
                Slot: Number 5, PowerLimit 10.000000
                Slot: Enabled AtnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq-
                Slot: AttnInd Unknown, PwrInd Unknown, Power-
                Root: Correctable- Non-Fatal- Fatal- PME-
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
                Address: 00000000  Data: 0000
        Capabilities: [90] Subsystem: Intel Corporation Unknown device [8086:2948]
        Capabilities: [a0] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:1d.0 USB Controller [0c03]: Intel Corporation Unknown device [8086:2934] (rev 02) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation Unknown device [8086:5044]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 20
        Region 4: I/O ports at 2080 [size=32]
        Capabilities: [50] Vendor Specific Information

00:1d.1 USB Controller [0c03]: Intel Corporation Unknown device [8086:2935] (rev 02) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation Unknown device [8086:5044]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 19
        Region 4: I/O ports at 2060 [size=32]
        Capabilities: [50] Vendor Specific Information

00:1d.2 USB Controller [0c03]: Intel Corporation Unknown device [8086:2936] (rev 02) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation Unknown device [8086:5044]
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin C routed to IRQ 18
        Region 4: I/O ports at 2040 [size=32]
        Capabilities: [50] Vendor Specific Information

00:1d.7 USB Controller [0c03]: Intel Corporation Unknown device [8086:293a] (rev 02) (prog-if 20 [EHCI])
        Subsystem: Intel Corporation Unknown device [8086:5044]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 20
        Region 0: Memory at 543a5800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [58] Debug port
        Capabilities: [98] Vendor Specific Information

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 92) (prog-if 01 [Subtractive decode])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=32
        Memory behind bridge: 54000000-540fffff
        Prefetchable memory behind bridge: 0000000050000000-0000000053ffffff
        Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
        BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
        Capabilities: [50] Subsystem: Intel Corporation Unknown device [8086:5044]

00:1f.0 ISA bridge [0601]: Intel Corporation Unknown device [8086:2912] (rev 02)
        Subsystem: Intel Corporation Unknown device [8086:5044]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Capabilities: [e0] Vendor Specific Information

00:1f.2 SATA controller [0106]: Intel Corporation Unknown device [8086:2922] (rev 02) (prog-if 01 [AHCI 1.0])
        Subsystem: Intel Corporation Unknown device [8086:5044]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 21
        Region 0: I/O ports at 2128 [size=8]
        Region 1: I/O ports at 213c [size=4]
        Region 2: I/O ports at 2120 [size=8]
        Region 3: I/O ports at 2138 [size=4]
        Region 4: I/O ports at 2020 [size=32]
        Region 5: Memory at 543a5000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/4 Enable-
                Address: 00000000  Data: 0000
        Capabilities: [70] Power Management version 3
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [a8] #12 [0010]
        Capabilities: [b0] Vendor Specific Information

00:1f.3 SMBus [0c05]: Intel Corporation Unknown device [8086:2930] (rev 02)
        Subsystem: Intel Corporation Unknown device [8086:5044]
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin B routed to IRQ 10
        Region 0: Memory at 543a6000 (64-bit, non-prefetchable) [size=256]
        Region 4: I/O ports at 2000 [size=32]

02:00.0 IDE interface [0101]: Marvell Technology Group Ltd. Unknown device [11ab:6101] (rev b1) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Marvell Technology Group Ltd. Unknown device [11ab:6101]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 16
        Region 0: I/O ports at 1018 [size=8]
        Region 1: I/O ports at 1024 [size=4]
        Region 2: I/O ports at 1010 [size=8]
        Region 3: I/O ports at 1020 [size=4]
        Region 4: I/O ports at 1000 [size=16]
        Region 5: Memory at 54100000 (32-bit, non-prefetchable) [size=512]
        Capabilities: [48] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2- AuxCurrent=0mA PME(D0+,D1+,D2-,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=1 PME-
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
                Address: 00000000  Data: 0000
        Capabilities: [e0] Express Legacy Endpoint IRQ 0
                Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
                Device: Latency L0s unlimited, L1 unlimited
                Device: AtnBtn- AtnInd- PwrInd-
                Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
                Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr+ NoSnoop-
                Device: MaxPayload 128 bytes, MaxReadReq 512 bytes
                Link: Supported Speed 2.5Gb/s, Width x1, ASPM L0s, Port 0
                Link: Latency L0s <256ns, L1 unlimited
                Link: ASPM Disabled RCB 64 bytes CommClk+ ExtSynch-
                Link: Speed 2.5Gb/s, Width x1

06:01.0 Multimedia video controller [0400]: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder [4444:0016] (rev 01)
        Subsystem: Hauppauge computer works Inc. WinTV PVR 150 [0070:8003]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 128 (32000ns min, 2000ns max), Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 22
        Region 0: Memory at 50000000 (32-bit, prefetchable) [size=64M]
        Capabilities: [44] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

06:03.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) [104c:8023] (prog-if 10 [OHCI])
        Subsystem: Intel Corporation Unknown device [8086:5044]
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 128 (500ns min, 1000ns max), Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 19
        Region 0: Memory at 54004000 (32-bit, non-prefetchable) [size=2K]
        Region 1: Memory at 54000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME+

---

### Post by Kaimaka on 2007-08-01
I also have a Intel DG33BU motherboard and run Ubuntu 7.04 Feisty Fawn. I have the same two problems, ethernet network jack not recognized and integrated video not being auto detected or displaying my monitors native 1440 x 900 resolution even when I manually edit the xorg.conf.

The network think doesn't bother me so much right now because I'm using a USB thing for wireless. The video support thing bug me though because I have a widescreen I would like to use properly and am not ready to get a graphics card yet (even if I had the money)

I will watch this thread with interest to see if replies could help me as well

---

### Post by beefcurry on 2007-08-02
These two problems can be solved, but its not exactly cost free :P. I picked up an old 3com ethernet card and poped it into the pci slot to use lan (saved myself there) and popped in an old nvidea geforce into the graphics :D.

---

### Post by Kaimaka on 2007-08-03
> **beefcurry said:**
> These two problems can be solved, but its not exactly cost free :P. I picked up an old 3com ethernet card and poped it into the pci slot to use lan (saved myself there) and popped in an old nvidea geforce into the graphics :D.


I initially used a no name brand PCI wifi card I 'borrowed' from one of my other computers already successfully using Ubuntu while searching for another solution. Ended up buying a Netgear WG111v2 usb wifi thing after  seeing it on a list of hardware that work out of the box with Ubuntu. I was always planning on getting a Nvidia graphics card a few months later. I had hoped I could use the wide screen with my motherboard before then but it's look less likely :(

So yeah your solutions of spending money and buying things that just work occured to me too I just hoped it wouldn't be my only option.

---

### Post by beefcurry on 2007-08-03
Well it is not the only option, the Network card works in Gusty (well works abit in Gusty from what I've read) and the Graphics should also work perfectly in Gusty. This new Intel Board is quite new and is not fully supported in the current kernel, I expect everything to work out of the box with Gusty. Hope that helps :)

---

### Post by i6p0 on 2007-08-11
I, too, have the network card 8086:294c that isn't recognized and I can't find this ID anywhere on intel.com.  

I had to upgrade to this new computer when lightning took out the previous one.  I figured I'd get the latest hardware and, of course, I got stuck with Vista.  It doesn't run about 50% of the programs I've tried so far.  That makes me want to move to Linux (but I like the option to boot into Vista when absolutely necessary, so I'm using the Wubi installer).  

Anyway, it sounds like I'll have to take the suggested path and buy a PCI network card.  Is just any cheapo network card from MicroCenter or Fry's going to work?  

Doug

---

### Post by purnateja on 2007-08-18
I have Intel Dg33 FB classic. it has the same problems
*network card not detected
*audio card not detected

---

### Post by Ktj on 2007-08-19
HI
I have also a big problems with DG33BU ( Althought i use windows XP Essential). It doesnt recon LAN ( so i have to plug in another lan card on pci) and if i put in 7600GT (pci-e) system doesnt enven do POST!!
Well i gota admit i ve got a beta ver. of it(i have won it on UT2k4 competition)  and it bios cant be updated o_O.........
And biggest problem is whenever i start to use to much onboard gfx(enough is watching video), system crash..........

I think this is moast sux MB ever......

Btw: i ve tested ubuntu once and it is not for me: it has totaly messed up my HD...........

---

### Post by bimmerd00d on 2007-08-21
I updated to the Gutsy kernel and the onboard NIC works now!!!

---

### Post by beefcurry on 2007-08-21
> **bimmerd00d said:**
> I updated to the Gutsy kernel and the onboard NIC works now!!!

sweet :) nice to hear.

---

### Post by sos84 on 2007-08-21
I also had ethernet issues. When attempting to startup feisty, it would hang after failing to recognize the integrated ethernet controller. I then downloaded the text based version and installed from that image and everything worked fine. It recognized both the ethernet hardware and my GeForce 8800GTS card without a problem. However, after a couple of reboots, I am now losing my input devices after a minute or so. I have tried both PS2 and USB hardware with the same results.

---

### Post by beefcurry on 2007-08-21
> **sos84 said:**
> I also had ethernet issues. When attempting to startup feisty, it would hang after failing to recognize the integrated ethernet controller. I then downloaded the text based version and installed from that image and everything worked fine. It recognized both the ethernet hardware and my GeForce 8800GTS card without a problem. However, after a couple of reboots, I am now losing my input devices after a minute or so. I have tried both PS2 and USB hardware with the same results.

Thats odd, I never had that problem. Try usign Gusty. Also it could be your X server. Im using a GeForce 6600GT and I don't seem to have your problem.

are you using the Nvidea Drivers?

---

### Post by z35 on 2007-11-02
You do not have this problem? [http://ubuntuforums.org/showthread.php?t=545666](http://ubuntuforums.org/showthread.php?t=545666) What bios version and associated bios settings did you change? On a side not, does anybody know of a live cd that boots the 1st hd automatically, so that i don't have make one...

---

