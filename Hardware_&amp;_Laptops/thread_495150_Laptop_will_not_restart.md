---
title: "Laptop will not restart"
date: 2007-07-07
forum: Hardware &amp; Laptops
---

### Post by whayong on 2007-07-07
Hi all.  I've come to terms that my laptop will refuse to restart when selecting the "restart" option in the shutdown menu.  kerry_s however suggested I post /var/log/dmesg so I can try and figure out what's going on.  So here it is, and hopefully someone can help.

```
[    0.000000] Linux version 2.6.20-16-lowlatency (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP PREEMPT Thu Jun 7 20:23:03 UTC 2007 (Ubuntu Unofficial)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009e800 end: 000000000009e800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009e800 size: 0000000000001800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000c0000 size: 000000000000c000 end: 00000000000cc000 type: 2
[    0.000000] copy_e820_map() start: 00000000000d8000 size: 0000000000028000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 0000000017bf0000 end: 0000000017cf0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 0000000017cf0000 size: 000000000000c000 end: 0000000017cfc000 type: 3
[    0.000000] copy_e820_map() start: 0000000017cfc000 size: 0000000000004000 end: 0000000017d00000 type: 4
[    0.000000] copy_e820_map() start: 0000000017d00000 size: 0000000000180000 end: 0000000017e80000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 0000000017e80000 size: 0000000000180000 end: 0000000018000000 type: 2
[    0.000000] copy_e820_map() start: 00000000ff800000 size: 0000000000400000 end: 00000000ffc00000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff00000 size: 0000000000100000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
[    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000c0000 - 00000000000cc000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000017cf0000 (usable)
[    0.000000]  BIOS-e820: 0000000017cf0000 - 0000000017cfc000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000017cfc000 - 0000000017d00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000017d00000 - 0000000017e80000 (usable)
[    0.000000]  BIOS-e820: 0000000017e80000 - 0000000018000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 382MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 97920) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    97920
[    0.000000]   HighMem     97920 ->    97920
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    97920
[    0.000000] On node 0 totalpages: 97920
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 733 pages used for memmap
[    0.000000]   Normal zone: 93091 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 SONY                                  ) @ 0x000f6c60
[    0.000000] ACPI: RSDT (v001 SONY   U2       0x20020812 PTL  0x00000000) @ 0x17cf7ea3
[    0.000000] ACPI: FADT (v002   SONY       U2 0x20020812 PTL  0x01000000) @ 0x17cfbf54
[    0.000000] ACPI: BOOT (v001   SONY       U2 0x20020812 PTL  0x00000001) @ 0x17cfbfd8
[    0.000000] ACPI: DSDT (v001   SONY       U2 0x20020812 PTL  0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 18000000:e7800000)
[    0.000000] Detected 794.981 MHz processor.
[    7.849205] Built 1 zonelists.  Total pages: 97155
[    7.849215] Kernel command line: root=UUID=8d922f38-56fa-4b3c-b074-920c3af1e6d4 ro
[    7.849678] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    7.849702] mapped APIC to ffffd000 (0130b000)
[    7.849712] Enabling fast FPU save and restore... done.
[    7.849719] Enabling unmasked SIMD FPU exception support... done.
[    7.849749] Initializing CPU#0
[    7.849863] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    7.851919] Console: colour VGA+ 80x25
[    7.855748] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    7.856848] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    7.887695] Memory: 377228k/391680k available (2019k kernel code, 13856k reserved, 902k data, 328k init, 0k highmem)
[    7.887815] virtual kernel memory layout:
[    7.887818]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[    7.887822]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    7.887826]     vmalloc : 0xd8800000 - 0xff7fe000   ( 623 MB)
[    7.887829]     lowmem  : 0xc0000000 - 0xd7e80000   ( 382 MB)
[    7.887833]       .init : 0xc03e1000 - 0xc0433000   ( 328 kB)
[    7.887836]       .data : 0xc02f8c85 - 0xc03da6d4   ( 902 kB)
[    7.887840]       .text : 0xc0100000 - 0xc02f8c85   (2019 kB)
[    7.888327] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    7.947840] Calibrating delay using timer specific routine.. 1590.79 BogoMIPS (lpj=795399)
[    7.948095] Security Framework v1.0.0 initialized
[    7.948179] SELinux:  Disabled at boot.
[    7.948287] Mount-cache hash table entries: 512
[    7.948689] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[    7.948716] CPU: L1 I cache: 16K, L1 D cache: 16K
[    7.948812] CPU: L2 cache: 512K
[    7.948884] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[    7.948910] Compat vDSO mapped to ffffe000.
[    7.948977] Remapping vsyscall page to ffffe000
[    7.949055] Checking 'hlt' instruction... OK.
[    7.953036] SMP alternatives: switching to UP code
[    7.953345] Freeing SMP alternatives: 9k freed
[    7.953730] Early unpacking initramfs... done
[    8.663506] ACPI: Core revision 20060707
[    8.664990] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[    8.675279] CPU0: Intel(R) Pentium(R) III Mobile CPU       800MHz stepping 01
[    8.675425] SMP motherboard not detected.
[    8.675486] Local APIC not detected. Using dummy APIC emulation.
[    8.675694] Brought up 1 CPUs
[    8.676521] Booting paravirtualized kernel on bare hardware
[    8.676777] Time:  3:51:37  Date: 06/07/107
[    8.676954] NET: Registered protocol family 16
[    8.677327] EISA bus registered
[    8.677398] ACPI: bus type pci registered
[    8.679359] PCI: PCI BIOS revision 2.10 entry at 0xfd9b0, last bus=1
[    8.679427] PCI: Using configuration type 1
[    8.679489] Setting up standard PCI resources
[    8.694534] ACPI: Interpreter enabled
[    8.694617] ACPI: Using PIC for interrupt routing
[    8.695718] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    8.695796] PCI: Probing PCI hardware (bus 00)
[    8.699079] Boot video device is 0000:00:02.0
[    8.699227] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    8.699298] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[    8.699976] PCI: Firmware left 0000:01:08.0 e100 interrupts enabled, disabling
[    8.700147] PCI: Transparent bridge - 0000:00:1e.0
[    8.700313] PCI: Bus #02 (-#05) is hidden behind transparent bridge #01 (-#01) (try 'pci=assign-busses')
[    8.700403] Please report the result to linux-kernel to fix this permanently
[    8.700495] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    8.704688] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB_._PRT]
[    8.714326] ACPI: PCI Interrupt Link [LNKA] (IRQs *9)
[    8.715146] ACPI: PCI Interrupt Link [LNKB] (IRQs *9)
[    8.715955] ACPI: PCI Interrupt Link [LNKC] (IRQs 9) *0
[    8.716775] ACPI: PCI Interrupt Link [LNKD] (IRQs *9)
[    8.717563] ACPI: PCI Interrupt Link [LNKE] (IRQs *9)
[    8.718265] ACPI: PCI Interrupt Link [LNKF] (IRQs 9) *0, disabled.
[    8.719026] ACPI: PCI Interrupt Link [LNKG] (IRQs 9) *0, disabled.
[    8.719884] ACPI: PCI Interrupt Link [LNKH] (IRQs *9)
[    8.720318] Linux Plug and Play Support v0.97 (c) Adam Belay
[    8.720404] pnp: PnP ACPI init
[    8.728577] pnp: PnP ACPI: found 10 devices
[    8.728676] PnPBIOS: Disabled by ACPI PNP
[    8.728900] PCI: Using ACPI for IRQ routing
[    8.728964] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    8.732632] NET: Registered protocol family 8
[    8.732695] NET: Registered protocol family 20
[    8.734447] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[    8.734537] PCI: Bus 2, cardbus bridge: 0000:01:02.0
[    8.734601]   IO window: 00002400-000024ff
[    8.734678]   IO window: 00002800-000028ff
[    8.734743]   PREFETCH window: 20000000-23ffffff
[    8.734808]   MEM window: 24000000-27ffffff
[    8.734870] PCI: Bridge: 0000:00:1e.0
[    8.734932]   IO window: 2000-2fff
[    8.734995]   MEM window: f4100000-f41fffff
[    8.735059]   PREFETCH window: 20000000-23ffffff
[    8.735139] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    8.735763] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 9
[    8.735831] PCI: setting IRQ 9 as level-triggered
[    8.735838] ACPI: PCI Interrupt 0000:01:02.0[A] -> Link [LNKC] -> GSI 9 (level, low) -> IRQ 9
[    8.736067] NET: Registered protocol family 2
[    8.745834] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    8.746190] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[    8.747113] TCP bind hash table entries: 8192 (order: 4, 98304 bytes)
[    8.747652] TCP: Hash tables configured (established 16384 bind 8192)
[    8.747728] TCP reno registered
[    8.750972] checking if image is initramfs... it is
[   10.105120] Freeing initrd memory: 6639k freed
[   10.105817] Simple Boot Flag at 0x36 set to 0x1
[   10.106505] audit: initializing netlink socket (disabled)
[   10.106620] audit(1183780298.546:1): initialized
[   10.107140] VFS: Disk quotas dquot_6.5.1
[   10.107315] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   10.107549] io scheduler noop registered
[   10.107647] io scheduler anticipatory registered
[   10.107742] io scheduler deadline registered
[   10.107867] io scheduler cfq registered (default)
[   10.108737] isapnp: Scanning for PnP cards...
[   10.465708] isapnp: No Plug & Play device found
[   10.533304] Real Time Clock Driver v1.12ac
[   10.533499] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   10.535223] mice: PS/2 mouse device common for all mice
[   10.536831] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   10.537349] input: Macintosh mouse button emulation as /class/input/input0
[   10.537511] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   10.537582] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   10.538144] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUE] at 0x60,0x64 irq 1,12
[   10.540694] serio: i8042 KBD port at 0x60,0x64 irq 1
[   10.540923] serio: i8042 AUX port at 0x60,0x64 irq 12
[   10.541190] EISA: Probing bus 0 at eisa.0
[   10.541280] Cannot allocate resource for EISA slot 1
[   10.541346] Cannot allocate resource for EISA slot 2
[   10.541441] EISA: Detected 0 cards.
[   10.566608] input: AT Translated Set 2 keyboard as /class/input/input1
[   10.571732] TCP cubic registered
[   10.571814] NET: Registered protocol family 1
[   10.571929] Using IPI No-Shortcut mode
[   10.572084] Time: tsc clocksource has been installed.
[   10.572202] ACPI: (supports S0 S3 S4 S5)
[   10.572518]   Magic number: 15:185:866
[   10.572748]   hash matches device ptyw4
[   10.574189] Freeing unused kernel memory: 328k freed
[   11.043919] Capability LSM initialized
[   11.137982] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   11.138193] ACPI: Processor [CPU0] (supports 8 throttling states)
[   11.145347] ACPI: Thermal Zone [ATF0] (37 C)
[   12.594719] SCSI subsystem initialized
[   12.618561] libata version 2.20 loaded.
[   12.625031] ata_piix 0000:00:1f.1: version 2.10ac1
[   12.625102] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   12.625249] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011800 irq 14
[   12.625422] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011808 irq 15
[   12.625559] scsi0 : ata_piix
[   12.665096] usbcore: registered new interface driver usbfs
[   12.665226] usbcore: registered new interface driver hub
[   12.665353] usbcore: registered new device driver usb
[   12.669090] USB Universal Host Controller Interface driver v3.0
[   12.779897] ata1.00: ata_hpa_resize 1: sectors = 39070080, hpa_sectors = 39070080
[   12.779999] ata1.00: ATA-5: HITACHI_DK23CA-20, 00H1A0A3, max UDMA/100
[   12.780066] ata1.00: 39070080 sectors, multi 16: LBA 
[   12.783790] ata1.00: ata_hpa_resize 1: sectors = 39070080, hpa_sectors = 39070080
[   12.783878] ata1.00: configured for UDMA/100
[   12.783958] scsi1 : ata_piix
[   12.784185] ata2: port disabled. ignoring.
[   12.785496] scsi 0:0:0:0: Direct-Access     ATA      HITACHI_DK23CA-2 00H1 PQ: 0 ANSI: 5
[   12.795956] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[   12.796039] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 9 (level, low) -> IRQ 9
[   12.796211] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   12.796220] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[   12.796646] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[   12.796767] uhci_hcd 0000:00:1f.2: irq 9, io base 0x00001820
[   12.797123] usb usb1: configuration #1 chosen from 1 choice
[   12.797251] hub 1-0:1.0: USB hub found
[   12.797330] hub 1-0:1.0: 2 ports detected
[   12.852022] ieee1394: Initialized config rom entry `ip1394'
[   12.898468] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 9
[   12.898550] ACPI: PCI Interrupt 0000:00:1f.4[C] -> Link [LNKH] -> GSI 9 (level, low) -> IRQ 9
[   12.898716] PCI: Setting latency timer of device 0000:00:1f.4 to 64
[   12.898726] uhci_hcd 0000:00:1f.4: UHCI Host Controller
[   12.898840] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
[   12.898958] uhci_hcd 0000:00:1f.4: irq 9, io base 0x00001880
[   12.899249] usb usb2: configuration #1 chosen from 1 choice
[   12.899374] hub 2-0:1.0: USB hub found
[   12.899460] hub 2-0:1.0: 2 ports detected
[   12.953849] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI
[   12.953931] e100: Copyright(c) 1999-2006 Intel Corporation
[   13.002531] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 9
[   13.002612] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
[   13.053240] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[9]  MMIO=[f4101000-f41017ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   13.165480] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 9
[   13.165564] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [LNKE] -> GSI 9 (level, low) -> IRQ 9
[   13.189886] e100: eth0: e100_probe: addr 0xf4100000, irq 9, MAC addr 08:00:46:45:71:8D
[   13.206394] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   13.295365] SCSI device sda: 39070080 512-byte hdwr sectors (20004 MB)
[   13.296332] sda: Write Protect is off
[   13.296398] sda: Mode Sense: 00 3a 00 00
[   13.296948] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.297175] SCSI device sda: 39070080 512-byte hdwr sectors (20004 MB)
[   13.297266] sda: Write Protect is off
[   13.297343] sda: Mode Sense: 00 3a 00 00
[   13.297391] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.297482]  sda: sda1 sda2 < sda5 >
[   13.362753] sd 0:0:0:0: Attached scsi disk sda
[   13.374780] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   13.383162] usb 2-1: configuration #1 chosen from 1 choice
[   13.483009] usbcore: registered new interface driver libusual
[   13.494677] Initializing USB Mass Storage driver...
[   13.494942] scsi2 : SCSI emulation for USB Mass Storage devices
[   13.495154] usbcore: registered new interface driver usb-storage
[   13.495225] USB Mass Storage support registered.
[   13.495581] usb-storage: device found at 2
[   13.495588] usb-storage: waiting for device to settle before scanning
[    5.692000] Time: acpi_pm clocksource has been installed.
[    5.812000] Attempting manual resume
[    5.812000] swsusp: Resume From Partition 8:5
[    5.812000] PM: Checking swsusp image.
[    5.813000] PM: Resume from disk failed.
[    5.900000] kjournald starting.  Commit interval 5 seconds
[    5.900000] EXT3-fs: mounted filesystem with ordered data mode.
[    6.455000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0800460300f662b9]
[   10.641000] usb-storage: device scan complete
[   10.643000] scsi 2:0:0:0: Direct-Access     Sony     MSC-U03          1.00 PQ: 0 ANSI: 0 CCS
[   10.652000] SCSI device sdb: 253696 512-byte hdwr sectors (130 MB)
[   10.654000] sdb: Write Protect is off
[   10.654000] sdb: Mode Sense: 00 6a 10 00
[   10.654000] sdb: assuming drive cache: write through
[   10.664000] SCSI device sdb: 253696 512-byte hdwr sectors (130 MB)
[   10.666000] sdb: Write Protect is off
[   10.666000] sdb: Mode Sense: 00 6a 10 00
[   10.666000] sdb: assuming drive cache: write through
[   10.666000]  sdb: sdb1
[   10.883000] sd 2:0:0:0: Attached scsi removable disk sdb
[   10.883000] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   20.347000] NET: Registered protocol family 17
[   22.543000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   22.577000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   22.596000] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
[   23.053000] intel_rng: FWH not detected
[   23.163000] iTCO_vendor_support: vendor-support=0
[   23.175000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   23.175000] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   23.176000] iTCO_wdt: No card detected
[   23.619000] Linux agpgart interface v0.102 (c) Dave Jones
[   23.641000] agpgart: Detected an Intel i815 Chipset.
[   23.654000] agpgart: AGP aperture is 64M @ 0xf8000000
[   23.660000] input: PC Speaker as /class/input/input2
[   24.286000] Yenta: CardBus bridge found at 0000:01:02.0 [104d:80f2]
[   24.435000] Yenta: ISA IRQ mask 0x0cb8, PCI irq 9
[   24.435000] Socket status: 30000006
[   24.435000] Yenta: Raising subordinate bus# of parent bus (#01) from #01 to #05
[   24.435000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   24.435000] cs: IO port probe 0x2000-0x2fff: clean.
[   24.436000] pcmcia: parent PCI bridge Memory window: 0xf4100000 - 0xf41fffff
[   24.436000] pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x23ffffff
[   24.439000] ieee80211_crypt: registered algorithm 'NULL'
[   24.446000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   24.446000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   24.504000] input: PS/2 Mouse as /class/input/input3
[   24.524000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input4
[   24.534000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   24.534000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   24.535000] PCI: Enabling device 0000:01:05.0 (0110 -> 0112)
[   24.536000] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 9
[   24.536000] ACPI: PCI Interrupt 0000:01:05.0[A] -> Link [LNKF] -> GSI 9 (level, low) -> IRQ 9
[   24.536000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   26.075000] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
[   26.076000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
[   26.076000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[   26.076000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   26.141000] cs: IO port probe 0x100-0x3af: clean.
[   26.143000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   26.144000] cs: IO port probe 0x820-0x8ff: clean.
[   26.145000] cs: IO port probe 0xc00-0xcf7: clean.
[   26.146000] cs: IO port probe 0xa00-0xaff: clean.
[   26.385000] intel8x0_measure_ac97_clock: measured 50605 usecs
[   26.385000] intel8x0: clocking to 48000
[   26.772000] fuse init (API version 7.8)
[   26.878000] lp: driver loaded but no devices found
[   26.993000] Adding 859436k swap on /dev/disk/by-uuid/5874548a-3c20-4db6-9b40-fb97ecece10f.  Priority:-1 extents:1 across:859436k
[   27.185000] EXT3 FS on sda1, internal journal
```

---

### Post by whayong on 2007-07-07
Cancel that!  Thank you to kerry_s who suggested I add "pci=routeirq" to my boot line.

Everything works now!

---

