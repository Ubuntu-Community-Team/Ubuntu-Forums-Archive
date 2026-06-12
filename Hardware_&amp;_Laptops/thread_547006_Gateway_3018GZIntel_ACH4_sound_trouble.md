---
title: "Gateway 3018GZ/Intel ACH4 sound trouble"
date: 2007-09-09
forum: Hardware &amp; Laptops
---

### Post by amdefeo on 2007-09-09
After a distro update, I've lost sound output on my Gateway 3018GZ laptop, using an Intel ICH4 soundcard and an Analog Device AD1981b chip.

Initially, aplay -l and alsamixer saw the card and I was able to manage volume levels etc., but with no output whatsoever.

I've tried a number of solutions referred to here and on launchpad;
I've tried a number of settings in /etc/modprobe.d/alsa-base

```
options snd-hda-intel model=[auto, test,]
options snd-intel8x0
```
etc.

i uninstalled and reinstalled the ALSA packages, and recompiled ALSA to include the snd-hda-intel module, however the compile fails consistently.

now aplay -l returns
```
aplay: device_list:222: no soundcards found...

```


and alsamixer similarly sees no device

sudo lspci -vvnn returns

```
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 03)
        Subsystem: Rioworks Unknown device [161f:203e]
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin B routed to IRQ 10
        Region 0: I/O ports at 1c00 [size=256]
        Region 1: I/O ports at 18c0 [size=64]
        Region 2: Memory at e0100c00 (32-bit, non-prefetchable) [size=512]
        Region 3: Memory at e0100800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
```


any ideas? how bad did I mess this up?

---

