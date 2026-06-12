---
title: "No sound HP ProBook 4520s"
date: 2010-11-20
forum: Hardware
---

### Post by ibogi on 2010-11-20
I've installed Ubuntu 10.10 and there is no sound. The sound device is not shown in the Sound Preferences (under Hardware, list is empty)

Here is the output of lspci -vv

```
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
    Subsystem: Hewlett-Packard Company Device 1413
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 5
    Region 0: Memory at 94900000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: snd-hda-intel
```What could be the problem?

And also from lsmod | grep snd_hda_intel

```
snd_hda_intel          31738  1 
snd_hda_codec          87552  1 snd_hda_intel
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd                    49006  8 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm

```

---

