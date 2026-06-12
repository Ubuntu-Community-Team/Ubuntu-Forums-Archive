---
title: "Very old notebook and new SSD - the drive is undetectable"
date: 2023-09-14
forum: Hardware
---

### Post by tvt2 on 2023-09-14
Hi!

I have very old notebook **MSI MEGA BOOK VR320** and lately the Ubuntu HDD partition became full. So I purchased the 240GB **Kingston SSD** drive and installed it in the notebook instead of old HDD having copied all partitions from HDD to SSD.

After powering on the notebook I was surprised by Ubuntu 12.04 to FAIL to boot. The most amazing thing was that before GRUB menu I saw the following messages:

After a certain delay the correct GRUB menu appears:

I tried to boot Ubuntu as usual from the 1st GRUB menu item I had a big delay in several minutes and then the initramfs prompt appeared.

I rebooted the notebook and selected the **Windows XP** item and to my surprise the Windows booted correctly without any problem:

Moreover, when I tried to boot old **openSUSE** it also booted normally and worked properly.

I suspected Ubuntu boot files have been damaged during migration process and tried to boot several Linux distributions. But I had the similar failures with the following key messages in the boot log:

```
[    4.908267] scsi host4: sata_sil
[    4.908382] ata3: SATA max UDMA/100 mmio m512@0xfebffc00 tf 0xfebffc80 irq 22
[    4.908388] ata4: SATA max UDMA/100 mmio m512@0xfebffc00 tf 0xfebffcc0 irq 22
[    5.221190] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   10.720049] ata3.00: qc timeout (cmd 0xec)
[   10.720055] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[   11.029180] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   21.472031] ata3.00: qc timeout (cmd 0xec)
[   21.472034] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[   21.781181] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   52.192031] ata3.00: qc timeout (cmd 0xec)
[   52.192035] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[   52.501165] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   52.805156] ata4: SATA link down (SStatus 0 SControl 310)
```

I took several commands outputs and attached them to the message. The full **dmesg** and **lshw** outputs are too big and I attached to the post.

The **lspci -vv** command gave the following output:

