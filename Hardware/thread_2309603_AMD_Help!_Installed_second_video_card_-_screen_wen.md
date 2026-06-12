---
title: "AMD Help! Installed second video card - screen went black and power won't shut down"
date: 2016-01-12
forum: Hardware
---

### Post by marseille2 on 2016-01-12
A few hours ago, I dropped in a new identical video card (Asus RADEON HD 6450 2GB DDR3). 

```
$ lspci | grep VGA
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM]
```


```
$ lspci -v -s 01:00.0

01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM] (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 0461
    Flags: bus master, fast devsel, latency 0, IRQ 84
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at fea20000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at e000 [size=256]
    Expansion ROM at fea00000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon

```

```
$ lspci -v -s 02:00.002:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM] (prog-if 00 [VGA controller])
    Subsystem: ASUSTeK Computer Inc. Device 0461
    Flags: bus master, fast devsel, latency 0, IRQ 85
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    Memory at fe920000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at d000 [size=256]
    Expansion ROM at fe900000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon

```


Once the computer went to sleep (not sure about the suspend/hibernation settings), it never woke up.


[LIST]
[*]The screen went black,
[*]and something weird happened to the power: I can't use the reset or the power button. The cord to the power supplied has to be pulled to shut off the system.
[/LIST]

I've managed to get it working by a fluke about 3 times. This time I'm afraid for it to suspend or shut down ... but have no idea what to do.



I tried upgrading the kernel from 3.13 low-latency to 3.16 low-latency... but it didn't change anything. 

```
$ uname -aLinux av 3.16.0-57-lowlatency #77~14.04.1-Ubuntu SMP PREEMPT Thu Dec 17 23:55:07 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```



Also ... I don't have any proprietary drivers installed, and have no clue where to start if I do need them (neither do I know much about what's going on with XORG, and if I need to do something there). Please note that I have no onboard graphics: my mobo is an Asrock 970 Extreme4, with an AMD FX-8350 CPU. I also have UbuntuStudio with XFCE desktop, but normally use ICEWM.


```
$ lspci -vvnn | grep VGA

    Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop+ ParErr- Stepping- SERR- FastB2B- DisINTx-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM] [1002:6779] (prog-if 00 [VGA controller])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
02:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Caicos [Radeon HD 6450/7450/8450 / R5 230 OEM] [1002:6779] (prog-if 00 [VGA controller])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+

```


