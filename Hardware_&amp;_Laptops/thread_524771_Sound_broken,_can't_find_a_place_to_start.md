---
title: "Sound broken, can't find a place to start"
date: 2007-08-13
forum: Hardware &amp; Laptops
---

### Post by cjtenny on 2007-08-13
Well my sound died yesterday.... I installed compiz-fusion with the latest nvidia driver the night before, but aside from that my system hasn't had much changed.  Alsamixer reveals no muted channels, I've attached the output from amixer, and fuser /dev/dsp and fuser /dev/snd reveals no processes using sound.  mpg321 can play files with alsa and oss, but no noise comes from the speakers even as mpg321's counter increments.  I don't know where to start... any ideas?

I'm running on a Compaq Presario v3000z CTO laptop with altec lansing speakers. MCP51 high-def audio thing.

---

### Post by maccam94 on 2007-08-13
Here's his lspci -vvv:
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30b5
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (500ns min, 1250ns max)
        Interrupt: pin B routed to IRQ 22
        Region 0: Memory at c0000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

---

### Post by cjtenny on 2007-08-13
yeah, here it is run as root:```

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30b5
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (500ns min, 1250ns max)
        Interrupt: pin B routed to IRQ 22
        Region 0: Memory at c0000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000
                Masking: 00000000  Pending: 00000000
        Capabilities: [6c] HyperTransport: MSI Mapping

```

---

