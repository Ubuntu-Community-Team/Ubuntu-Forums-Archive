---
title: "ath9k from backports problems with 9.10 Karmic"
date: 2010-01-01
forum: Hardware
---

### Post by ltsampros on 2010-01-01
Hello, 

everyone, I have an Acer Ferrari one and lspci reports the following:

09:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Foxconn International, Inc. Device e01f
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 19
    Region 0: Memory at f0000000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2- AuxCurrent=375mA PME(D0+,D1+,D2-,D3hot+,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Address: 00000000  Data: 0000
    Capabilities: [60] Express (v1) Legacy Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0, Latency L0s <512ns, L1 <64us
            ExtTag- AttnBtn- AttnInd- PwrInd- RBE- FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr+ UncorrErr+ FatalErr- UnsuppReq+ AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 2.5GT/s, Width x1, ASPM unknown, Latency L0 <512ns, L1 <64us
            ClockPM- Suprise- LLActRep- BwNot-
        LnkCtl:    ASPM L1 Enabled; RCB 128 bytes Disabled- Retrain- CommClk+
            ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x1, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
    Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
        Vector table: BAR=0 offset=00000000
        PBA: BAR=0 offset=00000000
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Virtual Channel <?>
    Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
    Kernel driver in use: ath9k
    Kernel modules: ath9k

When I first installed Ubuntu 9.10, the ath9k driver was pretty much unstable (low signal rates, frequent disconnects etc). I followed this [http://ubuntuforums.org/showthread.php?t=1309605](http://ubuntuforums.org/showthread.php?t=1309605) and installed these two packages:

linux-backports-modules-karmic
linux-backports-modules-wireless-karmic-generic

Things started to work better after this. Signal is so much better and the connection to the AP is very stable (no disc or such). However, I experience frequent small stalls. Small == a duration of 2-3 seconds. 

Has anyone experienced such behaviour ? I'm using a lot of interactive sessions (ssh) and this really bites me from a usability perspective.

Thanks 
Leonidas

---

### Post by ltsampros on 2010-01-06
*bump*

---

### Post by sirjasonr on 2010-02-10
hey :)
I've been having headaches with the old ath9k for a while, including intermittent dropouts. I compiled the ath9k using sources found on linuxwireless.org and that seemed to solve the issue of stability (although I'm not prepared to say so for sure since I only did it earlier today). As far as I can see, you don't really have anything to loose from trying. From what I recall however, they do recommend removing the backports packages before installing your own compiled module to avoid conflicts.

Give it a go and post back your findings. Hopefully you'll be able to help others in the same position.

Jason

---

