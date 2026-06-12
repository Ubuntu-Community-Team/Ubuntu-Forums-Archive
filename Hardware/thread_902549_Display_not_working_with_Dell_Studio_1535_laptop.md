---
title: "Display not working with Dell Studio 1535 laptop"
date: 2008-08-27
forum: Hardware
---

### Post by TallMatthew on 2008-08-27
This is a Hardy Heron install.

I just purchased one of these laptops and cannot get X running, except with the Vesa driver. All I get is white screens when using the intel driver.

lspci -vv output:

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
Subsystem: Dell Unknown device 0254
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
Latency: 0
Interrupt: pin A routed to IRQ 16
Region 0: Memory at f6e00000 (64-bit, non-prefetchable) [size=1M]
Region 2: Memory at e0000000 (64-bit, prefetchable) [size=256M]
Region 4: I/O ports at eff8 [size=8]
Capabilities: <access denied>

The relevant portion of xorg.conf:

Section "Device"
Identifier "Configured Video Device"
Driver "intel"
BusID "PCI:0:2:0"
VideoRam 258620
EndSection

Section "Monitor"
Identifier "Configured Monitor"
Option "DPMS"
HorizSync 30-62
VertRefresh 43-60
EndSection

Section "Module"
Load "glx"
Load "dri"
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
SubSection "Display"
Depth 24
Modes "1280x800"
EndSubSection
Device "Configured Video Device"
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Synaptics Touchpad"
EndSection


Note: the refresh values are from an attempted Opensuse live CD install (which also did not work). xresprobe on Ubuntu could not read any information from the monitor except for the one resolution (1280x800).

---

