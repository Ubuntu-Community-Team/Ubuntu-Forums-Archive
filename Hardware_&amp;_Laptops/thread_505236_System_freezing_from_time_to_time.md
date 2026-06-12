---
title: "System freezing from time to time"
date: 2007-07-20
forum: Hardware &amp; Laptops
---

### Post by Snifffurt on 2007-07-20
Hello

I've changed several hardware and made a new install of Feisty i386. Since then, my computer seems to freeze from time to time, and I could not jet figure out what the reason for this is.

What have I done:
[LIST]
[*] I've upgraded the CPU from Athlon 64 3500 to Athlon 64 X2 4200
[*] I've built in 2 new SATA drives and installed Ubuntu on it with a mdadm software raid0
[*] I've changed the Graphic Card from a ATI 9250 128MB to a ATI 9200 128MB AGP card, because the "old" one had the vga plug loose.
[/LIST]

The RAM is not under my suspicion, because I've been using it AFAIR for at least a year without any such trouble.
CPU overheating would result in a sudden complete blackout, so this is AFAIK not the reason too.
I've been looking at my logs form the last freeze, but I did not get anything out of this.
So my question is, can anyone tell from the included logs and the attached Xorg.0.log what might cause the freezes?

I've pastet the moment of the last freeze of all the log files I could think of beeing usefull and attached my Xorg.0.log  bz2ed.

TIA for any hints.

Regards

Sniff


