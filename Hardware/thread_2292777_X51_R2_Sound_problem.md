---
title: "X51 R2 Sound problem"
date: 2015-08-31
forum: Hardware
---

### Post by klebrun-5 on 2015-08-31
Hi,

I just got an Alienware Area 51 R2 box which I've dual booted with Windows 10. I got the nVidia drivers running, but now we're into the sound - there isn't any.

This box came with an integrated Creative SB C610/X99 chipset which is supposed to give me a 5.1 sound system - and it does, but so far only in Windows.

```
keith@keith-Alienware-Area-51-R2:/dev$ sudo lspci -vv -k | grep -A40 -i "audio"
00:1b.0 Audio device: Intel Corporation C610/X99 series chipset HD Audio Controller (rev 05)
    Subsystem: Dell Device 064c
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 37
    Region 0: Memory at fb310000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Address: 00000000fee00018  Data: 0000
    Capabilities: [70] Express (v1) Root Complex Integrated Endpoint, MSI 00
        DevCap:    MaxPayload 128 bytes, PhantFunc 0
            ExtTag- RBE-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
            MaxPayload 128 bytes, MaxReadReq 128 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr+ TransPend-
    Capabilities: [100 v1] Virtual Channel
        Caps:    LPEVC=0 RefClk=100ns PATEntryBits=1
        Arb:    Fixed- WRR32- WRR64- WRR128-
        Ctrl:    ArbSelect=Fixed
        Status:    InProgress-
        VC0:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
            Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
            Ctrl:    Enable+ ID=0 ArbSelect=Fixed TC/VC=01
            Status:    NegoPending- InProgress-
        VC1:    Caps:    PATOffset=00 MaxTimeSlots=1 RejSnoopTrans-
            Arb:    Fixed- WRR32- WRR64- WRR128- TWRR128- WRR256-
            Ctrl:    Enable+ ID=2 ArbSelect=Fixed TC/VC=04
            Status:    NegoPending- InProgress-
    Kernel driver in use: snd_hda_intel
03:00.1 Audio device: NVIDIA Corporation GM204 High Definition Audio Controller (rev a1)
    Subsystem: NVIDIA Corporation Device 1131
    Physical Slot: 6
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 32 bytes
    Interrupt: pin B routed to IRQ 38
    Region 0: Memory at fb080000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: [60] Power Management version 3
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst+ PME-Enable- DSel=0 DScale=0 PME-
    Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+
        Address: 0000000000000000  Data: 0000
    Capabilities: [78] Express (v2) Endpoint, MSI 00
        DevCap:    MaxPayload 256 bytes, PhantFunc 0, Latency L0s unlimited, L1 <64us
            ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
        DevCtl:    Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
            RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
            MaxPayload 256 bytes, MaxReadReq 512 bytes
        DevSta:    CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
        LnkCap:    Port #0, Speed 8GT/s, Width x16, ASPM L0s L1, Exit Latency L0s <512ns, L1 <4us
            ClockPM+ Surprise- LLActRep- BwNot-
        LnkCtl:    ASPM L0s L1 Enabled; RCB 64 bytes Disabled- CommClk+
            ExtSynch- ClockPM+ AutWidDis- BWInt- AutBWInt-
        LnkSta:    Speed 2.5GT/s, Width x8, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        DevCap2: Completion Timeout: Range AB, TimeoutDis+, LTR+, OBFF Via message
        DevCtl2: Completion Timeout: 50us to 50ms, TimeoutDis-, LTR-, OBFF Disabled
        LnkSta2: Current De-emphasis Level: -6dB, EqualizationComplete-, EqualizationPhase1-
             EqualizationPhase2-, EqualizationPhase3-, LinkEqualizationRequest-
    Kernel driver in use: snd_hda_intel

```

alsamixer only gives me a Master and PCM slider - nothing for the other channels, and the output devices listed in Sound Settings of Volume Control is Line Out and Headphones. No sound plays through the headphone jacks either. I'm thinking this is a driver issue - snd-hda-intel might not be the right one. Wondering if someone else ran into this?

---

### Post by Yellow Pasque on 2015-08-31
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

> snd-hda-intel might not be the right one
That's the right one. Possibly, you need a newer version of it, or you'll actually need a dev to do something like: [https://github.com/torvalds/linux/commit/d5c016b56cb08d5b043033010df958ba7bb384cc](https://github.com/torvalds/linux/commit/d5c016b56cb08d5b043033010df958ba7bb384cc)

But, provide the info first and then go from there.

---

### Post by klebrun-5 on 2015-08-31
Thanks for the reply.

Alsa-info:  [http://www.alsa-project.org/db/?f=7d181a0203525db9f6a02561dd1283022c88a05b](http://www.alsa-project.org/db/?f=7d181a0203525db9f6a02561dd1283022c88a05b)

---

### Post by Yellow Pasque on 2015-08-31
I was going to tell you to install this package (latest snd-hda-intel module from 4.2 kernel), but I'm not sure if it works with the lowlatency kernel: [https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+files/oem-audio-hda-daily-dkms_0.201508311546%7Eubuntu15.04.1_all.deb](https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+files/oem-audio-hda-daily-dkms_0.201508311546%7Eubuntu15.04.1_all.deb)

If things don't change/improve, then I would raise a bug on kernel bugzilla (be sure to get a fresh copy/link to your updated ALSA info).

---

### Post by klebrun-5 on 2015-08-31
I'll give it a try... if it blows up the system, there's always Win 10 and bugzilla.

---

### Post by klebrun-5 on 2015-09-01
If it was at all possible (and in Ubuntu, all things usually are), that .deb made things even worse. The ONLY thing visible was the HDMI output from the nVidia card. Let's see if I can escalate this to a dev.

Thanks again for your help.

---

