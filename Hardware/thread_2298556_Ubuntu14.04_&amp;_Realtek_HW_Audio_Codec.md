---
title: "Ubuntu14.04 &amp; Realtek HW Audio Codec"
date: 2015-10-12
forum: Hardware
---

### Post by kangzipo on 2015-10-12
Hello everyone, 
  I installed Ubuntu 14.04 and I don't have any sound. My laptop type is XPS13 and I find my audio card type in Windows 10, it's Realtek HW Audio Codec. It seems that Ubuntu cannot detect it. Another problem: every time I return to Win10 after exited Ubuntu, the driver of Realtek HW Audio Codec disappear and I have to reinstall it. What's wrong?
  Thank you in advance:)

here is my lspci:
```
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
    Subsystem: Dell Device 0665
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 49
    Region 0: Memory at f7418000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
```

---