last /var/log/messages
```
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e4000 size: 000000000001c000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000009feb0000 end: 000000009ffb0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000009ffb0000 size: 0000000000010000 end: 000000009ffc0000 type: 3
[    0.000000] copy_e820_map() start: 000000009ffc0000 size: 0000000000030000 end: 000000009fff0000 type: 4
[    0.000000] copy_e820_map() start: 000000009fff0000 size: 0000000000010000 end: 00000000a0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000ff780000 size: 0000000000880000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000009ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000009ffb0000 - 000000009ffc0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000009ffc0000 - 000000009fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009fff0000 - 00000000a0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] 1663MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 655280) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   655280
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   655280
[    0.000000] On node 0 totalpages: 655280
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 3327 pages used for memmap
[    0.000000]   HighMem zone: 422577 pages, LIFO batch:31
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v002 ACPIAM                                ) @ 0x000fa7c0
[    0.000000] ACPI: XSDT (v001 A M I  OEMXSDT  0x11000514 MSFT 0x00000097) @ 0x9ffb0100
[    0.000000] ACPI: FADT (v003 A M I  OEMFACP  0x11000514 MSFT 0x00000097) @ 0x9ffb0290
[    0.000000] ACPI: MADT (v001 A M I  OEMAPIC  0x11000514 MSFT 0x00000097) @ 0x9ffb0390
[    0.000000] ACPI: OEMB (v001 A M I  OEMBIOS  0x11000514 MSFT 0x00000097) @ 0x9ffc0040
[    0.000000] ACPI: DSDT (v001  A0036 A0036001 0x00000001 MSFT 0x0100000d) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:3 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:3 APIC version 16
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at a8000000 (gap: a0000000:5f780000)
[    0.000000] Detected 2202.913 MHz processor.
[   28.769011] Built 1 zonelists.  Total pages: 650161
[   28.769014] Kernel command line: root=/dev/md0 ro quiet splash
[   28.769130] mapped APIC to ffffd000 (fee00000)
[   28.769132] mapped IOAPIC to ffffc000 (fec00000)
[   28.769135] Enabling fast FPU save and restore... done.
[   28.769137] Enabling unmasked SIMD FPU exception support... done.
[   28.769144] Initializing CPU#0
[   28.769218] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   28.770515] Console: colour VGA+ 80x25
[   28.770905] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   28.771274] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   28.847221] Memory: 2587680k/2621120k available (1992k kernel code, 32076k reserved, 900k data, 328k init, 1703616k highmem)
[   28.847230] virtual kernel memory layout:
[   28.847230]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   28.847232]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   28.847233]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   28.847234]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   28.847235]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   28.847236]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   28.847237]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   28.847240] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   28.924948] Calibrating delay using timer specific routine.. 4410.98 BogoMIPS (lpj=8821976)
[   28.924985] Security Framework v1.0.0 initialized
[   28.924992] SELinux:  Disabled at boot.
[   28.925007] Mount-cache hash table entries: 512
[   28.925134] CPU: After generic identify, caps: 178bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000003
[   28.925142] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   28.925144] CPU: L2 Cache: 512K (64 bytes/line)
[   28.925146] CPU 0(2) -> Core 0
[   28.925148] CPU: After all inits, caps: 178bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000003
[   28.925158] Compat vDSO mapped to ffffe000.
[   28.925162] Remapping vsyscall page to ffffe000
[   28.925171] Checking 'hlt' instruction... OK.
[   28.941056] SMP alternatives: switching to UP code
[   28.941444] Early unpacking initramfs... done
[   29.202898] ACPI: Core revision 20060707
[   29.203376] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   29.204942] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 02
[   29.204963] SMP alternatives: switching to SMP code
[   29.205052] Booting processor 1/1 eip 3000
[   29.215426] Initializing CPU#1
[   29.292492] Calibrating delay using timer specific routine.. 4405.98 BogoMIPS (lpj=8811963)
[   29.292502] CPU: After generic identify, caps: 178bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000003
[   29.292508] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   29.292510] CPU: L2 Cache: 512K (64 bytes/line)
[   29.292512] CPU 1(2) -> Core 1
[   29.292513] CPU: After all inits, caps: 178bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000003
[   29.292465] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 02
[   29.292482] Total of 2 processors activated (8816.96 BogoMIPS).
[   29.292942] ENABLING IO-APIC IRQs
[   29.293259] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[   29.440034] checking TSC synchronization across 2 CPUs: 
[    0.000001] CPU#0 had -102 usecs TSC skew, fixed it up.
[    0.000003] CPU#1 had 102 usecs TSC skew, fixed it up.
[    0.003989] Brought up 2 CPUs
[    0.096932] migration_cost=347
[    0.097160] Booting paravirtualized kernel on bare hardware
[    0.097261] Time:  5:47:19  Date: 06/20/107
[    0.097296] NET: Registered protocol family 16
[    0.097372] EISA bus registered
[    0.097375] ACPI: bus type pci registered
[    0.098086] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[    0.098088] PCI: Using configuration type 1
[    0.098089] Setting up standard PCI resources
[    0.107847] ACPI: Interpreter enabled
[    0.107850] ACPI: Using IOAPIC for interrupt routing
[    0.108700] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.108704] PCI: Probing PCI hardware (bus 00)
[    0.109496] PCI: enabled onboard AC97/MC97 devices
[    0.109692] Boot video device is 0000:01:00.0
[    0.109751] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.124410] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 14 15)
[    0.124618] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 14 15)
[    0.124821] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 11 14 15)
[    0.125025] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.125233] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.125436] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.125648] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.125852] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.125948] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.125957] pnp: PnP ACPI init
[    0.129564] pnp: PnP ACPI: found 13 devices
[    0.129568] PnPBIOS: Disabled by ACPI PNP
[    0.129612] PCI: Using ACPI for IRQ routing
[    0.129614] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.134148] NET: Registered protocol family 8
[    0.134149] NET: Registered protocol family 20
[    0.134703] pnp: 00:07: ioport range 0x680-0x6ff has been reserved
[    0.134705] pnp: 00:07: ioport range 0x290-0x297 has been reserved
[    0.134907] PCI: Bridge: 0000:00:01.0
[    0.134910]   IO window: e000-efff
[    0.134914]   MEM window: fbd00000-fbffffff
[    0.134917]   PREFETCH window: e8000000-faffffff
[    0.134933] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.134980] NET: Registered protocol family 2
[    0.187717] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.187889] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.188695] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.189064] TCP: Hash tables configured (established 131072 bind 65536)
[    0.189066] TCP reno registered
[    0.203741] checking if image is initramfs... it is
[    0.720586] Freeing initrd memory: 7038k freed
[    1.288000] audit: initializing netlink socket (disabled)
[    1.288000] audit(1184910439.472:1): initialized
[    1.288000] highmem bounce pool size: 64 pages
[    1.288000] VFS: Disk quotas dquot_6.5.1
[    1.288000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.288000] io scheduler noop registered
[    1.288000] io scheduler anticipatory registered
[    1.288000] io scheduler deadline registered
[    1.288000] io scheduler cfq registered (default)
[    1.312000] isapnp: Scanning for PnP cards...
[    1.664000] isapnp: No Plug & Play device found
[    1.684000] Real Time Clock Driver v1.12ac
[    1.684000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.684000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.684000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.684000] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.684000] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.684000] mice: PS/2 mouse device common for all mice
[    1.684000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.684000] input: Macintosh mouse button emulation as /class/input/input0
[    1.684000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.684000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.688000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.688000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[    1.688000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.688000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.688000] EISA: Probing bus 0 at eisa.0
[    1.688000] Cannot allocate resource for EISA slot 1
[    1.688000] Cannot allocate resource for EISA slot 8
[    1.688000] EISA: Detected 0 cards.
[    1.708000] input: AT Translated Set 2 keyboard as /class/input/input1
[    1.716000] TCP cubic registered
[    1.716000] NET: Registered protocol family 1
[    1.716000] Starting balanced_irq
[    1.716000] Using IPI No-Shortcut mode
[    1.716000] ACPI: (supports S0 S1 S3 S4 S5)
[    1.716000]   Magic number: 15:272:770
[    1.716000]   hash matches device ptyp6
[    1.716000] Freeing unused kernel memory: 328k freed
[    1.720000] Time: acpi_pm clocksource has been installed.
[    2.916000] Capability LSM initialized
[    3.152000] md: raid0 personality registered for level 0
[    3.416000] SCSI subsystem initialized
[    3.420000] libata version 2.20 loaded.
[    3.484000] sata_via 0000:00:0f.0: version 2.1
[    3.484000] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 16
[    3.484000] sata_via 0000:00:0f.0: routed to hard irq line 10
[    3.484000] ata1: SATA max UDMA/133 cmd 0x0001c000 ctl 0x0001b802 bmdma 0x0001a800 irq 16
[    3.484000] ata2: SATA max UDMA/133 cmd 0x0001b400 ctl 0x0001b002 bmdma 0x0001a808 irq 16
[    3.484000] scsi0 : sata_via
[    3.508000] ieee1394: Initialized config rom entry `ip1394'
[    3.508000] usbcore: registered new interface driver usbfs
[    3.508000] usbcore: registered new interface driver hub
[    3.508000] usbcore: registered new device driver usb
[    3.520000] Floppy drive(s): fd0 is 1.44M
[    3.520000] USB Universal Host Controller Interface driver v3.0
[    3.540000] FDC 0 is a post-1991 82077
[    3.688000] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    3.700000] ATA: abnormal status 0x7F on port 0x0001c007
[    3.700000] scsi1 : sata_via
[    3.904000] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    3.916000] ATA: abnormal status 0x7F on port 0x0001b407
[    3.916000] ACPI: PCI Interrupt 0000:00:07.0[A] -> GSI 16 (level, low) -> IRQ 17
[    3.972000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[17]  MMIO=[fb600000-fb6007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.976000] sata_promise 0000:00:08.0: version 2.01
[    3.976000] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 18 (level, low) -> IRQ 18
[    3.976000] sata_promise PATA port found
[    3.992000] ata3: SATA max UDMA/133 cmd 0xf893a200 ctl 0xf893a238 bmdma 0x00000000 irq 18
[    3.992000] ata4: SATA max UDMA/133 cmd 0xf893a280 ctl 0xf893a2b8 bmdma 0x00000000 irq 18
[    3.992000] ata5: PATA max UDMA/133 cmd 0xf893a300 ctl 0xf893a338 bmdma 0x00000000 irq 18
[    3.992000] scsi2 : sata_promise
[    4.460000] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.472000] ata3.00: ATA-7: SAMSUNG SP2504C, VT100-54, max UDMA7
[    4.472000] ata3.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[    4.484000] ata3.00: configured for UDMA/133
[    4.484000] scsi3 : sata_promise
[    4.952000] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.964000] ata4.00: ATA-7: SAMSUNG SP2504C, VT100-54, max UDMA7
[    4.964000] ata4.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[    4.972000] ata4.00: configured for UDMA/133
[    4.976000] scsi4 : sata_promise
[    5.132000] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG SP2504C  VT10 PQ: 0 ANSI: 5
[    5.136000] scsi 3:0:0:0: Direct-Access     ATA      SAMSUNG SP2504C  VT10 PQ: 0 ANSI: 5
[    5.136000] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 19
[    5.136000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    5.136000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[    5.136000] uhci_hcd 0000:00:10.0: irq 19, io base 0x0000c400
[    5.136000] usb usb1: configuration #1 chosen from 1 choice
[    5.136000] hub 1-0:1.0: USB hub found
[    5.136000] hub 1-0:1.0: 2 ports detected
[    5.244000] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 19
[    5.244000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    5.244000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[    5.244000] uhci_hcd 0000:00:10.1: irq 19, io base 0x0000c800
[    5.244000] usb usb2: configuration #1 chosen from 1 choice
[    5.244000] hub 2-0:1.0: USB hub found
[    5.244000] hub 2-0:1.0: 2 ports detected
[    5.252000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0180000b9b54b]
[    5.352000] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 19
[    5.352000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    5.352000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[    5.352000] uhci_hcd 0000:00:10.2: irq 19, io base 0x0000d000
[    5.352000] usb usb3: configuration #1 chosen from 1 choice
[    5.352000] hub 3-0:1.0: USB hub found
[    5.352000] hub 3-0:1.0: 2 ports detected
[    5.460000] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 19
[    5.460000] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    5.460000] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[    5.460000] uhci_hcd 0000:00:10.3: irq 19, io base 0x0000d400
[    5.460000] usb usb4: configuration #1 chosen from 1 choice
[    5.460000] hub 4-0:1.0: USB hub found
[    5.460000] hub 4-0:1.0: 2 ports detected
[    5.568000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 17 (level, low) -> IRQ 20
[    5.568000] skge 1.9 addr 0xfba00000 irq 20 chip Yukon-Lite rev 7
[    5.568000] skge eth0: addr 00:11:2f:f6:5e:e6
[    5.568000] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[    5.568000] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 16
[    5.568000] VP_IDE: chipset revision 6
[    5.568000] VP_IDE: not 100% native mode: will probe irqs later
[    5.568000] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[    5.568000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:pio, hdb:pio
[    5.568000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:pio
[    5.568000] Probing IDE interface ide0...
[    5.584000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[    5.584000] sda: Write Protect is off
[    5.584000] sda: Mode Sense: 00 3a 00 00
[    5.584000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.584000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[    5.584000] sda: Write Protect is off
[    5.584000] sda: Mode Sense: 00 3a 00 00
[    5.584000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.584000]  sda: sda1 sda2 sda3 < sda5 sda6 > sda4
[    5.656000] sd 2:0:0:0: Attached scsi disk sda
[    5.656000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[    5.656000] sdb: Write Protect is off
[    5.656000] sdb: Mode Sense: 00 3a 00 00
[    5.656000] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.656000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[    5.656000] sdb: Write Protect is off
[    5.656000] sdb: Mode Sense: 00 3a 00 00
[    5.656000] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.656000]  sdb: sdb1 sdb2 sdb3 < sdb5 sdb6 sdb7 >
[    5.732000] sd 3:0:0:0: Attached scsi disk sdb
[    5.736000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    5.736000] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    5.740000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    5.848000] md: md0 stopped.
[    5.924000] md: bind<sdb1>
[    5.928000] md: bind<sda1>
[    5.928000] usb 2-1: configuration #1 chosen from 1 choice
[    5.932000] md0: setting max_sectors to 128, segment boundary to 32767
[    5.932000] raid0: looking at sda1
[    5.932000] raid0:   comparing sda1(24410624) with sda1(24410624)
[    5.932000] raid0:   END
[    5.932000] raid0:   ==> UNIQUE
[    5.932000] raid0: 1 zones
[    5.932000] raid0: looking at sdb1
[    5.932000] raid0:   comparing sdb1(24410624) with sda1(24410624)
[    5.932000] raid0:   EQUAL
[    5.932000] raid0: FINAL 1 zones
[    5.932000] raid0: done.
[    5.932000] raid0 : md_size is 48821248 blocks.
[    5.932000] raid0 : conf->hash_spacing is 48821248 blocks.
[    5.932000] raid0 : nb_zone is 1.
[    5.932000] raid0 : Allocating 4 bytes for hash.
[    5.932000] md: md1 stopped.
[    5.984000] md: md1 stopped.
[    5.996000] md: bind<sdb5>
[    5.996000] md: bind<sda5>
[    6.000000] md1: setting max_sectors to 128, segment boundary to 32767
[    6.000000] raid0: looking at sda5
[    6.000000] raid0:   comparing sda5(97659008) with sda5(97659008)
[    6.000000] raid0:   END
[    6.000000] raid0:   ==> UNIQUE
[    6.000000] raid0: 1 zones
[    6.000000] raid0: looking at sdb5
[    6.000000] raid0:   comparing sdb5(97659008) with sda5(97659008)
[    6.000000] raid0:   EQUAL
[    6.000000] raid0: FINAL 1 zones
[    6.000000] raid0: done.
[    6.000000] raid0 : md_size is 195318016 blocks.
[    6.000000] raid0 : conf->hash_spacing is 195318016 blocks.
[    6.000000] raid0 : nb_zone is 1.
[    6.000000] raid0 : Allocating 4 bytes for hash.
[    6.076000] Attempting manual resume
[    6.076000] swsusp: Resume From Partition 8:2
[    6.076000] PM: Checking swsusp image.
[    6.076000] PM: Resume from disk failed.
[    6.084000] EXT3-fs: INFO: recovery required on readonly filesystem.
[    6.084000] EXT3-fs: write access will be enabled during recovery.
[    6.140000] Probing IDE interface ide1...
[    7.008000] hdc: HL-DT-ST DVDRAM GSA-H42N, ATAPI CD/DVD-ROM drive
[    7.348000] ide1 at 0x170-0x177,0x376 on irq 15
[    7.352000] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 19
[    7.352000] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    7.352000] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[    7.352000] ehci_hcd 0000:00:10.4: irq 19, io mem 0xfbc00000
[    7.352000] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    7.352000] usb usb5: configuration #1 chosen from 1 choice
[    7.352000] hub 5-0:1.0: USB hub found
[    7.352000] hub 5-0:1.0: 8 ports detected
[    7.360000] hdc: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
[    7.360000] Uniform CD-ROM driver Revision: 3.20
[    7.368000] usb 2-1: USB disconnect, address 2
[    7.680000] usbcore: registered new interface driver hiddev
[    7.684000] usbcore: registered new interface driver usbhid
[    7.684000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[    8.112000] usb 2-1: new low speed USB device using uhci_hcd and address 3
[    8.296000] usb 2-1: configuration #1 chosen from 1 choice
[    8.316000] input: Razer Razer Diamonback Optical Mouse as /class/input/input2
[    8.316000] input: USB HID v1.10 Mouse [Razer Razer Diamonback Optical Mouse] on usb-0000:00:10.1-1
[    8.452000] kjournald starting.  Commit interval 5 seconds
[    8.452000] EXT3-fs: recovery complete.
[    8.460000] EXT3-fs: mounted filesystem with ordered data mode.
[   14.608000] skge eth0: enabling interface
[   15.372000] md: bind<sdb6>
[   15.372000] md: bind<sda6>
[   15.436000] md2: setting max_sectors to 8, segment boundary to 2047
[   15.436000] blk_queue_segment_boundary: set to minimum fff
[   15.436000] raid0: looking at sda6
[   15.436000] raid0:   comparing sda6(48829440) with sda6(48829440)
[   15.436000] raid0:   END
[   15.436000] raid0:   ==> UNIQUE
[   15.436000] raid0: 1 zones
[   15.436000] raid0: looking at sdb6
[   15.436000] raid0:   comparing sdb6(48829440) with sda6(48829440)
[   15.436000] raid0:   EQUAL
[   15.436000] raid0: FINAL 1 zones
[   15.436000] raid0: done.
[   15.436000] raid0 : md_size is 97658880 blocks.
[   15.436000] raid0 : conf->hash_spacing is 97658880 blocks.
[   15.436000] raid0 : nb_zone is 1.
[   15.436000] raid0 : Allocating 4 bytes for hash.
[   15.860000] Linux agpgart interface v0.102 (c) Dave Jones
[   15.924000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.048000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.116000] agpgart: Detected AGP bridge 0
[   16.120000] agpgart: AGP aperture is 64M @ 0xe4000000
[   16.132000] input: PC Speaker as /class/input/input3
[   16.140000] NET: Registered protocol family 17
[   16.424000] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 21
[   16.424000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   16.944000] PCI: Enabling device 0000:00:11.6 (0000 -> 0001)
[   16.944000] ACPI: PCI Interrupt 0000:00:11.6[C] -> GSI 22 (level, low) -> IRQ 21
[   17.112000] skge eth0: Link is up at 1000 Mbps, full duplex, flow control both
[   17.696000] PCI: Setting latency timer of device 0000:00:11.6 to 64
[   18.200000] ACPI: PCI interrupt for device 0000:00:11.6 disabled
[   18.200000] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
[   18.340000] lp: driver loaded but no devices found
[   18.544000] w83627hf 9191-0290: Reading VID from GPIO5
[   18.584000] Adding 586364k swap on /dev/disk/by-uuid/e574d3da-59bd-4dba-87c7-c0018ce9a3dc.  Priority:-1 extents:1 across:586364k
[   18.588000] Adding 586364k swap on /dev/disk/by-uuid/344740a6-d43e-4ee4-9619-ad4976b9384b.  Priority:-2 extents:1 across:586364k
[   18.744000] EXT3 FS on md0, internal journal
[   21.908000] kjournald starting.  Commit interval 5 seconds
[   21.908000] EXT3 FS on md1, internal journal
[   21.908000] EXT3-fs: mounted filesystem with ordered data mode.
[   21.952000] ReiserFS: md2: found reiserfs format "3.6" with standard journal
[   21.952000] ReiserFS: md2: using ordered data mode
[   21.956000] ReiserFS: md2: journal params: device md2, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   21.956000] ReiserFS: md2: checking transaction log (md2)
[   22.356000] ReiserFS: md2: replayed 132 transactions in 1 seconds
[   22.380000] ReiserFS: md2: Using r5 hash to sort names

```

last /var/log/syslog
```
Jul 19 22:59:44 bean dhclient: DHCPACK from 192.168.0.1
Jul 19 22:59:44 bean NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
Jul 19 22:59:44 bean dhclient: bound to 192.168.0.20 -- renewal in 1479 seconds.
Jul 19 23:17:01 bean /USR/SBIN/CRON[8208]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 19 23:24:23 bean dhclient: DHCPREQUEST on eth0 to 192.168.0.1 port 67
Jul 19 23:24:23 bean dhclient: DHCPACK from 192.168.0.1
Jul 19 23:24:23 bean NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
Jul 19 23:24:23 bean dhclient: bound to 192.168.0.20 -- renewal in 1789 seconds.
Jul 19 23:31:26 bean gconfd (root-8687): (Version 2.18.0.1) wird gestartet, Prozesskennung 8687, Benutzer »root«
Jul 19 23:31:26 bean gconfd (root-8687): Die Adresse »xml:readonly:/etc/gconf/gconf.xml.mandatory« wurde an der Position 0 zu einer nur lesbaren Konfigurationsquelle a
ufgelöst
Jul 19 23:31:26 bean gconfd (root-8687): Die Adresse »xml:readwrite:/root/.gconf« wurde an der Position 1 zu einer schreibbaren Konfigurationsquelle aufgelöst
Jul 19 23:31:26 bean gconfd (root-8687): Die Adresse »xml:readonly:/etc/gconf/gconf.xml.defaults« wurde an der Position 2 zu einer nur lesbaren Konfigurationsquelle au
fgelöst
Jul 19 23:31:26 bean gconfd (root-8687): Die Adresse »xml:readonly:/var/lib/gconf/debian.defaults« wurde an der Position 3 zu einer nur lesbaren Konfigurationsquelle a
ufgelöst
Jul 19 23:31:26 bean gconfd (root-8687): Die Adresse »xml:readonly:/var/lib/gconf/defaults« wurde an der Position 4 zu einer nur lesbaren Konfigurationsquelle aufgelös
t
Jul 19 23:49:01 bean -- MARK --
Jul 19 23:54:12 bean dhclient: DHCPREQUEST on eth0 to 192.168.0.1 port 67
Jul 19 23:54:12 bean dhclient: DHCPACK from 192.168.0.1
Jul 19 23:54:12 bean NetworkManager: <information>^IDHCP daemon state is now 3 (renew) for interface eth0 
Jul 19 23:54:12 bean dhclient: bound to 192.168.0.20 -- renewal in 1669 seconds.

```

last /var/log/user.log
```
ul 19 22:09:28 bean gconfd (kaspi-5893): Die Adresse »xml:readwrite:/home/kaspi/.gconf« wurde an der Position 0 zu einer schreibbaren Konfigurationsquelle aufgelöst
Jul 19 22:54:59 bean gconfd (root-7392): (Version 2.18.0.1) wird gestartet, Prozesskennung 7392, Benutzer »root«
Jul 19 22:54:59 bean gconfd (root-7392): Die Adresse »xml:readonly:/etc/gconf/gconf.xml.mandatory« wurde an der Position 0 zu einer nur lesbaren Konfigurationsquelle a
ufgelöst
Jul 19 22:54:59 bean gconfd (root-7392): Die Adresse »xml:readwrite:/root/.gconf« wurde an der Position 1 zu einer schreibbaren Konfigurationsquelle aufgelöst
Jul 19 22:54:59 bean gconfd (root-7392): Die Adresse »xml:readonly:/etc/gconf/gconf.xml.defaults« wurde an der Position 2 zu einer nur lesbaren Konfigurationsquelle au
fgelöst
Jul 19 22:54:59 bean gconfd (root-7392): Die Adresse »xml:readonly:/var/lib/gconf/debian.defaults« wurde an der Position 3 zu einer nur lesbaren Konfigurationsquelle a
ufgelöst
Jul 19 22:54:59 bean gconfd (root-7392): Die Adresse »xml:readonly:/var/lib/gconf/defaults« wurde an der Position 4 zu einer nur lesbaren Konfigurationsquelle aufgelös
t
Jul 19 22:55:29 bean gconfd (root-7392): SIGHUP empfangen, alle Datenbanken werden neu geladen
Jul 19 22:55:29 bean gconfd (root-7392): Die Adresse »xml:readonly:/etc/gconf/gconf.xml.mandatory« wurde an der Position 0 zu einer nur lesbaren Konfigurationsquelle a
ufgelöst
Jul 19 22:55:29 bean gconfd (root-7392): Die Adresse »xml:readwrite:/root/.gconf« wurde an der Position 1 zu einer schreibbaren Konfigurationsquelle aufgelöst
Jul 19 22:55:29 bean gconfd (root-7392): Die Adresse »xml:readonly:/etc/gconf/gconf.xml.defaults« wurde an der Position 2 zu einer nur lesbaren Konfigurationsquelle au
fgelöst
Jul 19 22:55:29 bean gconfd (root-7392): Die Adresse »xml:readonly:/var/lib/gconf/debian.defaults« wurde an der Position 3 zu einer nur lesbaren Konfigurationsquelle a
ufgelöst
Jul 19 22:55:29 bean gconfd (root-7392): Die Adresse »xml:readonly:/var/lib/gconf/defaults« wurde an der Position 4 zu einer nur lesbaren Konfigurationsquelle aufgelös
t
Jul 19 22:55:29 bean gconfd (root-7392): Der GConf-Server wird nicht verwendet und daher beendet.
Jul 19 22:55:29 bean gconfd (root-7392): Beenden
Jul 19 23:31:26 bean gconfd (root-8687): (Version 2.18.0.1) wird gestartet, Prozesskennung 8687, Benutzer »root«
Jul 19 23:31:26 bean gconfd (root-8687): Die Adresse »xml:readonly:/etc/gconf/gconf.xml.mandatory« wurde an der Position 0 zu einer nur lesbaren Konfigurationsquelle a
ufgelöst
Jul 19 23:31:26 bean gconfd (root-8687): Die Adresse »xml:readwrite:/root/.gconf« wurde an der Position 1 zu einer schreibbaren Konfigurationsquelle aufgelöst
Jul 19 23:31:26 bean gconfd (root-8687): Die Adresse »xml:readonly:/etc/gconf/gconf.xml.defaults« wurde an der Position 2 zu einer nur lesbaren Konfigurationsquelle au
fgelöst
Jul 19 23:31:26 bean gconfd (root-8687): Die Adresse »xml:readonly:/var/lib/gconf/debian.defaults« wurde an der Position 3 zu einer nur lesbaren Konfigurationsquelle a
ufgelöst
Jul 19 23:31:26 bean gconfd (root-8687): Die Adresse »xml:readonly:/var/lib/gconf/defaults« wurde an der Position 4 zu einer nur lesbaren Konfigurationsquelle aufgelös
t

```

dmesg
```
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e4000 size: 000000000001c000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000009feb0000 end: 000000009ffb0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000009ffb0000 size: 0000000000010000 end: 000000009ffc0000 type: 3
[    0.000000] copy_e820_map() start: 000000009ffc0000 size: 0000000000030000 end: 000000009fff0000 type: 4
[    0.000000] copy_e820_map() start: 000000009fff0000 size: 0000000000010000 end: 00000000a0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000ff780000 size: 0000000000880000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000009ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000009ffb0000 - 000000009ffc0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000009ffc0000 - 000000009fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009fff0000 - 00000000a0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] 1663MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 655280) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   655280
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   655280
[    0.000000] On node 0 totalpages: 655280
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 3327 pages used for memmap
[    0.000000]   HighMem zone: 422577 pages, LIFO batch:31
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v002 ACPIAM                                ) @ 0x000fa7c0
[    0.000000] ACPI: XSDT (v001 A M I  OEMXSDT  0x11000514 MSFT 0x00000097) @ 0x9ffb0100
[    0.000000] ACPI: FADT (v003 A M I  OEMFACP  0x11000514 MSFT 0x00000097) @ 0x9ffb0290
[    0.000000] ACPI: MADT (v001 A M I  OEMAPIC  0x11000514 MSFT 0x00000097) @ 0x9ffb0390
[    0.000000] ACPI: OEMB (v001 A M I  OEMBIOS  0x11000514 MSFT 0x00000097) @ 0x9ffc0040
[    0.000000] ACPI: DSDT (v001  A0036 A0036001 0x00000001 MSFT 0x0100000d) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:3 APIC version 16
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:3 APIC version 16
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at a8000000 (gap: a0000000:5f780000)
[    0.000000] Detected 2202.913 MHz processor.
[   28.769011] Built 1 zonelists.  Total pages: 650161
[   28.769014] Kernel command line: root=/dev/md0 ro quiet splash
[   28.769130] mapped APIC to ffffd000 (fee00000)
[   28.769132] mapped IOAPIC to ffffc000 (fec00000)
[   28.769135] Enabling fast FPU save and restore... done.
[   28.769137] Enabling unmasked SIMD FPU exception support... done.
[   28.769144] Initializing CPU#0
[   28.769218] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   28.770515] Console: colour VGA+ 80x25
[   28.770905] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   28.771274] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   28.847221] Memory: 2587680k/2621120k available (1992k kernel code, 32076k reserved, 900k data, 328k init, 1703616k highmem)
[   28.847230] virtual kernel memory layout:
[   28.847230]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   28.847232]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   28.847233]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   28.847234]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   28.847235]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   28.847236]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   28.847237]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   28.847240] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   28.924948] Calibrating delay using timer specific routine.. 4410.98 BogoMIPS (lpj=8821976)
[   28.924985] Security Framework v1.0.0 initialized
[   28.924992] SELinux:  Disabled at boot.
[   28.925007] Mount-cache hash table entries: 512
[   28.925134] CPU: After generic identify, caps: 178bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000003
[   28.925142] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   28.925144] CPU: L2 Cache: 512K (64 bytes/line)
[   28.925146] CPU 0(2) -> Core 0
[   28.925148] CPU: After all inits, caps: 178bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000003
[   28.925158] Compat vDSO mapped to ffffe000.
[   28.925162] Remapping vsyscall page to ffffe000
[   28.925171] Checking 'hlt' instruction... OK.
[   28.941056] SMP alternatives: switching to UP code
[   28.941444] Early unpacking initramfs... done
[   29.202898] ACPI: Core revision 20060707
[   29.203376] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   29.204942] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 02
[   29.204963] SMP alternatives: switching to SMP code
[   29.205052] Booting processor 1/1 eip 3000
[   29.215426] Initializing CPU#1
[   29.292492] Calibrating delay using timer specific routine.. 4405.98 BogoMIPS (lpj=8811963)
[   29.292502] CPU: After generic identify, caps: 178bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000003
[   29.292508] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   29.292510] CPU: L2 Cache: 512K (64 bytes/line)
[   29.292512] CPU 1(2) -> Core 1
[   29.292513] CPU: After all inits, caps: 178bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000003
[   29.292465] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 02
[   29.292482] Total of 2 processors activated (8816.96 BogoMIPS).
[   29.292942] ENABLING IO-APIC IRQs
[   29.293259] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[   29.440034] checking TSC synchronization across 2 CPUs: 
[    0.000001] CPU#0 had -102 usecs TSC skew, fixed it up.
[    0.000003] CPU#1 had 102 usecs TSC skew, fixed it up.
[    0.003989] Brought up 2 CPUs
[    0.096932] migration_cost=347
[    0.097160] Booting paravirtualized kernel on bare hardware
[    0.097261] Time:  5:47:19  Date: 06/20/107
[    0.097296] NET: Registered protocol family 16
[    0.097372] EISA bus registered
[    0.097375] ACPI: bus type pci registered
[    0.098086] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[    0.098088] PCI: Using configuration type 1
[    0.098089] Setting up standard PCI resources
[    0.107847] ACPI: Interpreter enabled
[    0.107850] ACPI: Using IOAPIC for interrupt routing
[    0.108700] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.108704] PCI: Probing PCI hardware (bus 00)
[    0.109496] PCI: enabled onboard AC97/MC97 devices
[    0.109692] Boot video device is 0000:01:00.0
[    0.109751] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.124410] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 14 15)
[    0.124618] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 14 15)
[    0.124821] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 11 14 15)
[    0.125025] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.125233] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.125436] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.125648] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.125852] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[    0.125948] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.125957] pnp: PnP ACPI init
[    0.129564] pnp: PnP ACPI: found 13 devices
[    0.129568] PnPBIOS: Disabled by ACPI PNP
[    0.129612] PCI: Using ACPI for IRQ routing
[    0.129614] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.134148] NET: Registered protocol family 8
[    0.134149] NET: Registered protocol family 20
[    0.134703] pnp: 00:07: ioport range 0x680-0x6ff has been reserved
[    0.134705] pnp: 00:07: ioport range 0x290-0x297 has been reserved
[    0.134907] PCI: Bridge: 0000:00:01.0
[    0.134910]   IO window: e000-efff
[    0.134914]   MEM window: fbd00000-fbffffff
[    0.134917]   PREFETCH window: e8000000-faffffff
[    0.134933] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.134980] NET: Registered protocol family 2
[    0.187717] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.187889] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.188695] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.189064] TCP: Hash tables configured (established 131072 bind 65536)
[    0.189066] TCP reno registered
[    0.203741] checking if image is initramfs... it is
[    0.720586] Freeing initrd memory: 7038k freed
[    1.288000] audit: initializing netlink socket (disabled)
[    1.288000] audit(1184910439.472:1): initialized
[    1.288000] highmem bounce pool size: 64 pages
[    1.288000] VFS: Disk quotas dquot_6.5.1
[    1.288000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.288000] io scheduler noop registered
[    1.288000] io scheduler anticipatory registered
[    1.288000] io scheduler deadline registered
[    1.288000] io scheduler cfq registered (default)
[    1.312000] isapnp: Scanning for PnP cards...
[    1.664000] isapnp: No Plug & Play device found
[    1.684000] Real Time Clock Driver v1.12ac
[    1.684000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.684000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.684000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.684000] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.684000] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.684000] mice: PS/2 mouse device common for all mice
[    1.684000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.684000] input: Macintosh mouse button emulation as /class/input/input0
[    1.684000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.684000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.688000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.688000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[    1.688000] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.688000] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.688000] EISA: Probing bus 0 at eisa.0
[    1.688000] Cannot allocate resource for EISA slot 1
[    1.688000] Cannot allocate resource for EISA slot 8
[    1.688000] EISA: Detected 0 cards.
[    1.708000] input: AT Translated Set 2 keyboard as /class/input/input1
[    1.716000] TCP cubic registered
[    1.716000] NET: Registered protocol family 1
[    1.716000] Starting balanced_irq
[    1.716000] Using IPI No-Shortcut mode
[    1.716000] ACPI: (supports S0 S1 S3 S4 S5)
[    1.716000]   Magic number: 15:272:770
[    1.716000]   hash matches device ptyp6
[    1.716000] Freeing unused kernel memory: 328k freed
[    1.720000] Time: acpi_pm clocksource has been installed.
[    2.916000] Capability LSM initialized
[    3.152000] md: raid0 personality registered for level 0
[    3.416000] SCSI subsystem initialized
[    3.420000] libata version 2.20 loaded.
[    3.484000] sata_via 0000:00:0f.0: version 2.1
[    3.484000] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 20 (level, low) -> IRQ 16
[    3.484000] sata_via 0000:00:0f.0: routed to hard irq line 10
[    3.484000] ata1: SATA max UDMA/133 cmd 0x0001c000 ctl 0x0001b802 bmdma 0x0001a800 irq 16
[    3.484000] ata2: SATA max UDMA/133 cmd 0x0001b400 ctl 0x0001b002 bmdma 0x0001a808 irq 16
[    3.484000] scsi0 : sata_via
[    3.508000] ieee1394: Initialized config rom entry `ip1394'
[    3.508000] usbcore: registered new interface driver usbfs
[    3.508000] usbcore: registered new interface driver hub
[    3.508000] usbcore: registered new device driver usb
[    3.520000] Floppy drive(s): fd0 is 1.44M
[    3.520000] USB Universal Host Controller Interface driver v3.0
[    3.540000] FDC 0 is a post-1991 82077
[    3.688000] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    3.700000] ATA: abnormal status 0x7F on port 0x0001c007
[    3.700000] scsi1 : sata_via
[    3.904000] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[    3.916000] ATA: abnormal status 0x7F on port 0x0001b407
[    3.916000] ACPI: PCI Interrupt 0000:00:07.0[A] -> GSI 16 (level, low) -> IRQ 17
[    3.972000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[17]  MMIO=[fb600000-fb6007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.976000] sata_promise 0000:00:08.0: version 2.01
[    3.976000] ACPI: PCI Interrupt 0000:00:08.0[A] -> GSI 18 (level, low) -> IRQ 18
[    3.976000] sata_promise PATA port found
[    3.992000] ata3: SATA max UDMA/133 cmd 0xf893a200 ctl 0xf893a238 bmdma 0x00000000 irq 18
[    3.992000] ata4: SATA max UDMA/133 cmd 0xf893a280 ctl 0xf893a2b8 bmdma 0x00000000 irq 18
[    3.992000] ata5: PATA max UDMA/133 cmd 0xf893a300 ctl 0xf893a338 bmdma 0x00000000 irq 18
[    3.992000] scsi2 : sata_promise
[    4.460000] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.472000] ata3.00: ATA-7: SAMSUNG SP2504C, VT100-54, max UDMA7
[    4.472000] ata3.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[    4.484000] ata3.00: configured for UDMA/133
[    4.484000] scsi3 : sata_promise
[    4.952000] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.964000] ata4.00: ATA-7: SAMSUNG SP2504C, VT100-54, max UDMA7
[    4.964000] ata4.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[    4.972000] ata4.00: configured for UDMA/133
[    4.976000] scsi4 : sata_promise
[    5.132000] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG SP2504C  VT10 PQ: 0 ANSI: 5
[    5.136000] scsi 3:0:0:0: Direct-Access     ATA      SAMSUNG SP2504C  VT10 PQ: 0 ANSI: 5
[    5.136000] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 19
[    5.136000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    5.136000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[    5.136000] uhci_hcd 0000:00:10.0: irq 19, io base 0x0000c400
[    5.136000] usb usb1: configuration #1 chosen from 1 choice
[    5.136000] hub 1-0:1.0: USB hub found
[    5.136000] hub 1-0:1.0: 2 ports detected
[    5.244000] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 21 (level, low) -> IRQ 19
[    5.244000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    5.244000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[    5.244000] uhci_hcd 0000:00:10.1: irq 19, io base 0x0000c800
[    5.244000] usb usb2: configuration #1 chosen from 1 choice
[    5.244000] hub 2-0:1.0: USB hub found
[    5.244000] hub 2-0:1.0: 2 ports detected
[    5.252000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0180000b9b54b]
[    5.352000] ACPI: PCI Interrupt 0000:00:10.2[B] -> GSI 21 (level, low) -> IRQ 19
[    5.352000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    5.352000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[    5.352000] uhci_hcd 0000:00:10.2: irq 19, io base 0x0000d000
[    5.352000] usb usb3: configuration #1 chosen from 1 choice
[    5.352000] hub 3-0:1.0: USB hub found
[    5.352000] hub 3-0:1.0: 2 ports detected
[    5.460000] ACPI: PCI Interrupt 0000:00:10.3[B] -> GSI 21 (level, low) -> IRQ 19
[    5.460000] uhci_hcd 0000:00:10.3: UHCI Host Controller
[    5.460000] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[    5.460000] uhci_hcd 0000:00:10.3: irq 19, io base 0x0000d400
[    5.460000] usb usb4: configuration #1 chosen from 1 choice
[    5.460000] hub 4-0:1.0: USB hub found
[    5.460000] hub 4-0:1.0: 2 ports detected
[    5.568000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 17 (level, low) -> IRQ 20
[    5.568000] skge 1.9 addr 0xfba00000 irq 20 chip Yukon-Lite rev 7
[    5.568000] skge eth0: addr 00:11:2f:f6:5e:e6
[    5.568000] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[    5.568000] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 20 (level, low) -> IRQ 16
[    5.568000] VP_IDE: chipset revision 6
[    5.568000] VP_IDE: not 100% native mode: will probe irqs later
[    5.568000] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[    5.568000]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:pio, hdb:pio
[    5.568000]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:DMA, hdd:pio
[    5.568000] Probing IDE interface ide0...
[    5.584000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[    5.584000] sda: Write Protect is off
[    5.584000] sda: Mode Sense: 00 3a 00 00
[    5.584000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.584000] SCSI device sda: 488397168 512-byte hdwr sectors (250059 MB)
[    5.584000] sda: Write Protect is off
[    5.584000] sda: Mode Sense: 00 3a 00 00
[    5.584000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.584000]  sda: sda1 sda2 sda3 < sda5 sda6 > sda4
[    5.656000] sd 2:0:0:0: Attached scsi disk sda
[    5.656000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[    5.656000] sdb: Write Protect is off
[    5.656000] sdb: Mode Sense: 00 3a 00 00
[    5.656000] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.656000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[    5.656000] sdb: Write Protect is off
[    5.656000] sdb: Mode Sense: 00 3a 00 00
[    5.656000] SCSI device sdb: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.656000]  sdb: sdb1 sdb2 sdb3 < sdb5 sdb6 sdb7 >
[    5.732000] sd 3:0:0:0: Attached scsi disk sdb
[    5.736000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    5.736000] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    5.740000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    5.848000] md: md0 stopped.
[    5.924000] md: bind<sdb1>
[    5.928000] md: bind<sda1>
[    5.928000] usb 2-1: configuration #1 chosen from 1 choice
[    5.932000] md0: setting max_sectors to 128, segment boundary to 32767
[    5.932000] raid0: looking at sda1
[    5.932000] raid0:   comparing sda1(24410624) with sda1(24410624)
[    5.932000] raid0:   END
[    5.932000] raid0:   ==> UNIQUE
[    5.932000] raid0: 1 zones
[    5.932000] raid0: looking at sdb1
[    5.932000] raid0:   comparing sdb1(24410624) with sda1(24410624)
[    5.932000] raid0:   EQUAL
[    5.932000] raid0: FINAL 1 zones
[    5.932000] raid0: done.
[    5.932000] raid0 : md_size is 48821248 blocks.
[    5.932000] raid0 : conf->hash_spacing is 48821248 blocks.
[    5.932000] raid0 : nb_zone is 1.
[    5.932000] raid0 : Allocating 4 bytes for hash.
[    5.932000] md: md1 stopped.
[    5.984000] md: md1 stopped.
[    5.996000] md: bind<sdb5>
[    5.996000] md: bind<sda5>
[    6.000000] md1: setting max_sectors to 128, segment boundary to 32767
[    6.000000] raid0: looking at sda5
[    6.000000] raid0:   comparing sda5(97659008) with sda5(97659008)
[    6.000000] raid0:   END
[    6.000000] raid0:   ==> UNIQUE
[    6.000000] raid0: 1 zones
[    6.000000] raid0: looking at sdb5
[    6.000000] raid0:   comparing sdb5(97659008) with sda5(97659008)
[    6.000000] raid0:   EQUAL
[    6.000000] raid0: FINAL 1 zones
[    6.000000] raid0: done.
[    6.000000] raid0 : md_size is 195318016 blocks.
[    6.000000] raid0 : conf->hash_spacing is 195318016 blocks.
[    6.000000] raid0 : nb_zone is 1.
[    6.000000] raid0 : Allocating 4 bytes for hash.
[    6.076000] Attempting manual resume
[    6.076000] swsusp: Resume From Partition 8:2
[    6.076000] PM: Checking swsusp image.
[    6.076000] PM: Resume from disk failed.
[    6.084000] EXT3-fs: INFO: recovery required on readonly filesystem.
[    6.084000] EXT3-fs: write access will be enabled during recovery.
[    6.140000] Probing IDE interface ide1...
[    7.008000] hdc: HL-DT-ST DVDRAM GSA-H42N, ATAPI CD/DVD-ROM drive
[    7.348000] ide1 at 0x170-0x177,0x376 on irq 15
[    7.352000] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 19
[    7.352000] ehci_hcd 0000:00:10.4: EHCI Host Controller
[    7.352000] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[    7.352000] ehci_hcd 0000:00:10.4: irq 19, io mem 0xfbc00000
[    7.352000] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    7.352000] usb usb5: configuration #1 chosen from 1 choice
[    7.352000] hub 5-0:1.0: USB hub found
[    7.352000] hub 5-0:1.0: 8 ports detected
[    7.360000] hdc: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
[    7.360000] Uniform CD-ROM driver Revision: 3.20
[    7.368000] usb 2-1: USB disconnect, address 2
[    7.680000] usbcore: registered new interface driver hiddev
[    7.684000] usbcore: registered new interface driver usbhid
[    7.684000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[    8.112000] usb 2-1: new low speed USB device using uhci_hcd and address 3
[    8.296000] usb 2-1: configuration #1 chosen from 1 choice
[    8.316000] input: Razer Razer Diamonback Optical Mouse as /class/input/input2
[    8.316000] input: USB HID v1.10 Mouse [Razer Razer Diamonback Optical Mouse] on usb-0000:00:10.1-1
[    8.452000] kjournald starting.  Commit interval 5 seconds
[    8.452000] EXT3-fs: recovery complete.
[    8.460000] EXT3-fs: mounted filesystem with ordered data mode.
[   14.608000] skge eth0: enabling interface
[   15.372000] md: bind<sdb6>
[   15.372000] md: bind<sda6>
[   15.436000] md2: setting max_sectors to 8, segment boundary to 2047
[   15.436000] blk_queue_segment_boundary: set to minimum fff
[   15.436000] raid0: looking at sda6
[   15.436000] raid0:   comparing sda6(48829440) with sda6(48829440)
[   15.436000] raid0:   END
[   15.436000] raid0:   ==> UNIQUE
[   15.436000] raid0: 1 zones
[   15.436000] raid0: looking at sdb6
[   15.436000] raid0:   comparing sdb6(48829440) with sda6(48829440)
[   15.436000] raid0:   EQUAL
[   15.436000] raid0: FINAL 1 zones
[   15.436000] raid0: done.
[   15.436000] raid0 : md_size is 97658880 blocks.
[   15.436000] raid0 : conf->hash_spacing is 97658880 blocks.
[   15.436000] raid0 : nb_zone is 1.
[   15.436000] raid0 : Allocating 4 bytes for hash.
[   15.860000] Linux agpgart interface v0.102 (c) Dave Jones
[   15.924000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.048000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.116000] agpgart: Detected AGP bridge 0
[   16.120000] agpgart: AGP aperture is 64M @ 0xe4000000
[   16.132000] input: PC Speaker as /class/input/input3
[   16.140000] NET: Registered protocol family 17
[   16.424000] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 21
[   16.424000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   16.944000] PCI: Enabling device 0000:00:11.6 (0000 -> 0001)
[   16.944000] ACPI: PCI Interrupt 0000:00:11.6[C] -> GSI 22 (level, low) -> IRQ 21
[   17.112000] skge eth0: Link is up at 1000 Mbps, full duplex, flow control both
[   17.696000] PCI: Setting latency timer of device 0000:00:11.6 to 64
[   18.200000] ACPI: PCI interrupt for device 0000:00:11.6 disabled
[   18.200000] VIA 82xx Modem: probe of 0000:00:11.6 failed with error -13
[   18.340000] lp: driver loaded but no devices found
[   18.544000] w83627hf 9191-0290: Reading VID from GPIO5
[   18.584000] Adding 586364k swap on /dev/disk/by-uuid/e574d3da-59bd-4dba-87c7-c0018ce9a3dc.  Priority:-1 extents:1 across:586364k
[   18.588000] Adding 586364k swap on /dev/disk/by-uuid/344740a6-d43e-4ee4-9619-ad4976b9384b.  Priority:-2 extents:1 across:586364k
[   18.744000] EXT3 FS on md0, internal journal
[   21.908000] kjournald starting.  Commit interval 5 seconds
[   21.908000] EXT3 FS on md1, internal journal
[   21.908000] EXT3-fs: mounted filesystem with ordered data mode.
[   21.952000] ReiserFS: md2: found reiserfs format "3.6" with standard journal
[   21.952000] ReiserFS: md2: using ordered data mode
[   21.956000] ReiserFS: md2: journal params: device md2, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   21.956000] ReiserFS: md2: checking transaction log (md2)
[   22.356000] ReiserFS: md2: replayed 132 transactions in 1 seconds
[   22.380000] ReiserFS: md2: Using r5 hash to sort names

```

