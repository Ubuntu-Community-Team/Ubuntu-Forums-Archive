---
title: "ATI 3d rage pro, 3d acceleration"
date: 2006-03-17
forum: Hardware &amp; Laptops
---

### Post by mehdicherti on 2006-03-17
Hi everybody , I have ubuntu breezy , and I want to know if it's possible to enable 3d acceleration  ?

name of my graphic card : ATI Technologies Inc 3D Rage Pro
lspci -vv : 

0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c) (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Rage Pro Turbo AGP 2X
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 66 (2000ns min), Cache Line Size: 0x08 (32 bytes)
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at 40000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: I/O ports at 1000 [size=256]
        Region 2: Memory at 41000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

---

### Post by mehdicherti on 2006-03-17
can you help me please :(  !

---

### Post by Teroedni on 2006-03-17
Its seems it is not possible as default.
The reason for this is that the dri driver for the mach64 is unsecure and therefore not included with xorg by default.


I have a machine with this card myself and have found out i need to build dri :/

Instruction here
[http://dri.freedesktop.org/wiki/ATIMach64](http://dri.freedesktop.org/wiki/ATIMach64)

---

### Post by mehdicherti on 2006-03-17
thanks ,
i compiled Mesa , and DRM
but how can I compile Xorg (i must have the latest CVS version) ?
there isn't a makefile , there is "Imakefile" and when i try to do "imake" it doesn't work :confused:

---

