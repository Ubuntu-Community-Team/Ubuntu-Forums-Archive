---
title: "Being forced to use low-graphic mode"
date: 2008-09-21
forum: Hardware
---

### Post by vinhtantran on 2008-09-21
Hello,

I'm using Hardy on Dell Vostro 1510 laptop. Yesterday, when Ubuntu was running startup page after I restarted, it told that I must use low-graphic. This is what I received when I type *dmesg*:

```
[   17.795098] monitor/mwait feature present.
[   17.795101] CPU: L1 I cache: 32K, L1 D cache: 32K
[   17.795102] CPU: L2 cache: 2048K
[   17.795104] CPU: Physical Processor ID: 0
[   17.795105] CPU: Processor Core ID: 1
[   17.795106] CPU: After all inits, caps: bfebfbff 20100000 00000000 00003940 0000e3bd 00000000 00000001 00000001
[   17.795588] CPU1: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz stepping 0d
[   17.795606] Total of 2 processors activated (7983.87 BogoMIPS).
[   17.795776] ENABLING IO-APIC IRQs
[   17.795958] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   17.943103] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   17.963109] Brought up 2 CPUs
[   17.963129] CPU0 attaching sched-domain:
[   17.963131]  domain 0: span 03
[   17.963133]   groups: 01 02
[   17.963136] CPU1 attaching sched-domain:
[   17.963137]  domain 0: span 03
[   17.963139]   groups: 02 01
[   17.963322] net_namespace: 64 bytes
[   17.963329] Booting paravirtualized kernel on bare hardware
[   17.963718] Time: 10:41:58  Date: 09/21/08
[   17.963742] NET: Registered protocol family 16
[   17.963897] EISA bus registered
[   17.963901] ACPI: bus type pci registered
[   17.964298] PCI: PCI BIOS revision 3.00 entry at 0xfde11, last bus=8
[   17.964300] PCI: Using configuration type 1
[   17.964310] Setting up standard PCI resources
[   17.966760] ACPI: EC: Look up EC in DSDT
[   17.973816] ACPI: BIOS _OSI(Linux) query ignored
[   17.973818] ACPI: DMI System Vendor: Dell Inc.
[   17.973820] ACPI: DMI Product Name: Vostro1510
[   17.973821] ACPI: DMI Product Version: Null
[   17.973822] ACPI: DMI Board Name: 0M277C
[   17.973823] ACPI: DMI BIOS Vendor: Dell Inc.
[   17.973825] ACPI: DMI BIOS Date: 09/10/2008
[   17.973826] ACPI: Please send DMI info above to linux-acpi@vger.kernel.org
[   17.973828] ACPI: If "acpi_osi=Linux" works better, please notify linux-acpi@vger.kernel.org
[   17.974305] ACPI: Interpreter enabled
[   17.974308] ACPI: (supports S0 S3 S4 S5)
[   17.974320] ACPI: Using IOAPIC for interrupt routing
[   17.978947] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   18.031445] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[   18.031447] ACPI: EC: driver started in interrupt mode
[   18.031480] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   18.032484] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   18.032487] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   18.034109] PCI: Transparent bridge - 0000:00:1e.0
[   18.034156] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   18.034476] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   18.034593] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   18.034709] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[   18.034823] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[   18.034953] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   18.045905] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[   18.045999] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   18.046094] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   18.046184] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   18.046274] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[   18.046365] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   18.046458] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   18.046548] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   18.046679] Linux Plug and Play Support v0.97 (c) Adam Belay
[   18.046704] pnp: PnP ACPI init
[   18.046710] ACPI: bus type pnp registered
[   18.075121] pnp: PnP ACPI: found 10 devices
[   18.075123] ACPI: ACPI bus type pnp unregistered
[   18.075126] PnPBIOS: Disabled by ACPI PNP
[   18.075296] PCI: Using ACPI for IRQ routing
[   18.075299] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   18.186977] NET: Registered protocol family 8
[   18.186979] NET: Registered protocol family 20
[   18.187006] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   18.187010] hpet0: 3 64-bit timers, 14318180 Hz
[   18.188039] AppArmor: AppArmor Filesystem Enabled
[   18.190871] Time: tsc clocksource has been installed.
[   18.190883] Switched to high resolution mode on CPU 0
[   18.190972] Switched to high resolution mode on CPU 1
[   18.199857] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   18.199860] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   18.199862] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   18.199864] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   18.199867] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   18.199869] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
[   18.199872] system 00:01: iomem range 0xfed40000-0xfed44fff could not be reserved
[   18.199874] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
[   18.199881] system 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[   18.199886] system 00:06: ioport range 0x680-0x69f has been reserved
[   18.199888] system 00:06: ioport range 0x800-0x80f has been reserved
[   18.199890] system 00:06: ioport range 0x1000-0x107f has been reserved
[   18.199893] system 00:06: ioport range 0x1180-0x11bf has been reserved
[   18.199895] system 00:06: ioport range 0xfe00-0xfe00 has been reserved
[   18.199897] system 00:06: ioport range 0xff00-0xff7f has been reserved
[   18.230232] PCI: Bridge: 0000:00:1c.0
[   18.230236]   IO window: 2000-2fff
[   18.230241]   MEM window: c4000000-c7ffffff
[   18.230246]   PREFETCH window: cc000000-cdffffff
[   18.230251] PCI: Bridge: 0000:00:1c.1
[   18.230253]   IO window: 3000-3fff
[   18.230259]   MEM window: f0000000-f3ffffff
[   18.230263]   PREFETCH window: fa000000-fbffffff
[   18.230268] PCI: Bridge: 0000:00:1c.3
[   18.230271]   IO window: 4000-4fff
[   18.230276]   MEM window: f4000000-f7ffffff
[   18.230280]   PREFETCH window: fc000000-fdffffff
[   18.230286] PCI: Bridge: 0000:00:1c.4
[   18.230289]   IO window: 5000-5fff
[   18.230294]   MEM window: c2000000-c20fffff
[   18.230298]   PREFETCH window: f8600000-f86fffff
[   18.230303] PCI: Bridge: 0000:00:1e.0
[   18.230304]   IO window: disabled.
[   18.230310]   MEM window: f8200000-f82fffff
[   18.230313]   PREFETCH window: disabled.
[   18.230344] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   18.230351] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   18.230375] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[   18.230380] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   18.230404] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 18
[   18.230409] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   18.230433] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 17 (level, low) -> IRQ 16
[   18.230438] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   18.230452] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   18.230461] NET: Registered protocol family 2
[   18.267842] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   18.268034] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   18.268401] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   18.268590] TCP: Hash tables configured (established 131072 bind 65536)
[   18.268592] TCP reno registered
[   18.279904] checking if image is initramfs... it is
[   18.844478] Freeing initrd memory: 7309k freed
[   18.844604] Simple Boot Flag at 0x36 set to 0x1
[   18.845123] audit: initializing netlink socket (disabled)
[   18.845136] audit(1221993718.300:1): initialized
[   18.845343] highmem bounce pool size: 64 pages
[   18.846959] VFS: Disk quotas dquot_6.5.1
[   18.847019] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   18.847132] io scheduler noop registered
[   18.847134] io scheduler anticipatory registered
[   18.847135] io scheduler deadline registered
[   18.847144] io scheduler cfq registered (default)
[   18.847154] Boot video device is 0000:00:02.0
[   18.847365] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   18.847424] assign_interrupt_mode Found MSI capability
[   18.847473] Allocate Port Service[0000:00:1c.0:pcie00]
[   18.847504] Allocate Port Service[0000:00:1c.0:pcie02]
[   18.847599] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   18.847658] assign_interrupt_mode Found MSI capability
[   18.847705] Allocate Port Service[0000:00:1c.1:pcie00]
[   18.847732] Allocate Port Service[0000:00:1c.1:pcie02]
[   18.847826] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   18.847884] assign_interrupt_mode Found MSI capability
[   18.847931] Allocate Port Service[0000:00:1c.3:pcie00]
[   18.847957] Allocate Port Service[0000:00:1c.3:pcie02]
[   18.848055] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   18.848113] assign_interrupt_mode Found MSI capability
[   18.848159] Allocate Port Service[0000:00:1c.4:pcie00]
[   18.848185] Allocate Port Service[0000:00:1c.4:pcie02]
[   18.848410] isapnp: Scanning for PnP cards...
[   19.202505] isapnp: No Plug & Play device found
[   19.222926] Real Time Clock Driver v1.12ac
[   19.223123] hpet_resources: 0xfed00000 is busy
[   19.223146] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   19.224119] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   19.224172] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   19.224249] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   19.260168] serio: i8042 KBD port at 0x60,0x64 irq 1
[   19.260172] serio: i8042 AUX port at 0x60,0x64 irq 12
[   19.274311] mice: PS/2 mouse device common for all mice
[   19.274400] EISA: Probing bus 0 at eisa.0
[   19.274407] Cannot allocate resource for EISA slot 1
[   19.274409] Cannot allocate resource for EISA slot 2
[   19.274411] Cannot allocate resource for EISA slot 3
[   19.274413] Cannot allocate resource for EISA slot 4
[   19.274414] Cannot allocate resource for EISA slot 5
[   19.274429] EISA: Detected 0 cards.
[   19.274431] cpuidle: using governor ladder
[   19.274433] cpuidle: using governor menu
[   19.274501] NET: Registered protocol family 1
[   19.274526] Using IPI No-Shortcut mode
[   19.274551] registered taskstats version 1
[   19.274657]   Magic number: 8:787:679
[   19.274719] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   19.274720] EDD information not available.
[   19.274884] Freeing unused kernel memory: 368k freed
[   19.298298] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   20.460237] fuse init (API version 7.9)
[   20.478597] ACPI: SSDT BF6D75A9, 027A (r1  PmRef  Cpu0Ist     3000 INTL 20061109)
[   20.478807] ACPI: SSDT BF6D6F3A, 05EA (r1  PmRef  Cpu0Cst     3001 INTL 20061109)
[   20.480534] Monitor-Mwait will be used to enter C-1 state
[   20.480537] Monitor-Mwait will be used to enter C-2 state
[   20.480539] Monitor-Mwait will be used to enter C-3 state
[   20.480639] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   20.480643] ACPI: Processor [CPU0] (supports 8 throttling states)
[   20.480845] ACPI: SSDT BF6D7823, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20061109)
[   20.481040] ACPI: SSDT BF6D7524, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20061109)
[   20.481988] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   20.481992] ACPI: Processor [CPU1] (supports 8 throttling states)
[   20.601653] usbcore: registered new interface driver usbfs
[   20.601673] usbcore: registered new interface driver hub
[   20.606586] usbcore: registered new device driver usb
[   20.615067] USB Universal Host Controller Interface driver v3.0
[   20.615114] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 17
[   20.615125] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   20.615129] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   20.615331] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   20.615365] uhci_hcd 0000:00:1a.0: irq 17, io base 0x00001820
[   20.615480] usb usb1: configuration #1 chosen from 1 choice
[   20.615502] hub 1-0:1.0: USB hub found
[   20.615507] hub 1-0:1.0: 2 ports detected
[   20.717548] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 19
[   20.717560] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   20.717564] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   20.717584] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   20.717617] uhci_hcd 0000:00:1a.1: irq 19, io base 0x00001840
[   20.717714] usb usb2: configuration #1 chosen from 1 choice
[   20.717735] hub 2-0:1.0: USB hub found
[   20.717739] hub 2-0:1.0: 2 ports detected
[   20.821492] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   20.821504] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   20.821509] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   20.821529] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[   20.821561] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001860
[   20.821660] usb usb3: configuration #1 chosen from 1 choice
[   20.821679] hub 3-0:1.0: USB hub found
[   20.821684] hub 3-0:1.0: 2 ports detected
[   20.906565] SCSI subsystem initialized
[   20.925425] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
[   20.925437] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   20.925441] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   20.925461] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[   20.925494] uhci_hcd 0000:00:1d.1: irq 18, io base 0x00001880
[   20.925592] usb usb4: configuration #1 chosen from 1 choice
[   20.925612] hub 4-0:1.0: USB hub found
[   20.925617] hub 4-0:1.0: 2 ports detected
[   20.934575] libata version 3.00 loaded.
[   21.029397] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 21
[   21.029408] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   21.029412] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   21.029433] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[   21.029464] uhci_hcd 0000:00:1d.2: irq 21, io base 0x000018a0
[   21.029566] usb usb5: configuration #1 chosen from 1 choice
[   21.029585] hub 5-0:1.0: USB hub found
[   21.029590] hub 5-0:1.0: 2 ports detected
[   21.133368] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 21
[   21.133383] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   21.133387] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   21.133410] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[   21.137309] ehci_hcd 0000:00:1a.7: debug port 1
[   21.137315] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   21.137320] ehci_hcd 0000:00:1a.7: irq 21, io mem 0xf8504800
[   21.149218] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   21.149319] usb usb6: configuration #1 chosen from 1 choice
[   21.149337] hub 6-0:1.0: USB hub found
[   21.149342] hub 6-0:1.0: 4 ports detected
[   21.253346] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[   21.253365] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   21.253371] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   21.253403] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   21.257300] ehci_hcd 0000:00:1d.7: debug port 1
[   21.257307] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   21.257311] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xf8504c00
[   21.273163] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   21.273310] usb usb7: configuration #1 chosen from 1 choice
[   21.273343] hub 7-0:1.0: USB hub found
[   21.273349] hub 7-0:1.0: 6 ports detected
[   21.377356] ACPI: PCI Interrupt 0000:08:05.0[A] -> GSI 22 (level, low) -> IRQ 22
[   21.428052] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[f8200000-f82007ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[   21.430165] ata_piix 0000:00:1f.1: version 2.12
[   21.430180] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 21
[   21.430211] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   21.430279] scsi0 : ata_piix
[   21.431043] scsi1 : ata_piix
[   21.431495] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[   21.431497] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[   21.541004] Clocksource tsc unstable (delta = -4906299077 ns)
[   21.541021] usb 6-3: new high speed USB device using ehci_hcd and address 2
[   21.550151] Time: hpet clocksource has been installed.
[   21.717134] usb 6-3: configuration #1 chosen from 1 choice
[   21.769386] ata1.00: ATAPI: TEAC   DVD+/-RW DVW28SLC, A.06, max UDMA/33
[   21.872247] ata1.00: configured for UDMA/33
[   21.891783] usb 4-1: new low speed USB device using uhci_hcd and address 2
[   21.896310] scsi 0:0:0:0: CD-ROM            TEAC     DVD+-RW DVW28SLC A.06 PQ: 0 ANSI: 5
[   21.896636] ahci 0000:00:1f.2: version 3.0
[   21.896662] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 18 (level, low) -> IRQ 21
[   21.914721] usb 4-1: configuration #1 chosen from 1 choice
[   21.927448] usbcore: registered new interface driver hiddev
[   21.930340] input: Mitsumi Optical Wheel Mouse (USB) as /devices/pci0000:00/0000:00:1d.1/usb4/4-1/4-1:1.0/input/input2
[   21.934524] input,hidraw0: USB HID v1.10 Mouse [Mitsumi Optical Wheel Mouse (USB)] on usb-0000:00:1d.1-1
[   21.934543] usbcore: registered new interface driver usbhid
[   21.934548] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   21.963714] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0000c010a000b000]
[   21.986477] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[   21.986482] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[   21.986490] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   21.986731] scsi2 : ahci
[   21.986877] scsi3 : ahci
[   21.987025] scsi4 : ahci
[   21.987099] ata3: SATA max UDMA/133 abar m2048@0xf8504000 port 0xf8504100 irq 219
[   21.987103] ata4: SATA max UDMA/133 abar m2048@0xf8504000 port 0xf8504180 irq 219
[   21.987106] ata5: SATA max UDMA/133 abar m2048@0xf8504000 port 0xf8504200 irq 219
[   22.020633] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   22.322423] ata3.00: ATA-8: WDC WD2500BEVS-75UST0, 01.01A01, max UDMA/133
[   22.322428] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   22.323341] ata3.00: configured for UDMA/133
[   22.338823] ata4: SATA link down (SStatus 0 SControl 300)
[   22.353910] ata5: SATA link down (SStatus 0 SControl 300)
[   22.354126] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2500BEVS-7 01.0 PQ: 0 ANSI: 5
[   22.363144] Driver 'sd' needs updating - please use bus_type methods
[   22.365292] Driver 'sr' needs updating - please use bus_type methods
[   22.367742] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   22.367788] sd 2:0:0:0: [sda] Write Protect is off
[   22.367793] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.367871] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.367987] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   22.368028] sd 2:0:0:0: [sda] Write Protect is off
[   22.368031] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.368088] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.368091]  sda:sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda caddy
[   22.403250] Uniform CD-ROM driver Revision: 3.20
[   22.403312] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   22.414745]  sda1 sda2 sda3 sda4 < sda5 sda6 >
[   22.452636] sd 2:0:0:0: [sda] Attached SCSI disk
[   22.456307] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   22.456324] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   22.864218] Attempting manual resume
[   22.864221] swsusp: Resume From Partition 8:6
[   22.864223] PM: Checking swsusp image.
[   22.864395] PM: Resume from disk failed.
[   22.893847] kjournald starting.  Commit interval 5 seconds
[   22.893885] EXT3-fs: mounted filesystem with ordered data mode.
[   32.803259] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   32.829617] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   32.982335] Linux agpgart interface v0.102
[   33.038398] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   33.067335] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   33.098195] agpgart: Detected an Intel 965GM Chipset.
[   33.099076] agpgart: Detected 7676K stolen memory.
[   33.111810] agpgart: AGP aperture is 256M @ 0xd0000000
[   33.121034] iTCO_vendor_support: vendor-support=0
[   33.124872] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   33.126317] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   33.126354] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   33.127401] input: Power Button (FF) as /devices/virtual/input/input4
[   33.181227] ACPI: Power Button (FF) [PWRF]
[   33.181282] input: Lid Switch as /devices/virtual/input/input5
[   33.213267] ACPI: Lid Switch [LID0]
[   33.213320] input: Power Button (CM) as /devices/virtual/input/input6
[   33.279135] ACPI: Power Button (CM) [PWRB]
[   33.279192] input: Sleep Button (CM) as /devices/virtual/input/input7
[   33.338188] ACPI: Sleep Button (CM) [SLPB]
[   33.338254] ACPI: WMI-Acer: Mapper loaded
[   33.388217] ieee80211_crypt: registered algorithm 'NULL'
[   33.435334] wl: module license 'unspecified' taints kernel.
[   33.452875] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 19 (level, low) -> IRQ 18
[   33.452891] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   33.605945] ieee80211_crypt: registered algorithm 'TKIP'
[   33.606089] eth0: Broadcom BCM4315 802.11 Wireless Controller 5.10.18.0
[   33.641973] r8168 Gigabit Ethernet driver 8.008.00-NAPI loaded
[   33.642039] ACPI: PCI Interrupt 0000:07:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[   33.642106] PCI: Setting latency timer of device 0000:07:00.0 to 64
[   33.642542] r8168: This product is covered by one or more of the following patents: US5,307,459, US5,434,872, US5,732,094, US6,570,884, US6,115,776, and US6,327,625.
[   33.642547] eth1: Identified chip type is 'RTL8168C/8111C'.
[   33.642551] eth1: RTL8168B/8111B at 0xf892e000, 00:1c:23:4b:d3:65, IRQ 218
[   33.687131] sdhci: Secure Digital Host Controller Interface driver
[   33.687134] sdhci: Copyright(c) Pierre Ossman
[   33.687176] sdhci: SDHCI controller found at 0000:08:05.2 [1217:7120] (rev 2)
[   33.687199] ACPI: PCI Interrupt 0000:08:05.2[A] -> GSI 22 (level, low) -> IRQ 22
[   33.687218] sdhci:slot0: Unknown controller version (2). You may experience problems.
[   33.687262] mmc0: SDHCI at 0xf8202800 irq 22 DMA
[   33.738053] ACPI: AC Adapter [ACAD] (on-line)
[   33.775773] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/LNXVIDEO:00/input/input8
[   33.825824] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   33.841972] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input9
[   33.896780] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   33.932435] input: PS/2 Mouse as /devices/virtual/input/input10
[   34.033599] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input11
[   34.102123] ACPI: Battery Slot [BAT1] (battery present)
[   34.284638] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   34.284663] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   34.318821] hda_codec: Unknown model for ALC268, trying auto-probe from BIOS...
[   34.341128] Linux video capture interface: v2.00
[   34.430524] uvcvideo: Found UVC 1.00 device Integrated Webcam (0c45:63e0)
[   34.446034] usbcore: registered new interface driver uvcvideo
[   34.446038] USB Video Class driver (v0.1.0)
[   34.892625] udev: renamed network interface eth1 to eth0
[   34.937981] udev: renamed network interface eth0_rename to eth1
[   35.243863] lp: driver loaded but no devices found
[   35.327159] Adding 1309256k swap on /dev/sda6.  Priority:-1 extents:1 across:1309256k
[   35.793275] EXT3 FS on sda5, internal journal
[   36.435482] ip_tables: (C) 2000-2006 Netfilter Core Team
[   36.853087] No dock devices found.
[   39.496360] apm: BIOS not found.
[   39.769152] ppdev: user-space parallel port driver
[   40.286697] audit(1221968549.128:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5368 profile="/usr/sbin/cupsd" namespace="default"
[   41.485991] r8168: eth0: link up
[   41.575176] Bluetooth: Core ver 2.11
[   41.575257] NET: Registered protocol family 31
[   41.575259] Bluetooth: HCI device and connection manager initialized
[   41.575262] Bluetooth: HCI socket layer initialized
[   41.586139] Bluetooth: L2CAP ver 2.9
[   41.586143] Bluetooth: L2CAP socket layer initialized
[   41.685015] Bluetooth: RFCOMM socket layer initialized
[   41.685038] Bluetooth: RFCOMM TTY layer initialized
[   41.685041] Bluetooth: RFCOMM ver 1.8
[   42.565739] NET: Registered protocol family 17
[   42.883658] NET: Registered protocol family 10
[   42.884286] lo: Disabled Privacy Extensions
[   43.832706] eth1: no IPv6 routers present
[   44.892566] mtrr: no more MTRRs available
[   44.892595] mtrr: no more MTRRs available
[   45.195245] eth0: no IPv6 routers present
[   48.056422] mtrr: no more MTRRs available
[   48.056449] mtrr: no more MTRRs available
[   66.368888] CPU0 attaching NULL sched-domain.
[   66.368894] CPU1 attaching NULL sched-domain.
[   66.377805] CPU0 attaching sched-domain:
[   66.377812]  domain 0: span 03
[   66.377814]   groups: 01 02
[   66.377819] CPU1 attaching sched-domain:
[   66.377822]  domain 0: span 03
[   66.377824]   groups: 02 01
```

I don't know the reason why, can anybody help me?

---