```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC410 Host Bridge (rev 01)    Subsystem: Micro-Star International Co., Ltd. [MSI] RC410 Host Bridge
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR- INTx-
    Latency: 64


00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Bridge [int gfx] (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    I/O behind bridge: 00005000-00005fff [size=4K]
    Memory behind bridge: fd800000-fd8fffff [size=1M]
    Prefetchable memory behind bridge: bbf00000-dbefffff [size=512M]
    Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA- VGA+ MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: [b0] Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Bridge [int gfx]
    Kernel modules: shpchp


00:06.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Express Port 3 (prog-if 00 [Normal decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
    I/O behind bridge: 00006000-00006fff [size=4K]
    Memory behind bridge: fd900000-fe0fffff [size=8M]
    Prefetchable memory behind bridge: 00000000dbf00000-00000000ddefffff [size=32M]
    Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
    BridgeCtl: Parity+ SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Capabilities: [50] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [58] Express (v1) Root Port (Slot+), MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0
            ExtTag+ RBE-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag+ PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
        LnkCap:    Port #247, Speed 2.5GT/s, Width x1, ASPM L0s L1, Exit Latency L0s <64ns, L1 <1us
            ClockPM- Surprise- LLActRep- BwNot- ASPMOptComp-
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- CommClk-
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x16, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        SltCap:    AttnBtn- PwrCtrl- MRL- AttnInd- PwrInd- HotPlug- Surprise-
            Slot #0, PowerLimit 0.000W; Interlock- NoCompl-
        SltCtl:    Enable: AttnBtn- PwrFlt- MRL- PresDet- CmdCplt- HPIrq- LinkChg-
            Control: AttnInd Off, PwrInd Off, Power- Interlock-
        SltSta:    Status: AttnBtn- PowerFlt- MRL- CmdCplt- PresDet- Interlock-
            Changed: MRL- PresDet- LinkState-
        RootCtl: ErrCorrectable- ErrNon-Fatal- ErrFatal- PMEIntEna- CRSVisible-
        RootCap: CRSVisible-
        RootSta: PME ReqID 0000, PMEStatus- PMEPending-
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
        Address: 00000000  Data: 0000
    Capabilities: [b0] Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Express Port 3
    Capabilities: [b8] HyperTransport: MSI Mapping Enable+ Fixed+
    Kernel driver in use: pcieport
    Kernel modules: shpchp


00:12.0 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 Serial ATA Controller
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 22
    Region 0: I/O ports at b800 [size=8]
    Region 1: I/O ports at b400 [size=4]
    Region 2: I/O ports at b000 [size=8]
    Region 3: I/O ports at ac00 [size=4]
    Region 4: I/O ports at a800 [size=16]
    Region 5: Memory at febffc00 (32-bit, non-prefetchable) [size=512]
    Expansion ROM at feb00000 [disabled] [size=512K]
    Capabilities: [60] Power Management version 2
        Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=2 PME-
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit-
        Address: 00000000  Data: 0000
    Kernel driver in use: sata_sil
    Kernel modules: sata_sil, pata_acpi, ata_generic


00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller (rev 80) (prog-if 10 [OHCI])
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at febfe000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci


00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller (rev 80) (prog-if 10 [OHCI])
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at febfd000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci-pci


00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB2 Host Controller
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at febfc000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [dc] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
        Bridge: PM- B3+
    Kernel driver in use: ehci-pci


00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 SMBus Controller (rev 82)
    Subsystem: Micro-Star International Co., Ltd. [MSI] IXP SB4x0 SMBus Controller
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Region 0: I/O ports at 0b00 [size=16]
    Region 1: Memory at 38000000 (32-bit, non-prefetchable) [size=1K]
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c_piix4


00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 IDE Controller (rev 80) (prog-if 8a [Master SecP PriP])
    Subsystem: Micro-Star International Co., Ltd. [MSI] IXP SB4x0 IDE Controller
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Interrupt: pin A routed to IRQ 16
    Region 0: I/O ports at 01f0 [size=8]
    Region 1: I/O ports at 03f4
    Region 2: I/O ports at 0170 [size=8]
    Region 3: I/O ports at 0374
    Region 4: I/O ports at ff00 [size=16]
    Capabilities: [70] MSI: Enable- Count=1/1 Maskable- 64bit-
        Address: 00000000  Data: 0000
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp, pata_acpi, ata_generic


00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 High Definition Audio Controller (rev 01)
    Subsystem: Micro-Star International Co., Ltd. [MSI] IXP SB4x0 High Definition Audio Controller
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 3
    Region 0: Memory at febf8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [60] MSI: Enable- Count=1/1 Maskable- 64bit+
        Address: 0000000000000000  Data: 0000


00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-ISA Bridge (rev 80)
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-ISA Bridge
    Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0


00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Bus: primary=00, secondary=04, subordinate=05, sec-latency=64
    I/O behind bridge: 00007000-00008fff [size=8K]
    Memory behind bridge: fe100000-fe9fffff [size=9M]
    Prefetchable memory behind bridge: ddf00000-dfefffff [size=32M]
    Secondary status: 66MHz- FastB2B+ ParErr+ DEVSEL=medium >TAbort- <TAbort- <MAbort+ <SERR- <PERR+
    BridgeCtl: Parity+ SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-


01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RC410M [Mobility Radeon Xpress 200M] (prog-if 00 [VGA controller])
    Subsystem: Micro-Star International Co., Ltd. [MSI] RC410M [Mobility Radeon Xpress 200M]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (2000ns min), Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at c0000000 (32-bit, prefetchable) [size=256M]
    Region 1: I/O ports at 5800 [size=256]
    Region 2: Memory at fd8f0000 (32-bit, non-prefetchable) [size=64K]
    Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
        Address: 00000000  Data: 0000
    Kernel driver in use: radeon
    Kernel modules: radeon


04:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter (rev 10)
    Subsystem: Micro-Star International Co., Ltd. [MSI] RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64 (8000ns min, 16000ns max)
    Interrupt: pin A routed to IRQ 18
    Region 0: I/O ports at 8800 [size=256]
    Region 1: Memory at fe9ffc00 (32-bit, non-prefetchable) [size=256]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0-,D1+,D2+,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: 8139too
    Kernel modules: 8139cp, 8139too


04:04.0 CardBus bridge: O2 Micro, Inc. OZ711MP1/MS1 MemoryCardBus Controller (rev 21)
    Subsystem: Micro-Star International Co., Ltd. [MSI] OZ711MP1/MS1 MemoryCardBus Controller
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 168
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at 3c000000 (32-bit, non-prefetchable) [size=4K]
    Bus: primary=04, secondary=05, subordinate=05, sec-latency=176
    Memory window 0: 40000000-43ffffff (prefetchable)
    Memory window 1: 44000000-47ffffff
    I/O window 0: 00007000-000070ff
    I/O window 1: 00007400-000074ff
    BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
    16-bit legacy interface ports at 0001
    Capabilities: [a0] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=2 PME-
        Bridge: PM- B3+
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket


04:04.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Integrated MMC/SD Controller
    Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at fe9ff800 (32-bit, non-prefetchable) [size=256]
    Capabilities: [a0] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci_pci


04:04.3 Bridge: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Integrated MS/xD Controller
    Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 5
    Region 0: Memory at fe9fe000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: [a0] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-


04:04.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02) (prog-if 10 [OHCI])
    Subsystem: O2 Micro, Inc. Firewire (IEEE 1394)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx+
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at fe9fd000 (32-bit, non-prefetchable) [size=4K]
    Region 1: Memory at fe9ff000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [60] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME+
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire_ohci


04:09.0 Network controller: Ralink corp. RT2561/RT61 rev B 802.11g
    Subsystem: Micro-Star International Co., Ltd. [MSI] RT2561/RT61 rev B 802.11g
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at fe9f0000 (32-bit, non-prefetchable) [size=32K]
    Capabilities: [40] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: rt61pci
    Kernel modules: rt61pci
```

