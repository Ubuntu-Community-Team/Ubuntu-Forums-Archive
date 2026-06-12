---
title: "PCI: Cannot Allocate Resorce Region 0...."
date: 2007-11-10
forum: Hardware &amp; Laptops
---

### Post by 4nDr3s on 2007-11-10
Hi All.

I have a problem.When i boot Ubuntu Gutsy Gibbon amd64, I get this message right after grub:
[CENTER][B]
PCI: Cannot Allocate Resource Region 0 of device 0000:00:00.0.[/B][/CENTER]

(The device seems to be my chipset)

But that is not the only thing... right after that message i get a black screen and after a few seconds i get the Ubuntu login screen (boot splash screen)... I dont get the ubuntu loading interface.. just a black screen and then the login screen....

This is the ouput of: lspci | grep 00:00.0
[B][CENTER]
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 755 Host (rev 01)[/CENTER][/B]

I'm running Gutsy Gibon amd64 on a UNIWILL AMD Athlon 64 3700+, 2gb Ram, SiS Chipset.

Thanks for help in advanced...

---

### Post by thingy on 2007-11-10
Post output from dmesg + lscpi

Are you using a standard kernel or a custom one?

Does the BIOS have any options to reset configuration data?

---

### Post by 4nDr3s on 2007-11-11
Hi, the kernel is standard one:

2.6.22-14-generic

BIOS does not have any reset feature.

