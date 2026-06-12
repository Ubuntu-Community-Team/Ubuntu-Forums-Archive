---
title: "ATA: abnormal status 0x80"
date: 2009-03-16
forum: Hardware
---

### Post by bobp on 2009-03-16
I'm having trouble with a system running Ubuntu 7.04. The most visible symptom is that occasionally the system just stops, with no useful diagnostic that I can see, although the system is currently sealed inside a pressure vessel and I have only ethernet comms to it. There could also be a temperature-related factor, although that seems to be unlikely.

I do, however, see the following messages in syslog at times:

```
Mar 15 23:12:12 bcam kernel: [   32.849755] ATA: abnormal status 0x80 on port 0x000101f7
Mar 15 23:12:12 bcam kernel: [   32.860746] ATA: abnormal status 0x80 on port 0x000101f7
Mar 15 23:12:12 bcam kernel: [   32.871744] ATA: abnormal status 0x80 on port 0x000101f7
```

occasionally followed by:
```
Mar 14 15:26:11 bcam kernel: [   91.348985] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Mar 14 15:26:11 bcam kernel: [   91.348999] ata1.00: cmd 25/00:08:a7:01:b4/00:00:1b:00:00/e0 tag 0 cdb 0x0 data 4096 in
Mar 14 15:26:11 bcam kernel: [   91.349002]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Mar 14 15:26:11 bcam kernel: [   91.349028] ata1: soft resetting port
```

or
```
Mar 15 21:18:12 bcam kernel: [   42.056018] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Mar 15 21:18:12 bcam kernel: [   42.056025] ata1.01: (BMDMA stat 0x65)
Mar 15 21:18:12 bcam kernel: [   42.056035] ata1.01: cmd 25/00:08:80:58:1c/00:00:1d:00:00/f0 tag 0 cdb 0x0 data 4096 in
Mar 15 21:18:12 bcam kernel: [   42.056038]          res 7f/7f:7f:7f:7f:7f/01:3f:7f:7f:7f/7f Emask 0x2 (HSM violation)
Mar 15 21:18:12 bcam kernel: [   42.056065] ata1: soft resetting port
```

Can anybody point me in a useful direction? I'd really appreciate any advice.

In case it is useful here is dmesg output:

