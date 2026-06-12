---
title: "[kubuntu] Software Renderer In Use. Rendering may be degraded (18.04, 19.04, 19.10)"
date: 2020-01-30
forum: Hardware
---

### Post by robospark on 2020-01-30
Hello My Dear Ubuntians,

Struggling with this problem for few weeks now. Was running kubuntu 18.04 LTS for a number of months and few weeks ago after a periodic update and reboot things went pear-shape. Graphic mode after reboot reset to something abysmal like 640x480, xrandr would show no output detected and using "default", display settings would also show "Default" and do not allow me to change resolution settings to anything higher. 

I've tried few things, to change drivers to other options that were available in Software & Updates (nvidia meta, nouveau, nvidia binary), reboot, delete all nvidia from the system, reinstall it again, finally decided to upgrade up to latest kubuntu 19.10, resetting drivers again to nouveau deleting all nvidia stuff and removing nouveau blacklist. Recently tried nomodeset,acpi_osi=,acpi_osi=\"Linux\" kernel options, different video card, different video port and cable (DVI, VGA) changing BIOS settings but not to much success.

While screen resolution got back to normal after OS upgrade and going to nouveau, it is still showing that Software Renderer Is In Use message which tells me that it is not using video card properly. I am now ready to throw a towel and ask for help. It is an older desktop (8yrs), but lasted well so far and I have no option for a major upgrade at the moment. Would someone know what went wrong and how to fix it please? I really prefer not to reinstall, as I have a lot of time invested in set up.

```

$ sudo lshw -numeric -class video
  *-display                 
       description: VGA compatible controller
       product: GF114 [GeForce GTX 560 Ti] [10DE:1200]
       vendor: NVIDIA Corporation [10DE]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:28 memory:ea000000-ebffffff memory:d0000000-d7ffffff memory:dc000000-dfffffff ioport:df00(size=128) memory:c0000-dffff
```

```
lspci -k | grep -iEA5 'vga|3d|display'
01:00.0 VGA compatible controller: NVIDIA Corporation GF114 [GeForce GTX 560 Ti] (rev a1)
        Subsystem: Micro-Star International Co., Ltd. [MSI] GF114 [GeForce GTX 560 Ti]
        Kernel driver in use: nouveau
        Kernel modules: nvidiafb, nouveau
01:00.1 Audio device: NVIDIA Corporation GF114 HDMI Audio Controller (rev a1)
        Subsystem: Micro-Star International Co., Ltd. [MSI] GF114 HDMI Audio Controller
```


        ```

sudo lspci -vvn | grep -i VGA
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        BridgeCtl: Parity- SERR+ NoISA- VGA+ VGA16- MAbort- >Reset- FastB2B-
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
        BridgeCtl: Parity- SERR+ NoISA- VGA- VGA16- MAbort- >Reset- FastB2B-
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx+
        BridgeCtl: Parity- SERR+ NoISA- VGA- VGA16- MAbort- >Reset- FastB2B-
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        BridgeCtl: Parity- SERR+ NoISA- VGA- VGA16- MAbort- >Reset- FastB2B-
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
01:00.0 0300: 10de:1200 (rev a1) (prog-if 00 [VGA controller])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
pcilib: sysfs_read_vpd: read failed: Input/output error
```

```
glxinfo | grep renderer
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer,
    GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer, GLX_MESA_query_renderer,
Extended renderer info (GLX_MESA_query_renderer):
OpenGL renderer string: NVCE
```