For any case I'm adding **lsmod** command output:

```
Module                  Size  Used bybinfmt_misc            16384  1
arc4                   16384  2
rt61pci                28672  0
rt2x00pci              16384  1 rt61pci
rt2x00mmio             16384  1 rt61pci
rt2x00lib              57344  3 rt2x00mmio,rt61pci,rt2x00pci
amdkfd                110592  1
amd_iommu_v2           16384  1 amdkfd
mac80211              626688  2 rt2x00pci,rt2x00lib
radeon               1228800  1
cfg80211              495616  2 rt2x00lib,mac80211
coretemp               16384  0
sdhci_pci              28672  0
8139too                32768  0
i2c_algo_bit           16384  1 radeon
sdhci                  40960  1 sdhci_pci
joydev                 24576  0
8139cp                 28672  0
mmc_core              110592  2 sdhci,sdhci_pci
ttm                    77824  1 radeon
eeprom_93cx6           16384  1 rt61pci
firewire_ohci          40960  0
serio_raw              16384  0
mii                    16384  2 8139cp,8139too
rfkill                 24576  1 cfg80211
drm_kms_helper        131072  1 radeon
firewire_core          53248  1 firewire_ohci
drm                   311296  4 drm_kms_helper,radeon,ttm
i2c_piix4              24576  0
video                  40960  0
ata_generic            16384  0
pata_acpi              16384  0
shpchp                 32768  0
raid10                 45056  0
raid456               139264  0
async_raid6_recov      16384  1 raid456
async_pq               16384  2 raid456,async_raid6_recov
async_xor              16384  3 async_pq,raid456,async_raid6_recov
async_memcpy           16384  2 raid456,async_raid6_recov
async_tx               16384  5 async_pq,async_memcpy,async_xor,raid456,async_raid6_recov
raid1                  36864  0
raid0                  20480  0
multipath              16384  0
linear                 16384  0
yenta_socket           32768  0
uas                    20480  0
usb_storage            69632  2 uas
sata_sil               16384  0
pata_atiixp            16384  0
```

And more I'm adding **lsblk -fs** command and it shows the only USB drive partitions:

```
NAME  FSTYPE   LABEL        UUID                                 MOUNTPOINT
loop0 squashfs                                                   /livemnt/squashfs
sda1  vfat     MULTIBOOT    14FF-1D45                            
&#9492;&#9472;sda                                                            
sda4  iso9660  sysrcd-5.3.2 2018-11-14-16-35-14-00               /livemnt/boot
&#9492;&#9472;sda                                                            
sr0
```

As an experiment I tried to boot the FreeBSD 13.2 and it also failed to boot but I cannot add the screen image because of attachment limitations.

If Windows and openSUSE also couldn't boot I'd think that there's hardware problem but now I think that it possibly kernel module problem... Grub had to read initramfs image from the SSD to display initramfs prompt?

I'd be happy to listen to the professional opinions about my situation especially taking in account that AI systems could give me no constructive advice.

Thanks!

---

### Post by Rubi1200 on 2023-09-15
Hi and welcome to the forums :-)

I need to point out that Ubuntu 12.04 and Windows XP are long past EOL. Using them is seriously risky. Please consider upgrading to the latest versions.

It would help if you can post the results from the boot info script in my signature. Run it from a liveUSB and paste the link to the file. I would recommend not repairing until we can view and diagnose the results.

---

### Post by yancek on 2023-09-15
>  HDD having copied all partitions from HDD to SSD.


