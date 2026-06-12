---
title: "PCI TV tuner card not recognised"
date: 2016-09-10
forum: Hardware
---

### Post by lemarc on 2016-09-10
I have an old HP desktop that I am repurposing to run in my home theatre.  I am having a bit of trouble figuring out how to get the TV Tuner going.

It is an AVerMedia CX23887/8 analog/DVB-T card.  MeTV shows the error "There are no DVB devices available", but the card seems to be recognised.

```
04:00.0 Multimedia video controller: Conexant Systems, Inc. CX23887/8 PCIe Broadcast Audio and Video Decoder with 3D Comb (rev 04)
    Subsystem: Avermedia Technologies Inc CX23887/8 PCIe Broadcast Audio and Video Decoder with 3D Comb
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at fbe00000 (64-bit, non-prefetchable) [size=2M]
    Capabilities: [40] Express (v1) Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr+ UncorrErr- FatalErr- UnsuppReq+ AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM L0s L1, Exit Latency L0s <2us, L1 <4us
            ClockPM- Surprise- LLActRep- BwNot- ASPMOptComp-
        LnkCtl:    ASPM Disabled; RCB 64 bytes Disabled- CommClk-
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
    Capabilities: [80] Power Management version 3
        Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [90] Vital Product Data
        Unknown small resource type 0a, will not decode more.
    Capabilities: [a0] MSI: Enable- Count=1/1 Maskable- 64bit+
        Address: 0000000000000000  Data: 0000
    Capabilities: [100 v1] Advanced Error Reporting
        UESta:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UEMsk:    DLP- SDES- TLP- FCP- CmpltTO- CmpltAbrt- UnxCmplt- RxOF- MalfTLP- ECRC- UnsupReq- ACSViol-
        UESvrt:    DLP+ SDES- TLP- FCP+ CmpltTO- CmpltAbrt- UnxCmplt- RxOF+ MalfTLP+ ECRC- UnsupReq- ACSViol-
        CESta:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr-
        CEMsk:    RxErr- BadTLP- BadDLLP- Rollover- Timeout- NonFatalErr+
        AERCap:    First Error Pointer: 00, GenCap- CGenEn- ChkCap- ChkEn-
    Capabilities: [200 v1] Virtual Channel
        Caps:    LPEVC=1 RefClk=100ns PATEntryBits=1
        Arb:    Fixed+ WRR32+ WRR64+ WRR128-
        Ctrl:    ArbSelect=WRR64
        Status:    InProgress-
        Port Arbitration Table [240] <?>
        VC0:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
            Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
            Ctrl:    Enable+ ID=0 ArbSelect=Fixed TC/VC=ff
            Status:    NegoPending- InProgress-
        VC1:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
            Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
            Ctrl:    Enable- ID=1 ArbSelect=Fixed TC/VC=00
            Status:    NegoPending- InProgress-
    Kernel driver in use: cx23885
    Kernel modules: cx23885
00: f1 14 80 88 06 00 10 00 04 00 00 04 08 00 00 00
10: 04 00 e0 fb 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 61 14 39 e1
30: 00 00 00 00 40 00 00 00 00 00 00 00 0f 01 00 00


```

I have had a look around and I can't find anything that might be wrong.  Any help would be gratefully appreciated.

---

### Post by donbrew on 2017-01-04
Check for sure at linuxtv.org, but it is my understanding that Avermedia TV PCIe adapters are NOT supported.  My m791 cards with cx23885 are not supported at all.  Most Hauppauge cards are.

---