```
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Tue Feb 12 05:41:34 UTC 2008 (Ubuntu 2.6.20-16.35-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e8000 size: 0000000000018000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003dde0000 end: 000000003dee0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003dee0000 size: 0000000000003000 end: 000000003dee3000 type: 4
[    0.000000] copy_e820_map() start: 000000003dee3000 size: 000000000000d000 end: 000000003def0000 type: 3
[    0.000000] copy_e820_map() start: 000000003def0000 size: 0000000000010000 end: 000000003df00000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000001400000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003dee0000 (usable)
[    0.000000]  BIOS-e820: 000000003dee0000 - 000000003dee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003dee3000 - 000000003def0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003def0000 - 000000003df00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 94MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f3b60
[    0.000000] Entering add_active_range(0, 0, 253664) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   253664
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   253664
[    0.000000] On node 0 totalpages: 253664
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 189 pages used for memmap
[    0.000000]   HighMem zone: 24099 pages, LIFO batch:3
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 Lip-AT                                ) @ 0x000f5be0
[    0.000000] ACPI: RSDT (v001 Lip-AT AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3dee3040
[    0.000000] ACPI: FADT (v001 Lip-AT AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3dee30c0
[    0.000000] ACPI: MADT (v001 Lip-AT AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3dee68c0
[    0.000000] ACPI: DSDT (v001 LIP-AT AWRDACPI 0x00001000 MSFT 0x03000000) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:13 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3df00000:c0d00000)
[    0.000000] Detected 999.918 MHz processor.
[   17.675085] Built 1 zonelists.  Total pages: 251683
[   17.675092] Kernel command line: root=UUID=3834a17a-94c2-41b4-8089-03af2efbb2dc ro quiet splash
[   17.675359] mapped APIC to ffffd000 (fee00000)
[   17.675363] mapped IOAPIC to ffffc000 (fec00000)
[   17.675368] Enabling fast FPU save and restore... done.
[   17.675373] Enabling unmasked SIMD FPU exception support... done.
[   17.675385] Initializing CPU#0
[   17.675462] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   17.676968] Console: colour VGA+ 80x25
[   17.677430] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   17.678187] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   17.726303] Memory: 994812k/1014656k available (1993k kernel code, 19212k reserved, 900k data, 328k init, 97152k highmem)
[   17.726320] virtual kernel memory layout:
[   17.726322]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   17.726324]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   17.726327]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   17.726329]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   17.726331]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   17.726333]       .data : 0xc02f24c9 - 0xc03d36d4   ( 900 kB)
[   17.726335]       .text : 0xc0100000 - 0xc02f24c9   (1993 kB)
[   17.726341] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   17.803460] Calibrating delay using timer specific routine.. 2001.33 BogoMIPS (lpj=4002675)
[   17.803529] Security Framework v1.0.0 initialized
[   17.803545] SELinux:  Disabled at boot.
[   17.803572] Mount-cache hash table entries: 512
[   17.803814] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000000 00000000 00000000
[   17.803833] CPU: L1 I cache: 32K, L1 D cache: 32K
[   17.803837] CPU: L2 cache: 512K
[   17.803843] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002040 00000000 00000000 00000000
[   17.803861] Compat vDSO mapped to ffffe000.
[   17.803870] Remapping vsyscall page to ffffe000
[   17.803888] Checking 'hlt' instruction... OK.
[   17.819639] SMP alternatives: switching to UP code
[   17.819981] Freeing SMP alternatives: 11k freed
[   17.820292] Early unpacking initramfs... done
[   18.366702] ACPI: Core revision 20060707
[   18.371771] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   18.415178] CPU0: Intel(R) Celeron(R) M processor         1.00GHz stepping 08
[   18.415211] Total of 1 processors activated (2001.33 BogoMIPS).
[   18.415342] ENABLING IO-APIC IRQs
[   18.415552] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   18.559473] Brought up 1 CPUs
[   18.559822] Booting paravirtualized kernel on bare hardware
[   18.559916] Time: 12:16:13  Date: 02/16/109
[   18.559963] NET: Registered protocol family 16
[   18.560093] EISA bus registered
[   18.560101] ACPI: bus type pci registered
[   18.583566] PCI: PCI BIOS revision 2.10 entry at 0xfad20, last bus=2
[   18.583570] PCI: Using configuration type 1
[   18.583573] Setting up standard PCI resources
[   18.599140] ACPI: Interpreter enabled
[   18.599146] ACPI: Using IOAPIC for interrupt routing
[   18.599939] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   18.599948] PCI: Probing PCI hardware (bus 00)
[   18.600389] Boot video device is 0000:00:02.0
[   18.600679] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[   18.600681] * this clock source is slow. If you are sure your timer does not have
[   18.600684] * this bug, please use "acpi_pm_good" to disable the workaround
[   18.600728] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[   18.600733] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[   18.601083] PCI: Transparent bridge - 0000:00:1e.0
[   18.601114] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   18.615927] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   18.619291] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   18.619680] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   18.620049] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 *7 9 10 11 12 14 15)
[   18.620420] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   18.620788] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   18.621167] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 *15)
[   18.621540] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   18.621914] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   18.622124] Linux Plug and Play Support v0.97 (c) Adam Belay
[   18.622141] pnp: PnP ACPI init
[   18.624960] pnp: PnP ACPI: found 9 devices
[   18.624968] PnPBIOS: Disabled by ACPI PNP
[   18.625046] PCI: Using ACPI for IRQ routing
[   18.625051] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   18.637343] NET: Registered protocol family 8
[   18.637347] NET: Registered protocol family 20
[   18.637908] pnp: 00:06: ioport range 0x400-0x4bf could not be reserved
[   18.638341] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[   18.638359] PCI: Bridge: 0000:00:01.0
[   18.638362]   IO window: disabled.
[   18.638367]   MEM window: disabled.
[   18.638371]   PREFETCH window: disabled.
[   18.638377] PCI: Bridge: 0000:00:1e.0
[   18.638381]   IO window: d000-dfff
[   18.638388]   MEM window: ec000000-ec0fffff
[   18.638393]   PREFETCH window: 48000000-480fffff
[   18.638411] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   18.638448] NET: Registered protocol family 2
[   18.675506] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   18.675691] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   18.677409] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   18.678380] TCP: Hash tables configured (established 131072 bind 65536)
[   18.678386] TCP reno registered
[   18.687660] checking if image is initramfs... it is
[   19.771372] Freeing initrd memory: 6779k freed
[   19.772008] audit: initializing netlink socket (disabled)
[   19.772029] audit(1237205774.140:1): initialized
[   19.772140] highmem bounce pool size: 64 pages
[   19.772237] VFS: Disk quotas dquot_6.5.1
[   19.772266] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   19.772340] io scheduler noop registered
[   19.772345] io scheduler anticipatory registered
[   19.772349] io scheduler deadline registered
[   19.772365] io scheduler cfq registered (default)
[   19.772769] isapnp: Scanning for PnP cards...
[   20.126660] isapnp: No Plug & Play device found
[   20.186262] Real Time Clock Driver v1.12ac
[   20.186341] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   20.187713] mice: PS/2 mouse device common for all mice
[   20.188524] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   20.188877] input: Macintosh mouse button emulation as /class/input/input0
[   20.188933] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   20.188939] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   20.189267] PNP: No PS/2 controller found. Probing ports directly.
[   20.192783] serio: i8042 KBD port at 0x60,0x64 irq 1
[   20.192793] serio: i8042 AUX port at 0x60,0x64 irq 12
[   20.192989] EISA: Probing bus 0 at eisa.0
[   20.193031] EISA: Detected 0 cards.
[   20.223170] TCP cubic registered
[   20.223182] NET: Registered protocol family 1
[   20.223217] Using IPI No-Shortcut mode
[   20.223299] ACPI: (supports S0 S1<6>Time: tsc clocksource has been installed.
[   20.223329]  S3 S4 S5)
[   20.223387]   Magic number: 1:175:279
[   20.223425]   hash matches device ttyy7
[   20.223443]   hash matches device ttyva
[   20.223573]   hash matches device tty16
[   20.223786] Freeing unused kernel memory: 328k freed
[   21.568921] Capability LSM initialized
[   21.629026] ACPI: Processor [CPU0] (supports 2 throttling states)
[   22.349636] usbcore: registered new interface driver usbfs
[   22.349672] usbcore: registered new interface driver hub
[   22.349707] usbcore: registered new device driver usb
[   22.351115] USB Universal Host Controller Interface driver v3.0
[   22.351186] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[   22.351207] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   22.351213] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   22.351441] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   22.351475] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000eb00
[   22.351631] usb usb1: configuration #1 chosen from 1 choice
[   22.351672] hub 1-0:1.0: USB hub found
[   22.351681] hub 1-0:1.0: 2 ports detected
[   22.455461] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 17
[   22.455478] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   22.455484] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   22.455524] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   22.455554] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000ed00
[   22.455693] usb usb2: configuration #1 chosen from 1 choice
[   22.455730] hub 2-0:1.0: USB hub found
[   22.455739] hub 2-0:1.0: 2 ports detected
[   22.509108] Intel(R) PRO/1000 Network Driver - version 7.3.15-k2-NAPI
[   22.509115] Copyright (c) 1999-2006 Intel Corporation.
[   22.559458] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   22.559474] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   22.559481] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   22.559514] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   22.559544] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000e800
[   22.559678] usb usb3: configuration #1 chosen from 1 choice
[   22.559719] hub 3-0:1.0: USB hub found
[   22.559728] hub 3-0:1.0: 2 ports detected
[   22.663774] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 19
[   22.663794] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   22.663800] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   22.663842] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   22.663884] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   22.663899] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xec180000
[   22.667782] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   22.667899] usb usb4: configuration #1 chosen from 1 choice
[   22.667938] hub 4-0:1.0: USB hub found
[   22.667948] hub 4-0:1.0: 6 ports detected
[   22.780746] SCSI subsystem initialized
[   22.791288] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 21 (level, low) -> IRQ 20
[   22.807858] libata version 2.20 loaded.
[   23.057315] e1000: 0000:02:00.0: e1000_probe: (PCI:33MHz:32-bit) 00:20:9d:11:51:20
[   23.229451] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[   23.232966] ata_piix 0000:00:1f.1: version 2.10ac1
[   23.232985] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[   23.233007] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   23.233075] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001f000 irq 14
[   23.233114] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001f008 irq 15
[   23.233136] scsi0 : ata_piix
[   23.462399] ata1.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
[   23.462406] ata1.00: ATA-8: WDC WD2500BEVE-00WZT0, 01.01A01, max UDMA/100
[   23.462411] ata1.00: 488397168 sectors, multi 16: LBA48 
[   23.512870] ata1.01: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
[   23.512877] ata1.01: ATA-8: WDC WD2500BEVE-00WZT0, 01.01A01, max UDMA/100
[   23.512882] ata1.01: 488397168 sectors, multi 16: LBA48 
[   23.512891] ata1.00: limited to UDMA/33 due to 40-wire cable
[   23.512897] ata1.01: limited to UDMA/33 due to 40-wire cable
[   23.520253] ata1.00: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
[   23.520258] ata1.00: configured for UDMA/33
[   23.527730] ata1.01: ata_hpa_resize 1: sectors = 488397168, hpa_sectors = 488397168
[   23.527734] ata1.01: configured for UDMA/33
[   23.527747] scsi1 : ata_piix
[   23.528046] ata2: port disabled. ignoring.
[   23.528221] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVE-0 01.0 PQ: 0 ANSI: 5
[   23.528711] scsi 0:0:1:0: Direct-Access     ATA      WDC WD2500BEVE-0 01.0 PQ: 0 ANSI: 5
[   23.546136] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[   23.546168] sda: Write Protect is off
[   23.546172] sda: Mode Sense: 00 3a 00 00
[   23.546194] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.546278] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[   23.546291] sda: Write Protect is off
[   23.546295] sda: Mode Sense: 00 3a 00 00
[   23.546316] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.546322]  sda: sda1 sda2 < sda5 >
[   23.574087] sd 0:0:0:0: Attached scsi disk sda
[   23.574322] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[   23.574339] sdb: Write Protect is off
[   23.574342] sdb: Mode Sense: 00 3a 00 00
[   23.574363] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.574424] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[   23.574437] sdb: Write Protect is off
[   23.574441] sdb: Mode Sense: 00 3a 00 00
[   23.574461] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.574466]  sdb: sdb1
[   23.577546] sd 0:0:1:0: Attached scsi disk sdb
[   23.584886] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   23.585077] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   23.976621] Attempting manual resume
[   23.976627] swsusp: Resume From Partition 8:5
[   23.976630] PM: Checking swsusp image.
[   23.976994] PM: Resume from disk failed.
[   24.002278] EXT3-fs: INFO: recovery required on readonly filesystem.
[   24.002285] EXT3-fs: write access will be enabled during recovery.
[   24.271125] kjournald starting.  Commit interval 5 seconds
[   24.271145] EXT3-fs: recovery complete.
[   24.282148] EXT3-fs: mounted filesystem with ordered data mode.
[   34.976437] e1000: eth1: e1000_watchdog: NIC Link is Up 1000 Mbps Full Duplex
[   35.472647] NET: Registered protocol family 10
[   35.472795] lo: Disabled Privacy Extensions
[   37.138660] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   37.164880] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   37.547914] Linux agpgart interface v0.102 (c) Dave Jones
[   37.944651] agpgart: Detected an Intel 855 Chipset.
[   37.944800] agpgart: Detected 32636K stolen memory.
[   37.952541] agpgart: AGP aperture is 128M @ 0xe0000000
[   37.963920] iTCO_vendor_support: vendor-support=0
[   37.965884] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   37.966010] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460)
[   37.966065] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   38.043716] intel_rng: FWH not detected
[   38.534958] input: PC Speaker as /class/input/input1
[   39.106152] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 21
[   39.106187] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   39.418596] intel8x0_measure_ac97_clock: measured 55468 usecs
[   39.418601] intel8x0: clocking to 48000
[   39.616336] fuse init (API version 7.8)
[   39.695810] lp: driver loaded but no devices found
[   39.737279] Adding 2931820k swap on /dev/disk/by-uuid/2b95e50f-daec-4cab-84e4-39d6e4545a92.  Priority:-1 extents:1 across:2931820k
[   39.933180] EXT3 FS on sda1, internal journal
[   40.419953] EXT2-fs warning: mounting unchecked fs, running e2fsck is recommended
[   42.156790] NET: Registered protocol family 17
[   46.270324] eth1: no IPv6 routers present
[   46.542585] input: Power Button (FF) as /class/input/input2
[   46.548573] ACPI: Power Button (FF) [PWRF]
[   46.611877] input: Power Button (CM) as /class/input/input3
[   46.617768] ACPI: Power Button (CM) [PWRB]
[   46.638151] Using specific hotkey driver
[   46.673625] No dock devices found.
[   46.754268] ibm_acpi: ec object not found
[   46.855676] pcc_acpi: loading...
[   51.376584] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   51.376592] apm: overridden by ACPI.
[   54.240760] [drm] Initialized drm 1.1.0 20060810
[   54.248761] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   54.252503] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   54.252819] PCI: Enabling device 0000:00:02.1 (0000 -> 0002)
[   54.256452] [drm] Initialized i915 1.6.0 20060119 on minor 1
[   56.531568] e1000: eth1: e1000_watchdog: NIC Link is Up 1000 Mbps Full Duplex

```