How did you do the copy?  If you have XP, I expect your Linux systems are Legacy with boot code in the MBR and the Ubuntu root filesystem partition.  Which OS is the default bootloader, Ubuntu or OpenSuse?  The 'no such device' error means the bootloader is looking for that UUID and it doesn't exist.  Probably the UUID for a partition on the old drive.  You need to run the blkid command to get the correct UUID for whatever partition.  

If you simply copied the Ubuntu partition(s) without reinstalling Grub to the MBR on the new I would not expect it to boot .  Number of possibilities so if you haven't solved this, run the boot repair script and post the link to the output as suggested above.

---

### Post by tvt2 on 2023-09-15
> **yancek said:**
> How did you do the copy?  If you have XP, I expect your Linux systems are Legacy with boot code in the MBR and the Ubuntu root filesystem partition.  Which OS is the default bootloader, Ubuntu or OpenSuse?  The 'no such device' error means the bootloader is looking for that UUID and it doesn't exist.  Probably the UUID for a partition on the old drive.  You need to run the blkid command to get the correct UUID for whatever partition. 

Drive copying was made with Acronis True image. It's capable of copying Windows partitions as well as Linux ones.

The partition table is in MBR format. The default bootloader is the one installed by **Ubuntu 12.04**. The **ext3 filesystem** UUID is kept inside the filesystem header so it cannot change during binary copying. Here's the **blkid** command output:

```
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="MULTIBOOT" UUID="14FF-1D45" TYPE="vfat"
/dev/sda4: UUID="2018-11-14-16-35-14-00" LABEL="sysrcd-5.3.2" TYPE="iso9660"
```

As you can see there's detected no other partition except the USB drive ones. And there's no reason to discuss partitions if the system is unable to detect the whole drive that contains those partitions.

> **yancek said:**
>  If you simply copied the Ubuntu partition(s) without reinstalling Grub to the MBR on the new I would not expect it to boot .  Number of possibilities so if you haven't solved this, run the boot repair script and post the link to the output as suggested above.

There's no possibility to reinstall/repair GRUB on the undetected drive.

---

### Post by tvt2 on 2023-09-16
> **Rubi1200 said:**
> Hi and welcome to the forums :-) 

Thanks for your invitation! I'm using Ubuntu starting from version 8.x and all that time I managed to
 avoid disturbing busy people from this forum. ;)

> **Rubi1200 said:**
>  I need to point out that Ubuntu 12.04 and Windows XP are long past EOL. Using them is seriously risky. Please consider upgrading to the latest versions. 

That's reasonable point out. But! Windows XP is not used for a long time but containing valuable information. As to Ubuntu 12.04 it is used for vary old application that cannot be moved to a newer system because of list of reasons. One of them is that it's based on Qt3 library and U12.04 is the latest LTS that has development tools for Qt3.

> **Rubi1200 said:**
>  It would help if you can post the results from the boot info script in my signature. Run it from a liveUSB and paste the link to the file. I would recommend not repairing until we can view and diagnose the results.

