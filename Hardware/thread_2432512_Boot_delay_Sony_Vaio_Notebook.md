---
title: "Boot delay Sony Vaio Notebook"
date: 2019-12-03
forum: Hardware
---

### Post by dragutsan-alexandr on 2019-12-03
Hello, dear locals!


I've noticed a boot delay on my Vaio notebook:
```
$ systemd-analyze 
Startup finished in 36.235s (kernel) + 11.818s (userspace) = 48.054s
graphical.target reached after 11.803s in userspace

```

And I think this may be the cause:
```

$ dmesg -T | grep keyboard
[Tue Dec  3 20:08:23 2019] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[Tue Dec  3 20:08:59 2019] sony_laptop: handle 0x014b: keyboard backlight setup already done for 0x0143
[Tue Dec  3 20:08:59 2019] sony_laptop: couldn't set up keyboard backlight function (-16)

```


Just for detalization - keyboard backlight works fine. 


expanded dmesg log with some trace info goes here(260 lines):
```

[Tue Dec  3 20:08:23 2019] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[Tue Dec  3 20:08:23 2019] Write protecting the kernel read-only data: 20480k
[Tue Dec  3 20:08:23 2019] Freeing unused kernel image memory: 2008K
[Tue Dec  3 20:08:23 2019] Freeing unused kernel image memory: 1880K
[Tue Dec  3 20:08:23 2019] x86/mm: Checked W+X mappings: passed, no W+X pages found.
[Tue Dec  3 20:08:23 2019] x86/mm: Checking user space page tables
[Tue Dec  3 20:08:23 2019] x86/mm: Checked W+X mappings: passed, no W+X pages found.
[Tue Dec  3 20:08:23 2019] ahci 0000:00:1f.2: version 3.0
[Tue Dec  3 20:08:23 2019] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[Tue Dec  3 20:08:23 2019] r8169 0000:05:00.0: can't disable ASPM; OS doesn't have ASPM control
[Tue Dec  3 20:08:23 2019] ahci 0000:00:1f.2: SSS flag set, parallel bus scan disabled
[Tue Dec  3 20:08:23 2019] r8169 0000:05:00.0 eth0: RTL8168e/8111e at 0x        (ptrval), f0:bf:97:e4:e0:c2, XID 0c200000 IRQ 31
[Tue Dec  3 20:08:23 2019] r8169 0000:05:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[Tue Dec  3 20:08:23 2019] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x11 impl RAID mode
[Tue Dec  3 20:08:23 2019] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part apst 
[Tue Dec  3 20:08:23 2019] r8169 0000:05:00.0 enp5s0: renamed from eth0
[Tue Dec  3 20:08:23 2019] scsi host0: ahci
[Tue Dec  3 20:08:23 2019] scsi host1: ahci
[Tue Dec  3 20:08:23 2019] scsi host2: ahci
[Tue Dec  3 20:08:23 2019] scsi host3: ahci
[Tue Dec  3 20:08:23 2019] scsi host4: ahci
[Tue Dec  3 20:08:23 2019] scsi host5: ahci
[Tue Dec  3 20:08:23 2019] ata1: SATA max UDMA/133 abar m2048@0xc9407000 port 0xc9407100 irq 30
[Tue Dec  3 20:08:23 2019] ata2: DUMMY
[Tue Dec  3 20:08:23 2019] ata3: DUMMY
[Tue Dec  3 20:08:23 2019] ata4: DUMMY
[Tue Dec  3 20:08:23 2019] ata5: SATA max UDMA/133 abar m2048@0xc9407000 port 0xc9407300 irq 30
[Tue Dec  3 20:08:23 2019] ata6: DUMMY
[Tue Dec  3 20:08:23 2019] [drm] radeon kernel modesetting enabled.
[Tue Dec  3 20:08:23 2019] [drm] Memory usable by graphics device = 2048M
[Tue Dec  3 20:08:23 2019] checking generic (b0000000 7f0000) vs hw (b0000000 10000000)
[Tue Dec  3 20:08:23 2019] fb: switching to inteldrmfb from VESA VGA
[Tue Dec  3 20:08:23 2019] Console: switching 
[Tue Dec  3 20:08:23 2019] vga_switcheroo: detected switching method \_SB_.PCI0.GFX0.ATPX handle
[Tue Dec  3 20:08:23 2019] to colour dummy device 80x25
[Tue Dec  3 20:08:23 2019] [drm] Replacing VGA console driver
[Tue Dec  3 20:08:23 2019] ATPX version 1, functions 0x00000032
[Tue Dec  3 20:08:23 2019] radeon 0000:01:00.0: enabling device (0000 -> 0003)
[Tue Dec  3 20:08:23 2019] [drm] initializing kernel modesetting (TURKS 0x1002:0x6741 0x104D:0x907B 0x00).
[Tue Dec  3 20:08:23 2019] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[Tue Dec  3 20:08:23 2019] [drm] Driver supports precise vblank timestamp query.
[Tue Dec  3 20:08:23 2019] vga_switcheroo: enabled
[Tue Dec  3 20:08:23 2019] usb 1-1: new high-speed USB device number 2 using ehci-pci
[Tue Dec  3 20:08:23 2019] ATOM BIOS: Sony
[Tue Dec  3 20:08:23 2019] radeon 0000:01:00.0: VRAM: 1024M 0x0000000000000000 - 0x000000003FFFFFFF (1024M used)
[Tue Dec  3 20:08:23 2019] radeon 0000:01:00.0: GTT: 1024M 0x0000000040000000 - 0x000000007FFFFFFF
[Tue Dec  3 20:08:23 2019] [drm] Detected VRAM RAM=1024M, BAR=256M
[Tue Dec  3 20:08:23 2019] [drm] RAM width 128bits DDR
[Tue Dec  3 20:08:23 2019] i915 0000:00:02.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=none:owns=io+mem
[Tue Dec  3 20:08:23 2019] radeon 0000:01:00.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=none:owns=none
[Tue Dec  3 20:08:23 2019] [TTM] Zone  kernel: Available graphics memory: 4040758 kiB
[Tue Dec  3 20:08:23 2019] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[Tue Dec  3 20:08:23 2019] [TTM] Initializing pool allocator
[Tue Dec  3 20:08:23 2019] [TTM] Initializing DMA pool allocator
[Tue Dec  3 20:08:23 2019] [drm] radeon: 1024M of VRAM memory ready
[Tue Dec  3 20:08:23 2019] [drm] radeon: 1024M of GTT memory ready.
[Tue Dec  3 20:08:23 2019] [drm] Loading TURKS Microcode
[Tue Dec  3 20:08:23 2019] [drm] Internal thermal controller without fan control
[Tue Dec  3 20:08:23 2019] [drm] radeon: dpm initialized
[Tue Dec  3 20:08:23 2019] [drm] GART: num cpu pages 262144, num gpu pages 262144
[Tue Dec  3 20:08:23 2019] [drm] PCIE gen 2 link speeds already enabled
[Tue Dec  3 20:08:23 2019] ------------[ cut here ]------------
[Tue Dec  3 20:08:23 2019] Could not determine valid watermarks for inherited state
[Tue Dec  3 20:08:23 2019] WARNING: CPU: 1 PID: 196 at /build/linux-E6MDAa/linux-4.15.0/drivers/gpu/drm/i915/intel_display.c:14537 intel_modeset_init+0xfcf/0x1010 [i915]
[Tue Dec  3 20:08:23 2019] Modules linked in: fjes(-) radeon(+) i915(+) rtsx_pci_sdmmc ttm i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops psmouse ahci r8169 libahci drm mii rtsx_pci video
[Tue Dec  3 20:08:23 2019] CPU: 1 PID: 196 Comm: systemd-udevd Not tainted 4.15.0-72-generic #81-Ubuntu
[Tue Dec  3 20:08:23 2019] Hardware name: Sony Corporation VPCSE2S1E/VAIO, BIOS R2087H4 06/15/2012
[Tue Dec  3 20:08:23 2019] RIP: 0010:intel_modeset_init+0xfcf/0x1010 [i915]
[Tue Dec  3 20:08:23 2019] RSP: 0018:fffface5c10b39b0 EFLAGS: 00010286
[Tue Dec  3 20:08:23 2019] RAX: 0000000000000000 RBX: ffff90e1caac8000 RCX: ffffffff96863a28
[Tue Dec  3 20:08:23 2019] RDX: 0000000000000001 RSI: 0000000000000082 RDI: 0000000000000247
[Tue Dec  3 20:08:23 2019] RBP: fffface5c10b3a40 R08: 00000000000002b8 R09: 0000000000000004
[Tue Dec  3 20:08:23 2019] R10: 0000000000000040 R11: 0000000000000001 R12: ffff90e1cb1ec000
[Tue Dec  3 20:08:23 2019] R13: ffff90e1cb1ecc00 R14: 00000000ffffffea R15: ffff90e1caac8358
[Tue Dec  3 20:08:23 2019] FS:  00007fb80d62b680(0000) GS:ffff90e1dfa40000(0000) knlGS:0000000000000000
[Tue Dec  3 20:08:23 2019] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[Tue Dec  3 20:08:23 2019] CR2: 00005561fe478668 CR3: 000000024b006003 CR4: 00000000000606e0
[Tue Dec  3 20:08:23 2019] Call Trace:
[Tue Dec  3 20:08:23 2019]  i915_driver_load+0xa73/0xe60 [i915]
[Tue Dec  3 20:08:23 2019]  i915_pci_probe+0x42/0x70 [i915]
[Tue Dec  3 20:08:23 2019]  local_pci_probe+0x47/0xa0
[Tue Dec  3 20:08:23 2019]  pci_device_probe+0x10e/0x1c0
[Tue Dec  3 20:08:23 2019]  driver_probe_device+0x30c/0x490
[Tue Dec  3 20:08:23 2019]  __driver_attach+0xcc/0xf0
[Tue Dec  3 20:08:23 2019]  ? driver_probe_device+0x490/0x490
[Tue Dec  3 20:08:23 2019]  bus_for_each_dev+0x70/0xc0
[Tue Dec  3 20:08:23 2019]  driver_attach+0x1e/0x20
[Tue Dec  3 20:08:23 2019]  bus_add_driver+0x1c7/0x270
[Tue Dec  3 20:08:23 2019]  ? 0xffffffffc03f6000
[Tue Dec  3 20:08:23 2019]  driver_register+0x60/0xe0
[Tue Dec  3 20:08:23 2019]  ? 0xffffffffc03f6000
[Tue Dec  3 20:08:23 2019]  __pci_register_driver+0x5a/0x60
[Tue Dec  3 20:08:23 2019]  i915_init+0x5c/0x5f [i915]
[Tue Dec  3 20:08:23 2019]  do_one_initcall+0x52/0x19f
[Tue Dec  3 20:08:23 2019]  ? __vunmap+0x8e/0xc0
[Tue Dec  3 20:08:23 2019]  ? _cond_resched+0x19/0x40
[Tue Dec  3 20:08:23 2019]  ? kmem_cache_alloc_trace+0xa6/0x1b0
[Tue Dec  3 20:08:23 2019]  ? do_init_module+0x27/0x213
[Tue Dec  3 20:08:23 2019]  do_init_module+0x5f/0x213
[Tue Dec  3 20:08:23 2019]  load_module+0x16bc/0x1f10
[Tue Dec  3 20:08:23 2019]  ? ima_post_read_file+0x96/0xa0
[Tue Dec  3 20:08:23 2019]  SYSC_finit_module+0xfc/0x120
[Tue Dec  3 20:08:23 2019]  ? SYSC_finit_module+0xfc/0x120
[Tue Dec  3 20:08:23 2019]  SyS_finit_module+0xe/0x10
[Tue Dec  3 20:08:23 2019]  do_syscall_64+0x73/0x130
[Tue Dec  3 20:08:23 2019]  entry_SYSCALL_64_after_hwframe+0x3d/0xa2
[Tue Dec  3 20:08:23 2019] RIP: 0033:0x7fb80d135839
[Tue Dec  3 20:08:23 2019] RSP: 002b:00007ffed5525888 EFLAGS: 00000246 ORIG_RAX: 0000000000000139
[Tue Dec  3 20:08:23 2019] RAX: ffffffffffffffda RBX: 00005561fe41b360 RCX: 00007fb80d135839
[Tue Dec  3 20:08:23 2019] RDX: 0000000000000000 RSI: 00007fb80ce14145 RDI: 0000000000000012
[Tue Dec  3 20:08:23 2019] RBP: 00007fb80ce14145 R08: 0000000000000000 R09: 00007ffed55259a0
[Tue Dec  3 20:08:23 2019] R10: 0000000000000012 R11: 0000000000000246 R12: 0000000000000000
[Tue Dec  3 20:08:23 2019] R13: 00005561fe438350 R14: 0000000000020000 R15: 00005561fe41b360
[Tue Dec  3 20:08:23 2019] Code: e9 46 fc ff ff 48 c7 c6 d7 4d 38 c0 48 c7 c7 2f 41 38 c0 e8 94 78 19 d5 0f 0b e9 73 fe ff ff 48 c7 c7 b0 a5 39 c0 e8 81 78 19 d5 <0f> 0b e9 4b fe ff ff 48 c7 c6 e4 4d 38 c0 48 c7 c7 2f 41 38 c0 
[Tue Dec  3 20:08:23 2019] ---[ end trace 5ba2d0bed80ae83e ]---
[Tue Dec  3 20:08:23 2019] usb 2-1: new high-speed USB device number 2 using ehci-pci
[Tue Dec  3 20:08:23 2019] [drm] PCIE GART of 1024M enabled (table at 0x0000000000162000).
[Tue Dec  3 20:08:23 2019] radeon 0000:01:00.0: WB enabled
[Tue Dec  3 20:08:23 2019] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0x        (ptrval)
[Tue Dec  3 20:08:23 2019] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000040000c0c and cpu addr 0x        (ptrval)
[Tue Dec  3 20:08:23 2019] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000072118 and cpu addr 0x        (ptrval)
[Tue Dec  3 20:08:23 2019] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[Tue Dec  3 20:08:23 2019] [drm] Driver supports precise vblank timestamp query.
[Tue Dec  3 20:08:23 2019] radeon 0000:01:00.0: radeon: MSI limited to 32-bit
[Tue Dec  3 20:08:23 2019] radeon 0000:01:00.0: radeon: using MSI.
[Tue Dec  3 20:08:23 2019] [drm] radeon: irq initialized.
[Tue Dec  3 20:08:23 2019] [drm] ring test on 0 succeeded in 3 usecs
[Tue Dec  3 20:08:23 2019] [drm] ring test on 3 succeeded in 8 usecs
[Tue Dec  3 20:08:24 2019] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[Tue Dec  3 20:08:24 2019] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[Tue Dec  3 20:08:24 2019] hub 2-1:1.0: USB hub found
[Tue Dec  3 20:08:24 2019] hub 2-1:1.0: 8 ports detected
[Tue Dec  3 20:08:24 2019] [drm] ring test on 5 succeeded in 2 usecs
[Tue Dec  3 20:08:24 2019] [drm] UVD initialized successfully.
[Tue Dec  3 20:08:24 2019] [drm] ib test on ring 0 succeeded in 0 usecs
[Tue Dec  3 20:08:24 2019] [drm] ib test on ring 3 succeeded in 0 usecs
[Tue Dec  3 20:08:24 2019] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[Tue Dec  3 20:08:24 2019] ata1.00: supports DRM functions and may not be fully accessible
[Tue Dec  3 20:08:24 2019] ata1.00: disabling queued TRIM support
[Tue Dec  3 20:08:24 2019] ata1.00: ATA-9: Samsung SSD 850 EVO 250GB, EMT02B6Q, max UDMA/133
[Tue Dec  3 20:08:24 2019] ata1.00: 488397168 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[Tue Dec  3 20:08:24 2019] ata1.00: supports DRM functions and may not be fully accessible
[Tue Dec  3 20:08:24 2019] ata1.00: disabling queued TRIM support
[Tue Dec  3 20:08:24 2019] ata1.00: configured for UDMA/133
[Tue Dec  3 20:08:24 2019] scsi 0:0:0:0: Direct-Access     ATA      Samsung SSD 850  2B6Q PQ: 0 ANSI: 5
[Tue Dec  3 20:08:24 2019] sd 0:0:0:0: Attached scsi generic sg0 type 0
[Tue Dec  3 20:08:24 2019] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/233 GiB)
[Tue Dec  3 20:08:24 2019] sd 0:0:0:0: [sda] Write Protect is off
[Tue Dec  3 20:08:24 2019] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[Tue Dec  3 20:08:24 2019] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[Tue Dec  3 20:08:24 2019]  sda: sda1 sda2 < sda5 >
[Tue Dec  3 20:08:24 2019] sd 0:0:0:0: [sda] supports TCG Opal
[Tue Dec  3 20:08:24 2019] sd 0:0:0:0: [sda] Attached SCSI disk
[Tue Dec  3 20:08:24 2019] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[Tue Dec  3 20:08:24 2019] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[Tue Dec  3 20:08:24 2019] hub 1-1:1.0: USB hub found
[Tue Dec  3 20:08:24 2019] hub 1-1:1.0: 6 ports detected
[Tue Dec  3 20:08:24 2019] random: fast init done
[Tue Dec  3 20:08:24 2019] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[Tue Dec  3 20:08:24 2019] ata5.00: ATAPI: MATSHITADVD-RAM UJ8A2AS, 1.20, max UDMA/100
[Tue Dec  3 20:08:24 2019] ata5.00: configured for UDMA/100
[Tue Dec  3 20:08:24 2019] scsi 4:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ8A2AS  1.20 PQ: 0 ANSI: 5
[Tue Dec  3 20:08:24 2019] random: systemd-udevd: uninitialized urandom read (16 bytes read)
[Tue Dec  3 20:08:24 2019] random: systemd-udevd: uninitialized urandom read (16 bytes read)
[Tue Dec  3 20:08:24 2019] random: systemd-udevd: uninitialized urandom read (16 bytes read)
[Tue Dec  3 20:08:24 2019] usb 1-1.3: new high-speed USB device number 3 using ehci-pci
[Tue Dec  3 20:08:24 2019] psmouse serio1: synaptics: queried max coordinates: x [..5508], y [..4550]
[Tue Dec  3 20:08:24 2019] sr 4:0:0:0: [sr0] scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[Tue Dec  3 20:08:24 2019] cdrom: Uniform CD-ROM driver Revision: 3.20
[Tue Dec  3 20:08:24 2019] sr 4:0:0:0: Attached scsi CD-ROM sr0
[Tue Dec  3 20:08:24 2019] sr 4:0:0:0: Attached scsi generic sg1 type 5
[Tue Dec  3 20:08:24 2019] tsc: Refined TSC clocksource calibration: 2494.333 MHz
[Tue Dec  3 20:08:24 2019] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x23f45085418, max_idle_ns: 440795285711 ns
[Tue Dec  3 20:08:24 2019] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04771/0xa40000/0xa0400/0x0, board id: 0, fw id: 886330
[Tue Dec  3 20:08:24 2019] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input4
[Tue Dec  3 20:08:24 2019] usb 1-1.3: New USB device found, idVendor=05ca, idProduct=18c0
[Tue Dec  3 20:08:24 2019] usb 1-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[Tue Dec  3 20:08:24 2019] usb 1-1.3: Product: USB2.0 Camera
[Tue Dec  3 20:08:24 2019] usb 1-1.3: Manufacturer: Ricoh Company Ltd.
[Tue Dec  3 20:08:24 2019] [drm] ib test on ring 5 succeeded
[Tue Dec  3 20:08:24 2019] [drm] Radeon Display Connectors
[Tue Dec  3 20:08:24 2019] [drm] Initialized radeon 2.50.0 20080528 for 0000:01:00.0 on minor 1
[Tue Dec  3 20:08:24 2019] [drm] Initialized i915 1.6.0 20171023 for 0000:00:02.0 on minor 0
[Tue Dec  3 20:08:24 2019] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[Tue Dec  3 20:08:24 2019] ACPI: Video Device [PEGP] (multi-head: yes  rom: no  post: no)
[Tue Dec  3 20:08:24 2019] acpi LNXVIDEO:02: registered as cooling_device4
[Tue Dec  3 20:08:24 2019] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:26/LNXVIDEO:00/input/input5
[Tue Dec  3 20:08:24 2019] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[Tue Dec  3 20:08:24 2019] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[Tue Dec  3 20:08:24 2019] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[Tue Dec  3 20:08:24 2019] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[Tue Dec  3 20:08:24 2019] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[Tue Dec  3 20:08:24 2019] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[Tue Dec  3 20:08:24 2019] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[Tue Dec  3 20:08:24 2019] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[Tue Dec  3 20:08:24 2019] acpi device:29: registered as cooling_device5
[Tue Dec  3 20:08:24 2019] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:09/input/input6
[Tue Dec  3 20:08:24 2019] fbcon: inteldrmfb (fb0) is primary device
[Tue Dec  3 20:08:24 2019] Console: switching to colour frame buffer device 240x67
[Tue Dec  3 20:08:24 2019] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[Tue Dec  3 20:08:25 2019] clocksource: Switched to clocksource tsc
[Tue Dec  3 20:08:29 2019] random: crng init done
[Tue Dec  3 20:08:29 2019] random: 7 urandom warning(s) missed due to ratelimiting
[Tue Dec  3 20:08:31 2019] [drm] PCIE gen 2 link speeds already enabled
[Tue Dec  3 20:08:31 2019] [drm] PCIE GART of 1024M enabled (table at 0x0000000000162000).
[Tue Dec  3 20:08:31 2019] radeon 0000:01:00.0: WB enabled
[Tue Dec  3 20:08:31 2019] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0x00000000832a5f28
[Tue Dec  3 20:08:31 2019] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000040000c0c and cpu addr 0x00000000636f53cd
[Tue Dec  3 20:08:31 2019] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000072118 and cpu addr 0x0000000073eb6cc5
[Tue Dec  3 20:08:31 2019] [drm] ring test on 0 succeeded in 2 usecs
[Tue Dec  3 20:08:31 2019] [drm] ring test on 3 succeeded in 8 usecs
[Tue Dec  3 20:08:31 2019] [drm] ring test on 5 succeeded in 2 usecs
[Tue Dec  3 20:08:31 2019] [drm] UVD initialized successfully.
[Tue Dec  3 20:08:31 2019] [drm] ib test on ring 0 succeeded in 0 usecs
[Tue Dec  3 20:08:31 2019] [drm] ib test on ring 3 succeeded in 0 usecs
[Tue Dec  3 20:08:31 2019] [drm] ib test on ring 5 succeeded
[Tue Dec  3 20:08:58 2019] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[Tue Dec  3 20:08:58 2019] ip_tables: (C) 2000-2006 Netfilter Core Team
[Tue Dec  3 20:08:58 2019] systemd[1]: systemd 237 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ +LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD -IDN2 +IDN -PCRE2 default-hierarchy=hybrid)
[Tue Dec  3 20:08:58 2019] systemd[1]: Detected architecture x86-64.
[Tue Dec  3 20:08:58 2019] systemd[1]: Set hostname to <Station>.
[Tue Dec  3 20:08:58 2019] systemd[392]: /lib/systemd/system-generators/netplan failed with exit status 1.
[Tue Dec  3 20:08:58 2019] systemd[1]: Created slice System Slice.
[Tue Dec  3 20:08:58 2019] systemd[1]: Listening on udev Control Socket.
[Tue Dec  3 20:08:58 2019] systemd[1]: Listening on fsck to fsckd communication Socket.
[Tue Dec  3 20:08:58 2019] systemd[1]: Listening on Journal Socket (/dev/log).
[Tue Dec  3 20:08:58 2019] systemd[1]: Listening on Journal Audit Socket.
[Tue Dec  3 20:08:58 2019] systemd[1]: Listening on udev Kernel Socket.
[Tue Dec  3 20:08:58 2019] ashmem_linux: loading out-of-tree module taints kernel.
[Tue Dec  3 20:08:58 2019] ashmem_linux: module verification failed: signature and/or required key missing - tainting kernel
[Tue Dec  3 20:08:58 2019] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[Tue Dec  3 20:08:58 2019] lp: driver loaded but no devices found
[Tue Dec  3 20:08:58 2019] ppdev: user-space parallel port driver
[Tue Dec  3 20:08:58 2019] systemd-journald[428]: Received request to flush runtime journal from PID 1
[Tue Dec  3 20:08:58 2019] ACPI: watchdog: Skipping WDAT on this system because it uses RTC SRAM
[Tue Dec  3 20:08:58 2019] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x0000000000000400-0x000000000000047F (\PMIO) (20170831/utaddress-247)
[Tue Dec  3 20:08:58 2019] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x0000000000000400-0x000000000000047F (\PMIO) (20170831/utaddress-247)
[Tue Dec  3 20:08:58 2019] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[Tue Dec  3 20:08:58 2019] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
[Tue Dec  3 20:08:58 2019] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
[Tue Dec  3 20:08:58 2019] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x000000000000055F (\_SB.PCI0.PEG0.PEGP.GPIO) (20170831/utaddress-247)
[Tue Dec  3 20:08:58 2019] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x000000000000055F (\_SB.PCI0.PEG0.PEGP.GPIO) (20170831/utaddress-247)
[Tue Dec  3 20:08:58 2019] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[Tue Dec  3 20:08:58 2019] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
[Tue Dec  3 20:08:58 2019] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
[Tue Dec  3 20:08:58 2019] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x000000000000055F (\_SB.PCI0.PEG0.PEGP.GPIO) (20170831/utaddress-247)
[Tue Dec  3 20:08:58 2019] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x000000000000055F (\_SB.PCI0.PEG0.PEGP.GPIO) (20170831/utaddress-247)
[Tue Dec  3 20:08:58 2019] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[Tue Dec  3 20:08:58 2019] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
[Tue Dec  3 20:08:58 2019] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
[Tue Dec  3 20:08:58 2019] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x000000000000055F (\_SB.PCI0.PEG0.PEGP.GPIO) (20170831/utaddress-247)
[Tue Dec  3 20:08:58 2019] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x000000000000055F (\_SB.PCI0.PEG0.PEGP.GPIO) (20170831/utaddress-247)
[Tue Dec  3 20:08:58 2019] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[Tue Dec  3 20:08:58 2019] lpc_ich: Resource conflict(s) found affecting gpio_ich
[Tue Dec  3 20:08:58 2019] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[Tue Dec  3 20:08:59 2019] input: Sony Vaio Keys as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/SNY5001:00/input/input7
[Tue Dec  3 20:08:59 2019] input: Sony Vaio Jogdial as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/SNY5001:00/input/input8
[Tue Dec  3 20:08:59 2019] sony_laptop: handle 0x014b: keyboard backlight setup already done for 0x0143
[Tue Dec  3 20:08:59 2019] sony_laptop: couldn't set up keyboard backlight function (-16)
[Tue Dec  3 20:08:59 2019] sony_laptop: SNC setup done.

```