dmesg output:
```
[    0.000000] Linux version 2.6.22-14-generic (buildd@crested) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 21:45:15 GMT 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] Command line: root=UUID=43c63495-6ced-4e9d-a83c-cc4396c52c8f ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffd0000 (usable)
[    0.000000]  BIOS-e820: 000000007ffd0000 - 000000007ffdf000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffdf000 - 0000000080000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524240) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xFFFF8100000F7970 checksum 0
[    0.000000] ACPI: RSDP 000F7970, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 7FFD0000, 0030 (r1 A M I  OEMRSDT   9000406 MSFT       97)
[    0.000000] ACPI: FACP 7FFD0200, 0081 (r2 A M I  OEMFACP   9000406 MSFT       97)
[    0.000000] ACPI: DSDT 7FFD03F0, 3A1B (r1  258KA 258KA000        0 INTL  2002026)
[    0.000000] ACPI: FACS 7FFDF000, 0040
[    0.000000] ACPI: APIC 7FFD0390, 0054 (r1 A M I  OEMAPIC   9000406 MSFT       97)
[    0.000000] ACPI: OEMB 7FFDF040, 0108 (r1 A M I  AMI_OEM   9000406 MSFT       97)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007ffd0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524240) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000007ffd0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   524240
[    0.000000] On node 0 totalpages: 524143
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1125 pages reserved
[    0.000000]   DMA zone: 2818 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7111 pages used for memmap
[    0.000000]   DMA32 zone: 513033 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 10 global_irq 10 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ10 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7ff80000)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 515851
[    0.000000] Kernel command line: root=UUID=43c63495-6ced-4e9d-a83c-cc4396c52c8f ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   21.333659] time.c: Detected 798.241 MHz processor.
[   21.334590] Console: colour VGA+ 80x25
[   21.334622] Checking aperture...
[   21.334629] CPU 0: aperture @ e0000000 size 128 MB
[   21.373091] Memory: 2055496k/2096960k available (2274k kernel code, 41076k reserved, 1181k data, 296k init)
[   21.373188] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   21.451590] Calibrating delay using timer specific routine.. 1597.54 BogoMIPS (lpj=3195087)
[   21.451654] Security Framework v1.0.0 initialized
[   21.451668] SELinux:  Disabled at boot.
[   21.452047] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   21.454429] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   21.455615] Mount-cache hash table entries: 256
[   21.455857] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   21.455863] CPU: L2 Cache: 1024K (64 bytes/line)
[   21.455870] CPU 0/0 -> Node 0
[   21.455899] SMP alternatives: switching to UP code
[   21.456147] Freeing SMP alternatives: 24k freed
[   21.457029] Early unpacking initramfs... done
[   22.237351] ACPI: Core revision 20070126
[   22.237449] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   22.282561] Using local APIC timer interrupts.
[   22.407763] result 12472523
[   22.407768] Detected 12.472 MHz APIC timer.
[   22.411096] Brought up 1 CPUs
[   22.411423] NET: Registered protocol family 16
[   22.411559] ACPI: bus type pci registered
[   22.411570] PCI: Using configuration type 1
[   22.414317] ACPI: EC: Look up EC in DSDT
[   22.416017] ACPI: EC: GPE=0x0b, ports=0x66, 0x62
[   22.425938] ACPI: Interpreter enabled
[   22.425944] ACPI: (supports S0 S1 S3 S4 S5)
[   22.425982] ACPI: Using IOAPIC for interrupt routing
[   22.442468] ACPI: EC: GPE=0x0b, ports=0x66, 0x62
[   22.442644] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   22.442663] PCI: Probing PCI hardware (bus 00)
[   22.442843] Enabling SiS 96x SMBus.
[   22.443684] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   22.481559] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 12 14 15)
[   22.481769] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 *11 12 14 15)
[   22.481976] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *10 11 12 14 15)
[   22.482187] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 10 11 12 14 15)
[   22.482393] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 *11 12 14 15)
[   22.482603] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 *4 5 7 10 11 12 14 15)
[   22.482813] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[   22.483033] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 7 10 11 12 14 15)
[   22.483189] Linux Plug and Play Support v0.97 (c) Adam Belay
[   22.483211] pnp: PnP ACPI init
[   22.483224] ACPI: bus type pnp registered
[   22.493048] pnp: PnP ACPI: found 12 devices
[   22.493053] ACPI: ACPI bus type pnp unregistered
[   22.493146] PCI: Using ACPI for IRQ routing
[   22.493152] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   22.493167] PCI: Cannot allocate resource region 0 of device 0000:00:00.0
[   22.493296] NET: Registered protocol family 8
[   22.493301] NET: Registered protocol family 20
[   22.493398] agpgart: Detected AGP bridge 0
[   22.500733] agpgart: AGP aperture is 128M @ 0xe0000000
[   22.500892] pnp: 00:09: iomem range 0xfff80000-0xffffffff could not be reserved
[   22.500901] pnp: 00:09: iomem range 0xffe80000-0xffefffff has been reserved
[   22.500909] pnp: 00:09: iomem range 0xfed00000-0xfed003ff has been reserved
[   22.500921] pnp: 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[   22.500929] pnp: 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
[   22.500941] pnp: 00:0b: iomem range 0x0-0x9ffff could not be reserved
[   22.500948] pnp: 00:0b: iomem range 0xc0000-0xd0fff has been reserved
[   22.500955] pnp: 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[   22.500963] pnp: 00:0b: iomem range 0x100000-0x7fffffff could not be reserved
[   22.501538] PCI: Bridge: 0000:00:01.0
[   22.501544]   IO window: c000-cfff
[   22.501551]   MEM window: fea00000-feafffff
[   22.501558]   PREFETCH window: ee900000-fe8fffff
[   22.501565] PCI: Bus 2, cardbus bridge: 0000:00:09.0
[   22.501570]   IO window: 00001000-000010ff
[   22.501577]   IO window: 00001400-000014ff
[   22.501584]   PREFETCH window: 88000000-8bffffff
[   22.501591]   MEM window: 8c000000-8fffffff
[   22.501597] PCI: Bus 6, cardbus bridge: 0000:00:09.1
[   22.501602]   IO window: 00001800-000018ff
[   22.501607]   IO window: 00001c00-00001cff
[   22.501614]   PREFETCH window: 90000000-93ffffff
[   22.501621]   MEM window: 94000000-97ffffff
[   22.501652] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 17
[   22.501668] ACPI: PCI Interrupt 0000:00:09.1[A] -> GSI 17 (level, low) -> IRQ 17
[   22.501775] NET: Registered protocol family 2
[   22.502973] Time: tsc clocksource has been installed.
[   22.539087] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   22.540307] TCP established hash table entries: 262144 (order: 10, 6291456 bytes)
[   22.546584] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   22.547774] TCP: Hash tables configured (established 262144 bind 65536)
[   22.547781] TCP reno registered
[   22.559185] checking if image is initramfs... it is
[   24.078909] Freeing initrd memory: 7741k freed
[   24.087805] audit: initializing netlink socket (disabled)
[   24.087829] audit(1194776332.628:1): initialized
[   24.091811] VFS: Disk quotas dquot_6.5.1
[   24.091916] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   24.092082] io scheduler noop registered
[   24.092087] io scheduler anticipatory registered
[   24.092091] io scheduler deadline registered
[   24.092276] io scheduler cfq registered (default)
[   24.162624] Boot video device is 0000:01:00.0
[   24.212664] Real Time Clock Driver v1.12ac
[   24.212816] Linux agpgart interface v0.102 (c) Dave Jones
[   24.212823] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   24.213081] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a NS16550A
[   24.213828] ACPI: PCI Interrupt 0000:00:02.6[C] -> GSI 18 (level, low) -> IRQ 18
[   24.213841] ACPI: PCI interrupt for device 0000:00:02.6 disabled
[   24.214970] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   24.215339] input: Macintosh mouse button emulation as /class/input/input0
[   24.215480] PNP: PS/2 Controller [PNP030b:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   24.220859] i8042.c: Detected active multiplexing controller, rev 1.0.
[   24.222051] serio: i8042 KBD port at 0x60,0x64 irq 1
[   24.222060] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   24.222067] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   24.222073] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   24.222079] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   24.222547] mice: PS/2 mouse device common for all mice
[   24.222755] TCP cubic registered
[   24.222882] NET: Registered protocol family 1
[   24.223206] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   24.223221] Freeing unused kernel memory: 296k freed
[   24.257937] input: AT Translated Set 2 keyboard as /class/input/input1
[   25.695110] AppArmor: AppArmor initialized<5>audit(1194776334.236:2):  type=1505 info="AppArmor initialized" pid=1204
[   25.906731] fuse init (API version 7.8)
[   25.915532] Failure registering capabilities with primary security module.
[   26.029161] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   26.030822] ACPI: Thermal Zone [THRM] (75 C)
[   36.481846] SCSI subsystem initialized
[   36.492833] libata version 2.21 loaded.
[   36.495753] pata_sis 0000:00:02.5: version 0.5.1
[   36.495991] scsi0 : pata_sis
[   36.496077] scsi1 : pata_sis
[   36.496290] ata1: PATA max UDMA/133 cmd 0x00000000000101f0 ctl 0x00000000000103f6 bmdma 0x000000000001ffa0 irq 14
[   36.496300] ata2: PATA max UDMA/133 cmd 0x0000000000010170 ctl 0x0000000000010376 bmdma 0x000000000001ffa8 irq 15
[   36.659122] ata1.00: ATA-6: HTS721080G9AT00, MC4OA51A, max UDMA/100
[   36.659132] ata1.00: 156301488 sectors, multi 16: LBA48 
[   36.659146] ata1.00: limited to UDMA/33 due to 40-wire cable
[   36.675098] ata1.00: configured for UDMA/33
[   36.781587] usbcore: registered new interface driver usbfs
[   36.781637] usbcore: registered new interface driver hub
[   36.781684] usbcore: registered new device driver usb
[   36.783080] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   36.994702] ata2.00: ATAPI: Slimtype DVDRW SOSW-833S, VS04, max UDMA/33
[   37.166606] ata2.00: configured for UDMA/33
[   37.174405] scsi 0:0:0:0: Direct-Access     ATA      HTS721080G9AT00  MC4O PQ: 0 ANSI: 5
[   37.175072] scsi 1:0:0:0: CD-ROM            Slimtype DVDRW SOSW-833S  VS04 PQ: 0 ANSI: 5
[   37.179355] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 20
[   37.179656] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   37.179892] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   37.179926] ohci_hcd 0000:00:03.0: irq 20, io mem 0xfebfd000
[   37.236596] usb usb1: configuration #1 chosen from 1 choice
[   37.236657] hub 1-0:1.0: USB hub found
[   37.236676] hub 1-0:1.0: 3 ports detected
[   37.264657] sis900.c: v1.08.10 Apr. 2 2006
[   37.338502] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 21
[   37.338815] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   37.338916] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[   37.338949] ohci_hcd 0000:00:03.1: irq 21, io mem 0xfebfe000
[   37.396489] usb usb2: configuration #1 chosen from 1 choice
[   37.396547] hub 2-0:1.0: USB hub found
[   37.396567] hub 2-0:1.0: 3 ports detected
[   37.499428] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 19
[   37.500648] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[   37.510751] 0000:00:04.0: Using transceiver found at address 1 as default
[   37.571423] eth0: SiS 900 PCI Fast Ethernet at 0xd800, IRQ 19, 00:03:0d:3c:27:0b.
[   37.571979] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 23
[   37.572447] ehci_hcd 0000:00:03.3: EHCI Host Controller
[   37.572549] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 3
[   37.572602] PCI: cache line size of 64 is not supported by device 0000:00:03.3
[   37.572623] ehci_hcd 0000:00:03.3: irq 23, io mem 0xfebff000
[   37.642135] usb 1-2: new low speed USB device using ohci_hcd and address 2
[   37.642171] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   37.642381] usb usb3: configuration #1 chosen from 1 choice
[   37.642438] hub 3-0:1.0: USB hub found
[   37.642452] hub 3-0:1.0: 6 ports detected
[   37.746688] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 19 (level, low) -> IRQ 19
[   37.796974] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[febfb800-febfbfff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   38.345727] usb 1-2: new low speed USB device using ohci_hcd and address 3
[   38.465684] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   38.469630] sd 0:0:0:0: [sda] Write Protect is off
[   38.469638] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   38.477631] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.485620] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   38.489625] sd 0:0:0:0: [sda] Write Protect is off
[   38.489631] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   38.497610] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.497622]  sda: sda1 sda2 < sda5 sda6<6>usb 1-2: configuration #1 chosen from 1 choice
[   38.587676]  sda7 sda8 >
[   38.596119] sd 0:0:0:0: [sda] Attached SCSI disk
[   38.603101] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   38.603140] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[   38.729316] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   38.729327] Uniform CD-ROM driver Revision: 3.20
[   38.729424] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   39.065450] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00030d53258297a3]
[   39.236731] usbcore: registered new interface driver hiddev
[   39.256932] input: Microsoft Microsoft USB Wireless Mouse as /class/input/input2
[   39.256977] input: USB HID v1.11 Mouse [Microsoft Microsoft USB Wireless Mouse] on usb-0000:00:03.0-2
[   39.257002] usbcore: registered new interface driver usbhid
[   39.257009] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   40.762061] Attempting manual resume
[   40.762070] swsusp: Resume From Partition 8:7
[   40.762074] PM: Checking swsusp image.
[   40.860224] PM: Resume from disk failed.
[   41.483935] kjournald starting.  Commit interval 5 seconds
[   41.483955] EXT3-fs: mounted filesystem with ordered data mode.
[  134.047816] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  134.061530] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  134.297575] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[  135.832041] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 18
[  136.656102] intel8x0_measure_ac97_clock: measured 55436 usecs
[  136.656111] intel8x0: clocking to 48000
[  136.658124] Yenta: CardBus bridge found at 0000:00:09.0 [1584:3005]
[  136.658147] Yenta O2: res at 0x94/0xD4: 00/ea
[  136.658152] Yenta O2: enabling read prefetch/write burst
[  136.784963] Yenta: ISA IRQ mask 0x0af8, PCI irq 17
[  136.784972] Socket status: 30000006
[  136.785535] Yenta: CardBus bridge found at 0000:00:09.1 [1584:3005]
[  136.912926] Yenta: ISA IRQ mask 0x0af8, PCI irq 17
[  136.912935] Socket status: 30000006
[  137.148673] ieee80211_crypt: registered algorithm 'NULL'
[  137.153802] ieee80211: 802.11 data/management/control stack, git-1.1.13
[  137.153809] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[  137.186318] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[  137.186327] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[  137.186484] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 19
[  137.186949] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[  137.829233] input: PC Speaker as /class/input/input3
[  138.259926] irda_init()
[  138.259966] NET: Registered protocol family 23
[  138.404961] Synaptics Touchpad, model: 1, fw: 5.9, id: 0xa36eb3, caps: 0x904713/0x10008
[  138.440437] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[  138.644880] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 1.
[  138.644913] nsc-ircc, chip->init
[  138.644926] nsc-ircc, Found chip at base=0x02e
[  138.644955] nsc-ircc, driver loaded (Dag Brattli)
[  138.644965] nsc_ircc_open(), can't get iobase of 0x2f8
[  138.644997] nsc-ircc, Found chip at base=0x02e
[  138.645025] nsc-ircc, driver loaded (Dag Brattli)
[  138.645031] nsc_ircc_open(), can't get iobase of 0x2f8
[  138.645047] nsc-ircc, chip->init
[  138.645058] nsc-ircc, Found chip at base=0x02e
[  138.645086] nsc-ircc, driver loaded (Dag Brattli)
[  138.645281] pnp: Device 00:07 disabled.
[  138.645403] parport_pc 00:08: reported by Plug and Play ACPI
[  138.645509] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,EPP,ECP]
[  139.455688] APIC error on CPU0: 00(40)
[  139.455748] APIC error on CPU0: 40(40)
[  139.456307] APIC error on CPU0: 40(40)
[  139.456348] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[  139.529638] APIC error on CPU0: 40(40)
[  139.554193] APIC error on CPU0: 40(40)
[  139.650697] APIC error on CPU0: 40(40)
[  139.654474] APIC error on CPU0: 40(40)
```


*Note: After that APCI error on CPU0: 40(40) i have lots of lines like that...
I didnt have that in edgy but i did in debian sarge and etch (all of were in i386), but not so much.

lspci output:
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 755 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
00:09.0 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
00:09.1 CardBus bridge: O2 Micro, Inc. OZ711M1/MC1 4-in-1 MemoryCardBus Controller (rev 20)
00:09.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator
00:0b.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

```

---

### Post by thingy on 2007-11-11
Regarding the:
```

APIC error on CPU0: 00(40)

```


lines, I saw this post on google and can you confirm whether this applies to you?

[http://osdir.com/ml/linux.ubuntu.laptop.testing/2006-02/msg00050.html](http://osdir.com/ml/linux.ubuntu.laptop.testing/2006-02/msg00050.html)

Look at thread message and then click the link for the ubuntu forums:

[http://ubuntuforums.org/showthread.php?p=278589](http://ubuntuforums.org/showthread.php?p=278589)


Can you also confirm whether you've updated the BIOS to the latest version...APIC problems sometimes get fixed by the manufacturers via BIOS updates.

---

