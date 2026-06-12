---
title: "Hard Drive Problem"
date: 2008-11-26
forum: General Help
---

### Post by Sipheren on 2008-11-26
Hi,

I have 2 drives that are both HFS formatted.

One will always mount with read/write access but the other only does sometimes. Its really annoying and I don't understand why it would sometimes and then the next time I turn on the system its read only.

Does anyone have any idea why this would happen?

Running on Hardy

---

### Post by __Ryan__ on 2008-11-26
If the drive detects errors it might mount readonly the next time. 

Check your entries in **/etc/fstab**, it should give some insight in what is going on. 

Also you may want to check the kernel logs by running:

```
dmesg
```

and look for any errors that have occurred during the boot process.

---

### Post by Sipheren on 2008-11-27
I ran dmesg straight after I booted into Ubuntu, last boot I had write support this time I don't.

```
[   25.493103] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   25.493197] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[   25.493272] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[   25.504458] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   25.504553] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   25.504646] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[   25.504738] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   25.504831] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   25.504924] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 *14 15)
[   25.505017] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   25.505111] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   25.505195] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  A3, should be A2 [20070126]
[   25.505202] Linux Plug and Play Support v0.97 (c) Adam Belay
[   25.505220] pnp: PnP ACPI init
[   25.505225] ACPI: bus type pnp registered
[   25.507356] pnp: PnP ACPI: found 15 devices
[   25.507357] ACPI: ACPI bus type pnp unregistered
[   25.507360] PnPBIOS: Disabled by ACPI PNP
[   25.507491] PCI: Using ACPI for IRQ routing
[   25.507492] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   25.531603] NET: Registered protocol family 8
[   25.531605] NET: Registered protocol family 20
[   25.531636] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[   25.531641] hpet0: 4 64-bit timers, 14318180 Hz
[   25.532662] AppArmor: AppArmor Filesystem Enabled
[   25.535520] Time: tsc clocksource has been installed.
[   25.535527] Switched to high resolution mode on CPU 0
[   25.535598] Switched to high resolution mode on CPU 1
[   25.548517] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[   25.548526] system 00:06: ioport range 0x290-0x29f has been reserved
[   25.548531] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[   25.548534] system 00:07: ioport range 0x800-0x87f has been reserved
[   25.548537] system 00:07: ioport range 0x500-0x57f has been reserved
[   25.548540] system 00:07: iomem range 0xfed08000-0xfed08fff has been reserved
[   25.548547] system 00:07: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   25.548549] system 00:07: iomem range 0xfed20000-0xfed3ffff has been reserved
[   25.548551] system 00:07: iomem range 0xfed50000-0xfed8ffff has been reserved
[   25.548556] system 00:0a: iomem range 0xffc00000-0xffefffff has been reserved
[   25.548560] system 00:0c: iomem range 0xfec00000-0xfec00fff has been reserved
[   25.548562] system 00:0c: iomem range 0xfee00000-0xfee00fff could not be reserved
[   25.548565] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
[   25.548569] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[   25.548571] system 00:0e: iomem range 0xc0000-0xcffff could not be reserved
[   25.548573] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[   25.548575] system 00:0e: iomem range 0x100000-0xcfffffff could not be reserved
[   25.548576] system 00:0e: iomem range 0x0-0x0 could not be reserved
[   25.578824] PCI: Bridge: 0000:00:01.0
[   25.578826]   IO window: c000-cfff
[   25.578828]   MEM window: fa000000-fe9fffff
[   25.578830]   PREFETCH window: d0000000-dfffffff
[   25.578832] PCI: Bridge: 0000:00:1c.0
[   25.578833]   IO window: disabled.
[   25.578836]   MEM window: disabled.
[   25.578839]   PREFETCH window: f8f00000-f8ffffff
[   25.578842] PCI: Bridge: 0000:00:1c.5
[   25.578844]   IO window: d000-dfff
[   25.578847]   MEM window: fea00000-feafffff
[   25.578849]   PREFETCH window: disabled.
[   25.578854] PCI: Bridge: 0000:00:1e.0
[   25.578855]   IO window: e000-efff
[   25.578859]   MEM window: feb00000-febfffff
[   25.578861]   PREFETCH window: disabled.
[   25.578871] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   25.578875] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   25.578887] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[   25.578891] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   25.578904] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 16 (level, low) -> IRQ 16
[   25.578907] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   25.578914] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   25.578921] NET: Registered protocol family 2
[   25.616503] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   25.616645] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   25.616923] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   25.617054] TCP: Hash tables configured (established 131072 bind 65536)
[   25.617056] TCP reno registered
[   25.628545] checking if image is initramfs... it is
[   26.079976] Freeing initrd memory: 7327k freed
[   26.080490] audit: initializing netlink socket (disabled)
[   26.080499] audit(1227817994.072:1): initialized
[   26.080689] highmem bounce pool size: 64 pages
[   26.081907] VFS: Disk quotas dquot_6.5.1
[   26.081954] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   26.082038] io scheduler noop registered
[   26.082040] io scheduler anticipatory registered
[   26.082041] io scheduler deadline registered
[   26.082048] io scheduler cfq registered (default)
[   26.082157] Boot video device is 0000:01:00.0
[   26.082226] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   26.082250] assign_interrupt_mode Found MSI capability
[   26.082270] Allocate Port Service[0000:00:01.0:pcie00]
[   26.082318] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   26.082349] assign_interrupt_mode Found MSI capability
[   26.082374] Allocate Port Service[0000:00:1c.0:pcie00]
[   26.082393] Allocate Port Service[0000:00:1c.0:pcie02]
[   26.082450] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   26.082481] assign_interrupt_mode Found MSI capability
[   26.082505] Allocate Port Service[0000:00:1c.5:pcie00]
[   26.082524] Allocate Port Service[0000:00:1c.5:pcie02]
[   26.082679] isapnp: Scanning for PnP cards...
[   26.435565] isapnp: No Plug & Play device found
[   26.451385] Real Time Clock Driver v1.12ac
[   26.451507] hpet_resources: 0xfed00000 is busy
[   26.451533] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   26.451629] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   26.452042] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   26.452484] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   26.452526] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   26.452610] PNP: No PS/2 controller found. Probing ports directly.
[   26.455281] serio: i8042 KBD port at 0x60,0x64 irq 1
[   26.455284] serio: i8042 AUX port at 0x60,0x64 irq 12
[   26.475090] mice: PS/2 mouse device common for all mice
[   26.475156] EISA: Probing bus 0 at eisa.0
[   26.475178] EISA: Detected 0 cards.
[   26.475180] cpuidle: using governor ladder
[   26.475181] cpuidle: using governor menu
[   26.475237] NET: Registered protocol family 1
[   26.475255] Using IPI No-Shortcut mode
[   26.475274] registered taskstats version 1
[   26.475343]   Magic number: 0:213:600
[   26.475354]   hash matches device ptyd4
[   26.475375] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   26.475377] EDD information not available.
[   26.475493] Freeing unused kernel memory: 368k freed
[   26.475509] Write protecting the kernel read-only data: 801k
[   27.619812] fuse init (API version 7.9)
[   27.633423] ACPI: SSDT CFF7E0D0, 0277 (r1 DpgPmm  P001Ist       11 INTL 20060113)
[   27.633579] ACPI: SSDT CFF7E5D0, 04B2 (r1  PmRef  P001Cst     3001 INTL 20060113)
[   27.634014] Monitor-Mwait will be used to enter C-1 state
[   27.634016] Monitor-Mwait will be used to enter C-2 state
[   27.634018] Monitor-Mwait will be used to enter C-3 state
[   27.634094] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   27.634245] ACPI: SSDT CFF7E350, 0277 (r1 DpgPmm  P002Ist       12 INTL 20060113)
[   27.634391] ACPI: SSDT CFF7EA90, 0085 (r1  PmRef  P002Cst     3000 INTL 20060113)
[   27.634954] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   27.634965] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   27.634972] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   27.762032] usbcore: registered new interface driver usbfs
[   27.762050] usbcore: registered new interface driver hub
[   27.767378] usbcore: registered new device driver usb
[   27.783053] USB Universal Host Controller Interface driver v3.0
[   27.783093] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   27.783101] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   27.783104] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   27.783299] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   27.783325] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000b800
[   27.783419] usb usb1: configuration #1 chosen from 1 choice
[   27.783435] hub 1-0:1.0: USB hub found
[   27.783438] hub 1-0:1.0: 2 ports detected
[   27.887369] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 18
[   27.887379] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   27.887382] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   27.887398] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   27.887421] uhci_hcd 0000:00:1a.1: irq 18, io base 0x0000b880
[   27.887498] usb usb2: configuration #1 chosen from 1 choice
[   27.887512] hub 2-0:1.0: USB hub found
[   27.887516] hub 2-0:1.0: 2 ports detected
[   27.957449] SCSI subsystem initialized
[   27.962790] libata version 3.00 loaded.
[   27.991301] ACPI: PCI Interrupt 0000:00:1a.2[C] -> GSI 18 (level, low) -> IRQ 19
[   27.991309] PCI: Setting latency timer of device 0000:00:1a.2 to 64
[   27.991313] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[   27.991328] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[   27.991350] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000bc00
[   27.991423] usb usb3: configuration #1 chosen from 1 choice
[   27.991438] hub 3-0:1.0: USB hub found
[   27.991441] hub 3-0:1.0: 2 ports detected
[   28.095256] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   28.095263] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   28.095266] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   28.095281] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
[   28.095303] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000b080
[   28.095378] usb usb4: configuration #1 chosen from 1 choice
[   28.095392] hub 4-0:1.0: USB hub found
[   28.095395] hub 4-0:1.0: 2 ports detected
[   28.199193] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 21
[   28.199201] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   28.199203] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   28.199220] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
[   28.199241] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000b400
[   28.199314] usb usb5: configuration #1 chosen from 1 choice
[   28.199330] hub 5-0:1.0: USB hub found
[   28.199333] hub 5-0:1.0: 2 ports detected
[   28.303154] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[   28.303160] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   28.303163] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   28.303178] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
[   28.303196] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000b480
[   28.303269] usb usb6: configuration #1 chosen from 1 choice
[   28.303283] hub 6-0:1.0: USB hub found
[   28.303286] hub 6-0:1.0: 2 ports detected
[   28.334069] usb 3-1: new full speed USB device using uhci_hcd and address 2
[   28.406280] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 19
[   28.406287] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   28.406290] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   28.406308] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 7
[   28.410206] ehci_hcd 0000:00:1a.7: debug port 1
[   28.410210] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   28.410214] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xf9fffc00
[   28.459002] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   28.459093] usb usb7: configuration #1 chosen from 1 choice
[   28.459110] hub 7-0:1.0: USB hub found
[   28.459114] hub 7-0:1.0: 6 ports detected
[   28.505968] Clocksource tsc unstable (delta = -92583966 ns)
[   28.533285] Time: hpet clocksource has been installed.
[   28.556809] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[   28.556818] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   28.556820] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   28.556836] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[   28.560741] ehci_hcd 0000:00:1d.7: debug port 1
[   28.560745] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   28.560750] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xf9fff800
[   28.572024] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   28.572108] usb usb8: configuration #1 chosen from 1 choice
[   28.572123] hub 8-0:1.0: USB hub found
[   28.572126] hub 8-0:1.0: 6 ports detected
[   28.657991] r8169 Gigabit Ethernet driver 2.2LK loaded
[   28.658005] ACPI: PCI Interrupt 0000:04:01.0[A] -> GSI 17 (level, low) -> IRQ 17
[   28.658168] eth0: RTL8169sb/8110sb at 0xf8838c00, 00:1d:0f:be:96:bb, XID 10000000 IRQ 17
[   28.658703] ACPI: PCI Interrupt 0000:04:03.0[A] -> GSI 19 (level, low) -> IRQ 21
[   28.710358] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[febfe000-febfe7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[   28.717401] ahci 0000:00:1f.2: version 3.0
[   28.717418] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 21
[   28.808418] usb 3-1: device not accepting address 2, error -71
[   29.350745] usb 7-5: new high speed USB device using ehci_hcd and address 2
[   29.487142] usb 7-5: configuration #1 chosen from 3 choices
[   29.562634] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[   29.562638] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part 
[   29.562643] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   29.562879] scsi0 : ahci
[   29.562917] scsi1 : ahci
[   29.562947] scsi2 : ahci
[   29.562976] scsi3 : ahci
[   29.563005] scsi4 : ahci
[   29.563057] scsi5 : ahci
[   29.563126] ata1: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffe900 irq 220
[   29.563128] ata2: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffe980 irq 220
[   29.563130] ata3: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffea00 irq 220
[   29.563132] ata4: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffea80 irq 220
[   29.563134] ata5: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffeb00 irq 220
[   29.563136] ata6: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffeb80 irq 220
[   29.678595] usb 7-6: new high speed USB device using ehci_hcd and address 3
[   29.778613] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c00014bae68]
[   29.813954] usb 7-6: configuration #1 chosen from 1 choice
[   30.051707] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   30.052514] ata1.00: ATA-8: WDC WD3200AAKS-00B3A0, 01.03A01, max UDMA/133
[   30.052517] ata1.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 31/32)
[   30.053451] ata1.00: configured for UDMA/133
[   30.086964] usb 8-4: new high speed USB device using ehci_hcd and address 3
[   30.227451] usb 8-4: configuration #1 chosen from 1 choice
[   30.227505] hub 8-4:1.0: USB hub found
[   30.227613] hub 8-4:1.0: 3 ports detected
[   30.331220] usbcore: registered new interface driver libusual
[   30.334462] Initializing USB Mass Storage driver...
[   30.570641] usb 5-1: new low speed USB device using uhci_hcd and address 2
[   30.642604] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   30.684066] ata2.00: ATA-7: ST3160815AS, 4.AAB, max UDMA/133
[   30.684069] ata2.00: 312581808 sectors, multi 0: LBA48 NCQ (depth 31/32)
[   30.742363] ata2.00: configured for UDMA/133
[   30.750049] usb 5-1: configuration #1 chosen from 1 choice
[   30.771668] scsi6 : SCSI emulation for USB Mass Storage devices
[   30.771710] usb-storage: device found at 3
[   30.771711] usb-storage: waiting for device to settle before scanning
[   30.967515] usb 8-4.1: new low speed USB device using ehci_hcd and address 4
[   31.063796] usb 8-4.1: configuration #1 chosen from 1 choice
[   31.262371] usb 8-4.2: new low speed USB device using ehci_hcd and address 5
[   31.360900] usb 8-4.2: configuration #1 chosen from 1 choice
[   31.361589] usbcore: registered new interface driver usb-storage
[   31.361591] usbcore: registered new interface driver hiddev
[   31.361592] USB Mass Storage support registered.
[   31.373723] hiddev96hidraw0: USB HID v1.00 Device [Griffin Technology, Inc. AirClick USB] on usb-0000:00:1d.1-1
[   31.376074] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:1d.7/usb8/8-4/8-4.1/8-4.1:1.0/input/input1
[   31.379219] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   31.379816] ata3.00: ATA-7: WDC WD5000AAKS-65TMA0, 12.01C01, max UDMA/133
[   31.379819] ata3.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[   31.380549] ata3.00: configured for UDMA/133
[   31.402220] input,hidraw1: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:1d.7-4.1
[   31.405228] input: Apple, Inc Apple Keyboard as /devices/pci0000:00/0000:00:1d.7/usb8/8-4/8-4.2/8-4.2:1.0/input/input2
[   31.435203] input,hidraw2: USB HID v1.11 Keyboard [Apple, Inc Apple Keyboard] on usb-0000:00:1d.7-4.2
[   31.437716] input: Apple, Inc Apple Keyboard as /devices/pci0000:00/0000:00:1d.7/usb8/8-4/8-4.2/8-4.2:1.1/input/input3
[   31.446195] input,hidraw3: USB HID v1.11 Device [Apple, Inc Apple Keyboard] on usb-0000:00:1d.7-4.2
[   31.446210] usbcore: registered new interface driver usbhid
[   31.446212] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   32.021852] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   32.022464] ata4.00: ATA-7: WDC WD5000AAKS-65TMA0, 12.01C01, max UDMA/133
[   32.022467] ata4.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[   32.023172] ata4.00: configured for UDMA/133
[   32.341683] ata5: SATA link down (SStatus 0 SControl 300)
[   32.981335] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   33.139805] ata6.00: ATAPI: HL-DT-ST DVDRAM GH20NS10, EL00, max UDMA/100
[   33.295814] ata6.00: configured for UDMA/100
[   33.295935] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200AAKS-0 01.0 PQ: 0 ANSI: 5
[   33.296019] scsi 1:0:0:0: Direct-Access     ATA      ST3160815AS      4.AA PQ: 0 ANSI: 5
[   33.296098] scsi 2:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-6 12.0 PQ: 0 ANSI: 5
[   33.296170] scsi 3:0:0:0: Direct-Access     ATA      WDC WD5000AAKS-6 12.0 PQ: 0 ANSI: 5
[   33.299402] scsi 5:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH20NS10  EL00 PQ: 0 ANSI: 5
[   33.306423] Driver 'sd' needs updating - please use bus_type methods
[   33.310177] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   33.310186] sd 0:0:0:0: [sda] Write Protect is off
[   33.310187] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   33.310198] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.310232] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors (320073 MB)
[   33.310239] sd 0:0:0:0: [sda] Write Protect is off
[   33.310240] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   33.310251] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.310253]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   33.365297]  sda1 sda2 sda3
[   33.365364] sd 0:0:0:0: [sda] Attached SCSI disk
[   33.365396] sd 1:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   33.365403] sd 1:0:0:0: [sdb] Write Protect is off
[   33.365404] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   33.365415] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.365442] sd 1:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   33.365449] sd 1:0:0:0: [sdb] Write Protect is off
[   33.365450] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   33.365466] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.365468]  sdb: sdb1 sdb2 < sdb5 >
[   33.412484] sd 1:0:0:0: [sdb] Attached SCSI disk
[   33.412513] sd 2:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
[   33.412520] sd 2:0:0:0: [sdc] Write Protect is off
[   33.412522] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   33.412532] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.412557] sd 2:0:0:0: [sdc] 976773168 512-byte hardware sectors (500108 MB)
[   33.412563] sd 2:0:0:0: [sdc] Write Protect is off
[   33.412565] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[   33.412580] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.412582]  sdc: sdc2
[   33.484262] sd 2:0:0:0: [sdc] Attached SCSI disk
[   33.484292] sd 3:0:0:0: [sdd] 976773168 512-byte hardware sectors (500108 MB)
[   33.484299] sd 3:0:0:0: [sdd] Write Protect is off
[   33.484300] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[   33.484311] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.484334] sd 3:0:0:0: [sdd] 976773168 512-byte hardware sectors (500108 MB)
[   33.484341] sd 3:0:0:0: [sdd] Write Protect is off
[   33.484342] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[   33.484353] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.484355]  sdd: sdd2
[   33.539436] sd 3:0:0:0: [sdd] Attached SCSI disk
[   33.542665] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   33.542677] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   33.542689] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   33.542700] sd 3:0:0:0: Attached scsi generic sg3 type 0
[   33.542710] sr 5:0:0:0: Attached scsi generic sg4 type 5
[   33.981588] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   33.981592] Uniform CD-ROM driver Revision: 3.20
[   33.981642] sr 5:0:0:0: Attached scsi CD-ROM sr0
[   35.767988] usb-storage: device scan complete
[   35.768862] scsi 6:0:0:0: Direct-Access     Lexar    JD Secure II +   1100 PQ: 0 ANSI: 0 CCS
[   35.774832] sd 6:0:0:0: [sde] 7864320 512-byte hardware sectors (4027 MB)
[   35.775705] sd 6:0:0:0: [sde] Write Protect is off
[   35.775707] sd 6:0:0:0: [sde] Mode Sense: 43 00 00 00
[   35.775708] sd 6:0:0:0: [sde] Assuming drive cache: write through
[   35.783210] sd 6:0:0:0: [sde] 7864320 512-byte hardware sectors (4027 MB)
[   35.784084] sd 6:0:0:0: [sde] Write Protect is off
[   35.784087] sd 6:0:0:0: [sde] Mode Sense: 43 00 00 00
[   35.784089] sd 6:0:0:0: [sde] Assuming drive cache: write through
[   35.784092]  sde: sde1
[   35.784895] sd 6:0:0:0: [sde] Attached SCSI removable disk
[   35.784920] sd 6:0:0:0: Attached scsi generic sg5 type 0
[   36.275741] Attempting manual resume
[   36.275744] swsusp: Resume From Partition 8:21
[   36.275745] PM: Checking swsusp image.
[   36.275875] PM: Resume from disk failed.
[   36.317924] kjournald starting.  Commit interval 5 seconds
[   36.317937] EXT3-fs: mounted filesystem with ordered data mode.
[   42.244167] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   42.346803] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   42.349020] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   42.677514] input: Power Button (FF) as /devices/virtual/input/input5
[   42.728158] Linux agpgart interface v0.102
[   42.733053] ACPI: Power Button (FF) [PWRF]
[   42.733114] input: Power Button (CM) as /devices/virtual/input/input6
[   42.801024] ACPI: Power Button (CM) [PWRB]
[   42.932644] gameport: EMU10K1 is pci0000:04:00.1/gameport0, io 0xec00, speed 1028kHz
[   43.034122] nvidia: module license 'NVIDIA' taints kernel.
[   43.424209] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   43.424216] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   43.424282] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   43.690531] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   43.694127] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/emu10k1/../../alsa-kernel/pci/emu10k1/emufx.c:1544: Installing spdif_bug patch: Audigy 1 ES [SB0160]
[   43.970245] lp: driver loaded but no devices found
[   44.026854] Adding 6385796k swap on /dev/sdb5.  Priority:-1 extents:1 across:6385796k
[   44.569168] EXT3 FS on sdb1, internal journal
[   45.351314] hfs: Filesystem was not cleanly unmounted, running fsck.hfsplus is recommended.  mounting read-only.
[   45.751338] ip_tables: (C) 2000-2006 Netfilter Core Team
[   46.235649] No dock devices found.
[   47.256375] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   47.256378] apm: disabled - APM is not SMP safe.
[   47.370637] ppdev: user-space parallel port driver
[   47.487136] audit(1227782016.625:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5571 profile="/usr/sbin/cupsd" namespace="default"
[   50.151570] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   50.151575] vboxdrv: Successfully done.
[   50.151577] vboxdrv: Found 2 processor cores.
[   50.151622] vboxdrv: fAsync=0 offMin=0x2c9 offMax=0x993
[   50.151626] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   50.151628] vboxdrv: Successfully loaded version 2.0.6 (interface 0x00090000).
[   50.732592] NET: Registered protocol family 10
[   50.732821] lo: Disabled Privacy Extensions
[   51.898240] r8169: eth0: link up
[   51.950001] Bluetooth: Core ver 2.11
[   51.950250] NET: Registered protocol family 31
[   51.950253] Bluetooth: HCI device and connection manager initialized
[   51.950256] Bluetooth: HCI socket layer initialized
[   51.965296] Bluetooth: L2CAP ver 2.9
[   51.965300] Bluetooth: L2CAP socket layer initialized
[   51.992270] Bluetooth: RFCOMM socket layer initialized
[   51.992282] Bluetooth: RFCOMM TTY layer initialized
[   51.992283] Bluetooth: RFCOMM ver 1.8
[   55.298444] NET: Registered protocol family 17
[   70.666578] eth0: no IPv6 routers present
[  103.108498] compiz.real[6433]: segfault at 0000127e eip 08055a80 esp bfb9e020 error 4
david@david-ubuntu:~$ 
```