```
dmesg |grep nouv
[    1.125482] fb0: switching to nouveaufb from VESA VGA
[    1.125685] nouveau 0000:01:00.0: NVIDIA GF114 (0ce000a1)
[    1.261524] nouveau 0000:01:00.0: bios: version 70.24.11.00.00
[    1.284810] nouveau 0000:01:00.0: fb: 1024 MiB GDDR5
[    1.345901] nouveau 0000:01:00.0: DRM: VRAM: 1024 MiB
[    1.345903] nouveau 0000:01:00.0: DRM: GART: 1048576 MiB
[    1.345906] nouveau 0000:01:00.0: DRM: TMDS table version 2.0
[    1.345908] nouveau 0000:01:00.0: DRM: DCB version 4.0
[    1.345910] nouveau 0000:01:00.0: DRM: DCB outp 00: 02000300 00000000
[    1.345911] nouveau 0000:01:00.0: DRM: DCB outp 01: 01000302 00020030
[    1.345913] nouveau 0000:01:00.0: DRM: DCB outp 02: 04011380 00000000
[    1.345915] nouveau 0000:01:00.0: DRM: DCB outp 03: 08011382 00020030
[    1.345916] nouveau 0000:01:00.0: DRM: DCB outp 04: 02022362 00020010
[    1.345918] nouveau 0000:01:00.0: DRM: DCB conn 00: 00001030
[    1.345919] nouveau 0000:01:00.0: DRM: DCB conn 01: 00010130
[    1.345921] nouveau 0000:01:00.0: DRM: DCB conn 02: 00002261
[    1.346775] nouveau 0000:01:00.0: DRM: MM: using COPY0 for buffer copies
[    1.461737] nouveau 0000:01:00.0: DRM: allocated 1920x1080 fb: 0x60000, bo (____ptrval____)
[    1.463790] fbcon: nouveaudrmfb (fb0) is primary device
[    1.463794] nouveau 0000:01:00.0: fb0: nouveaudrmfb frame buffer device
[    1.516007] [drm] Initialized nouveau 1.3.1 20120801 for 0000:01:00.0 on minor 0
[   35.833621] nouveau 0000:01:00.0: fifo: read fault at 0000257000 engine 05 [BAR3] client 07 [BAR_READ] reason 02 [PAGE_NOT_PRESENT] on channel -1 [003fdf7000 unknown]
```

```
uname -a
Linux 5.3.0-29-generic #31-Ubuntu SMP Fri Jan 17 17:27:26 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```

```
lsmod | grep nouv
nouveau              1949696  20
mxm_wmi                16384  1 nouveau
wmi                    32768  2 mxm_wmi,nouveau
video                  49152  1 nouveau
i2c_algo_bit           16384  1 nouveau
ttm                   106496  1 nouveau
drm_kms_helper        184320  1 nouveau
drm                   491520  13 drm_kms_helper,ttm,nouveau
```

```
less /var/log/Xorg.0.log | grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    32.133] (II) Initializing extension MIT-SCREEN-SAVER
[    32.560] (EE) Failed to open authorization file "/var/run/sddm/{d48cd4db-e7fe-4402-98e3-f4c2ee19fe27}": No such file or directory
[  2199.042] (EE) client bug: timer event3 debounce: offset negative (-4ms)
[  2199.128] (EE) client bug: timer event3 debounce: offset negative (-3ms)
[  2199.128] (EE) client bug: timer event3 debounce short: offset negative (-16ms)
[  2265.906] (EE) client bug: timer event3 debounce: offset negative (-20ms)
[  2266.963] (EE) client bug: timer event3 debounce: offset negative (-30ms)
```

```
dmesg | grep nouv
[    1.125482] fb0: switching to nouveaufb from VESA VGA
[    1.125685] nouveau 0000:01:00.0: NVIDIA GF114 (0ce000a1)
[    1.261524] nouveau 0000:01:00.0: bios: version 70.24.11.00.00
[    1.284810] nouveau 0000:01:00.0: fb: 1024 MiB GDDR5
[    1.345901] nouveau 0000:01:00.0: DRM: VRAM: 1024 MiB
[    1.345903] nouveau 0000:01:00.0: DRM: GART: 1048576 MiB
[    1.345906] nouveau 0000:01:00.0: DRM: TMDS table version 2.0
[    1.345908] nouveau 0000:01:00.0: DRM: DCB version 4.0
[    1.345910] nouveau 0000:01:00.0: DRM: DCB outp 00: 02000300 00000000
[    1.345911] nouveau 0000:01:00.0: DRM: DCB outp 01: 01000302 00020030
[    1.345913] nouveau 0000:01:00.0: DRM: DCB outp 02: 04011380 00000000
[    1.345915] nouveau 0000:01:00.0: DRM: DCB outp 03: 08011382 00020030
[    1.345916] nouveau 0000:01:00.0: DRM: DCB outp 04: 02022362 00020010
[    1.345918] nouveau 0000:01:00.0: DRM: DCB conn 00: 00001030
[    1.345919] nouveau 0000:01:00.0: DRM: DCB conn 01: 00010130
[    1.345921] nouveau 0000:01:00.0: DRM: DCB conn 02: 00002261
[    1.346775] nouveau 0000:01:00.0: DRM: MM: using COPY0 for buffer copies
[    1.461737] nouveau 0000:01:00.0: DRM: allocated 1920x1080 fb: 0x60000, bo (____ptrval____)
[    1.463790] fbcon: nouveaudrmfb (fb0) is primary device
[    1.463794] nouveau 0000:01:00.0: fb0: nouveaudrmfb frame buffer device
[    1.516007] [drm] Initialized nouveau 1.3.1 20120801 for 0000:01:00.0 on minor 0
[   35.833621] nouveau 0000:01:00.0: fifo: read fault at 0000257000 engine 05 [BAR3] client 07 [BAR_READ] reason 02 [PAGE_NOT_PRESENT] on channel -1 [003fdf7000 unknown]
```