```

$ dmesg | egrep 'drm|radeon'
[   12.845788] [drm] Initialized drm 1.1.0 20060810
[   13.247353] [drm] radeon kernel modesetting enabled.
[   13.247421] fb: switching to radeondrmfb from VESA VGA
[   13.247765] [drm] initializing kernel modesetting (CAICOS 0x1002:0x6779 0x1043:0x0461).
[   13.247776] [drm] register mmio base: 0xFEA20000
[   13.247777] [drm] register mmio size: 131072
[   13.247804] radeon 0000:01:00.0: Invalid ROM contents
[   13.248351] radeon 0000:01:00.0: VRAM: 2048M 0x0000000000000000 - 0x000000007FFFFFFF (2048M used)
[   13.248353] radeon 0000:01:00.0: GTT: 1024M 0x0000000080000000 - 0x00000000BFFFFFFF
[   13.248354] [drm] Detected VRAM RAM=2048M, BAR=256M
[   13.248355] [drm] RAM width 64bits DDR
[   13.248423] [drm] radeon: 2048M of VRAM memory ready
[   13.248424] [drm] radeon: 1024M of GTT memory ready.
[   13.248440] [drm] Loading CAICOS Microcode
[   13.418555] [drm] Internal thermal controller without fan control
[   13.422990] [drm] radeon: dpm initialized
[   13.454744] [drm] GART: num cpu pages 262144, num gpu pages 262144
[   13.455772] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
[   13.473626] [drm] PCIE GART of 1024M enabled (table at 0x0000000000273000).
[   13.473733] radeon 0000:01:00.0: WB enabled
[   13.473737] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00 and cpu addr 0xffff880235e9ec00
[   13.473740] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c and cpu addr 0xffff880235e9ec0c
[   13.475344] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000072118 and cpu addr 0xffffc90010f32118
[   13.475346] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   13.475347] [drm] Driver supports precise vblank timestamp query.
[   13.475349] radeon 0000:01:00.0: radeon: MSI limited to 32-bit
[   13.475375] radeon 0000:01:00.0: irq 84 for MSI/MSI-X
[   13.475386] radeon 0000:01:00.0: radeon: using MSI.
[   13.475589] [drm] radeon: irq initialized.
[   13.492292] [drm] ring test on 0 succeeded in 2 usecs
[   13.492304] [drm] ring test on 3 succeeded in 7 usecs
[   13.679777] [drm] ring test on 5 succeeded in 2 usecs
[   13.679786] [drm] UVD initialized successfully.
[   13.680144] [drm] ib test on ring 0 succeeded in 0 usecs
[   13.680197] [drm] ib test on ring 3 succeeded in 0 usecs
[   13.833044] [drm] ib test on ring 5 succeeded
[   13.833592] [drm] Radeon Display Connectors
[   13.833593] [drm] Connector 0:
[   13.833594] [drm]   HDMI-A-1
[   13.833595] [drm]   HPD1
[   13.833597] [drm]   DDC: 0x6460 0x6460 0x6464 0x6464 0x6468 0x6468 0x646c 0x646c
[   13.833597] [drm]   Encoders:
[   13.833598] [drm]     DFP1: INTERNAL_UNIPHY1
[   13.833599] [drm] Connector 1:
[   13.833600] [drm]   DVI-D-1
[   13.833600] [drm]   HPD4
[   13.833602] [drm]   DDC: 0x6450 0x6450 0x6454 0x6454 0x6458 0x6458 0x645c 0x645c
[   13.833602] [drm]   Encoders:
[   13.833603] [drm]     DFP2: INTERNAL_UNIPHY
[   13.833604] [drm] Connector 2:
[   13.833604] [drm]   VGA-1
[   13.833605] [drm]   DDC: 0x6430 0x6430 0x6434 0x6434 0x6438 0x6438 0x643c 0x643c
[   13.833606] [drm]   Encoders:
[   13.833607] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   13.875687] [drm] fb mappable at 0xC0474000
[   13.875688] [drm] vram apper at 0xC0000000
[   13.875689] [drm] size 7299072
[   13.875690] [drm] fb depth is 24
[   13.875691] [drm]    pitch is 6912
[   13.875772] fbcon: radeondrmfb (fb0) is primary device
[   13.875878] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[   13.875879] radeon 0000:01:00.0: registered panic notifier
[   13.878851] [drm] Initialized radeon 2.39.0 20080528 for 0000:01:00.0 on minor 0
[   13.878912] radeon 0000:02:00.0: enabling device (0000 -> 0003)
[   13.879078] [drm] initializing kernel modesetting (CAICOS 0x1002:0x6779 0x1043:0x0461).
[   13.879088] [drm] register mmio base: 0xFE920000
[   13.879089] [drm] register mmio size: 131072
[   14.111257] [drm] GPU not posted. posting now...
[   14.114581] radeon 0000:02:00.0: VRAM: 2048M 0x0000000000000000 - 0x000000007FFFFFFF (2048M used)
[   14.114583] radeon 0000:02:00.0: GTT: 1024M 0x0000000080000000 - 0x00000000BFFFFFFF
[   14.114584] [drm] Detected VRAM RAM=2048M, BAR=256M
[   14.114585] [drm] RAM width 64bits DDR
[   14.114593] [drm] radeon: 2048M of VRAM memory ready
[   14.114594] [drm] radeon: 1024M of GTT memory ready.
[   14.114606] [drm] Loading CAICOS Microcode
[   14.114611] [drm] Internal thermal controller without fan control
[   14.119009] [drm] radeon: dpm initialized
[   14.119023] [drm] GART: num cpu pages 262144, num gpu pages 262144
[   14.120040] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
[   14.123315] [drm] PCIE GART of 1024M enabled (table at 0x0000000000273000).
[   14.123419] radeon 0000:02:00.0: WB enabled
[   14.123421] radeon 0000:02:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00 and cpu addr 0xffff8802350ffc00
[   14.123423] radeon 0000:02:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c and cpu addr 0xffff8802350ffc0c
[   14.124977] radeon 0000:02:00.0: fence driver on ring 5 use gpu addr 0x0000000000072118 and cpu addr 0xffffc90012db2118
[   14.124979] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   14.124979] [drm] Driver supports precise vblank timestamp query.
[   14.124980] radeon 0000:02:00.0: radeon: MSI limited to 32-bit
[   14.125002] radeon 0000:02:00.0: irq 85 for MSI/MSI-X
[   14.125011] radeon 0000:02:00.0: radeon: using MSI.
[   14.125169] [drm] radeon: irq initialized.
[   14.141868] [drm] ring test on 0 succeeded in 2 usecs
[   14.141879] [drm] ring test on 3 succeeded in 7 usecs
[   14.329343] [drm] ring test on 5 succeeded in 2 usecs
[   14.329352] [drm] UVD initialized successfully.
[   14.329768] [drm] ib test on ring 0 succeeded in 0 usecs
[   14.329847] [drm] ib test on ring 3 succeeded in 0 usecs
[   14.482585] [drm] ib test on ring 5 succeeded
[   14.483097] [drm] Radeon Display Connectors
[   14.483098] [drm] Connector 0:
[   14.483099] [drm]   HDMI-A-2
[   14.483100] [drm]   HPD1
[   14.483102] [drm]   DDC: 0x6460 0x6460 0x6464 0x6464 0x6468 0x6468 0x646c 0x646c
[   14.483102] [drm]   Encoders:
[   14.483103] [drm]     DFP1: INTERNAL_UNIPHY1
[   14.483104] [drm] Connector 1:
[   14.483105] [drm]   DVI-D-2
[   14.483106] [drm]   HPD4
[   14.483107] [drm]   DDC: 0x6450 0x6450 0x6454 0x6454 0x6458 0x6458 0x645c 0x645c
[   14.483107] [drm]   Encoders:
[   14.483108] [drm]     DFP2: INTERNAL_UNIPHY
[   14.483109] [drm] Connector 2:
[   14.483109] [drm]   VGA-2
[   14.483111] [drm]   DDC: 0x6430 0x6430 0x6434 0x6434 0x6438 0x6438 0x643c 0x643c
[   14.483111] [drm]   Encoders:
[   14.483112] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   14.499132] radeon 0000:02:00.0: No connectors reported connected with modes
[   14.499135] [drm] Cannot find any crtc or sizes - going 1024x768
[   14.500280] [drm] fb mappable at 0xB0474000
[   14.500281] [drm] vram apper at 0xB0000000
[   14.500282] [drm] size 3145728
[   14.500283] [drm] fb depth is 24
[   14.500284] [drm]    pitch is 4096
[   14.500447] radeon 0000:02:00.0: fb1: radeondrmfb frame buffer device
[   14.500490] [drm] Initialized radeon 2.39.0 20080528 for 0000:02:00.0 on minor 1
[   25.815293] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 200
[   25.844022] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 194
[   25.909541] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 254
[  204.490457] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 130
[  220.756302] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 229

```

---