and...
```
camera@bcam:~$ sudo hdparm -I /dev/sda1

/dev/sda1:

ATA device, with non-removable media
	Model Number:       WDC WD2500BEVE-00WZT0                   
	Serial Number:      WD-WXEZ07E75031
	Firmware Revision:  01.01A01
Standards:
	Supported: 8 7 6 5 
	Likely used: 8
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:  268435455
	LBA48  user addressable sectors:  488397168
	device size with M = 1024*1024:      238475 MBytes
	device size with M = 1000*1000:      250059 MBytes (250 GB)
Capabilities:
	LBA, IORDY(can be disabled)
	Standby timer values: spec'd by Standard, with device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
	Advanced power management level: unknown setting (0x0080)
	Recommended acoustic management value: 128, current value: 254
	DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2 udma3 udma4 udma5 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	    	Security Mode feature set
	   *	Power Management feature set
	   *	Write cache
	   *	Look-ahead
	   *	Host Protected Area feature set
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	NOP cmd
	   *	DOWNLOAD_MICROCODE
	   *	Advanced Power Management feature set
	   *	SET_MAX security extension
	    	Automatic Acoustic Management feature set
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	   *	General Purpose Logging feature set
	   *	64-bit World wide name
	   *	IDLE_IMMEDIATE with UNLOAD
	   *	Segmented DOWNLOAD_MICROCODE
	   *	SMART Command Transport (SCT) feature set
	   *	SCT Long Sector Access (AC1)
	   *	SCT LBA Segment Access (AC2)
	   *	SCT Error Recovery Control (AC3)
	   *	SCT Features Control (AC4)
	   *	SCT Data Tables (AC5)
	    	unknown 206[13]
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
	not	frozen
	not	expired: security count
	not	supported: enhanced erase
	92min for SECURITY ERASE UNIT. 
HW reset results:
	CBLID- below Vih
	Device num = 0 determined by the jumper
Checksum: correct
```

---