```
Some selected dmesg entries that might be of interest:
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-5.3.0-29-generic root=/dev/mapper/ubuntu--vg-root ro quiet splash acpi_osi= vt.handoff=7

[    0.331809] ACPI: Added _OSI(Module Device)
[    0.331809] ACPI: Added _OSI(Processor Device)
[    0.331809] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.331809] ACPI: Added _OSI(Processor Aggregator Device)
[    0.331809] ACPI: Added _OSI(Linux-Dell-Video)
[    0.331809] ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)
[    0.331809] ACPI: Added _OSI(Linux-HPI-Hybrid-Graphics)
[    0.336402] ACPI: 6 ACPI AML tables successfully acquired and loaded
[    0.338900] ACPI: Dynamic OEM Table Load:
[    0.338906] ACPI: SSDT 0xFFFF8CEE26364C00 00022A (v01 PmRef  Cpu0Ist  00003000 INTL 20040311)
[    0.339373] ACPI: Dynamic OEM Table Load:
[    0.339378] ACPI: SSDT 0xFFFF8CEE26363000 000152 (v01 PmRef  Cpu1Ist  00003000 INTL 20040311)
[    0.339748] ACPI: Dynamic OEM Table Load:
[    0.339753] ACPI Error: AE_ALREADY_EXISTS, SSDT 0xFFFF8CEE26363600 Table is already loaded (20190703/tbdata-520)
[    0.339760] No Local Variables are initialized for Method [_PDC]
[    0.339762] Initialized Arguments for Method [_PDC]:  (1 arguments defined for method invocation)
[    0.339763]   Arg0:   (____ptrval____) <Obj>           Buffer(12) 01 00 00 00 01 00 00 00
[    0.339771] ACPI Error: Aborting method \_PR.CPU1._PDC due to previous error (AE_ALREADY_EXISTS) (20190703/psparse-529)
[    0.339898] ACPI: Dynamic OEM Table Load:
[    0.339903] ACPI: SSDT 0xFFFF8CEE26363600 000152 (v01 PmRef  Cpu2Ist  00003000 INTL 20040311)
[    0.340269] ACPI: Dynamic OEM Table Load:
[    0.340274] ACPI Error: AE_ALREADY_EXISTS, SSDT 0xFFFF8CEE26362600 Table is already loaded (20190703/tbdata-520)
[    0.340280] No Local Variables are initialized for Method [_PDC]
[    0.340282] Initialized Arguments for Method [_PDC]:  (1 arguments defined for method invocation)
[    0.340283]   Arg0:   (____ptrval____) <Obj>           Buffer(12) 01 00 00 00 01 00 00 00
[    0.340289] ACPI Error: Aborting method \_PR.CPU2._PDC due to previous error (AE_ALREADY_EXISTS) (20190703/psparse-529)
[    0.340416] ACPI: Dynamic OEM Table Load:
[    0.340421] ACPI: SSDT 0xFFFF8CEE26362600 000152 (v01 PmRef  Cpu3Ist  00003000 INTL 20040311)
[    0.340789] ACPI: Dynamic OEM Table Load:
[    0.340794] ACPI Error: AE_ALREADY_EXISTS, SSDT 0xFFFF8CEE26363A00 Table is already loaded (20190703/tbdata-520)
[    0.340800] No Local Variables are initialized for Method [_PDC]
[    0.340801] Initialized Arguments for Method [_PDC]:  (1 arguments defined for method invocation)
[    0.340802]   Arg0:   (____ptrval____) <Obj>           Buffer(12) 01 00 00 00 01 00 00 00
[    0.340809] ACPI Error: Aborting method \_PR.CPU3._PDC due to previous error (AE_ALREADY_EXISTS) (20190703/psparse-529)
[    0.341131] ACPI: Interpreter enabled
[    0.341153] ACPI: (supports S0 S3 S4 S5)
[    0.341154] ACPI: Using IOAPIC for interrupt routing
[    0.341181] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.341391] ACPI: Enabled 11 GPEs in block 00 to 3F
[    0.348322] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3f])
[    0.348328] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI HPX-Type3]
[    0.348644] PCI host bridge to bus 0000:00

[    0.351895] pci 0000:00:01.0: ASPM: current common clock configuration is broken, reconfiguring

[    0.847714] platform eisa.0: Probing EISA bus 0
[    0.847716] platform eisa.0: EISA: Cannot allocate resource for mainboard
[    0.847717] platform eisa.0: Cannot allocate resource for EISA slot 1
[    0.847722] platform eisa.0: Cannot allocate resource for EISA slot 2
[    0.847723] platform eisa.0: Cannot allocate resource for EISA slot 3
[    0.847725] platform eisa.0: Cannot allocate resource for EISA slot 4
[    0.847726] platform eisa.0: Cannot allocate resource for EISA slot 5
[    0.847727] platform eisa.0: Cannot allocate resource for EISA slot 6
[    0.847729] platform eisa.0: Cannot allocate resource for EISA slot 7
[    0.847730] platform eisa.0: Cannot allocate resource for EISA slot 8
[    0.847731] platform eisa.0: EISA: Detected 0 cards
[    0.847734] intel_pstate: CPU model not supported

[    0.929351] Run /init as init process
[    1.034077] r8169 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.036466] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x000000000000042C-0x000000000000042D (\GP2C) (20190703/utaddress-204)
[    1.036472] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    1.036509] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    1.038945] libphy: r8169: probed
[    1.041100] r8169 0000:03:00.0 eth0: RTL8168c/8111c, 00:1f:d0:d9:22:e9, XID 3c4, IRQ 16
[    1.041102] r8169 0000:03:00.0 eth0: jumbo features [frames: 6128 bytes, tx checksumming: ko]
[    1.062593] ahci 0000:00:1f.2: version 3.0
[    1.062780] ahci 0000:00:1f.2: SSS flag set, parallel bus scan disabled
[    1.062810] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    1.062812] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part ccc ems 
[    1.067542] i801_smbus 0000:00:1f.3: SMBus using PCI interrupt
[    1.068203] r8169 0000:03:00.0 enp3s0: renamed from eth0
[    1.068422] gpio_ich gpio_ich.1.auto: GPIO from 451 to 511
[    1.120574] scsi host0: ahci
[    1.120916] scsi host1: ahci
[    1.121093] scsi host2: ahci
[    1.124124] scsi host3: ahci
[    1.124304] scsi host4: ahci
[    1.125479] checking generic (dd000000 130000) vs hw (d0000000 8000000)
[    1.125481] checking generic (dd000000 130000) vs hw (dc000000 4000000)
[    1.125482] fb0: switching to nouveaufb from VESA VGA
[    1.125606] scsi host5: ahci

[    3.339743] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.340438] ata6.00: supports DRM functions and may not be fully accessible
[    3.340484] ata6.00: ATA-10: CT250MX500SSD1, M3CR023, max UDMA/133
[    3.340486] ata6.00: 488397168 sectors, multi 1: LBA48 NCQ (depth 32), AA
[    3.341195] ata6.00: supports DRM functions and may not be fully accessible
[    3.341782] ata6.00: configured for UDMA/133

[   16.162299] systemd[1]: Failed to bump fs.file-max, ignoring: Invalid argument

[   31.760612] kauditd_printk_skb: 56 callbacks suppressed

[   35.833621] nouveau 0000:01:00.0: fifo: read fault at 0000257000 engine 05 [BAR3] client 07 [BAR_READ] reason 02 [PAGE_NOT_PRESENT] on channel -1 [003fdf7000 unknown]
[  455.048733] perf: interrupt took too long (2509 > 2500), lowering kernel.perf_event_max_sample_rate to 79500
[  743.338931] perf: interrupt took too long (3138 > 3136), lowering kernel.perf_event_max_sample_rate to 63500
[ 1998.315320] perf: interrupt took too long (3929 > 3922), lowering kernel.perf_event_max_sample_rate to 50750

[ 3675.274999] r8169 0000:03:00.0: invalid short VPD tag 00 at offset 1


```