last /var/log/kern.log
```
Jul 19 22:09:05 bean kernel: [   28.568000] /dev/vmnet: port on hub 8 successfully opened
Jul 19 22:09:05 bean kernel: [   28.904000] Bluetooth: Core ver 2.11
Jul 19 22:09:05 bean kernel: [   28.904000] NET: Registered protocol family 31
Jul 19 22:09:05 bean kernel: [   28.904000] Bluetooth: HCI device and connection manager initialized
Jul 19 22:09:05 bean kernel: [   28.904000] Bluetooth: HCI socket layer initialized
Jul 19 22:09:05 bean kernel: [   28.912000] Bluetooth: L2CAP ver 2.8
Jul 19 22:09:05 bean kernel: [   28.912000] Bluetooth: L2CAP socket layer initialized
Jul 19 22:09:05 bean kernel: [   29.028000] Bluetooth: RFCOMM socket layer initialized
Jul 19 22:09:05 bean kernel: [   29.028000] Bluetooth: RFCOMM TTY layer initialized
Jul 19 22:09:05 bean kernel: [   29.028000] Bluetooth: RFCOMM ver 1.8
Jul 19 22:09:15 bean kernel: [   38.476000] eth0: no IPv6 routers present
Jul 19 22:09:15 bean kernel: [   38.524000] /dev/vmnet: open called by PID 5819 (vmnet-netifup)
Jul 19 22:09:15 bean kernel: [   38.524000] /dev/vmnet: hub 1 does not exist, allocating memory.
Jul 19 22:09:15 bean kernel: [   38.524000] /dev/vmnet: port on hub 1 successfully opened
Jul 19 22:09:15 bean kernel: [   38.528000] /dev/vmnet: open called by PID 5820 (vmnet-netifup)
Jul 19 22:09:15 bean kernel: [   38.528000] /dev/vmnet: port on hub 8 successfully opened
Jul 19 22:09:15 bean kernel: [   38.624000] /dev/vmnet: open called by PID 5841 (vmnet-dhcpd)
Jul 19 22:09:15 bean kernel: [   38.624000] /dev/vmnet: port on hub 8 successfully opened
Jul 19 22:09:15 bean kernel: [   38.628000] /dev/vmnet: open called by PID 5842 (vmnet-dhcpd)
Jul 19 22:09:15 bean kernel: [   38.628000] /dev/vmnet: port on hub 1 successfully opened
Jul 19 22:09:25 bean kernel: [   48.968000] vmnet8: no IPv6 routers present
Jul 19 22:09:26 bean kernel: [   49.224000] vmnet1: no IPv6 routers present

```

