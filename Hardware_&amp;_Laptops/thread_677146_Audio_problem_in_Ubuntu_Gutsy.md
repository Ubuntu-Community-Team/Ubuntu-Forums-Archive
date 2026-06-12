---
title: "Audio problem in Ubuntu Gutsy"
date: 2008-01-24
forum: Hardware &amp; Laptops
---

### Post by chr05210084 on 2008-01-24
Hello everyone,

I have Ubuntu Gutsy installed in ECS W341UI laptop, everything is working fine except the audio, sound and mic were not working. I have tried every possible solutions posted here [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) and here [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting). Here is the specs of my audio device:

Using lspci -vv
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
        Subsystem: Rioworks Unknown device 205f
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 32 bytes
        Interrupt: pin ? routed to IRQ 17
        Region 0: Memory at c0500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

Using cat /proc/asound/card0/codec#* | grep Codec

Codec: SigmaTel STAC9200
Codec: Generic 11c1 Si3054

Please help. Thank you very much.

---

### Post by Yellow Pasque on 2008-01-24
Seen this thread? ([http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845))
The STAC9200 is listed with a bunch of options for the model= parameter. True, they're all for Dell, but I would still try them, as I have seen people get sound working by entering another manufacturer's option in the alsa-base file.

---