```
$ xrandr -q
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 16384 x 16384
DVI-I-1 disconnected (normal left inverted right x axis y axis)
DVI-I-2 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 509mm x 286mm
   1920x1080     60.00*+  59.96    59.93
   1680x1050     69.88    59.95    59.88
   1600x1024     60.17
   1400x1050     74.76    70.00    59.98
   1600x900      59.95    59.82
   1280x1024     75.02    60.02
   1440x900      59.89
   1400x900      59.96    59.88
   1280x960      60.00
   1440x810      59.97
   1368x768      59.88    59.85
   1360x768      59.80    59.96
   1280x800      59.99    59.97    59.81    59.91
   1152x864      75.00    75.00    70.00    60.00
   1280x720      60.00    59.99    59.86    59.74
   1024x768      75.05    60.04    75.03    70.07    60.00
   960x720       75.00    60.00
   928x696       75.00    60.05
   896x672       75.05    60.01
   1024x576      59.95    59.96    59.90    59.82
   960x600       59.93    60.00
   832x624       74.55
   960x540       59.96    59.99    59.63    59.82
   800x600       75.00    70.00    65.00    60.00    72.19    75.00    60.32    56.25
   840x525       74.96    69.88    60.01    59.88
   864x486       59.92    59.57
   800x512       60.17
   700x525       74.76    70.06    59.98
   800x450       59.95    59.82
   640x512       75.02    60.02
   720x450       59.89
   700x450       59.96    59.88
   640x480       60.00    75.00    72.81    75.00    59.94
   720x405       59.51    58.99
   720x400       70.08
   684x384       59.88    59.85
   680x384       59.80    59.96
   640x400       59.88    59.98
   576x432       75.00    75.00    70.00    60.06
   640x360       59.86    59.83    59.84    59.32
   512x384       75.03    70.07    60.00
   512x288       60.00    59.92
   416x312       74.66
   480x270       59.63    59.82
   400x300       72.19    75.12    60.32    56.34
   432x243       59.92    59.57
   320x240       72.81    75.00    60.05
   360x202       59.51    59.13
   320x180       59.84    59.32

HDMI-1 disconnected (normal left inverted right x axis y axis)
```

