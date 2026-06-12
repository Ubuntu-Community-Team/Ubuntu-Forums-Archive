---
title: "ACPI issues. Please tell me what is going on here..."
date: 2007-02-28
forum: Hardware &amp; Laptops
---

### Post by noxxle on 2007-02-28
I am on feisty at the moment, however i get this same problem with edgy. I tried feisty to see if it was resolved, and it wasnt. When i use a generic kernel it takes twice as long to boot and performance is sluggist (mouse and typing lags a bit too). When I use a 386 kernel, I dont notice this. It seems to run just find with 386. It is the same with every other distro i have used. I have a suspicion that it has something to do with my hard drive. Ill post my dmesg from the generic and 386 kernel. Can someone please compare them and comment. Here is my dmesg from the generic kernel:

[    0.000000] Linux version 2.6.20-9-generic (root@rothera) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu3)) #2 SMP Mon Feb 26 03:01:44 UTC 2007 (Ubuntu 2.6.20-9.16-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001eec0000 end: 000000001efc0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001efc0000 size: 000000000000f000 end: 000000001efcf000 type: 3
[    0.000000] copy_e820_map() start: 000000001efcf000 size: 0000000000031000 end: 000000001f000000 type: 4
[    0.000000] copy_e820_map() start: 00000000fed14000 size: 0000000000006000 end: 00000000fed1a000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed1c000 size: 0000000000004000 end: 00000000fed20000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffb80000 size: 0000000000480000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001efc0000 (usable)
[    0.000000]  BIOS-e820: 000000001efc0000 - 000000001efcf000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001efcf000 - 000000001f000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 495MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 126912) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   126912
[    0.000000]   HighMem    126912 ->   126912
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   126912
[    0.000000] On node 0 totalpages: 126912
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 959 pages used for memmap
[    0.000000]   Normal zone: 121857 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f6a40
[    0.000000] ACPI: RSDT (v001 A M I  OEMRSDT  0x06000510 MSFT 0x00000097) @ 0x1efc0000
[    0.000000] ACPI: FADT (v002 A M I  OEMFACP  0x06000510 MSFT 0x00000097) @ 0x1efc0200
[    0.000000] ACPI: MADT (v001 A M I  OEMAPIC  0x06000510 MSFT 0x00000097) @ 0x1efc0390
[    0.000000] ACPI: MCFG (v001 A M I  OEMMCFG  0x06000510 MSFT 0x00000097) @ 0x1efc03f0
[    0.000000] ACPI: OEMB (v001 A M I  AMI_OEM  0x06000510 MSFT 0x00000097) @ 0x1efcf040
[    0.000000] ACPI: SSDT (v001    AMI   CPU1PM 0x00000001 INTL 0x02002026) @ 0x1efc80d0
[    0.000000] ACPI: DSDT (v001  0AAAA 0AAAA000 0x00000000 INTL 0x02002026) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:13 APIC version 20
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1f000000:dfd14000)
[    0.000000] Detected 1729.039 MHz processor.
[    9.209879] Built 1 zonelists.  Total pages: 125921
[    9.209883] Kernel command line: root=UUID=8c211361-afcb-4b7b-8527-db36c57fc458 ro 
[    9.210030] mapped APIC to ffffd000 (fee00000)
[    9.210032] mapped IOAPIC to ffffc000 (fec00000)
[    9.210036] Enabling fast FPU save and restore... done.
[    9.210039] Enabling unmasked SIMD FPU exception support... done.
[    9.210047] Initializing CPU#0
[    9.210111] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    9.211765] Console: colour VGA+ 80x25
[    9.214564] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    9.214833] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    9.226752] Memory: 492636k/507648k available (1979k kernel code, 14492k reserved, 882k data, 324k init, 0k highmem)
[    9.226839] virtual kernel memory layout:
[    9.226840]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[    9.226842]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    9.226843]     vmalloc : 0xdf800000 - 0xff7fe000   ( 511 MB)
[    9.226844]     lowmem  : 0xc0000000 - 0xdefc0000   ( 495 MB)
[    9.226845]       .init : 0xc03d1000 - 0xc0422000   ( 324 kB)
[    9.226847]       .data : 0xc02eed54 - 0xc03cb6d4   ( 882 kB)
[    9.226848]       .text : 0xc0100000 - 0xc02eed54   (1979 kB)
[    9.227264] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    9.306083] Calibrating delay using timer specific routine.. 3461.05 BogoMIPS (lpj=6922103)
[    9.306222] Security Framework v1.0.0 initialized
[    9.306279] SELinux:  Disabled at boot.
[    9.306343] Mount-cache hash table entries: 512
[    9.306528] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000 00000000
[    9.306540] CPU: L1 I cache: 32K, L1 D cache: 32K
[    9.306619] CPU: L2 cache: 2048K
[    9.306668] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002040 00000180 00000000 00000000
[    9.306686] Checking 'hlt' instruction... OK.
[    9.322210] SMP alternatives: switching to UP code
[    9.322434] Freeing SMP alternatives: 11k freed
[    9.322563] ACPI: Core revision 20060707
[    9.337911] CPU0: Intel(R) Pentium(R) M processor 1.73GHz stepping 08
[    9.338035] Total of 1 processors activated (3461.05 BogoMIPS).
[    9.338247] ENABLING IO-APIC IRQs
[    9.338481] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    9.486056] Brought up 1 CPUs
[    9.486320] Booting paravirtualized kernel on bare hardware
[    9.486429] Time:  1:32:25  Date: 01/28/107
[    9.486502] NET: Registered protocol family 16
[    9.486625] EISA bus registered
[    9.486676] ACPI: bus type pci registered
[    9.486732] PCI: BIOS Bug: MCFG area at e0000000 is not E820-reserved
[    9.486788] PCI: Not using MMCONFIG.
[    9.486909] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[    9.486964] PCI: Using configuration type 1
[    9.487014] Setting up standard PCI resources
[    9.554211] ACPI: Interpreter enabled
[    9.554261] ACPI: Using IOAPIC for interrupt routing
[    9.554681] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    9.554739] PCI: Probing PCI hardware (bus 00)
[    9.555042] Boot video device is 0000:00:02.0
[    9.555480] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    9.555538] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[    9.556054] PCI: Transparent bridge - 0000:00:1e.0
[    9.556163] PCI: Bus #02 (-#05) is hidden behind transparent bridge #01 (-#02) (try 'pci=assign-busses')
[    9.556241] Please report the result to linux-kernel to fix this permanently
[    9.556317] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    9.560103] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    9.565317] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *11 12)
[    9.565910] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 12) *11
[    9.566515] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 12)
[    9.567077] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *7 12)
[    9.567637] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 *4 5 6 7 12)
[    9.568197] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 12) *0, disabled.
[    9.568811] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 *6 7 12)
[    9.569374] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 12)
[    9.569883] ACPI: Power Resource [GFAN] (off)
[    9.569938] Linux Plug and Play Support v0.97 (c) Adam Belay
[    9.570020] pnp: PnP ACPI init
[    9.572862] pnp: PnP ACPI: found 13 devices
[    9.572917] PnPBIOS: Disabled by ACPI PNP
[    9.573004] PCI: Using ACPI for IRQ routing
[    9.573056] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    9.580400] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[    9.580463] PCI: Bus 2, cardbus bridge: 0000:01:03.0
[    9.580515]   IO window: 0000d000-0000d0ff
[    9.580568]   IO window: 0000d400-0000d4ff
[    9.580621]   PREFETCH window: 20000000-23ffffff
[    9.580675]   MEM window: 24000000-27ffffff
[    9.580729] PCI: Bridge: 0000:00:1e.0
[    9.580779]   IO window: d000-dfff
[    9.580830]   MEM window: fe800000-fe8fffff
[    9.580883]   PREFETCH window: 20000000-23ffffff
[    9.580948] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    9.580965] ACPI: PCI Interrupt 0000:01:03.0[A] -> GSI 21 (level, low) -> IRQ 16
[    9.581083] NET: Registered protocol family 2
[    9.618016] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    9.618136] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    9.618305] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    9.618409] TCP: Hash tables configured (established 16384 bind 8192)
[    9.618464] TCP reno registered
[    9.630074] checking if image is initramfs... it is
[   10.232721] Freeing initrd memory: 6457k freed
[   10.233230] audit: initializing netlink socket (disabled)
[   10.233301] audit(1172626346.044:1): initialized
[   10.233482] VFS: Disk quotas dquot_6.5.1
[   10.233550] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   10.233654] io scheduler noop registered
[   10.233750] io scheduler anticipatory registered
[   10.233827] io scheduler deadline registered
[   10.233912] io scheduler cfq registered (default)
[   10.234300] isapnp: Scanning for PnP cards...
[   10.588373] isapnp: No Plug & Play device found
[   10.611578] Real Time Clock Driver v1.12ac
[   10.611695] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   10.612416] mice: PS/2 mouse device common for all mice
[   10.612986] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   10.613286] input: Macintosh mouse button emulation as /class/input/input0
[   10.613377] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   10.613435] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   10.613772] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   10.616983] i8042.c: Detected active multiplexing controller, rev 1.1.
[   10.618229] serio: i8042 KBD port at 0x60,0x64 irq 1
[   10.618284] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   10.618337] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   10.618390] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   10.618444] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   10.618603] EISA: Probing bus 0 at eisa.0
[   10.618680] EISA: Detected 0 cards.
[   10.648816] TCP cubic registered
[   10.648871] NET: Registered protocol family 1
[   10.648926] NET: Registered protocol family 8
[   10.648976] NET: Registered protocol family 20
[   10.649063] Using IPI No-Shortcut mode
[   10.649187] ACPI: (supports S0 S3 S4 S5)
[   10.649408]   Magic number: 11:658:509
[   10.649591] Time: tsc clocksource has been installed.
[   10.649806] Freeing unused kernel memory: 324k freed
[   10.663769] input: AT Translated Set 2 keyboard as /class/input/input1
[   10.810439] Capability LSM initialized
[   10.834827] ACPI: Transitioning device [FN00] to D3
[   10.834882] ACPI: Transitioning device [FN00] to D3
[   10.834937] ACPI: Fan [FN00] (off)
[   10.838925] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   10.839055] ACPI: Processor [CPU1] (supports 8 throttling states)
[   10.903358] ACPI: Thermal Zone [THRM] (50 C)
[   11.189488] usbcore: registered new interface driver usbfs
[   11.189564] usbcore: registered new interface driver hub
[   11.189637] usbcore: registered new device driver usb
[   11.190430] USB Universal Host Controller Interface driver v3.0
[   11.190530] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 17
[   11.190636] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   11.190640] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   11.190840] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   11.190941] uhci_hcd 0000:00:1d.0: irq 17, io base 0x0000e400
[   11.191084] usb usb1: configuration #1 chosen from 1 choice
[   11.191160] hub 1-0:1.0: USB hub found
[   11.191212] hub 1-0:1.0: 2 ports detected
[   11.243707] SCSI subsystem initialized
[   11.248066] libata version 2.00 loaded.
[   11.283540] ieee1394: Initialized config rom entry `ip1394'
[   11.297417] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
[   11.297532] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   11.297537] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   11.297607] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   11.297706] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000e480
[   11.297839] usb usb2: configuration #1 chosen from 1 choice
[   11.297914] hub 2-0:1.0: USB hub found
[   11.297966] hub 2-0:1.0: 2 ports detected
[   11.319905] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   11.405386] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[   11.405498] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   11.405502] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   11.405573] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   11.405675] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000e800
[   11.405810] usb usb3: configuration #1 chosen from 1 choice
[   11.405885] hub 3-0:1.0: USB hub found
[   11.405938] hub 3-0:1.0: 2 ports detected
[    2.108000] Time: acpi_pm clocksource has been installed.
[    2.340000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 20
[    2.340000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    2.340000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.340000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    2.340000] uhci_hcd 0000:00:1d.3: irq 20, io base 0x0000e880
[    2.340000] usb usb4: configuration #1 chosen from 1 choice
[    2.340000] hub 4-0:1.0: USB hub found
[    2.340000] hub 4-0:1.0: 2 ports detected
[    2.604000] ata_piix 0000:00:1f.1: version 2.00ac7
[    2.604000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 19
[    2.604000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    2.604000] ata1: PATA max UDMA/100 cmd 0x1F0 ctl 0x3F6 bmdma 0xFFA0 irq 14
[    2.604000] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xFFA8 irq 15
[    2.604000] scsi0 : ata_piix
[    2.816000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    2.960000] ACPI Error (dsopcode-0481): Attempt to CreateField of length zero [20060707]
[    2.960000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.IDE0.RATA] (Node de953d38), AE_AML_OPERAND_VALUE
[    2.964000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.IDE0.CHN0.DRV0._GTF] (Node de953f54), AE_AML_OPERAND_VALUE
[    2.964000] ata1.00: ATA-7, max UDMA/100, 234441648 sectors: LBA48 
[    2.964000] ata1.00: ata1: dev 0 multi count 16
[    3.364000] usb 2-1: configuration #1 chosen from 1 choice
[    3.368000] ACPI Error (dsopcode-0481): Attempt to CreateField of length zero [20060707]
[    3.368000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.IDE0.RATA] (Node de953d38), AE_AML_OPERAND_VALUE
[    3.368000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.IDE0.CHN0.DRV0._GTF] (Node de953f54), AE_AML_OPERAND_VALUE
[    3.368000] ata1.01: ATAPI, max UDMA/33
[    3.376000] ACPI Error (dsopcode-0481): Attempt to CreateField of length zero [20060707]
[    3.376000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.IDE0.RATA] (Node de953d38), AE_AML_OPERAND_VALUE
[    3.376000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.IDE0.CHN0.DRV0._GTF] (Node de953f54), AE_AML_OPERAND_VALUE
[    3.376000] ata1.00: configured for UDMA/100
[    3.380000] usbcore: registered new interface driver hiddev
[    3.392000] input: Microsoft Basic Optical Mouse as /class/input/input2
[    3.392000] input: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:1d.1-1
[    3.392000] usbcore: registered new interface driver usbhid
[    3.392000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[    4.136000] ACPI Error (dsopcode-0481): Attempt to CreateField of length zero [20060707]
[    4.136000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.IDE0.RATA] (Node de953d38), AE_AML_OPERAND_VALUE
[    4.136000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.IDE0.CHN0.DRV0._GTF] (Node de953f54), AE_AML_OPERAND_VALUE
[    4.136000] ata1.01: configured for UDMA/33
[    4.136000] scsi1 : ata_piix
[    4.448000] ATA: abnormal status 0x7F on port 0x177
[    4.452000] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM120JC  YL10 PQ: 0 ANSI: 5
[    4.460000] scsi 0:0:1:0: CD-ROM            TSSTcorp CDW/DVD TS-U462A TS30 PQ: 0 ANSI: 5
[    4.464000] ACPI: PCI Interrupt 0000:01:03.1[B] -> GSI 22 (level, low) -> IRQ 21
[    4.516000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 17
[    4.516000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.516000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.516000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    4.516000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.516000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.516000] ehci_hcd 0000:00:1d.7: irq 17, io mem 0xfeb3fc00
[    4.520000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.520000] usb usb5: configuration #1 chosen from 1 choice
[    4.520000] hub 5-0:1.0: USB hub found
[    4.520000] hub 5-0:1.0: 8 ports detected
[    4.524000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[fe8fd800-fe8fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    5.092000] usb 2-1: USB disconnect, address 2
[    5.096000] 8139cp 0000:01:04.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    5.096000] 8139cp 0000:01:04.0: Try the "8139too" driver instead.
[    5.100000] 8139too Fast Ethernet driver 0.9.28
[    5.100000] ACPI: PCI Interrupt 0000:01:04.0[A] -> GSI 20 (level, low) -> IRQ 22
[    5.100000] eth0: RealTek RTL8139 at 0xdf8a6c00, 00:15:f2:7d:05:35, IRQ 22
[    5.100000] eth0:  Identified 8139 chip type 'RTL-8101'
[    5.120000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[    5.120000] sda: Write Protect is off
[    5.120000] sda: Mode Sense: 00 3a 00 00
[    5.120000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.120000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[    5.120000] sda: Write Protect is off
[    5.120000] sda: Mode Sense: 00 3a 00 00
[    5.120000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.120000]  sda: sda1 sda2 sda3 sda4
[    5.176000] sd 0:0:0:0: Attached scsi disk sda
[    5.180000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.180000] scsi 0:0:1:0: Attached scsi generic sg1 type 5
[    5.268000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    5.268000] Uniform CD-ROM driver Revision: 3.20
[    5.268000] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    5.584000] Attempting manual resume
[    5.584000] swsusp: Resume From Partition 8:2
[    5.584000] PM: Checking swsusp image.
[    5.584000] PM: Resume from disk failed.
[    5.612000] kjournald starting.  Commit interval 5 seconds
[    5.612000] EXT3-fs: mounted filesystem with ordered data mode.
[    6.128000] usb 2-1: new low speed USB device using uhci_hcd and address 3
[    6.128000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e01800034737c8]
[    6.904000] usb 2-1: configuration #1 chosen from 1 choice
[    6.920000] input: Microsoft Basic Optical Mouse as /class/input/input3
[    6.920000] input: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:1d.1-1
[   19.660000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   20.520000] Linux agpgart interface v0.101 (c) Dave Jones
[   20.524000] agpgart: Detected an Intel 915GM Chipset.
[   20.524000] agpgart: Detected 16124K stolen memory.
[   20.540000] agpgart: AGP aperture is 256M @ 0xd0000000
[   21.308000] iTCO_vendor_support: vendor-support=0
[   21.308000] input: PC Speaker as /class/input/input4
[   21.644000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   21.644000] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x0860)
[   21.644000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   21.680000] intel_rng: FWH not detected
[   21.692000] NET: Registered protocol family 17
[   22.032000] sdhci: Secure Digital Host Controller Interface driver, 0.12
[   22.032000] sdhci: Copyright(c) Pierre Ossman
[   22.032000] sdhci: SDHCI controller found at 0000:01:03.2 [1180:0822] (rev 17)
[   22.032000] ACPI: PCI Interrupt 0000:01:03.2[C] -> GSI 20 (level, low) -> IRQ 22
[   22.032000] sdhci:slot0: Controller reports > 25 MHz base clock, but no high speed support.
[   22.032000] mmc0: SDHCI at 0xfe8fe400 irq 22 DMA
[   22.240000] ieee80211_crypt: registered algorithm 'NULL'
[   22.240000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   22.240000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   22.264000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   22.264000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   22.264000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 18 (level, low) -> IRQ 19
[   22.264000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[   22.560000] ipw2200: Detected geography ZZA (11 802.11bg channels, 13 802.11a channels)
[   22.560000] Yenta: CardBus bridge found at 0000:01:03.0 [1043:1997]
[   22.648000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 20
[   22.648000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   22.708000] Yenta: ISA IRQ mask 0x04b8, PCI irq 16
[   22.708000] Socket status: 30000006
[   22.708000] Yenta: Raising subordinate bus# of parent bus (#01) from #02 to #05
[   22.708000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xdfff
[   22.708000] cs: IO port probe 0xd000-0xdfff: clean.
[   22.708000] pcmcia: parent PCI bridge Memory window: 0xfe800000 - 0xfe8fffff
[   22.708000] pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x23ffffff
[   22.856000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x116eb1, caps: 0xa04713/0x0
[   22.896000] input: SynPS/2 Synaptics TouchPad as /class/input/input5
[   23.068000] cs: IO port probe 0x100-0x3af: clean.
[   23.072000] cs: IO port probe 0x3e0-0x4ff: excluding 0x400-0x41f 0x4d0-0x4d7
[   23.072000] cs: IO port probe 0x820-0x8ff: clean.
[   23.072000] cs: IO port probe 0xc00-0xcf7: clean.
[   23.072000] cs: IO port probe 0xa00-0xaff: clean.
[   29.464000] fuse init (API version 7.8)
[   29.600000] lp: driver loaded but no devices found
[   29.640000] Adding 979956k swap on /dev/disk/by-uuid/115a8be2-5b01-4802-8af7-ca4a65872226.  Priority:-1 extents:1 across:979956k
[   30.556000] EXT3 FS on sda3, internal journal
[   31.288000] NET: Registered protocol family 10
[   31.288000] lo: Disabled Privacy Extensions
[   32.572000] kjournald starting.  Commit interval 5 seconds
[   32.572000] EXT3 FS on sda4, internal journal
[   32.572000] EXT3-fs: mounted filesystem with ordered data mode.
[   32.604000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   32.680000] NTFS volume version 3.1.
[   42.852000] eth0: no IPv6 routers present
[   42.852000] eth1: no IPv6 routers present
[   44.760000] No dock devices found.
[   44.792000] Asus Laptop ACPI Extras version 0.30
[   44.792000]   unsupported model M5A, trying default values
[   44.792000]   send /proc/acpi/dsdt to the developers
[   44.808000] ibm_acpi: ec object not found
[   44.936000] input: Power Button (FF) as /class/input/input6
[   44.956000] ACPI: Power Button (FF) [PWRF]
[   45.008000] input: Sleep Button (CM) as /class/input/input7
[   45.028000] ACPI: Sleep Button (CM) [SLPB]
[   45.080000] input: Lid Switch as /class/input/input8
[   45.096000] ACPI: Lid Switch [LID]
[   45.144000] ACPI: Battery Slot [BAT0] (battery present)
[   45.200000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   45.200000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   45.228000] ACPI: AC Adapter [AC0] (on-line)
[   45.236000] Using specific hotkey driver
[   50.300000] ppdev: user-space parallel port driver
[   50.984000] [drm] Initialized drm 1.1.0 20060810
[   51.096000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 20
[   51.096000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   54.112000] apm: BIOS not found.
[   60.892000] Bluetooth: Core ver 2.11
[   60.892000] NET: Registered protocol family 31
[   60.892000] Bluetooth: HCI device and connection manager initialized
[   60.892000] Bluetooth: HCI socket layer initialized
[   60.928000] Bluetooth: L2CAP ver 2.8
[   60.928000] Bluetooth: L2CAP socket layer initialized
[   61.236000] Bluetooth: RFCOMM socket layer initialized
[   61.236000] Bluetooth: RFCOMM TTY layer initialized
[   61.236000] Bluetooth: RFCOMM ver 1.8
[   77.140000] eth0: no IPv6 routers present

---

### Post by noxxle on 2007-02-28
And here is the dmesg from 386:

[    0.000000] Linux version 2.6.20-9-386 (root@rothera) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu3)) #2 Mon Feb 26 02:58:41 UTC 2007 (Ubuntu 2.6.20-9.16-386)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001eec0000 end: 000000001efc0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001efc0000 size: 000000000000f000 end: 000000001efcf000 type: 3
[    0.000000] copy_e820_map() start: 000000001efcf000 size: 0000000000031000 end: 000000001f000000 type: 4
[    0.000000] copy_e820_map() start: 00000000fed14000 size: 0000000000006000 end: 00000000fed1a000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed1c000 size: 0000000000004000 end: 00000000fed20000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffb80000 size: 0000000000480000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001efc0000 (usable)
[    0.000000]  BIOS-e820: 000000001efc0000 - 000000001efcf000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001efcf000 - 000000001f000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 495MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 126912) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   126912
[    0.000000]   HighMem    126912 ->   126912
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   126912
[    0.000000] On node 0 totalpages: 126912
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 959 pages used for memmap
[    0.000000]   Normal zone: 121857 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f6a40
[    0.000000] ACPI: RSDT (v001 A M I  OEMRSDT  0x06000510 MSFT 0x00000097) @ 0x1efc0000
[    0.000000] ACPI: FADT (v002 A M I  OEMFACP  0x06000510 MSFT 0x00000097) @ 0x1efc0200
[    0.000000] ACPI: MADT (v001 A M I  OEMAPIC  0x06000510 MSFT 0x00000097) @ 0x1efc0390
[    0.000000] ACPI: MCFG (v001 A M I  OEMMCFG  0x06000510 MSFT 0x00000097) @ 0x1efc03f0
[    0.000000] ACPI: OEMB (v001 A M I  AMI_OEM  0x06000510 MSFT 0x00000097) @ 0x1efcf040
[    0.000000] ACPI: SSDT (v001    AMI   CPU1PM 0x00000001 INTL 0x02002026) @ 0x1efc80d0
[    0.000000] ACPI: DSDT (v001  0AAAA 0AAAA000 0x00000000 INTL 0x02002026) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:13 APIC version 20
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1f000000:dfd14000)
[    0.000000] Detected 1729.099 MHz processor.
[    7.749059] Built 1 zonelists.  Total pages: 125921
[    7.749061] Kernel command line: root=UUID=8c211361-afcb-4b7b-8527-db36c57fc458 ro 
[    7.749209] mapped APIC to ffffd000 (fee00000)
[    7.749211] mapped IOAPIC to ffffc000 (fec00000)
[    7.749214] Enabling fast FPU save and restore... done.
[    7.749217] Enabling unmasked SIMD FPU exception support... done.
[    7.749224] Initializing CPU#0
[    7.749281] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    7.750941] Console: colour VGA+ 80x25
[    7.753704] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    7.753966] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    7.765718] Memory: 492780k/507648k available (1904k kernel code, 14288k reserved, 848k data, 324k init, 0k highmem)
[    7.765806] virtual kernel memory layout:
[    7.765807]     fixmap  : 0xfffa9000 - 0xfffff000   ( 344 kB)
[    7.765809]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    7.765810]     vmalloc : 0xdf800000 - 0xff7fe000   ( 511 MB)
[    7.765811]     lowmem  : 0xc0000000 - 0xdefc0000   ( 495 MB)
[    7.765812]       .init : 0xc03b4000 - 0xc0405000   ( 324 kB)
[    7.765814]       .data : 0xc02dc063 - 0xc03b0434   ( 848 kB)
[    7.765815]       .text : 0xc0100000 - 0xc02dc063   (1904 kB)
[    7.766230] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    7.845252] Calibrating delay using timer specific routine.. 3460.90 BogoMIPS (lpj=6921801)
[    7.845380] Security Framework v1.0.0 initialized
[    7.845438] SELinux:  Disabled at boot.
[    7.845496] Mount-cache hash table entries: 512
[    7.845643] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000 00000000
[    7.845652] CPU: L1 I cache: 32K, L1 D cache: 32K
[    7.845731] CPU: L2 cache: 2048K
[    7.845780] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002040 00000180 00000000 00000000
[    7.845794] CPU: Intel(R) Pentium(R) M processor 1.73GHz stepping 08
[    7.845903] Checking 'hlt' instruction... OK.
[    7.861540] ACPI: Core revision 20060707
[    7.877040] ENABLING IO-APIC IRQs
[    7.877270] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    8.021364] Booting paravirtualized kernel on bare hardware
[    8.021467] Time:  9:22:27  Date: 01/28/107
[    8.021541] NET: Registered protocol family 16
[    8.021661] EISA bus registered
[    8.021711] ACPI: bus type pci registered
[    8.021767] PCI: BIOS Bug: MCFG area at e0000000 is not E820-reserved
[    8.021822] PCI: Not using MMCONFIG.
[    8.021938] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2
[    8.021995] PCI: Using configuration type 1
[    8.022045] Setting up standard PCI resources
[    8.089163] ACPI: Interpreter enabled
[    8.089213] ACPI: Using IOAPIC for interrupt routing
[    8.089623] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    8.089681] PCI: Probing PCI hardware (bus 00)
[    8.089988] Boot video device is 0000:00:02.0
[    8.090412] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    8.090469] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[    8.090963] PCI: Transparent bridge - 0000:00:1e.0
[    8.091070] PCI: Bus #02 (-#05) is hidden behind transparent bridge #01 (-#02) (try 'pci=assign-busses')
[    8.091149] Please report the result to linux-kernel to fix this permanently
[    8.091224] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    8.094994] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    8.100116] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *11 12)
[    8.100717] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 12) *11
[    8.101330] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 12)
[    8.101897] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *7 12)
[    8.102464] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 *4 5 6 7 12)
[    8.103031] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 12) *0, disabled.
[    8.103653] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 *6 7 12)
[    8.104221] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 12)
[    8.104722] ACPI: Power Resource [GFAN] (off)
[    8.104779] Linux Plug and Play Support v0.97 (c) Adam Belay
[    8.104846] pnp: PnP ACPI init
[    8.107714] pnp: PnP ACPI: found 13 devices
[    8.107769] PnPBIOS: Disabled by ACPI PNP
[    8.107849] PCI: Using ACPI for IRQ routing
[    8.107900] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    8.115215] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[    8.115280] PCI: Bus 2, cardbus bridge: 0000:01:03.0
[    8.115334]   IO window: 0000d000-0000d0ff
[    8.115387]   IO window: 0000d400-0000d4ff
[    8.115441]   PREFETCH window: 20000000-23ffffff
[    8.115495]   MEM window: 24000000-27ffffff
[    8.115547] PCI: Bridge: 0000:00:1e.0
[    8.115597]   IO window: d000-dfff
[    8.115649]   MEM window: fe800000-fe8fffff
[    8.115702]   PREFETCH window: 20000000-23ffffff
[    8.115766] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    8.115782] ACPI: PCI Interrupt 0000:01:03.0[A] -> GSI 21 (level, low) -> IRQ 16
[    8.115895] NET: Registered protocol family 2
[    8.153174] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    8.153284] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[    8.153395] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[    8.153478] TCP: Hash tables configured (established 16384 bind 8192)
[    8.153534] TCP reno registered
[    8.165230] checking if image is initramfs... it is
[    8.753818] Freeing initrd memory: 6432k freed
[    8.817099] audit: initializing netlink socket (disabled)
[    8.817171] audit(1172654547.092:1): initialized
[    8.817320] VFS: Disk quotas dquot_6.5.1
[    8.817385] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    8.817486] io scheduler noop registered
[    8.817561] io scheduler anticipatory registered
[    8.817638] io scheduler deadline registered
[    8.817721] io scheduler cfq registered (default)
[    8.818093] isapnp: Scanning for PnP cards...
[    9.172158] isapnp: No Plug & Play device found
[    9.192491] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    9.193202] mice: PS/2 mouse device common for all mice
[    9.193696] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    9.193980] input: Macintosh mouse button emulation as /class/input/input0
[    9.194065] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    9.194125] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    9.194395] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    9.197532] i8042.c: Detected active multiplexing controller, rev 1.1.
[    9.198978] serio: i8042 KBD port at 0x60,0x64 irq 1
[    9.199034] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    9.199087] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    9.199140] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    9.199193] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    9.199342] EISA: Probing bus 0 at eisa.0
[    9.199421] EISA: Detected 0 cards.
[    9.229549] TCP cubic registered
[    9.229602] NET: Registered protocol family 1
[    9.229659] NET: Registered protocol family 8
[    9.229712] NET: Registered protocol family 20
[    9.229794] Using IPI Shortcut mode
[    9.229910] ACPI: (supports S0 S3 S4 S5)
[    9.230132]   Magic number: 11:853:374
[    9.230465] Freeing unused kernel memory: 324k freed
[    9.232746] Time: tsc clocksource has been installed.
[    9.244557] input: AT Translated Set 2 keyboard as /class/input/input1
[    9.386039] Capability LSM initialized
[    9.409098] ACPI: Transitioning device [FN00] to D3
[    9.409153] ACPI: Transitioning device [FN00] to D3
[    9.409206] ACPI: Fan [FN00] (off)
[    9.412842] ACPI: CPU0 (power states: C1[C1] C2[C2])
[    9.412971] ACPI: Processor [CPU1] (supports 8 throttling states)
[    9.477361] ACPI: Thermal Zone [THRM] (47 C)
[    9.746119] usbcore: registered new interface driver usbfs
[    9.746200] usbcore: registered new interface driver hub
[    9.746267] usbcore: registered new device driver usb
[    9.747965] USB Universal Host Controller Interface driver v3.0
[    9.748067] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 17
[    9.748172] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    9.748176] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    9.748385] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    9.748484] uhci_hcd 0000:00:1d.0: irq 17, io base 0x0000e400
[    9.748631] usb usb1: configuration #1 chosen from 1 choice
[    9.748703] hub 1-0:1.0: USB hub found
[    9.748756] hub 1-0:1.0: 2 ports detected
[    9.801068] SCSI subsystem initialized
[    9.805307] libata version 2.00 loaded.
[    9.824789] ieee1394: Initialized config rom entry `ip1394'
[    9.852663] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
[    9.852775] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    9.852780] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    9.852849] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    9.852950] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000e480
[    9.853089] usb usb2: configuration #1 chosen from 1 choice
[    9.853163] hub 2-0:1.0: USB hub found
[    9.853216] hub 2-0:1.0: 2 ports detected
[    9.860225] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    9.956636] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[    9.956747] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    9.956752] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    9.956822] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    9.956921] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000e800
[    9.957053] usb usb3: configuration #1 chosen from 1 choice
[    9.957127] hub 3-0:1.0: USB hub found
[    9.957179] hub 3-0:1.0: 2 ports detected
[    2.116000] Time: acpi_pm clocksource has been installed.
[    2.152000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 20
[    2.152000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    2.152000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    2.152000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    2.152000] uhci_hcd 0000:00:1d.3: irq 20, io base 0x0000e880
[    2.152000] usb usb4: configuration #1 chosen from 1 choice
[    2.152000] hub 4-0:1.0: USB hub found
[    2.152000] hub 4-0:1.0: 2 ports detected
[    2.256000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 17
[    2.256000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    2.256000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.256000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    2.256000] ehci_hcd 0000:00:1d.7: debug port 1
[    2.256000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    2.256000] ehci_hcd 0000:00:1d.7: irq 17, io mem 0xfeb3fc00
[    2.260000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    2.260000] usb usb5: configuration #1 chosen from 1 choice
[    2.260000] hub 5-0:1.0: USB hub found
[    2.260000] hub 5-0:1.0: 8 ports detected
[    2.288000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    2.364000] ata_piix 0000:00:1f.1: version 2.00ac7
[    2.364000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 19
[    2.364000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    2.364000] ata1: PATA max UDMA/100 cmd 0x1F0 ctl 0x3F6 bmdma 0xFFA0 irq 14
[    2.364000] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xFFA8 irq 15
[    2.364000] scsi0 : ata_piix
[    2.528000] ACPI Error (dsopcode-0481): Attempt to CreateField of length zero [20060707]
[    2.528000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.IDE0.RATA] (Node c1453d38), AE_AML_OPERAND_VALUE
[    2.528000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.IDE0.CHN0.DRV0._GTF] (Node c1453f54), AE_AML_OPERAND_VALUE
[    2.528000] ata1.00: ATA-7, max UDMA/100, 234441648 sectors: LBA48 
[    2.528000] ata1.00: ata1: dev 0 multi count 16
[    2.692000] ACPI Error (dsopcode-0481): Attempt to CreateField of length zero [20060707]
[    2.692000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.IDE0.RATA] (Node c1453d38), AE_AML_OPERAND_VALUE
[    2.692000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.IDE0.CHN0.DRV0._GTF] (Node c1453f54), AE_AML_OPERAND_VALUE
[    2.692000] ata1.01: ATAPI, max UDMA/33
[    2.700000] ACPI Error (dsopcode-0481): Attempt to CreateField of length zero [20060707]
[    2.700000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.IDE0.RATA] (Node c1453d38), AE_AML_OPERAND_VALUE
[    2.700000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.IDE0.CHN0.DRV0._GTF] (Node c1453f54), AE_AML_OPERAND_VALUE
[    2.700000] ata1.00: configured for UDMA/100
[    2.792000] usb 2-1: new low speed USB device using uhci_hcd and address 3
[    2.868000] ACPI Error (dsopcode-0481): Attempt to CreateField of length zero [20060707]
[    2.868000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.IDE0.RATA] (Node c1453d38), AE_AML_OPERAND_VALUE
[    2.868000] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.IDE0.CHN0.DRV0._GTF] (Node c1453f54), AE_AML_OPERAND_VALUE
[    2.868000] ata1.01: configured for UDMA/33
[    2.868000] scsi1 : ata_piix
[    2.968000] usb 2-1: configuration #1 chosen from 1 choice
[    2.980000] usbcore: registered new interface driver hiddev
[    2.992000] input: Microsoft Basic Optical Mouse as /class/input/input2
[    2.992000] input: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:1d.1-1
[    2.992000] usbcore: registered new interface driver usbhid
[    2.992000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[    3.024000] ATA: abnormal status 0x7F on port 0x177
[    3.028000] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HM120JC  YL10 PQ: 0 ANSI: 5
[    3.036000] scsi 0:0:1:0: CD-ROM            TSSTcorp CDW/DVD TS-U462A TS30 PQ: 0 ANSI: 5
[    3.040000] ACPI: PCI Interrupt 0000:01:03.1[B] -> GSI 22 (level, low) -> IRQ 21
[    3.092000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[fe8fd800-fe8fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    3.100000] 8139cp 0000:01:04.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    3.100000] 8139cp 0000:01:04.0: Try the "8139too" driver instead.
[    3.104000] 8139too Fast Ethernet driver 0.9.28
[    3.104000] ACPI: PCI Interrupt 0000:01:04.0[A] -> GSI 20 (level, low) -> IRQ 22
[    3.104000] eth0: RealTek RTL8139 at 0xdf8a6c00, 00:15:f2:7d:05:35, IRQ 22
[    3.104000] eth0:  Identified 8139 chip type 'RTL-8101'
[    3.112000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[    3.112000] sda: Write Protect is off
[    3.112000] sda: Mode Sense: 00 3a 00 00
[    3.112000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.112000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[    3.112000] sda: Write Protect is off
[    3.112000] sda: Mode Sense: 00 3a 00 00
[    3.112000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.112000]  sda: sda1 sda2 sda3 sda4
[    3.168000] sd 0:0:0:0: Attached scsi disk sda
[    3.168000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.172000] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    3.232000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    3.232000] Uniform CD-ROM driver Revision: 3.20
[    3.232000] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    3.552000] Attempting manual resume
[    3.552000] swsusp: Resume From Partition 8:2
[    3.552000] PM: Checking swsusp image.
[    3.556000] PM: Resume from disk failed.
[    3.588000] kjournald starting.  Commit interval 5 seconds
[    3.588000] EXT3-fs: mounted filesystem with ordered data mode.
[    4.372000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e01800034737c8]
[   12.528000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   13.668000] Linux agpgart interface v0.101 (c) Dave Jones
[   13.672000] agpgart: Detected an Intel 915GM Chipset.
[   13.672000] agpgart: Detected 16124K stolen memory.
[   13.688000] agpgart: AGP aperture is 256M @ 0xd0000000
[   13.868000] Real Time Clock Driver v1.12ac
[   14.108000] input: PC Speaker as /class/input/input3
[   14.140000] iTCO_vendor_support: vendor-support=0
[   14.156000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   14.156000] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x0860)
[   14.156000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   14.200000] intel_rng: FWH not detected
[   14.236000] NET: Registered protocol family 17
[   14.736000] sdhci: Secure Digital Host Controller Interface driver, 0.12
[   14.736000] sdhci: Copyright(c) Pierre Ossman
[   14.736000] sdhci: SDHCI controller found at 0000:01:03.2 [1180:0822] (rev 17)
[   14.736000] ACPI: PCI Interrupt 0000:01:03.2[C] -> GSI 20 (level, low) -> IRQ 22
[   14.736000] sdhci:slot0: Controller reports > 25 MHz base clock, but no high speed support.
[   14.736000] mmc0: SDHCI at 0xfe8fe400 irq 22 DMA
[   14.852000] Yenta: CardBus bridge found at 0000:01:03.0 [1043:1997]
[   14.876000] ieee80211_crypt: registered algorithm 'NULL'
[   14.892000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   14.892000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   14.920000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   14.920000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   14.980000] Yenta: ISA IRQ mask 0x04b8, PCI irq 16
[   14.980000] Socket status: 30000006
[   14.980000] Yenta: Raising subordinate bus# of parent bus (#01) from #02 to #05
[   14.980000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xdfff
[   14.980000] cs: IO port probe 0xd000-0xdfff: clean.
[   14.980000] pcmcia: parent PCI bridge Memory window: 0xfe800000 - 0xfe8fffff
[   14.980000] pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x23ffffff
[   14.984000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 18 (level, low) -> IRQ 19
[   14.984000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[   15.512000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x116eb1, caps: 0xa04713/0x0
[   15.552000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 20
[   15.552000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   15.552000] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[   16.384000] ipw2200: Detected geography ZZA (11 802.11bg channels, 13 802.11a channels)
[   16.440000] cs: IO port probe 0x100-0x3af: clean.
[   16.440000] cs: IO port probe 0x3e0-0x4ff: excluding 0x400-0x41f 0x4d0-0x4d7
[   16.440000] cs: IO port probe 0x820-0x8ff: clean.
[   16.440000] cs: IO port probe 0xc00-0xcf7: clean.
[   16.444000] cs: IO port probe 0xa00-0xaff: clean.
[   16.564000] fuse init (API version 7.8)
[   16.708000] lp: driver loaded but no devices found
[   16.748000] Adding 979956k swap on /dev/disk/by-uuid/115a8be2-5b01-4802-8af7-ca4a65872226.  Priority:-1 extents:1 across:979956k
[   16.952000] EXT3 FS on sda3, internal journal
[   17.208000] kjournald starting.  Commit interval 5 seconds
[   17.208000] EXT3 FS on sda4, internal journal
[   17.208000] EXT3-fs: mounted filesystem with ordered data mode.
[   17.236000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   17.312000] NTFS volume version 3.1.
[   18.088000] NET: Registered protocol family 10
[   18.088000] lo: Disabled Privacy Extensions
[   21.752000] No dock devices found.
[   21.792000] Asus Laptop ACPI Extras version 0.30
[   21.792000]   unsupported model M5A, trying default values
[   21.792000]   send /proc/acpi/dsdt to the developers
[   21.808000] ibm_acpi: ec object not found
[   21.884000] input: Power Button (FF) as /class/input/input5
[   21.904000] ACPI: Power Button (FF) [PWRF]
[   21.952000] input: Sleep Button (CM) as /class/input/input6
[   21.972000] ACPI: Sleep Button (CM) [SLPB]
[   22.024000] input: Lid Switch as /class/input/input7
[   22.024000] ACPI: Lid Switch [LID]
[   22.092000] ACPI: Battery Slot [BAT0] (battery present)
[   22.148000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   22.148000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   22.168000] ACPI: AC Adapter [AC0] (on-line)
[   22.180000] Using specific hotkey driver
[   23.432000] ppdev: user-space parallel port driver
[   24.220000] [drm] Initialized drm 1.1.0 20060810
[   24.232000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 20
[   24.232000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   26.416000] apm: BIOS not found.
[   28.556000] eth1: no IPv6 routers present
[   28.800000] eth0: no IPv6 routers present
[   31.660000] Bluetooth: Core ver 2.11
[   31.660000] NET: Registered protocol family 31
[   31.660000] Bluetooth: HCI device and connection manager initialized
[   31.660000] Bluetooth: HCI socket layer initialized
[   31.688000] Bluetooth: L2CAP ver 2.8
[   31.688000] Bluetooth: L2CAP socket layer initialized
[   31.796000] Bluetooth: RFCOMM socket layer initialized
[   31.796000] Bluetooth: RFCOMM TTY layer initialized
[   31.796000] Bluetooth: RFCOMM ver 1.8
[   49.892000] eth0: no IPv6 routers present

---

### Post by noxxle on 2007-02-28
plz help me

---

### Post by bapoumba on 2007-02-28
Hello :)
I will not be able to help you, but could you post your computer specs ?

---

### Post by SaddisticTwist on 2007-02-28
What does all this apic and acpi do anyways?

Example;

noapic nolapic
pci=acpi

What are they actually for? is there any side effects for using them?

---

### Post by noxxle on 2007-02-28
I dont understand you. If you are asking if i used those at boot options, then no they dont help.

---

### Post by noxxle on 2007-03-01
I have a  SAMSUNG Spinpoint M Series HM120JC 120GB hard drive, and lspci says this:

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
01:03.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
01:03.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
01:03.2 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
01:03.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
01:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:05.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)

---

### Post by noxxle on 2007-03-02
/cry

---

