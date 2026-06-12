---
title: "Sound system. Use one device for playback, and another one for capture."
date: 2009-01-01
forum: Hardware
---

### Post by Joe_Bishop on 2009-01-01
Intrepid x86_64.
I have two sound devices: integrated HDA Intel and ESI Juli@. Juli has no capturing capabilites, so I need to use integrated HDA Intel for this puprose . Gstreamer software works OK with it, as well as vlc, but Adobe flash plugin, mplayer and several games play through integrated sound device, not Juli.
I think I would have no issues when completely disable playback through onboard Intel card.
// Mplayer uses pulse audio, vlc needed manual setup (change audio device).
Intel HDA:
```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controlle$
        Subsystem: Giga-byte Technology Device a002
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at fa100000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0$
        Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [100] Virtual Channel <?>
        Capabilities: [130] Root Complex Link <?>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

```
Juli@:
```
05:02.0 Multimedia audio controller: VIA Technologies Inc. VT1720/24 [Envy24PT/$
        Subsystem: Device 3031:4553
        Flags: bus master, medium devsel, latency 32, IRQ 18
        I/O ports at d000 [size=32]
        I/O ports at d100 [size=128]
        Capabilities: [80] Power Management version 1
        Kernel driver in use: ICE1724
        Kernel modules: snd-ice1724

```

---

