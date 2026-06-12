---
title: "some issues about ati radeon 3650 card driver"
date: 2009-12-21
forum: Hardware
---

### Post by lixinfish on 2009-12-21
hi,
I'm on a Desktop with Ubuntu karmic 64bit, and my graphics card is ATI Radeon 3650.
I have come across some problems when I try to install the graphics card driver...

first I tried the open source driver, which works perfect. But the problem is it somehow doesn't support any hardware OpenGL or 3D acceleration at all when I'm using a software.
Such as when I run the Vmware Workstation 7.0, and it just tell me it can't find a card that support 3D acceleration and so turn the 3D acceleration off. The same with Google Earth, lag so much when I'm using it.

Then, I remove the opensource drivers and go to the ATI official site and download the driver's newist version. The performance was just soso as there's lag when I maxmize the windows. But it do "support" 3D acceleration in software. With this driver, 3D acceleration is turned on but the window just kept twinkling... Even when I move the window ofglxgear, it twiinkle so much that my eye can't tolerate it.

so...how can i solve this problem?
somemore information follows:
```
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3600 Series  
OpenGL version string: 2.1.9116
OpenGL shading language version string: 1.40
OpenGL extensions:
```

```
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Mobility Radeon HD 3600 Series [1002:9598]
    Subsystem: Dell Device [1028:2242]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0, Cache Line Size: 64 bytes
    Interrupt: pin A routed to IRQ 26
    Region 0: Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Region 2: Memory at fdde0000 (64-bit, non-prefetchable) [size=64K]
    Region 4: I/O ports at ce00 [size=256]
    [virtual] Expansion ROM at fdd00000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: fglrx_pci
    Kernel modules: fglrx, radeon
```

---