Would be nice to switch some check(s) off during boot process!
And to be able to turn on my keyboard backlight after boot. 

4.15.0-72-generic #81-Ubuntu SMP
Ubuntu 18.04.3 LTS

Just for detalization:
I have an additional gaming keyboard with backlight, but this problem persists both with and without it. This is definitely a problem related to integrated (native notebook) keyboard.

---

### Post by Autodave on 2019-12-03
I do not understand most of that, but let me get this correct: you are saying that this machine boots up in less than one minute?  If so, that sounds good to me.

---

### Post by him610 on 2019-12-03
You were on the right track originally.
Please show the results between the code tags:
```

systemd-analyze critical-chain
systemd-analyze blame

```

---

### Post by dragutsan-alexandr on 2019-12-14
Thank you for your attention:
```

@Station:~$ systemd-analyze && systemd-analyze blame
Startup finished in 36.572s (kernel) + 11.879s (userspace) = 48.452s
graphical.target reached after 11.867s in userspace
          7.746s NetworkManager-wait-online.service
          5.366s plymouth-quit-wait.service
          3.240s dev-sda1.device
          1.722s snapd.service
          1.659s apparmor.service
          1.127s NetworkManager.service



```

[B]2 [[COLOR=#000000]Autodave[/COLOR]]("https://ubuntuforums.org/member.php?u=917298")
[/B]
Or perhaps I do require excessive boot speed from this system, not sure...

---

### Post by Autodave on 2019-12-15
Keep in mind that if you had Win 10 on it before, Win10 does NOT shutdown: it merely hibernates.  That is why Win10 seems to boot quickly.  If you were to have disable the "fast boot" on Win10, you would find that it would take at least a couple minutes to boot.  My system here is quite fast.  I have fast boot disabled due to dual booting.  My Xubuntu boots in about 20 seconds, my Win10 takes almost a minute to the desktop and another 15 secs to a usable desktop.  Both OSes are running off of SSDs.

---