SOS!

---

### Post by CelticWarrior on 2020-01-30
The driver you need is Nvidia 390, that's all. If any issues arise troubleshoot from there, not from the open-source driver.

---

### Post by CatKiller on 2020-01-30
[Another poster had a similar issue](https://ubuntuforums.org/showthread.php?t=2435327) with that class of hardware, and it cleared itself up with a more recent update. Your attempts to "fix" it have made things a lot harder for you. You'll need to undo all the random boot options you've added, and you'll need to reinstall the nvidia driver. The 390 branch is the last that supports that card, as CelticWarrior says.

---

### Post by Yellow Pasque on 2020-01-30
I'm guessing you hit this bug when the newer 5.3 kernel was pushed out to 18.04.x users [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1851162](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1851162)
Anyway, make sure your distro is up-to-date and that you're installing nvidia driver >= 390.116

There's also a newer version of 390 currently in proposed repo (i.e. coming down pipes soon): [https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/390.132-0ubuntu0.18.04.1](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/390.132-0ubuntu0.18.04.1)
Maybe try that if all else fails.

---

### Post by robospark on 2020-01-31
Thanks for the replies guys. Will be trying out the suggestions.

> CelticWarrior[INDENT]                                                        The driver you need is Nvidia 390, that's all. If any issues arise troubleshoot from there, not from the open-source driver.         
[/INDENT]
    

Ok, is it because nouveau could not yet provide a reliable operation of nvidia cards and software rederer message is hence expected?

> 
[CatKiller]("https://ubuntuforums.org/showthread.php?t=2435327")[INDENT]                                                        [Another poster had a similar issue]("https://ubuntuforums.org/showthread.php?t=2435327")  with that class of hardware, and it cleared itself up with a more  recent update. Your attempts to "fix" it have made things a lot harder  for you. You'll need to undo all the random boot options you've added,  and you'll need to reinstall the nvidia driver. The 390 branch is the  last that supports that card, as CelticWarrior says.         
[/INDENT]
    

 Thank you for the link, I added boot options during recent troubleshooting via the grub menu on boot by clicking 'e' which I understand is temporary. Anything there I need to remove still?

> 
Yellow Pasque
I'm guessing you hit this bug when the newer 5.3 kernel was pushed out to 18.04.x users [https://bugs.launchpad.net/ubuntu/+s...0/+bug/1851162]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1851162")Anyway, make sure your distro is up-to-date and that you're installing nvidia driver >= 390.116
There's also a newer version of 390 currently in proposed repo (i.e. coming down pipes soon): [https://launchpad.net/ubuntu/+source...buntu0.18.04.1]("https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/390.132-0ubuntu0.18.04.1")
Maybe try that if all else fails.   


That must be it! Even though I tried to boot up with older 4.x kernel I had it did not have an effect. I guess at that point the video drivers were already botched and switching to older kernel did not have effect without reinstalling the drivers again which I did not try on older kernel. I wonder if I will still get this update or can try it somehow considering I am now on 19.10?

For now I've tried installing the nvidia drivers again:

```

ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
modalias : pci:v000010DEd00001200sv00001462sd00002382bc03sc00i00
vendor   : NVIDIA Corporation
model    : GF114 [GeForce GTX 560 Ti]
driver   : nvidia-driver-390 - distro non-free recommended
driver   : nvidia-340 - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin

sudo apt install nvidia-driver-390

reboot
```

Got greeted with "We are sorry, ksplashqml closed unexpectedly" (full crash log below). Same thing as last time I tried nvidia drivers on 19.10, so no surprises here, at least resolution is good 1920x1080.

"Software Renderer In Use" message still shows in System Tray. 

```
 lspci -k | grep -iEA5 'vga|3d|display'
01:00.0 VGA compatible controller: NVIDIA Corporation GF114 [GeForce GTX 560 Ti] (rev a1)
        Subsystem: Micro-Star International Co., Ltd. [MSI] GF114 [GeForce GTX 560 Ti]
        Kernel driver in use: nvidia
        Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
01:00.1 Audio device: NVIDIA Corporation GF114 HDMI Audio Controller (rev a1)
        Subsystem: Micro-Star International Co., Ltd. [MSI] GF114 HDMI Audio Controller
```

```
glxinfo | grep renderer
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  24 (X_GLXCreateNewContext)
  Value in failed request:  0x0
  Serial number of failed request:  41
  Current serial number in output stream:  42
```

Below could be a hint to the problem? But cannot figure out why 415.27 are listed here, don't recall installing this version, I don't think it even supports my card:
```
dmesg |grep NVRM
[    1.151236] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  390.129  Mon Jul 22 21:10:21 PDT 2019 (using threaded interrupts)
[   27.950245] NVRM: API mismatch: the client has the version 415.27, but
               NVRM: this kernel module has the version 390.129.  Please
               NVRM: make sure that this kernel module and all NVIDIA driver
               NVRM: components have the same version.
```

```
nvidia-smi -a
Failed to initialize NVML: Driver/library version mismatch
```

```
lsmod | grep nvidia
nvidia_uvm            790528  0
nvidia_drm             45056  2
nvidia_modeset       1056768  3 nvidia_drm
nvidia              14680064  84 nvidia_uvm,nvidia_modeset
drm_kms_helper        184320  1 nvidia_drm
drm                   491520  5 drm_kms_helper,nvidia_drm
ipmi_msghandler       102400  2 ipmi_devintf,nvidia
```

```
modinfo nvidia
filename:       /lib/modules/5.3.0-29-generic/updates/dkms/nvidia.ko
alias:          char-major-195-*
version:        390.129
supported:      external
license:        NVIDIA
srcversion:     D7BA57960EA8534340A9A2A
alias:          pci:v000010DEd00000E00sv*sd*bc04sc80i00*
alias:          pci:v000010DEd*sv*sd*bc03sc02i00*
alias:          pci:v000010DEd*sv*sd*bc03sc00i00*
depends:        ipmi_msghandler
retpoline:      Y
name:           nvidia
vermagic:       5.3.0-29-generic SMP mod_unload
parm:           NVreg_Mobile:int
parm:           NVreg_ResmanDebugLevel:int
parm:           NVreg_RmLogonRC:int
parm:           NVreg_ModifyDeviceFiles:int
parm:           NVreg_DeviceFileUID:int
parm:           NVreg_DeviceFileGID:int
parm:           NVreg_DeviceFileMode:int
parm:           NVreg_UpdateMemoryTypes:int
parm:           NVreg_InitializeSystemMemoryAllocations:int
parm:           NVreg_UsePageAttributeTable:int
parm:           NVreg_MapRegistersEarly:int
parm:           NVreg_RegisterForACPIEvents:int
parm:           NVreg_CheckPCIConfigSpace:int
parm:           NVreg_EnablePCIeGen3:int
parm:           NVreg_EnableMSI:int
parm:           NVreg_TCEBypassMode:int
parm:           NVreg_UseThreadedInterrupts:int
parm:           NVreg_EnableStreamMemOPs:int
parm:           NVreg_EnableBacklightHandler:int
parm:           NVreg_RestrictProfilingToAdminUsers:int
parm:           NVreg_EnableUserNUMAManagement:int
parm:           NVreg_EnableIBMNPURelaxedOrderingMode:int
parm:           NVreg_MemoryPoolSize:int
parm:           NVreg_KMallocHeapMaxSize:int
parm:           NVreg_VMallocHeapMaxSize:int
parm:           NVreg_IgnoreMMIOCheck:int
parm:           NVreg_RegistryDwords:charp
parm:           NVreg_RegistryDwordsPerDevice:charp
parm:           NVreg_RmMsg:charp
parm:           NVreg_AssignGpus:charp
```

ksplashqml Developer information below:
```
Application: ksplashqml (ksplashqml), signal: Aborted

 Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".

 [Current thread is 1 (Thread 0x7fbed00bf840 (LWP 2334))]
 

 Thread 4 (Thread 0x7fbecd1bd700 (LWP 2610)):
 #0  __GI___libc_read (nbytes=16, buf=0x7fbecd1bcb30, fd=8) at ../sysdeps/unix/sysv/linux/read.c:26
 #1  __GI___libc_read (fd=8, buf=0x7fbecd1bcb30, nbytes=16) at ../sysdeps/unix/sysv/linux/read.c:24
 #2  0x00007fbed27e563f in ?? () from /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0
 #3  0x00007fbed279d58e in g_main_context_check () from /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0
 #4  0x00007fbed279d9e2 in ?? () from /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0
 #5  0x00007fbed279db73 in g_main_context_iteration () from /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0
 #6  0x00007fbed486d6c3 in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
 #7  0x00007fbed481463b in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
 #8  0x00007fbed464da75 in QThread::exec() () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
 #9  0x00007fbed400a319 in ?? () from /usr/lib/x86_64-linux-gnu/libQt5Qml.so.5
 #10 0x00007fbed464ecc2 in ?? () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
 #11 0x00007fbed3810669 in start_thread (arg=<optimized out>) at pthread_create.c:479
 #12 0x00007fbed42d3323 in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:95
 

 Thread 3 (Thread 0x7fbecdf6b700 (LWP 2341)):
 #0  0x00007fbed42c6c2f in __GI___poll (fds=0x7fbec00029e0, nfds=1, timeout=-1) at ../sysdeps/unix/sysv/linux/poll.c:29
 #1  0x00007fbed279da3e in ?? () from /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0
 #2  0x00007fbed279db73 in g_main_context_iteration () from /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0
 #3  0x00007fbed486d6c3 in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
 #4  0x00007fbed481463b in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
 #5  0x00007fbed464da75 in QThread::exec() () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
 #6  0x00007fbed5123efa in ?? () from /usr/lib/x86_64-linux-gnu/libQt5DBus.so.5
 #7  0x00007fbed464ecc2 in ?? () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
 #8  0x00007fbed3810669 in start_thread (arg=<optimized out>) at pthread_create.c:479
 #9  0x00007fbed42d3323 in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:95
 

 Thread 2 (Thread 0x7fbecf244700 (LWP 2340)):
 #0  0x00007fbed42c6c2f in __GI___poll (fds=0x7fbecf243c68, nfds=1, timeout=-1) at ../sysdeps/unix/sysv/linux/poll.c:29
 #1  0x00007fbed365c917 in ?? () from /usr/lib/x86_64-linux-gnu/libxcb.so.1
 #2  0x00007fbed365e53a in xcb_wait_for_event () from /usr/lib/x86_64-linux-gnu/libxcb.so.1
 #3  0x00007fbecfa0c288 in ?? () from /usr/lib/x86_64-linux-gnu/libQt5XcbQpa.so.5
 #4  0x00007fbed464ecc2 in ?? () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
 #5  0x00007fbed3810669 in start_thread (arg=<optimized out>) at pthread_create.c:479
 #6  0x00007fbed42d3323 in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:95
 

 Thread 1 (Thread 0x7fbed00bf840 (LWP 2334)):
 [KCrash Handler]
 #6  __GI_raise (sig=sig@entry=6) at ../sysdeps/unix/sysv/linux/raise.c:50
 #7  0x00007fbed41d6899 in __GI_abort () at abort.c:79
 #8  0x00007fbed4615a99 in QMessageLogger::fatal(char const*, ...) const () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
 #9  0x00007fbed53ee94d in QSGRenderLoop::handleContextCreationFailure(QQuickWindow*, bool) () from /usr/lib/x86_64-linux-gnu/libQt5Quick.so.5
 #10 0x00007fbed53efa25 in ?? () from /usr/lib/x86_64-linux-gnu/libQt5Quick.so.5
 #11 0x00007fbed53f02ed in ?? () from /usr/lib/x86_64-linux-gnu/libQt5Quick.so.5
 #12 0x00007fbed4c08b3d in QWindow::event(QEvent*) () from /usr/lib/x86_64-linux-gnu/libQt5Gui.so.5
 #13 0x00007fbed546f67f in QQuickWindow::event(QEvent*) () from /usr/lib/x86_64-linux-gnu/libQt5Quick.so.5
 #14 0x00007fbed4815a9a in QCoreApplication::notifyInternal2(QObject*, QEvent*) () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
 #15 0x00007fbed4bff2d6 in QGuiApplicationPrivate::processExposeEvent(QWindowSystemInterfacePrivate::ExposeEvent*) () from /usr/lib/x86_64-linux-gnu/libQt5Gui.so.5
 #16 0x00007fbed4bff504 in QGuiApplicationPrivate::processWindowSystemEvent(QWindowSystemInterfacePrivate::WindowSystemEvent*) () from /usr/lib/x86_64-linux-gnu/libQt5Gui.so.5
 #17 0x00007fbed4bd926b in QWindowSystemInterface::sendWindowSystemEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQt5Gui.so.5
 #18 0x00007fbecfa0d28e in ?? () from /usr/lib/x86_64-linux-gnu/libQt5XcbQpa.so.5
 #19 0x00007fbed279d84d in g_main_context_dispatch () from /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0
 #20 0x00007fbed279dad0 in ?? () from /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0
 #21 0x00007fbed279db73 in g_main_context_iteration () from /usr/lib/x86_64-linux-gnu/libglib-2.0.so.0
 #22 0x00007fbed486d6a5 in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
 #23 0x00007fbed481463b in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
 #24 0x00007fbed481c3a6 in QCoreApplication::exec() () from /usr/lib/x86_64-linux-gnu/libQt5Core.so.5
 #25 0x000055720234e02b in ?? ()
 #26 0x00007fbed41d81e3 in __libc_start_main (main=0x55720234de70, argc=3, argv=0x7ffcdd98b5c8, init=<optimized out>, fini=<optimized out>, rtld_fini=<optimized out>, stack_end=0x7ffcdd98b5b8) at ../csu/libc-start.c:308
 #27 0x000055720234e09e in _start ()
 [Inferior 1 (process 2334) detached]
 



```

---

### Post by robospark on 2020-02-01
Deleted nvidia drivers once again: sudo apt --purge autoremove nvidia*

Rebooted with nouveau. 

Found few errors in the /var/log/nvidia-uninstall.log pointing to some old uninstall listing problematic 415.27 drivers that do not support my card:

```
-> Unable to restore symbolic link /usr/lib/x86_64-linux-gnu/vdpau/libvdpau_nvidia.so -> libvdpau_nvidia.so.415.27 (File exists).
-> Unable to restore symbolic link /usr/lib/i386-linux-gnu/libcuda.so.1 -> libcuda.so.415.27 (File exists).
```

Removed those links and the installed latest drivers for my card afresh: sudo apt install nvidia-driver-390

Rebooted and viola, splash crash went away. "NVRM: API mismatch: the client has the version 415.27" message disappeared from dmesg too.

Software Renderer in Use message still showed up though. Clicked on the icon and realised that it was set to Software mode, probably because of the issues. Set it to Auto, rebooted and message is gone.

Looking better now!

---

