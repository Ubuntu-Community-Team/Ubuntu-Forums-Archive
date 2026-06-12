---
title: "Burn failure on Amilio Si2636"
date: 2008-08-11
forum: Hardware
---

### Post by nukleuzN on 2008-08-11
I have trouble when burning dvd/cd's with my computer. Often i have to try burning the cd/dvd many times before success. I dont get any error msg that tells me anything else that the burn proccess fails. 

What could be the problem?

dmesg: 
```
[   17.694435]   PREFETCH window: f0000000-f1ffffff
[   17.694444] PCI: Bridge: 0000:00:1c.1
[   17.694449]   IO window: 3000-3fff
[   17.694458]   MEM window: f8000000-f9ffffff
[   17.694465]   PREFETCH window: f2000000-f3ffffff
[   17.694475] PCI: Bridge: 0000:00:1c.2
[   17.694480]   IO window: 4000-4fff
[   17.694489]   MEM window: fa000000-fbffffff
[   17.694496]   PREFETCH window: f4000000-f5ffffff
[   17.694505] PCI: Bridge: 0000:00:1c.3
[   17.694510]   IO window: 5000-5fff
[   17.694519]   MEM window: c6000000-c9ffffff
[   17.694526]   PREFETCH window: cc000000-cdffffff
[   17.694536] PCI: Bridge: 0000:00:1c.5
[   17.694541]   IO window: 6000-6fff
[   17.694549]   MEM window: fc200000-fc2fffff
[   17.694556]   PREFETCH window: 88000000-880fffff
[   17.694566] PCI: Bridge: 0000:00:1e.0
[   17.694568]   IO window: disabled.
[   17.694577]   MEM window: fc300000-fc3fffff
[   17.694583]   PREFETCH window: disabled.
[   17.694630] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[   17.694642] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   17.694679] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 16
[   17.694689] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   17.694726] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   17.694735] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   17.694772] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   17.694782] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   17.694816] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 16 (level, low) -> IRQ 16
[   17.694827] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   17.694849] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   17.694867] NET: Registered protocol family 2
[   17.729543] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   17.731041] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[   17.735400] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   17.736559] TCP: Hash tables configured (established 262144 bind 65536)
[   17.736564] TCP reno registered
[   17.745650] checking if image is initramfs... it is
[   19.445655] Freeing initrd memory: 7557k freed
[   19.453219] Simple Boot Flag at 0x36 set to 0x80
[   19.454947] audit: initializing netlink socket (disabled)
[   19.454982] audit(1218456604.996:1): initialized
[   19.459404] VFS: Disk quotas dquot_6.5.1
[   19.459547] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   19.459788] io scheduler noop registered
[   19.459793] io scheduler anticipatory registered
[   19.459796] io scheduler deadline registered
[   19.460020] io scheduler cfq registered (default)
[   19.460040] Boot video device is 0000:00:02.0
[   19.465017] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   19.465108] assign_interrupt_mode Found MSI capability
[   19.465183] Allocate Port Service[0000:00:1c.0:pcie00]
[   19.465256] Allocate Port Service[0000:00:1c.0:pcie02]
[   19.465434] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   19.465521] assign_interrupt_mode Found MSI capability
[   19.465591] Allocate Port Service[0000:00:1c.1:pcie00]
[   19.465655] Allocate Port Service[0000:00:1c.1:pcie02]
[   19.465827] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   19.465914] assign_interrupt_mode Found MSI capability
[   19.465983] Allocate Port Service[0000:00:1c.2:pcie00]
[   19.466050] Allocate Port Service[0000:00:1c.2:pcie02]
[   19.466217] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   19.466303] assign_interrupt_mode Found MSI capability
[   19.466373] Allocate Port Service[0000:00:1c.3:pcie00]
[   19.466441] Allocate Port Service[0000:00:1c.3:pcie02]
[   19.466609] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   19.466695] assign_interrupt_mode Found MSI capability
[   19.466765] Allocate Port Service[0000:00:1c.5:pcie00]
[   19.466830] Allocate Port Service[0000:00:1c.5:pcie02]
[   19.518868] Real Time Clock Driver v1.12ac
[   19.519314] hpet_resources: 0xfed00000 is busy
[   19.519367] Linux agpgart interface v0.102
[   19.519372] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   19.521617] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   19.521745] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   19.521939] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   19.525768] i8042.c: Detected active multiplexing controller, rev 1.1.
[   19.526439] serio: i8042 KBD port at 0x60,0x64 irq 1
[   19.526447] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   19.526453] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   19.526458] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   19.526462] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   19.541378] mice: PS/2 mouse device common for all mice
[   19.541463] cpuidle: using governor ladder
[   19.541467] cpuidle: using governor menu
[   19.541727] NET: Registered protocol family 1
[   19.541922] registered taskstats version 1
[   19.542162]   Magic number: 4:725:177
[   19.542216]   hash matches device ttyr3
[   19.542336]   hash matches device device:0d
[   19.542348] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   19.542354] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   19.542358] EDD information not available.
[   19.542373] Freeing unused kernel memory: 320k freed
[   19.596246] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   20.952527] fuse init (API version 7.9)
[   20.980921] ACPI: Transitioning device [FAN2] to D3
[   20.980928] ACPI: Transitioning device [FAN2] to D3
[   20.980934] ACPI: Fan [FAN2] (off)
[   20.981103] ACPI: Transitioning device [FAN0] to D3
[   20.981107] ACPI: Transitioning device [FAN0] to D3
[   20.981113] ACPI: Fan [FAN0] (off)
[   20.981279] ACPI: Transitioning device [FAN1] to D3
[   20.981282] ACPI: Transitioning device [FAN1] to D3
[   20.981289] ACPI: Fan [FAN1] (off)
[   20.993153] ACPI: SSDT 7F6D4E92, 027A (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[   20.993676] ACPI: SSDT 7F6D4823, 05EA (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   20.998157] Monitor-Mwait will be used to enter C-1 state
[   20.998163] Monitor-Mwait will be used to enter C-2 state
[   20.998168] Monitor-Mwait will be used to enter C-3 state
[   20.998409] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   20.998419] ACPI: Processor [CPU0] (supports 8 throttling states)
[   20.998952] ACPI: SSDT 7F6D510C, 00FA (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[   20.999453] ACPI: SSDT 7F6D4E0D, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[   21.001458] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   21.001469] ACPI: Processor [CPU1] (supports 8 throttling states)
[   21.007434] ACPI: Thermal Zone [TZ00] (30 C)
[   21.008523] ACPI: Thermal Zone [TZ01] (27 C)
[   21.253999] usbcore: registered new interface driver usbfs
[   21.254044] usbcore: registered new interface driver hub
[   21.254098] usbcore: registered new device driver usb
[   21.255864] USB Universal Host Controller Interface driver v3.0
[   21.255947] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   21.255969] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   21.255976] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   21.256417] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   21.256463] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
[   21.256703] usb usb1: configuration #1 chosen from 1 choice
[   21.256748] hub 1-0:1.0: USB hub found
[   21.256759] hub 1-0:1.0: 2 ports detected
[   21.359341] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 21
[   21.359367] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   21.359374] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   21.359436] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   21.359484] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
[   21.359696] usb usb2: configuration #1 chosen from 1 choice
[   21.359741] hub 2-0:1.0: USB hub found
[   21.359751] hub 2-0:1.0: 2 ports detected
[   21.463277] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[   21.463300] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   21.463307] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   21.463351] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[   21.463396] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
[   21.463611] usb usb3: configuration #1 chosen from 1 choice
[   21.463659] hub 3-0:1.0: USB hub found
[   21.463669] hub 3-0:1.0: 2 ports detected
[   21.567286] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   21.567311] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   21.567318] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   21.567363] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[   21.567411] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
[   21.567646] usb usb4: configuration #1 chosen from 1 choice
[   21.567689] hub 4-0:1.0: USB hub found
[   21.567700] hub 4-0:1.0: 2 ports detected
[   21.671161] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   21.671184] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   21.671192] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   21.671238] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[   21.671290] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[   21.671503] usb usb5: configuration #1 chosen from 1 choice
[   21.671550] hub 5-0:1.0: USB hub found
[   21.671560] hub 5-0:1.0: 2 ports detected
[   21.775161] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[   21.776273] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   21.776283] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   21.776367] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[   21.780296] ehci_hcd 0000:00:1a.7: debug port 1
[   21.780307] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   21.780319] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfc604800
[   21.794889] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   21.795096] usb usb6: configuration #1 chosen from 1 choice
[   21.795145] hub 6-0:1.0: USB hub found
[   21.795158] hub 6-0:1.0: 4 ports detected
[   21.802517] SCSI subsystem initialized
[   21.831891] libata version 3.00 loaded.
[   21.899043] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[   21.900246] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   21.900256] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   21.900342] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   21.904279] ehci_hcd 0000:00:1d.7: debug port 1
[   21.904289] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   21.904301] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfc604c00
[   21.918808] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   21.919023] usb usb7: configuration #1 chosen from 1 choice
[   21.919069] hub 7-0:1.0: USB hub found
[   21.919080] hub 7-0:1.0: 6 ports detected
[   22.023006] ahci 0000:00:1f.2: version 3.0
[   22.023068] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   22.262670] usb 7-2: new high speed USB device using ehci_hcd and address 2
[   22.409923] usb 7-2: configuration #1 chosen from 1 choice
[   22.937282] usb 4-2: new full speed USB device using uhci_hcd and address 2
[   22.940982] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[   22.940989] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[   22.940999] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   22.941849] scsi0 : ahci
[   22.942679] scsi1 : ahci
[   22.943222] scsi2 : ahci
[   22.943401] ata1: SATA max UDMA/133 abar m2048@0xfc604000 port 0xfc604100 irq 506
[   22.943408] ata2: SATA max UDMA/133 abar m2048@0xfc604000 port 0xfc604180 irq 506
[   22.943414] ata3: SATA max UDMA/133 abar m2048@0xfc604000 port 0xfc604200 irq 506
[   22.968926] usb 4-2: configuration #1 chosen from 1 choice
[   22.973661] usbcore: registered new interface driver libusual
[   22.992152] Initializing USB Mass Storage driver...
[   23.001822] scsi3 : SCSI emulation for USB Mass Storage devices
[   23.001967] usbcore: registered new interface driver usb-storage
[   23.001973] USB Mass Storage support registered.
[   23.002158] usb-storage: device found at 2
[   23.002162] usb-storage: waiting for device to settle before scanning
[   23.032771] Clocksource tsc unstable (delta = -399181276 ns)
[   23.043394] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   23.055783] ata1.00: ATA-8: WDC WD2500BEVS-22UST0, 01.01A01, max UDMA/133
[   23.055790] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   23.056360] ata1.00: configured for UDMA/133
[   23.094888] ata2: SATA link down (SStatus 0 SControl 300)
[   23.133746] ata3: SATA link down (SStatus 0 SControl 300)
[   23.134012] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVS-2 01.0 PQ: 0 ANSI: 5
[   23.134814] sata_sil24 0000:08:00.0: version 1.1
[   23.134862] ACPI: PCI Interrupt 0000:08:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[   23.136999] PCI: Setting latency timer of device 0000:08:00.0 to 64
[   23.137216] scsi4 : sata_sil24
[   23.137303] ata4: SATA max UDMA/100 host m128@0xc6000000 port 0xc8000000 irq 19
[   23.149792] Driver 'sd' needs updating - please use bus_type methods
[   23.153378] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   23.153403] sd 0:0:0:0: [sda] Write Protect is off
[   23.153408] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.153441] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.153542] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   23.153562] sd 0:0:0:0: [sda] Write Protect is off
[   23.153566] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.153598] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.153605]  sda: sda1 sda2 < sda5 >
[   23.181969] sd 0:0:0:0: [sda] Attached SCSI disk
[   23.191261] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   23.355484] Attempting manual resume
[   23.355491] swsusp: Resume From Partition 8:5
[   23.355494] PM: Checking swsusp image.
[   23.355759] PM: Resume from disk failed.
[   23.385130] kjournald starting.  Commit interval 5 seconds
[   23.385158] EXT3-fs: mounted filesystem with ordered data mode.
[   24.047915] ata4: SATA link down (SStatus 0 SControl 0)
[   24.048278] ata_piix 0000:00:1f.1: version 2.12
[   24.048310] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 19 (level, low) -> IRQ 19
[   24.048369] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   24.048599] scsi5 : ata_piix
[   24.048699] scsi6 : ata_piix
[   24.049894] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[   24.049900] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[   24.117473] ata5.00: ATAPI: MATSHITADVD-RAM UJ-875S, 1.00, max UDMA/66
[   24.156248] ata5.00: configured for UDMA/66
[   24.207686] scsi 5:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-875S  1.00 PQ: 0 ANSI: 5
[   24.207830] scsi 5:0:0:0: Attached scsi generic sg1 type 5
[   24.208284] ACPI: PCI Interrupt 0000:0b:03.0[A] -> GSI 16 (level, low) -> IRQ 16
[   24.260560] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[16]  MMIO=[fc300000-fc3007ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[   24.479159] usb-storage: device scan complete
[   24.482010] scsi 3:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[   24.484272] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[   24.484341] sd 3:0:0:0: Attached scsi generic sg2 type 0
[   24.489587] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0040ca01450052ee]
[   28.658993] agpgart: Detected an Intel 965GM Chipset.
[   28.661205] agpgart: Detected 7676K stolen memory.
[   28.680174] agpgart: AGP aperture is 256M @ 0xd0000000
[   28.775588] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   28.812998] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   28.935794] input: Power Button (FF) as /devices/virtual/input/input2
[   28.963420] ACPI: Power Button (FF) [PWRF]
[   28.963561] input: Lid Switch as /devices/virtual/input/input3
[   28.963686] ACPI: Lid Switch [LID]
[   28.963808] input: Power Button (CM) as /devices/virtual/input/input4
[   28.995341] ACPI: Power Button (CM) [PWRB]
[   28.995480] input: Sleep Button (CM) as /devices/virtual/input/input5
[   29.011354] ACPI: Sleep Button (CM) [SLPB]
[   29.327441] ACPI: AC Adapter [ACAD] (off-line)
[   29.463127] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.0
[   29.463135] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   29.463312] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   29.463328] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   29.464448] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   29.562478] ACPI: Battery Slot [BAT0] (battery present)
[   30.346847] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[   30.367498] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   31.022158] Bluetooth: Core ver 2.11
[   31.054203] NET: Registered protocol family 31
[   31.054209] Bluetooth: HCI device and connection manager initialized
[   31.054218] Bluetooth: HCI socket layer initialized
[   31.098132] Bluetooth: HCI USB driver ver 2.9
[   31.099812] usbcore: registered new interface driver hci_usb
[   31.246751] iTCO_vendor_support: vendor-support=0
[   31.264621] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   31.264772] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   31.264835] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   31.874678] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   32.741830] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x39a0b2, caps: 0xa04753/0x200000
[   32.798012] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   33.897875] ACPI: PCI Interrupt 0000:0a:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   33.897902] PCI: Setting latency timer of device 0000:0a:00.0 to 64
[   33.908839] sky2 0000:0a:00.0: v1.20 addr 0xfc200000 irq 17 Yukon-EC Ultra (0xb4) rev 3
[   33.909725] sky2 eth0: addr 00:14:0b:42:bc:47
[   33.946674] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   33.947796] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   34.136497] iwl4965: Tunable channels: 13 802.11bg, 19 802.11a channels
[   34.152023] wmaster0: Selected rate control algorithm 'iwl-4965-rs'
[   34.209267] Driver 'sr' needs updating - please use bus_type methods
[   34.215967] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda caddy
[   34.215975] Uniform CD-ROM driver Revision: 3.20
[   34.216071] sr 5:0:0:0: Attached scsi CD-ROM sr0
[   35.495036] lp: driver loaded but no devices found
[   35.745321] Adding 6016300k swap on /dev/sda5.  Priority:-1 extents:1 across:6016300k
[   35.786901] EXT3 FS on sda1, internal journal
[   36.624628] ip_tables: (C) 2000-2006 Netfilter Core Team
[   37.592187] No dock devices found.
[   40.969184] ppdev: user-space parallel port driver
[   41.237299] audit(1218456634.691:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5290 profile="/usr/sbin/cupsd" namespace="default"
[   42.430227] sky2 eth0: enabling interface
[   42.531754] Bluetooth: L2CAP ver 2.9
[   42.531763] Bluetooth: L2CAP socket layer initialized
[   42.605012] Bluetooth: RFCOMM socket layer initialized
[   42.605038] Bluetooth: RFCOMM TTY layer initialized
[   42.605042] Bluetooth: RFCOMM ver 1.8
[   44.569203] NET: Registered protocol family 10
[   44.569510] lo: Disabled Privacy Extensions
[   44.570064] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   44.570761] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   44.778740] [drm] Initialized drm 1.1.0 20060810
[   44.781120] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   44.781128] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   44.781182] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   58.656055] CPU0 attaching NULL sched-domain.
[   58.656067] CPU1 attaching NULL sched-domain.
[   58.680271] CPU0 attaching sched-domain:
[   58.680287]  domain 0: span 03
[   58.680292]   groups: 01 02
[   58.680299]   domain 1: span 03
[   58.680303]    groups: 03
[   58.680308]    domain 2: span 03
[   58.680312]     groups: 03
[   58.680317] CPU1 attaching sched-domain:
[   58.680321]  domain 0: span 03
[   58.680325]   groups: 02 01
[   58.680330]   domain 1: span 03
[   58.680335]    groups: 03
[   58.680339]    domain 2: span 03
[   58.680343]     groups: 03
[   60.516988] NET: Registered protocol family 17
[   61.965597] wlan0: Initial auth_alg=0
[   61.965610] wlan0: authenticate with AP 00:13:46:b7:f9:8c
[   62.113984] wlan0: authenticate with AP 00:13:46:b7:f9:8c
[   62.309898] wlan0: authenticate with AP 00:13:46:b7:f9:8c
[   62.486283] wlan0: authentication with AP 00:13:46:b7:f9:8c timed out
[   93.501551] wlan0: Initial auth_alg=0
[   93.501564] wlan0: authenticate with AP 00:13:46:b7:f9:8c
[   93.504423] wlan0: Initial auth_alg=0
[   93.504435] wlan0: authenticate with AP 00:13:46:b7:f9:8c
[   93.504467] wlan0: RX authentication from 00:13:46:b7:f9:8c (alg=0 transaction=2 status=0)
[   93.504471] wlan0: authenticated
[   93.504475] wlan0: associate with AP 00:13:46:b7:f9:8c
[   93.504494] wlan0: authentication frame received from 00:13:46:b7:f9:8c, but not in authenticate state - ignored
[   93.506131] wlan0: authentication frame received from 00:13:46:b7:f9:8c, but not in authenticate state - ignored
[   93.508018] wlan0: RX AssocResp from 00:13:46:b7:f9:8c (capab=0x411 status=0 aid=1)
[   93.508029] wlan0: associated
[   93.508037] wlan0: CTS protection enabled (BSSID=00:13:46:b7:f9:8c)
[   93.514647] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   97.289705] wlan0: no IPv6 routers present
[  104.385907] wlan0: no IPv6 routers present
[ 1558.715125] CPU0 attaching NULL sched-domain.
[ 1558.715135] CPU1 attaching NULL sched-domain.
[ 1558.741260] CPU0 attaching sched-domain:
[ 1558.741271]  domain 0: span 03
[ 1558.741275]   groups: 01 02
[ 1558.741282]   domain 1: span 03
[ 1558.741287]    groups: 03
[ 1558.741292] CPU1 attaching sched-domain:
[ 1558.741296]  domain 0: span 03
[ 1558.741300]   groups: 02 01
[ 1558.741306]   domain 1: span 03
[ 1558.741310]    groups: 03
[ 1559.288310] Monitor-Mwait will be used to enter C-2 state
[28599.932956] cdrom: This disc doesn't have any tracks I recognize!
[29126.212938] UDF-fs: Partition marked readonly; forcing readonly mount
[29126.304054] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'PROOF_D1', timestamp 2007/12/16 00:04 (1078)
[29137.183129] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[29137.183143] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current] 
[29137.183150] sr 5:0:0:0: [sr0] Add. Sense: No seek complete
[29137.183159] end_request: I/O error, dev sr0, sector 1032
[29137.183166] Buffer I/O error on device sr0, logical block 258
[29144.866341] sr 5:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[29144.866355] sr 5:0:0:0: [sr0] Sense Key : Medium Error [current] 
[29144.866363] sr 5:0:0:0: [sr0] Add. Sense: No seek complete
[29144.866371] end_request: I/O error, dev sr0, sector 1236
[29144.866378] Buffer I/O error on device sr0, logical block 309
[29238.194676] UDF-fs: Partition marked readonly; forcing readonly mount
[29238.258285] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'HOSTEL_PART_II', timestamp 2007/10/19 15:51 (1078)
[29245.898933] sr 5:0:0:0: [sr0] Device not ready: Sense Key : Not Ready [current] 
[29245.898941] sr 5:0:0:0: [sr0] Device not ready: Add. Sense: Medium not present
[29245.898946] end_request: I/O error, dev sr0, sector 361760
[29245.898950] Buffer I/O error on device sr0, logical block 90440
[29245.898955] Buffer I/O error on device sr0, logical block 90441
[29245.898959] Buffer I/O error on device sr0, logical block 90442
[29245.898961] Buffer I/O error on device sr0, logical block 90443
[29245.898964] Buffer I/O error on device sr0, logical block 90444
[29245.898966] Buffer I/O error on device sr0, logical block 90445
[29245.898968] Buffer I/O error on device sr0, logical block 90446
[29245.898971] Buffer I/O error on device sr0, logical block 90447
[29245.898973] Buffer I/O error on device sr0, logical block 90448
[29245.898976] Buffer I/O error on device sr0, logical block 90449
[29245.910193] sr 5:0:0:0: [sr0] Device not ready: Sense Key : Not Ready [current] 
[29245.910200] sr 5:0:0:0: [sr0] Device not ready: Add. Sense: Medium not present
[29245.910206] end_request: I/O error, dev sr0, sector 362016
[29245.952820] sr 5:0:0:0: [sr0] Device not ready: Sense Key : Not Ready [current] 
[29245.952832] sr 5:0:0:0: [sr0] Device not ready: Add. Sense: Medium not present
[29245.952837] end_request: I/O error, dev sr0, sector 361760
[29245.955554] sr 5:0:0:0: [sr0] Device not ready: Sense Key : Not Ready [current] 
[29245.955564] sr 5:0:0:0: [sr0] Device not ready: Add. Sense: Medium not present
[29245.955574] end_request: I/O error, dev sr0, sector 361760
[29273.103229] UDF-fs: Partition marked readonly; forcing readonly mount
[29273.167342] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'Brodre', timestamp 2005/08/01 08:45 (1078)
[29372.064134] UDF-fs: Partition marked readonly; forcing readonly mount
[29372.129056] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'Prison Break', timestamp 2006/11/21 04:53 (1078)

```

And YES! I have tried many different types of DVD's and CD's.

---

### Post by nukleuzN on 2008-08-12
ANyone have any options?

---

