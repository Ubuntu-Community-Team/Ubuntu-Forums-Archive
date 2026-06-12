---
title: "Backtrace with Dual Radeon HD 4350 configured for 4 monitors."
date: 2010-09-08
forum: Hardware
---

### Post by dhing on 2010-09-08
First, I've searched and tried the suggestions/solutions in [http://ubuntuforums.org/archive/index.php/t-920898.html](http://ubuntuforums.org/archive/index.php/t-920898.html) to no success.

It's also important to note that I think that this motherboard has an on-board ATI card, which might be messing up the screens portion of xorg, but I'm not sure that it should be backtracing.

**System Information:**
CPU: AMD Phenom 9950 quad-core
Motherboard: MSI DKA790GX - [http://www.msi.com/index.php?func=proddesc&maincat_no=1&prod_no=1625](http://www.msi.com/index.php?func=proddesc&maincat_no=1&prod_no=1625)
RAM: 8GB
Video Cards: Asus EAH4350 x 2 (PCIe) 512MB

**Process:**
Install Ubuntu 10.04.1 LTS 64 bit
Update all packages
Install Catalyst 10.8 through the restricted drivers icon in the taskbar
Reboot
Attempt to enable the second video card
Reboot
Backtrace...

Kernel: Linux Desktop 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64 GNU/Linux

**_Diagnostics:_**
Tried many aticonfig commands to try and correct the xorg.conf (if it needs fixing?)

Found both cards in the proc nodes:
```

#cat /proc/ati/0/name
fglrx 0xfa00001 PCI:1:0:0

# cat /proc/ati/1/name
fglrx 0xfa00001 PCI:2:0:0

```

**lspci -vv shows both cards:**
```

01:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4350]
        Subsystem: ASUSTeK Computer Inc. Device 02a8
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 18
        Region 0: Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Region 2: Memory at fe9f0000 (64-bit, non-prefetchable) [size=64K]
        Region 4: I/O ports at c000 [size=256]
        Expansion ROM at fe9c0000 [disabled] [size=128K]
        Capabilities: [50] Power Management version 3
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [58] Express (v2) Legacy Endpoint, MSI 00
                DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
                        ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
                        MaxPayload 128 bytes, MaxReadReq 128 bytes
                DevSta: CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
                LnkCap: Port #0, Speed 2.5GT/s, Width x16, ASPM L0s L1, Latency L0 <64ns, L1 <1us
                        ClockPM- Suprise- LLActRep- BwNot-
                LnkCtl: ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x8, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000
        Capabilities: [100] Vendor Specific Information <?>
        Kernel driver in use: fglrx_pci
        Kernel modules: fglrx, radeon

02:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4350]
        Subsystem: ASUSTeK Computer Inc. Device 02a8
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 19
        Region 0: Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Region 2: Memory at feaf0000 (64-bit, non-prefetchable) [size=64K]
        Region 4: I/O ports at d000 [size=256]
        Expansion ROM at feac0000 [disabled] [size=128K]
        Capabilities: [50] Power Management version 3
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [58] Express (v2) Legacy Endpoint, MSI 00
                DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s <4us, L1 unlimited
                        ExtTag+ AttnBtn- AttnInd- PwrInd- RBE+ FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd+ ExtTag- PhantFunc- AuxPwr- NoSnoop+
                        MaxPayload 128 bytes, MaxReadReq 128 bytes
                DevSta: CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend-
                LnkCap: Port #1, Speed 2.5GT/s, Width x16, ASPM L0s L1, Latency L0 <64ns, L1 <1us
                        ClockPM- Suprise- LLActRep- BwNot-
                LnkCtl: ASPM Disabled; RCB 64 bytes Disabled- Retrain- CommClk+
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed 2.5GT/s, Width x8, TrErr- Train- SlotClk+ DLActive- BWMgmt- ABWMgmt-
        Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
                Address: 0000000000000000  Data: 0000
        Capabilities: [100] Vendor Specific Information <?>
        Kernel driver in use: fglrx_pci
        Kernel modules: fglrx, radeon

```

**aticonfig see's both cards:**
```

# aticonfig --list-adapters
* 0. 01:00.0 ATI Radeon HD 4300/4500 Series
  1. 02:00.0 ATI Radeon HD 4300/4500 Series

* - Default adapter

```

**_Xorg.conf_**

**/etc/X11/xorg.conf**
```

Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
        Screen         "aticonfig-Screen[1]-0" RightOf "aticonfig-Screen[0]-0"
        Screen         "aticonfig-Screen[0]-1" RightOf "aticonfig-Screen[1]-0"
        Screen         "aticonfig-Screen[1]-1" RightOf "aticonfig-Screen[0]-1"
EndSection

Section "Files"
EndSection

Section "Module"
        Load  "glx"
EndSection

Section "ServerFlags"
        Option      "Xinerama" "on"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Monitor"
        Identifier   "0-DFP5"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
        Option      "PreferredMode" "1280x1024"
        Option      "TargetRefresh" "60"
        Option      "Position" "0 0"
        Option      "Rotate" "normal"
        Option      "Disable" "false"
EndSection

Section "Monitor"
        Identifier   "0-CRT2"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
        Option      "PreferredMode" "1280x1024"
        Option      "TargetRefresh" "75"
        Option      "Position" "1280 0"
        Option      "Rotate" "normal"
        Option      "Disable" "false"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[1]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-1"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[1]-1"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        Option      "Monitor-DFP5" "0-DFP5"
        Option      "Monitor-CRT2" "0-CRT2"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[1]-0"
        Driver      "fglrx"
        BusID       "PCI:2:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-1"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
        Screen      1
EndSection

Section "Device"
        Identifier  "aticonfig-Device[1]-1"
        Driver      "fglrx"
        BusID       "PCI:2:0:0"
        Screen      1
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Virtual   2560 2560
                Depth     24
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[1]-0"
        Device     "aticonfig-Device[1]-0"
        Monitor    "aticonfig-Monitor[1]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-1"
        Device     "aticonfig-Device[0]-1"
        Monitor    "aticonfig-Monitor[0]-1"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[1]-1"
        Device     "aticonfig-Device[1]-1"
        Monitor    "aticonfig-Monitor[1]-1"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

```

**_Log Analysis:_**
- There are no entries for GPU in the dmesg logs
- In the Xorg.0.log file: (Removed everything between the sub modules until the end for readability)
```

(II) Loading sub module "fglrxdrm"
(II) fglrx(0): pEnt->device->identifier=0xbc1790
(II) fglrx(1): pEnt->device->identifier=0xbc1b80
(II) Loading sub module "vgahw"
(II) Loading sub module "fglrxdrm"
(II) Loading sub module "vbe"
(II) Loading sub module "fb"
(II) Loading sub module "ddc"
(II) Loading sub module "ramdac"
(II) Loading sub module "vgahw"
(II) Loading sub module "fglrxdrm"
(II) Loading sub module "vbe"
(II) Loading sub module "fb"
(II) Loading sub module "ddc"
(II) Loading sub module "ddc"
(II) Loading sub module "ramdac"
(II) Loading sub module "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.2.1
        ABI class: X.Org Video Driver, version 6.0
(II) fglrx(0): GLESX enableFlags = 94
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        Solid Horizontal and Vertical Lines
        Driver provided ScreenToScreenBitBlt replacement
        Driver provided FillSolidRects replacement
(II) fglrx(0): GLESX is enabled
(II) LoadModule: "amdxmm"
(II) Loading /usr/lib/xorg/extra-modules/modules/amdxmm.so
(II) Module amdxmm: vendor="X.Org Foundation"
        compiled for 1.7.1, module version = 1.0.0
(II) Loading extension AMDXVOPL
(II) fglrx(0): Composite extension is not loaded
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using HW cursor of display infrastructure!
(II) fglrx(0): Disabling in-server RandR and enabling in-driver RandR 1.2.
(II) fglrx(0): User Preference Output DFP5 using refresh rate 60.0 Hz.
(II) fglrx(0): User Preference Output CRT2 using refresh rate 75.0 Hz.
(--) RandR disabled
(II) fglrx(1): doing swlDriScreenInit
(II) fglrx(1): swlDriScreenInit for fglrx driver
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiDynamicMajor: found major device number 250
ukiOpenByBusid: Searching for BusID PCI:2:0:0
ukiOpenDevice: node name is /dev/ati/card0
ukiOpenDevice: open result is 22, (OK)
ukiOpenByBusid: ukiOpenMinor returns 22
ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
ukiOpenDevice: node name is /dev/ati/card1
ukiOpenDevice: open result is 22, (OK)
ukiOpenByBusid: ukiOpenMinor returns 22
ukiOpenByBusid: ukiGetBusid reports PCI:2:0:0
(II) fglrx(1): [uki] DRM interface version 1.0
(II) fglrx(1): [uki] created "fglrx" driver at busid "PCI:2:0:0"
(II) fglrx(1): [uki] added 8192 byte SAREA at 0xe000
(II) fglrx(1): [uki] mapped SAREA 0xe000 to 0x7f74340bc000
(II) fglrx(1): [uki] framebuffer handle = 0xf000
(II) fglrx(1): [uki] added 1 reserved context for kernel
(II) fglrx(1): swlDriScreenInit done
(II) fglrx(1): Kernel Module Version Information:
(II) fglrx(1):     Name: fglrx
(II) fglrx(1):     Version: 8.72.11
(II) fglrx(1):     Date: Apr  8 2010
(II) fglrx(1):     Desc: ATI FireGL DRM kernel module
(II) fglrx(1): Kernel Module version matches driver.
(II) fglrx(1): Kernel Module Build Time Information:
(II) fglrx(1):     Build-Kernel UTS_RELEASE:        2.6.32-24-generic
(II) fglrx(1):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(1):     Build-Kernel __SMP__:            yes
(II) fglrx(1):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(1): [uki] register handle = 0x00010000
(II) fglrx(1): Display width adjusted to to 1664 due to alignment constraints
(II) fglrx(1): DRI initialization successfull!
(II) fglrx(1): FBADPhys: 0xf00000000 FBMappedSize: 0x00c4a000
(II) fglrx(1): FBMM initialized for area (0,0)-(1664,1936)
(II) fglrx(1): FBMM auto alloc for area (0,0)-(1664,1664) (front color buffer - assumption)
(II) fglrx(1): Largest offscreen area available: 1664 x 272
(==) fglrx(1): Backing store disabled
(**) fglrx(1): DPMS enabled
(**) fglrx(1): Textured Video is enabled.
(II) fglrx(1): GLESX enableFlags = 94
(II) fglrx(1): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        Solid Horizontal and Vertical Lines
        Driver provided ScreenToScreenBitBlt replacement
        Driver provided FillSolidRects replacement
(II) fglrx(1): GLESX is enabled
(II) fglrx(1): Composite extension is not loaded
(WW) fglrx(1): Option "VendorName" is not used
(WW) fglrx(1): Option "ModelName" is not used
(II) fglrx(1): X context handle = 0x1
(II) fglrx(1): [DRI] installation complete
(==) fglrx(1): Silken mouse enabled
(==) fglrx(1): Using HW cursor of display infrastructure!
(II) fglrx(1): Disabling in-server RandR and enabling in-driver RandR 1.2.
(--) RandR disabled
(II) Found 2 VGA devices: arbiter wrapping enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE

[B]Backtrace:
0: /usr/bin/X (xorg_backtrace+0x28) [0x4a3258]
1: /usr/bin/X (0x400000+0x655bd) [0x4655bd]
2: /lib/libpthread.so.0 (0x7f743af98000+0xf8f0) [0x7f743afa78f0]
3: /usr/lib/xorg/extra-modules/modules/glesx.so (0x7f7434459000+0x35925e) [0x7f74347b225e]
4: /usr/lib/xorg/extra-modules/modules/glesx.so (0x7f7434459000+0x35bfcc) [0x7f74347b4fcc]
5: /usr/lib/xorg/extra-modules/modules/glesx.so (0x7f7434459000+0x35c3d9) [0x7f74347b53d9]
6: /usr/lib/xorg/extra-modules/modules/glesx.so (0x7f7434459000+0x355743) [0x7f74347ae743]
7: /usr/lib/xorg/extra-modules/modules/glesx.so (0x7f7434459000+0x3322ec) [0x7f743478b2ec]
8: /usr/lib/xorg/extra-modules/modules/glesx.so (0x7f7434459000+0x1ba80c) [0x7f743461380c]
9: /usr/lib/xorg/extra-modules/modules/glesx.so (0x7f7434459000+0x1bb207) [0x7f7434614207]
10: /usr/lib/xorg/extra-modules/modules/glesx.so (0x7f7434459000+0x11b88d) [0x7f743457488d]
11: /usr/lib/xorg/extra-modules/modules/glesx.so (0x7f7434459000+0x13aa6a) [0x7f7434593a6a]
12: /usr/lib/xorg/extra-modules/modules/glesx.so (0x7f7434459000+0x13ae07) [0x7f7434593e07]
13: /usr/lib/xorg/extra-modules/modules/glesx.so (0x7f7434459000+0xd14a0) [0x7f743452a4a0]
14: /usr/lib/xorg/extra-modules/modules/glesx.so (0x7f7434459000+0xd2d8d) [0x7f743452bd8d]
15: /usr/lib/xorg/extra-modules/modules/glesx.so (0x7f7434459000+0x3e7ad) [0x7f74344977ad]
16: /usr/lib/xorg/extra-modules/modules/glesx.so (0x7f7434459000+0x35ac2) [0x7f743448eac2]
17: /usr/lib/xorg/extra-modules/modules/glesx.so (0x7f7434459000+0x35c49) [0x7f743448ec49]
18: /usr/lib/xorg/extra-modules/modules/glesx.so (esutInit+0x8b) [0x7f743448d5cb]
19: /usr/lib/xorg/extra-modules/modules/glesx.so (0x7f7434459000+0x2623c) [0x7f743447f23c]
20: /usr/lib/xorg/extra-modules/modules/glesx.so (GlesxExtensionInit+0x75) [0x7f743447f5a5]
21: /usr/bin/X (InitExtensions+0x89) [0x4854e9]
22: /usr/bin/X (0x400000+0x2601d) [0x42601d]
23: /lib/libc.so.6 (__libc_start_main+0xfd) [0x7f7439c8fc4d]
24: /usr/bin/X (0x400000+0x25d59) [0x425d59]
Floating point exception at address 0x7f74347b225e

Caught signal 8 (Floating point exception). Server aborting

Please consult the The X.Org Foundation support
         at http://wiki.x.org
 for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

(II) fglrx(0): Backup framebuffer data.
(II) fglrx(0): Backup complete.[/B]

```

- In the xorg logs, here are the entries related to the second card:
```

(II) fglrx(1): pEnt->device->identifier=0xbc1b80
(II) fglrx(1): === [atiddxPreInit] === begin
(**) fglrx(1): Depth 24, (--) framebuffer bpp 32
(II) fglrx(1): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(1): Default visual is TrueColor
(**) fglrx(1): Option "DPMS" "true"
(==) fglrx(1): RGB weight 888
(II) fglrx(1): Using 8 bits per RGB
(==) fglrx(1): Buffer Tiling is ON
(II) fglrx(1): Primary V_BIOS segment is: 0xc000
(II) fglrx(1): VESA BIOS detected
(II) fglrx(1): VESA VBE Version 3.0
(II) fglrx(1): VESA VBE Total Mem: 16384 kB
(II) fglrx(1): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(1): VESA VBE OEM Software Rev: 11.20
(II) fglrx(1): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc.
(II) fglrx(1): VESA VBE OEM Product: RV710
(II) fglrx(1): VESA VBE OEM Product Rev: 01.00
(II) fglrx(1): RandR 1.2 support is enabled!
(II) fglrx(1): RandR 1.2 rotation support is enabled!
(==) fglrx(1): Center Mode is disabled
(II) fglrx(1): Output DFP1 using monitor section aticonfig-Monitor[1]-0
(II) fglrx(1): Output DFP5 has no monitor section
(II) fglrx(1): Output CRT1 has no monitor section
(II) fglrx(1): Output CRT2 has no monitor section
(II) fglrx(1): Output DFP1 disconnected
(II) fglrx(1): Output DFP5 disconnected
(II) fglrx(1): Output CRT1 connected
(II) fglrx(1): Output CRT2 disconnected
(II) fglrx(1): Using exact sizes for initial modes
(II) fglrx(1): Output CRT1 using initial mode 1600x1200
(II) fglrx(1): DPI set to (96, 96)
(II) fglrx(1): Adapter ATI Radeon HD 4300/4500 Series has 2 configurable heads and 0 displays connected.
(==) fglrx(1): QBS disabled
(==) fglrx(1):  PseudoColor visuals disabled
(==) fglrx(1): NoAccel = NO
(==) fglrx(1): NoDRI = NO
(==) fglrx(1): Capabilities: 0x00000000
(==) fglrx(1): CapabilitiesEx: 0x00000000
(==) fglrx(1): OpenGL ClientDriverName: "fglrx_dri.so"
(==) fglrx(1): UseFastTLS=0
(==) fglrx(1): BlockSignalsOnLock=1
(II) fglrx(1): doing swlDriScreenInit
(II) fglrx(1): swlDriScreenInit for fglrx driver
(II) fglrx(1): [uki] DRM interface version 1.0
(II) fglrx(1): [uki] created "fglrx" driver at busid "PCI:2:0:0"
(II) fglrx(1): [uki] added 8192 byte SAREA at 0xe000
(II) fglrx(1): [uki] mapped SAREA 0xe000 to 0x7f74340bc000
(II) fglrx(1): [uki] framebuffer handle = 0xf000
(II) fglrx(1): [uki] added 1 reserved context for kernel
(II) fglrx(1): swlDriScreenInit done
(II) fglrx(1): Kernel Module Version Information:
(II) fglrx(1):     Name: fglrx
(II) fglrx(1):     Version: 8.72.11
(II) fglrx(1):     Date: Apr  8 2010
(II) fglrx(1):     Desc: ATI FireGL DRM kernel module
(II) fglrx(1): Kernel Module version matches driver.
(II) fglrx(1): Kernel Module Build Time Information:
(II) fglrx(1):     Build-Kernel UTS_RELEASE:        2.6.32-24-generic
(II) fglrx(1):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(1):     Build-Kernel __SMP__:            yes
(II) fglrx(1):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(1): [uki] register handle = 0x00010000
(II) fglrx(1): Display width adjusted to to 1664 due to alignment constraints
(II) fglrx(1): DRI initialization successfull!
(II) fglrx(1): FBADPhys: 0xf00000000 FBMappedSize: 0x00c4a000
(II) fglrx(1): FBMM initialized for area (0,0)-(1664,1936)
(II) fglrx(1): FBMM auto alloc for area (0,0)-(1664,1664) (front color buffer - assumption)
(II) fglrx(1): Largest offscreen area available: 1664 x 272
(==) fglrx(1): Backing store disabled
(**) fglrx(1): DPMS enabled
(**) fglrx(1): Textured Video is enabled.
(II) fglrx(1): GLESX enableFlags = 94
(II) fglrx(1): Using XFree86 Acceleration Architecture (XAA)
(II) fglrx(1): GLESX is enabled
(II) fglrx(1): Composite extension is not loaded
(WW) fglrx(1): Option "VendorName" is not used
(WW) fglrx(1): Option "ModelName" is not used
(II) fglrx(1): X context handle = 0x1
(II) fglrx(1): [DRI] installation complete
(==) fglrx(1): Silken mouse enabled
(==) fglrx(1): Using HW cursor of display infrastructure!
(II) fglrx(1): Disabling in-server RandR and enabling in-driver RandR 1.2.

```

Any suggestions?

---