My fstab reads the following:
```

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=6d58b2a2-367f-4afb-bb52-dfb462f8af16 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=318fbd69-3a5a-42ae-a90f-99ba57a40eb9 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sdc2 /media/Files hfsplus auto,user,rw 0 0
/dev/sdd2 /media/Files2 hfsplus auto,user,rw 0 0
```

The drive sdd is the problem one, the other drive works fine. Both drives are exactly the same.

---

### Post by geirha on 2008-11-27
```

[   45.351314] hfs: Filesystem was not cleanly unmounted, running fsck.hfsplus is recommended.  mounting read-only.

```

Try unmounting it and run fsck.hfsplus
```
sudo umount /dev/sdd2
sudo fsck.hfsplus /dev/sdd2

```

If you change the last field from 0 to 2 in fstab, it will run a filesystem check during boot.

---

### Post by Sipheren on 2008-11-27
It says cammand not found for fsck.hfsplus /dev/sdd2

I will add the 2 in fstab and reboot

thx for the reply

---

### Post by geirha on 2008-11-27
According to [http://packages.ubuntu.com/search?searchon=contents&keywords=fsck.hfsplus&mode=exactfilename&suite=intrepid&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=fsck.hfsplus&mode=exactfilename&suite=intrepid&arch=any), fsck.hfsplus is installed by the [apt://hfsprogs](apt://hfsprogs) package, so you'll probably need to install that.

---

### Post by Sipheren on 2008-11-27
Yeah, did a quick search and found it, works like a charm, thx for all your help.

---