Yes, please: [https://paste.ubuntu.com/p/KcRp2Yn2pj/](https://paste.ubuntu.com/p/KcRp2Yn2pj/)

Maybe you'll need some more info, please just ask me.

Thanks!

---

### Post by Rubi1200 on 2023-09-16
Have you checked BIOS to make sure the SSD is being properly recognized?

The script results confirm what you said and I am not sure where you go from here.

If BIOS settings are fine, I hope someone else has some ideas.

---

### Post by yancek on 2023-09-16
As pointed out in the post above, boot repair doesn't provide any useful information.  Is the link below the computer you are using?  It looks like it was released in 2009 so does your BIOS recognize the SSD.  I would think it had to for you to copy the data from the old drive to the new.  Something must have changed?
 
[https://www.msi.com/Laptop/VR320/Specification](https://www.msi.com/Laptop/VR320/Specification)

---

### Post by tvt2 on 2023-09-16
> **Rubi1200 said:**
> Have you checked BIOS to make sure the SSD is being properly recognized?

Yes. The BIOS can see the SSD:

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292739&stc=1[/IMG]

I suspect the problem requires certain kernel modules tuning but I don't know which ones... ](*,)

---

### Post by yancek on 2023-09-17
When you copied Ubuntu to the SSD, was it the only OS you copied?  Are OpenSuse and XP on the same or a different drive?  If they are on a different drive, is the OpenSuse Grub in the MBR of that drive?  If it is, can you set that drive to first boot priority in the BIOS and boot it or boot it from the Ubuntu boot menu?  Does it have an entry for Ubuntu?  Is it showing the old drive (UUID) to boot?  Which release of OpenSuse do you have, newer than Ubuntu 12.04?  Do you get any different results with the blkid command, is the SSD recognized?

I'm about out of guesses.  12.04 is pretty outdated and you can't update thing in the standard way (using apt or apt-get) but need to find the archives for your release online and maybe you can find the modules and downlooad/install them to see if that is the problem.

If you still have the old HD with Ubuntu on it, you might try accessing it and going to /var/log and deleting files there and also try to find large files you no longer need to delete to make room if you are unable to resolve this Ubuntu/SSD issue.  Good luck.

---

### Post by oldfred on 2023-09-17
You really need to update your qt3 app.
I had my own small app and have had to update it periodically to latest software.

I suspect the kernel does not have required drivers.
Are there any settings in BIOS for drive like AHCI? I normally would expect a standard SATA drive whether HDD or SSD would work, but may need settings.

---

### Post by tvt2 on 2023-09-17
> **yancek said:**
> When you copied Ubuntu to the SSD, was it the only OS you copied?  Are OpenSuse and XP on the same or a different drive?  If they are on a different drive, is the OpenSuse Grub in the MBR of that drive?  If it is, can you set that drive to first boot priority in the BIOS and boot it or boot it from the Ubuntu boot menu?  Does it have an entry for Ubuntu?  Is it showing the old drive (UUID) to boot?  Which release of OpenSuse do you have, newer than Ubuntu 12.04?  Do you get any different results with the blkid command, is the SSD recognized? 

The whole drive with all partitions were copied. All the OSes and GRUB are on the same drive. Notebook has the only one HDD/SSD. UUIDs of partitions did not change during binary copying.

It's not possible to install a newer **Ubuntu**/**Debian**/**Fedora**/... (even **FreeBSD**) because all the new Linux distributions are not capable to detect the SSD itself. The **blkid** command always show the same -- bootable USB drive partitions.

> **yancek said:**
>  I'm about out of guesses.  12.04 is pretty outdated and you can't update thing in the standard way (using apt or apt-get) but need to find the archives for your release online and maybe you can find the modules and downlooad/install them to see if that is the problem. 

To update the Ubuntu I 1st need to boot it.

> **yancek said:**
>  If you still have the old HD with Ubuntu on it, you might try accessing it and going to /var/log and deleting files there and also try to find large files you no longer need to delete to make room if you are unable to resolve this Ubuntu/SSD issue.  Good luck.

All big and/or unnecessary files were deleted but that was not enough. The new bigger drive is really required.

Thanks!

---

### Post by tvt2 on 2023-09-17
> **oldfred said:**
> You really need to update your qt3 app. 

It's not possible.

> **oldfred said:**
>  I had my own small app and have had to update it periodically to latest software. 

My app has no updates. It's developed by the team that's not available anymore.

> **oldfred said:**
>  I suspect the kernel does not have required drivers.
Are there any settings in BIOS for drive like AHCI? I normally would expect a standard SATA drive whether HDD or SSD would work, but may need settings.

The kernel does have required driver **sata_sil** but I don't know how to tune it to recognize the drive correctly. The notebook BIOS is very basic and "playing" with available options did not give positive results.

Thanks!

---

### Post by MAFoElffen on 2023-09-18
SSD's came out in 1991. Various interfaces since then... Crucial says that laptop supports SSD's as an upgrade.

But Linux kernel support for things like 'trim' only came out in Linux Kernel 3.7... When Ubuntu 12.04 LTS reached end of life, the kernel version 3.13. I think with ESM it reached version Linux Kernel 3.2...

The information missing is which Arch/CPU? 32bit or 64bit. That model laptop came in both, and was only upgradable to 2GB RAM. Is the BIOS upgrade to AMI version 1.14 (I would confirm that version first)? SATA mode set to AHCI? I can usually look up BIOS Settings, but the manual on MSI's website is wrong. It's spec's say SATA, and the manual they have there says in BIOS, that it has IDE... So I can't trust what is there.

If the BIOS can see the SSD drive, Then the BIOS 'is' supporting it. The only factor that I can think of that would prevent (recent) Ubuntu from seeing the drive is the BIOS SATA Mode setting... 12.04? I can't test that to confirm physically. What brand and model is this SSD?

Personally, I would migrate to more modern hardware to install an OS that is in current support, then migrate the data from Win XP to it. The app that only runs in QT3... On modern hardware you could run an isolated 12.04 VM in KVM. You didn't mention what this QT3 app was or what it did. There might be an alternative to it that runs on QT6.5 (current).

---

### Post by tvt2 on 2023-09-22
Dear friends!

*Thank you for your support!* The problem is solved by replacing the SSD with old kind 250GB HDD. Everything is working though much slower but reliably.

Thanks!

---

