---
title: "Get sound working with Creative X-fi Titanium HD?"
date: 2011-03-12
forum: Hardware
---

### Post by PudgyChicken on 2011-03-12
Hello,
I have a Creative X-fi Titanium HD, which unfortunately is not working with the included drivers in 10.10.

On boot I get the error "ctxfi: Something wrong!!!"

When I run ```
dmesg | grep -i xfi
``` I get:

[    9.318636] SB-XFi 0000:06:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.318791] SB-XFi 0000:06:00.0: setting latency timer to 64
[   46.028948] SB-XFi 0000:06:00.0: PCI INT A disabled
[   46.028950] ctxfi: Something wrong!!!
[   46.028970] SB-XFi: probe of 0000:06:00.0 failed with error -1

When I run ```
lspci -d 1102:000b -vv
``` I get:

06:00.0 Audio device: Creative Labs X-Fi Titanium series [EMU20k2] (rev 03)
    Subsystem: Creative Labs Device 0062
    Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at fbdf0000 (64-bit, non-prefetchable) [size=64K]
    Region 2: Memory at fba00000 (64-bit, non-prefetchable) [size=2M]
    Region 4: Memory at f4000000 (64-bit, non-prefetchable) [size=64M]
    Capabilities: [40] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
        Address: 0000000000000000  Data: 0000
    Capabilities: [58] Express (v2) Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Latency L0 <64ns, L1 <1us
            ClockPM- Surprise- LLActRep- BwNot-
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk-
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
        DevCap2: Completion Timeout: Range ABCD, TimeoutDis-
        DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-
        LnkCtl2: Target Link Speed: 2.5GT/s, EnterCompliance- SpeedDis-, Selectable De-emphasis: -6dB
             Transmit Margin: Normal Operating Range, EnterModifiedCompliance- ComplianceSOS-
             Compliance De-emphasis: -6dB
        LnkSta2: Current De-emphasis Level: -6dB
    Capabilities: [100 v1] Device Serial Number ff-ff-ff-ff-ff-ff-ff-ff
    Capabilities: [300 v1] Advanced Error Reporting
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UESvrt:    DLP+ SDES+ TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
        CESta:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
        AERCap:    First Error Pointer: 14, GenCap+ CGenEn- ChkCap+ ChkEn-
    Kernel modules: snd-ctxfi

In my infinite noobdom, I have no idea what any of this means.  Can anybody help me get my sound working?

PudgyChicken

Specs:
ASUS Rampage III Extreme
Intel Core i7 980X @4.25GHz
12GB Corsair Dominator DDR3 1866MHz
2x GTX 480 SLI
1x OCZ Vertex II 60GB (Windows boot)
2x WD Caviar Black 1TB SATA III RAID0 (storage)
2x WD Caviar Black 1TB SATA II (Other OS's)
Coolermaster HAF 932 Blue LED edition
1x BR drive
1x DVD drive w/ lightscribe
Corsair Hydro H50 in push pull
Creative X-fi Titanium HD

---