---

### Post by kngunn on 2007-07-20
A couple of quick suggestions:

1) It could be the RAM -- maybe a stray bit of voltage got it during the upgrades.  I would try testing it.

2) Try running from the LiveCD.  It is NOT definitive, but it does help isolate software from hardware as the issue (i.e.:  if the LiveCD freezes after a while it's probably hardware, if not, think software or configuration).

Good luck!

---

### Post by Snifffurt on 2007-07-20
Hello

> 1) It could be the RAM -- maybe a stray bit of voltage got it during the upgrades. I would try testing it.

This would be possible, your right. I'll run a ram check this night.

> 2) Try running from the LiveCD. It is NOT definitive, but it does help isolate software from hardware as the issue (i.e.: if the LiveCD freezes after a while it's probably hardware, if not, think software or configuration).
I'll try this too with knoppix soon.

But there is another possible reason I found. I've noticed that the AGP card was not well in the slot. The little white clip at the end of the AGP slot was not hooked in. I fixed this now. I hope it was just this.
Because of the need of verification I'll go on trying to run the given system as is, to see if it still freezes.

Thank you so much for your answer.

Regards

Sniff

---

### Post by Snifffurt on 2007-07-21
Hello

Sadly it was not the AGP card. Runnig memtest the whole day recovered an error. But I can't figure out wich bar it is? Do I have to test all my bars one after another or can you help me tell wich one it might be from the result of memtest:

Tst
6
Pass
1
Failing Adress
0003a7343fc     935.2MB
Good
00000008
Bad
00000088
Err-Bits
00000080
Count
1

My Mainboard is a Asus A8V Deluxe, wich has DualChannel RAM suport, what was used.
My populated pairs where:
A1 256 MB DDR-400
A2 1024 MB DDR-400
B1 256 MB DDR-400
B2 1024 MB DDR-400

So how can I tell where my damaged bar might be?
The RAM-Slots are on in the listed order on the board, and the two different ram types build 2 Dualchannel pairs.

For now I just removed the two 256MB RAM baars to see if it was one of these too. So far I had no freez jet. But I tested another configuration before and got a freez writhing this message, and had to start over again. So I will not loose too much time, so I will not have to do it a 3rd time.

Best Regards and thank you

Casper

---

### Post by Snifffurt on 2007-07-23
Hello

I made several checks now and explored the following things:
[LIST]
[*]The RAM may have some little fault, but is **definitely not** responsible for the freezes (I use another Ubuntu install from PATA drives on the same RAM right now without any freezes at all for ages, and I tryed RAM-Bars that where never built into this system and still had the freeezes)
[*]The SATA Harddrive is checked by Samsungs HUTIL as passed, no errors
[*]The Ubuntu Feisty i386 alternate install CD used for the install has passed the integrity check I made
[*]mdadm is not responsible for the freezes too. I deleted the mdadm install and installed the i386 ubuntu on normal ext3 partitions on the SATA disk and still had the freezes
[/LIST]

I explored that the SATA drives use the SATAII (300MB/s) protocol and my Motherboard only supports SATAI(150MB/s). The drives sort of worked on the Fasttrack controller, but did not work with the VIA 82xx SATA controllers from my Asus A8V Deluxe moterboard. Normally the SATA protocol should do a fall back to the lower speed by itself, but in some cases it doesn't. So I had to use the Jumpers on the Samsung Hardrives to make it 150MB/s.

But still, it freezes even on a normal Ext3 partition. What reasons are left? is it because I use a i386 ubuntu on a amd64 X2 CPU?
I'm pretty much out of hints..

Thank you for any ideas that could lead me to a non freezing ubuntu 7.04 on my sata drives.

Regards

Sniff

---

### Post by MrHippocampus on 2007-07-23
Firstly, I would disconnect as much as possible form the computer as you can, i.e. CD/DVD drives, random USB things. Then I would run htop in a window whilst using the PC and try and get it to freeze, then look at htop's output and see if anything has taken up loads of time on the CPU.

Also try and see if you can get temperature monitoring information from your motherboard, just to see if anything is overheating.

---

### Post by Snifffurt on 2007-07-24
Hi

> **MrHippocampus said:**
> Firstly, I would disconnect as much as possible form the computer as you can, i.e. CD/DVD drives, random USB things. Then I would run htop in a window whilst using the PC and try and get it to freeze, then look at htop's output and see if anything has taken up loads of time on the CPU.

Also try and see if you can get temperature monitoring information from your motherboard, just to see if anything is overheating.

I did try to overheat my CPU with running "cat /dev/radom > /dev/null" two times to load both cores of my cpu. I measured the temperature of my cpu with lm-sensors and GKrellM. I did this 100%load for maybe 20 mins or so, and the cpu stayed at 54°C AFAIR. I've been reading my CPU can stand 65°C so I doubt overheating to be the reason. Eaven if there is some process is going out of order, I doubt it will overheat my CPU.
Maybe it is some error with Xorg and the ati driver?

Regards

Sniff

---

### Post by Circuit99 on 2007-07-24
Stripping down the system is the best way to go.

I would use stresslinux from here,

[http://www.stresslinux.org/](http://www.stresslinux.org/)

to test the hardware.

Another suggestion check your current bios version fully supports the updated cpu and current hardware.

Another is the motherboard my need cooling and are the memory modules fitted with heat spreaders?

These suggestions to check hardware. 

Double check if the memory in what slots they are in, if matched pair then they have to be in matching :popcorn:slots.

Once your sure about hardware then you can start to look at software.

Good Luck !!

---

### Post by Snifffurt on 2007-07-24
Hello

> **Circuit99 said:**
> Stripping down the system is the best way to go.
[http://www.stresslinux.org/](http://www.stresslinux.org/)


I did not know about stress linux. I'll try this right away.

> 
Another suggestion check your current bios version fully supports the updated cpu and current hardware.


I had to update my bios, so it will support the new CPU. So it is the latest stable BIOS available for my board.

> 
Another is the motherboard my need cooling and are the memory modules fitted with heat spreaders?


Heat Spreaders? I bought my RAM bars without them, so I was assuming they are not needed for these bars. I've seen some hi-end DDR-400 RAM bars with heat spreaders, but most modules at this speed do not have them, so i suppose it is more luxury then needed and I do not overclock my hardware or stuff like that.
Please correct me on that if I'm wrong.

> 
Double check if the memory in what slots they are in, if matched pair then they have to be in matching :popcorn:slots.


You mean if they have the same CAS Latency. I think they have. But running in single channel mode with only one bar did not stop the freezings too, so I doubt it is a timing problem between linked RAM bars.

> 
Once your sure about hardware then you can start to look at software.


Probbably your right. I'll triy stresslinux. And I'll try other hardware testing methods. And probbably I'm going to get me some Kingston RAM bars to morrow, wich will exclude the possibillity of RAM faults anyway.

> 
Good Luck !!

Tank you. And thank you for your suggestions of course.

Regards

Sniff

---

### Post by fragility14 on 2007-07-24
thanks for the link, been looking for software like that.

I will try it when I get home.

---

### Post by Snifffurt on 2007-07-28
Hello again

After using two brand new Kingston bars, I can now exclude the failure of the RAM. Also CPU overheating can be excluded, I cannot get the CPU above 54°Celsius, wich is 11°C below AMD's specified max.
The Harddrive is also not responsible for this, I'm pretty much out of ideas now.

On e fresh install of either ubuntu feisty amd64 or i386 i get a instant freeze right after log in.

Does anybody have any idea what problem could be left now?

Regards

Sniff

---

### Post by Snifffurt on 2007-07-29
Hello

Another idea came to my mind. Is it possible that the CPU could be damaged? I mean it has some damage without overheating, some factory production fault?
How can I find out if the CPU would have such damage?

Regards

Sniff

---

### Post by milosv on 2007-07-29
Hello
I have similar problem with freezing.
Recently I installed Ubuntu 7.04 on my laptop HP E510 (p4@2.13, hdd 60, 512 MB etc).
The laptop is freezing every 5-10 mins. It gets freezed between 30-60 secs and then continue working normally.
First I thought that it is cpu temperature issue, but it continue freezing when cpu is under 50 C degrees.

Here is dmesg output:

> 
[224810.775000] ata1.00: configured for UDMA/33
[224810.965000] ata1.01: configured for MWDMA2
[224810.965000] ata1: EH complete
[224810.971000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[224810.977000] sda: Write Protect is off
[224810.977000] sda: Mode Sense: 00 3a 00 00
[224810.987000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[224810.990000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[224810.991000] sda: Write Protect is off
[224810.991000] sda: Mode Sense: 00 3a 00 00
[224810.991000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[224869.471000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[224869.471000] ata1.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x43 data 12 in
[224869.471000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[224876.512000] ata1: port is slow to respond, please be patient (Status 0xd0)
[224899.513000] ata1: port failed to respond (30 secs, Status 0xd0)
[224899.513000] ata1: soft resetting port
[224899.882000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
[224899.885000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
[224899.885000] ata1.00: configured for UDMA/33
[224900.075000] ata1.01: configured for MWDMA2
[224900.075000] ata1: EH complete
[224900.079000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[224900.085000] sda: Write Protect is off
[224900.085000] sda: Mode Sense: 00 3a 00 00
[224900.095000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[224900.105000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[224900.105000] sda: Write Protect is off
[224900.105000] sda: Mode Sense: 00 3a 00 00
[224900.106000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[225262.541000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[225262.541000] ata1.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x25 data 8 in
[225262.541000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[225269.582000] ata1: port is slow to respond, please be patient (Status 0xd0)
[225292.583000] ata1: port failed to respond (30 secs, Status 0xd0)
[225292.583000] ata1: soft resetting port
[225293.279000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
[225293.282000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
[225293.282000] ata1.00: configured for UDMA/33
[225293.472000] ata1.01: configured for MWDMA2
[225293.472000] ata1: EH complete
[225293.478000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[225293.484000] sda: Write Protect is off
[225293.484000] sda: Mode Sense: 00 3a 00 00
[225293.493000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[225293.494000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[225293.535000] sda: Write Protect is off
[225293.535000] sda: Mode Sense: 00 3a 00 00
[225293.535000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[225585.908000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[225585.908000] ata1.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x0 data 0 
[225585.908000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[225592.949000] ata1: port is slow to respond, please be patient (Status 0xd0)
[225615.950000] ata1: port failed to respond (30 secs, Status 0xd0)
[225615.950000] ata1: soft resetting port
[225616.641000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
[225616.644000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
[225616.644000] ata1.00: configured for UDMA/33
[225616.834000] ata1.01: configured for MWDMA2
[225616.834000] ata1: EH complete
[225616.840000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[225616.843000] sda: Write Protect is off
[225616.843000] sda: Mode Sense: 00 3a 00 00
[225616.867000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[225616.881000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[225616.881000] sda: Write Protect is off
[225616.881000] sda: Mode Sense: 00 3a 00 00
[225616.882000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[226284.518000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[226284.518000] ata1.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x0 data 0 
[226284.518000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[226291.559000] ata1: port is slow to respond, please be patient (Status 0xd0)
[226314.560000] ata1: port failed to respond (30 secs, Status 0xd0)
[226314.560000] ata1: soft resetting port
[226315.255000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
[226315.258000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
[226315.258000] ata1.00: configured for UDMA/33
[226315.448000] ata1.01: configured for MWDMA2
[226315.448000] ata1: EH complete
[226315.454000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[226315.457000] sda: Write Protect is off
[226315.457000] sda: Mode Sense: 00 3a 00 00
[226315.458000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[226315.458000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[226315.501000] sda: Write Protect is off
[226315.501000] sda: Mode Sense: 00 3a 00 00
[226315.502000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[226738.784000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[226738.784000] ata1.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x0 data 0 
[226738.784000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[226745.825000] ata1: port is slow to respond, please be patient (Status 0xd0)
[226768.826000] ata1: port failed to respond (30 secs, Status 0xd0)
[226768.826000] ata1: soft resetting port
[226769.298000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
[226769.301000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
[226769.301000] ata1.00: configured for UDMA/33
[226769.491000] ata1.01: configured for MWDMA2
[226769.491000] ata1: EH complete
[226769.497000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[226769.500000] sda: Write Protect is off
[226769.500000] sda: Mode Sense: 00 3a 00 00
[226769.502000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[226769.503000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[226769.504000] sda: Write Protect is off
[226769.504000] sda: Mode Sense: 00 3a 00 00
[226769.504000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[226893.266000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[226893.266000] ata1.01: cmd a0/01:00:00:00:00/00:00:00:00:00/b0 tag 0 cdb 0x43 data 12 in
[226893.266000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[226900.307000] ata1: port is slow to respond, please be patient (Status 0xd0)
[226923.308000] ata1: port failed to respond (30 secs, Status 0xd0)
[226923.308000] ata1: soft resetting port
[226924.002000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
[226924.006000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
[226924.006000] ata1.00: configured for UDMA/33
[226924.196000] ata1.01: configured for MWDMA2
[226924.196000] ata1: EH complete
[226924.203000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[226924.209000] sda: Write Protect is off
[226924.209000] sda: Mode Sense: 00 3a 00 00
[226924.217000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[226924.223000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[226924.228000] sda: Write Protect is off
[226924.228000] sda: Mode Sense: 00 3a 00 00
[226924.228000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA


Here is /var/log/messages:
> 
Jul 29 13:33:22 boj kernel: [226769.298000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
Jul 29 13:33:22 boj kernel: [226769.301000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
Jul 29 13:33:22 boj kernel: [226769.301000] ata1.00: configured for UDMA/33
Jul 29 13:33:22 boj kernel: [226769.491000] ata1.01: configured for MWDMA2
Jul 29 13:33:22 boj kernel: [226769.491000] ata1: EH complete
Jul 29 13:33:22 boj kernel: [226769.497000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
Jul 29 13:33:22 boj kernel: [226769.500000] sda: Write Protect is off
Jul 29 13:33:22 boj kernel: [226769.502000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 29 13:33:22 boj kernel: [226769.503000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
Jul 29 13:33:22 boj kernel: [226769.504000] sda: Write Protect is off
Jul 29 13:33:22 boj kernel: [226769.504000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 29 13:35:26 boj kernel: [226893.266000]          res 40/00:03:00:00:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
Jul 29 13:35:33 boj kernel: [226900.307000] ata1: port is slow to respond, please be patient (Status 0xd0)
Jul 29 13:35:56 boj kernel: [226923.308000] ata1: soft resetting port
Jul 29 13:35:57 boj kernel: [226924.002000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
Jul 29 13:35:57 boj kernel: [226924.006000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
Jul 29 13:35:57 boj kernel: [226924.006000] ata1.00: configured for UDMA/33
Jul 29 13:35:57 boj kernel: [226924.196000] ata1.01: configured for MWDMA2
Jul 29 13:35:57 boj kernel: [226924.196000] ata1: EH complete
Jul 29 13:35:57 boj kernel: [226924.203000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
Jul 29 13:35:57 boj kernel: [226924.209000] sda: Write Protect is off
Jul 29 13:35:57 boj kernel: [226924.217000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 29 13:35:57 boj kernel: [226924.223000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
Jul 29 13:35:57 boj kernel: [226924.228000] sda: Write Protect is off
Jul 29 13:35:57 boj kernel: [226924.228000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA


As I understand this may be disk related, but I think hardware is fine. Laptop is old 3 months and I was running windows on it without any problems. Still windows is working well but ubuntu gets freezed occassionally.
Do you have idea what might cause this problem. what should I check and do further?

Thanks in advance!

---

### Post by Snifffurt on 2007-07-30
Hello again the $n time ;)

After all of this, I tryed something real different. I just copied my existing Ubuntu install on IDE to my sata disc with cp -Rfpv, installed grub to sda with the grub console, changed all the values in the grub.conf and in the fstab on the copied sda partition. I even copied from ext3 partitions on IDE to reiserfs partitions on SATA, and have now a working system on my SATA disk. I ran this since yesterday and had no freezes jet. A fresh install on my SATA disk froze right after login.
This really looks like a software problem to me. What ever is different in my existing IDE install, it does not lead to these freezes, and on a fresh ubuntu install there is something freezes my system.
The only very unlikely possibility would be a too weak power supply for my new CPU, but I think this is not really it, because it is a Brand "Be Quiet" power supply, what used to be quite expansive the other day, and the rest of my hardware is not very power consuming (no heat producing Graphics adapter for ex.).

Hope this will last, and my system will stay stable.
I would still be interested in any ideas what could have caused this on the fresh install.

Thanks to all people that payed attention to my thread and had some advices for me.

Regards

Sniff

---

### Post by kiev on 2008-05-24
This kernel bug
 this problem already whole year

for me she showed up one time in the floor of hour, however as a result of this problem I lost a mysql database - mysql innodb not start - "Accertion error" - did not help even "innodb_force_recovery = 4", backup was an a week remoteness - the works of whole department lost data for a few days, the management simply in shock - I going to discharge from job (((

this problem already whole year:
-----------
I'm stumped trying to track down the below intermittent problem.....
I've confirmed this problem on 2.6.19, 2.6.20 and 2.6.21.
[http://lkml.org/lkml/2007/6/14/154](http://lkml.org/lkml/2007/6/14/154)
[http://kerneltrap.org/mailarchive/linux-kernel/2007/6/14/103765](http://kerneltrap.org/mailarchive/linux-kernel/2007/6/14/103765)
[http://kerneltrap.org/node/16175](http://kerneltrap.org/node/16175)
[http://lkml.org/lkml/2007/6/14/154](http://lkml.org/lkml/2007/6/14/154)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217920](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217920)
[https://bugs.launchpad.net/ubuntu/+bug/164183](https://bugs.launchpad.net/ubuntu/+bug/164183)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229747](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/229747)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/159521](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/159521)
[https://bugs.launchpad.net/ubuntu/+bug/164183](https://bugs.launchpad.net/ubuntu/+bug/164183)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/187146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/187146)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/221437](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/221437)
[https://bugs.launchpad.net/ubuntu/+bug/226600](https://bugs.launchpad.net/ubuntu/+bug/226600)

SUSE:

ata errors, system freeze
[https://bugzilla.novell.com/show_bug.cgi?id=393675](https://bugzilla.novell.com/show_bug.cgi?id=393675)

System lockup with concurrent acces to SATA disks on Promise PDC20378
[http://lists.opensuse.org/opensuse-bugs/2008-02/msg03458.html](http://lists.opensuse.org/opensuse-bugs/2008-02/msg03458.html)

Kernel panic / system hang / sata_promise
[https://bugzilla.novell.com/show_bug.cgi?id=350907](https://bugzilla.novell.com/show_bug.cgi?id=350907)

DELL Poweredge 2970 hangs sometimes (ata1)
[https://bugzilla.novell.com/show_bug.cgi?id=359333](https://bugzilla.novell.com/show_bug.cgi?id=359333)

Fedora:
ata device crashing system in Fedora 8
[http://www.experts-exchange.com/OS/Linux/Distributions/Fedora/Q_23125450.html](http://www.experts-exchange.com/OS/Linux/Distributions/Fedora/Q_23125450.html)

problème de mise à jour
[http://forums.fedora-fr.org/viewtopic.php?pid=253930](http://forums.fedora-fr.org/viewtopic.php?pid=253930)

Kernel 2.6.24.x boot problem - Anyone , Any idea
[http://fcp.surfsite.org/modules/newbb/viewtopic.php?viewmode=flat&order=ASC&topic_id=54760&forum=10](http://fcp.surfsite.org/modules/newbb/viewtopic.php?viewmode=flat&order=ASC&topic_id=54760&forum=10)

Thought though with the newest hard drive with support of NCQ such is not present, ... also same:

"With this kernel I’m getting frequent temporary freezes (system comes back responsive after a minute or so…)."
[http://kerneltrap.org/mailarchive/linux-kernel/2008/1/8/546296](http://kerneltrap.org/mailarchive/linux-kernel/2008/1/8/546296)

---

