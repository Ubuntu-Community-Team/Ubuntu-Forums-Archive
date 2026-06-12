---
title: "PATA Drive not mounting"
date: 2007-06-03
forum: Hardware &amp; Laptops
---

### Post by ap.sampson on 2007-06-03
My setup:

Asus P5W DH Deluxe Mobo
OS Run from Raptor[SATA] drive
Storage drive is ATA and not mounting or showing up.

This drive did show up when I was using Edgy. I did a clean install of Feisty and now I have no access to my storage drive.

sudo fdisk -l returns
```

isk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8666    69609613+  83  Linux
/dev/sda2            8667        9039     2996122+   5  Extended
/dev/sda5            8667        9039     2996091   82  Linux swap / Solaris

Disk /dev/sdb: 0 MB, 327680 bytes
255 heads, 63 sectors/track, 0 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table
```

dmesg returns:
```
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e4000 size: 000000000001c000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000007fe80000 end: 000000007ff80000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000007ff80000 size: 000000000000e000 end: 000000007ff8e000 type: 3
[    0.000000] copy_e820_map() start: 000000007ff8e000 size: 0000000000052000 end: 000000007ffe0000 type: 4
[    0.000000] copy_e820_map() start: 000000007ffe0000 size: 0000000000020000 end: 0000000080000000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffb00000 size: 0000000000500000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ff80000 (usable)
[    0.000000]  BIOS-e820: 000000007ff80000 - 000000007ff8e000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ff8e000 - 000000007ffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007ffe0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 524160) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   524160
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   524160
[    0.000000] On node 0 totalpages: 524160
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2303 pages used for memmap
[    0.000000]   HighMem zone: 292481 pages, LIFO batch:31
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v002 ACPIAM                                ) @ 0x000faf40
[    0.000000] ACPI: XSDT (v001 A M I  OEMXSDT  0x08000628 MSFT 0x00000097) @ 0x7ff80100
[    0.000000] ACPI: FADT (v003 A M I  OEMFACP  0x08000628 MSFT 0x00000097) @ 0x7ff80290
[    0.000000] ACPI: MADT (v001 A M I  OEMAPIC  0x08000628 MSFT 0x00000097) @ 0x7ff80390
[    0.000000] ACPI: OEMB (v001 A M I  AMI_OEM  0x08000628 MSFT 0x00000097) @ 0x7ff8e040
[    0.000000] ACPI: MCFG (v001 A M I  OEMMCFG  0x08000628 MSFT 0x00000097) @ 0x7ff893f0
[    0.000000] ACPI: DSDT (v001  A0543 A0543000 0x00000000 INTL 0x02002026) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:7fb00000)
[    0.000000] Detected 2404.174 MHz processor.
[   43.281428] Built 1 zonelists.  Total pages: 520065
[   43.281431] Kernel command line: root=UUID=2d9f691e-421a-475d-a9bb-0d7edc5e0d17 ro quiet splash
[   43.281531] mapped APIC to ffffd000 (fee00000)
[   43.281533] mapped IOAPIC to ffffc000 (fec00000)
[   43.281535] Enabling fast FPU save and restore... done.
[   43.281536] Enabling unmasked SIMD FPU exception support... done.
[   43.281541] Initializing CPU#0
[   43.281584] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   43.282727] Console: colour VGA+ 80x25
[   43.282894] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   43.283088] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   43.335830] Memory: 2067392k/2096640k available (1992k kernel code, 27940k reserved, 893k data, 328k init, 1179136k highmem)
[   43.335837] virtual kernel memory layout:
[   43.335837]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   43.335838]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   43.335839]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   43.335840]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   43.335841]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   43.335841]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   43.335842]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   43.335844] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   43.413306] Calibrating delay using timer specific routine.. 4811.90 BogoMIPS (lpj=9623805)
[   43.413334] Security Framework v1.0.0 initialized
[   43.413338] SELinux:  Disabled at boot.
[   43.413349] Mount-cache hash table entries: 512
[   43.413444] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e3bd 00000000 00000001
[   43.413449] monitor/mwait feature present.
[   43.413451] using mwait in idle threads.
[   43.413454] CPU: L1 I cache: 32K, L1 D cache: 32K
[   43.413455] CPU: L2 cache: 4096K
[   43.413457] CPU: Physical Processor ID: 0
[   43.413458] CPU: Processor Core ID: 0
[   43.413460] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e3bd 00000000 00000001
[   43.413467] Compat vDSO mapped to ffffe000.
[   43.413469] Remapping vsyscall page to ffffe000
[   43.413478] Checking 'hlt' instruction... OK.
[   43.429342] SMP alternatives: switching to UP code
[   43.429588] Early unpacking initramfs... done
[   43.656872] ACPI: Core revision 20060707
[   43.657069] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   43.672021] CPU0: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz stepping 06
[   43.672034] SMP alternatives: switching to SMP code
[   43.672081] Booting processor 1/1 eip 3000
[   43.682526] Initializing CPU#1
[   43.760559] Calibrating delay using timer specific routine.. 4808.56 BogoMIPS (lpj=9617138)
[   43.760563] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e3bd 00000000 00000001
[   43.760567] monitor/mwait feature present.
[   43.760569] CPU: L1 I cache: 32K, L1 D cache: 32K
[   43.760570] CPU: L2 cache: 4096K
[   43.760572] CPU: Physical Processor ID: 0
[   43.760573] CPU: Processor Core ID: 1
[   43.760574] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e3bd 00000000 00000001
[   43.761088] CPU1: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz stepping 06
[   43.761102] Total of 2 processors activated (9620.47 BogoMIPS).
[   43.761241] ENABLING IO-APIC IRQs
[   43.761400] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   43.928207] checking TSC synchronization across 2 CPUs: passed.
[    0.004151] Brought up 2 CPUs
[    0.065061] migration_cost=18
[    0.065239] Booting paravirtualized kernel on bare hardware
[    0.065292] Time: 17:25:24  Date: 04/12/107
[    0.065311] NET: Registered protocol family 16
[    0.065364] EISA bus registered
[    0.065367] ACPI: bus type pci registered
[    0.065468] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=6
[    0.065470] PCI: Using configuration type 1
[    0.065471] Setting up standard PCI resources
[    0.078194] ACPI: Interpreter enabled
[    0.078196] ACPI: Using IOAPIC for interrupt routing
[    0.078933] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.078938] PCI: Probing PCI hardware (bus 00)
[    0.079506] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.079509] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.079688] Boot video device is 0000:06:00.0
[    0.080337] PCI: Transparent bridge - 0000:00:1e.0
[    0.080395] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.082438] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.082680] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[    0.082920] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.083415] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[    0.083619] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.083838] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[    0.087597] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.087789] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.087990] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 11 12 *14 15)
[    0.088182] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.088374] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.088564] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.088756] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.088948] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.089030] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.089036] pnp: PnP ACPI init
[    0.091516] pnp: PnP ACPI: found 14 devices
[    0.091519] PnPBIOS: Disabled by ACPI PNP
[    0.091550] PCI: Using ACPI for IRQ routing
[    0.091552] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.101763] NET: Registered protocol family 8
[    0.101765] NET: Registered protocol family 20
[    0.102340] pnp: 00:07: ioport range 0x290-0x297 has been reserved
[    0.102345] pnp: 00:09: ioport range 0x3f6-0x3f6 has been reserved
[    0.102543] PCI: Bridge: 0000:00:01.0
[    0.102545]   IO window: c000-cfff
[    0.102548]   MEM window: faa00000-feafffff
[    0.102550]   PREFETCH window: cff00000-efefffff
[    0.102553] PCI: Bridge: 0000:00:1c.0
[    0.102553]   IO window: disabled.
[    0.102557]   MEM window: disabled.
[    0.102560]   PREFETCH window: cfe00000-cfefffff
[    0.102563] PCI: Bridge: 0000:00:1c.3
[    0.102565]   IO window: b000-bfff
[    0.102569]   MEM window: fa900000-fa9fffff
[    0.102572]   PREFETCH window: disabled.
[    0.102575] PCI: Bridge: 0000:00:1c.4
[    0.102577]   IO window: a000-afff
[    0.102581]   MEM window: fa800000-fa8fffff
[    0.102583]   PREFETCH window: disabled.
[    0.102587] PCI: Bridge: 0000:00:1c.5
[    0.102589]   IO window: 9000-9fff
[    0.102593]   MEM window: fa700000-fa7fffff
[    0.102595]   PREFETCH window: disabled.
[    0.102599] PCI: Bridge: 0000:00:1e.0
[    0.102600]   IO window: disabled.
[    0.102603]   MEM window: fa600000-fa6fffff
[    0.102606]   PREFETCH window: disabled.
[    0.102616] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.102620] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.102633] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[    0.102637] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.102651] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 17
[    0.102654] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    0.102667] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
[    0.102671] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[    0.102685] ACPI: PCI Interrupt 0000:00:1c.5[b] -> GSI 17 (level, low) -> IRQ 18
[    0.102689] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[    0.102697] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.102714] NET: Registered protocol family 2
[    0.139719] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.139782] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.140071] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.140218] TCP: Hash tables configured (established 131072 bind 65536)
[    0.140220] TCP reno registered
[    0.151741] checking if image is initramfs... it is
[    0.599700] Freeing initrd memory: 7009k freed
[    0.600128] audit: initializing netlink socket (disabled)
[    0.600139] audit(1178990724.304:1): initialized
[    0.600204] highmem bounce pool size: 64 pages
[    0.600261] VFS: Disk quotas dquot_6.5.1
[    0.600275] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.600310] io scheduler noop registered
[    0.600311] io scheduler anticipatory registered
[    0.600313] io scheduler deadline registered
[    0.600320] io scheduler cfq registered (default)
[    0.600497] PCI: Setting latency timer of device 0000:00:01.0 to 64
[    0.600523] assign_interrupt_mode Found MSI capability
[    0.600525] Allocate Port Service[0000:00:01.0:pcie00]
[    0.600586] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.600618] assign_interrupt_mode Found MSI capability
[    0.600620] Allocate Port Service[0000:00:1c.0:pcie00]
[    0.600644] Allocate Port Service[0000:00:1c.0:pcie02]
[    0.600719] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[    0.600751] assign_interrupt_mode Found MSI capability
[    0.600752] Allocate Port Service[0000:00:1c.3:pcie00]
[    0.600826] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[    0.600858] assign_interrupt_mode Found MSI capability
[    0.600859] Allocate Port Service[0000:00:1c.4:pcie00]
[    0.600932] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[    0.600964] assign_interrupt_mode Found MSI capability
[    0.600965] Allocate Port Service[0000:00:1c.5:pcie00]
[    0.601082] isapnp: Scanning for PnP cards...
[    0.953153] isapnp: No Plug & Play device found
[    0.967573] Real Time Clock Driver v1.12ac
[    0.967609] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    0.967705] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.968104] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.968206] mice: PS/2 mouse device common for all mice
[    0.968573] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    0.968671] input: Macintosh mouse button emulation as /class/input/input0
[    0.968694] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    0.968697] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    0.968872] PNP: No PS/2 controller found. Probing ports directly.
[    0.971480] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.971483] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.971546] EISA: Probing bus 0 at eisa.0
[    0.971569] EISA: Detected 0 cards.
[    1.001564] TCP cubic registered
[    1.001569] NET: Registered protocol family 1
[    1.001584] Starting balanced_irq
[    1.001588] Using IPI No-Shortcut mode
[    1.001653] ACPI: (supports S0 S1 S3 S4 S5)
[    1.001684]   Magic number: 7:73:441
[    1.001827] Freeing unused kernel memory: 328k freed
[    1.001839] Time: tsc clocksource has been installed.
[    2.166067] Capability LSM initialized
[    2.216904] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU1._PDC] (Node df85d838), AE_BAD_HEADER
[    2.217155] ACPI: Processor [CPU1] (supports 8 throttling states)
[    2.217194] ACPI Error (psparse-0537): Method parse/execution failed [\_PR_.CPU2._PDC] (Node df85d798), AE_BAD_HEADER
[    2.217425] ACPI: Processor [CPU2] (supports 8 throttling states)
[    2.217430] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.217434] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[    2.541386] usbcore: registered new interface driver usbfs
[    2.541494] usbcore: registered new interface driver hub
[    2.541512] usbcore: registered new device driver usb
[    2.557089] SCSI subsystem initialized
[    2.560521] libata version 2.20 loaded.
[    2.562667] ahci 0000:02:00.0: version 2.1
[    2.562689] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 18
[    2.565484] ieee1394: Initialized config rom entry `ip1394'
[    2.566263] USB Universal Host Controller Interface driver v3.0
[    2.570859] Floppy drive(s): fd0 is 1.44M
[    2.590101] FDC 0 is a post-1991 82077
[    3.568164] PCI: Setting latency timer of device 0000:02:00.0 to 64
[    3.568171] ahci 0000:02:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    3.568174] ahci 0000:02:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    3.568231] ata1: SATA max UDMA/133 cmd 0xf88a8100 ctl 0x00000000 bmdma 0x00000000 irq 18
[    3.568275] ata2: SATA max UDMA/133 cmd 0xf88a8180 ctl 0x00000000 bmdma 0x00000000 irq 18
[    3.568283] scsi0 : ahci
[    3.879458] ata1: SATA link down (SStatus 0 SControl 300)
[    3.879468] scsi1 : ahci
[    4.190771] ata2: SATA link down (SStatus 0 SControl 300)
[    4.191196] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 19
[    4.191204] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    4.191207] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.191279] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    4.191301] uhci_hcd 0000:00:1d.0: irq 19, io base 0x0000e480
[    4.191374] usb usb1: configuration #1 chosen from 1 choice
[    4.191391] hub 1-0:1.0: USB hub found
[    4.191395] hub 1-0:1.0: 2 ports detected
[    4.298584] ACPI: PCI Interrupt 0000:00:1d.1[b] -> GSI 17 (level, low) -> IRQ 18
[    4.298590] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    4.298592] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.298609] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    4.298627] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000e800
[    4.298683] usb usb2: configuration #1 chosen from 1 choice
[    4.298698] hub 2-0:1.0: USB hub found
[    4.298702] hub 2-0:1.0: 2 ports detected
[    4.402359] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
[    4.402364] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    4.402367] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.402382] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    4.402403] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000e880
[    4.402459] usb usb3: configuration #1 chosen from 1 choice
[    4.402475] hub 3-0:1.0: USB hub found
[    4.402479] hub 3-0:1.0: 2 ports detected
[    4.506112] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 17
[    4.506117] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    4.506120] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    4.506136] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    4.506157] uhci_hcd 0000:00:1d.3: irq 17, io base 0x0000ec00
[    4.506212] usb usb4: configuration #1 chosen from 1 choice
[    4.506227] hub 4-0:1.0: USB hub found
[    4.506231] hub 4-0:1.0: 2 ports detected
[    4.609945] ACPI: PCI Interrupt 0000:01:03.0[A] -> GSI 21 (level, low) -> IRQ 21
[    4.633976] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 19
[    4.633985] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.633988] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.634005] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    4.634028] ehci_hcd 0000:00:1d.7: debug port 1
[    4.634032] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.634036] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xfebfbc00
[    4.637899] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.637949] usb usb5: configuration #1 chosen from 1 choice
[    4.637965] hub 5-0:1.0: USB hub found
[    4.637969] hub 5-0:1.0: 8 ports detected
[    4.641936] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    4.659586] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[fa6ff800-fa6fffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.743219] ata_piix 0000:00:1f.1: version 2.10ac1
[    4.743230] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 22 (level, low) -> IRQ 22
[    4.743242] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    4.743604] ata3: PATA max UDMA/133 cmd 0x0001d800 ctl 0x0001d482 bmdma 0x0001d000 irq 22
[    4.743919] ata4: PATA max UDMA/133 cmd 0x0001d400 ctl 0x0001d082 bmdma 0x0001d008 irq 22
[    4.743929] scsi2 : ata_piix
[    5.065156] ata3.00: ATAPI, max UDMA/33
[    5.232788] ata3.00: configured for UDMA/33
[    5.232793] scsi3 : ata_piix
[    5.264564] usb 5-7: new high speed USB device using ehci_hcd and address 3
[    5.402778] ATA: abnormal status 0x7F on port 0x0001d407
[    5.408208] scsi 2:0:0:0: CD-ROM            _NEC     DVD_RW ND-4570A  1.02 PQ: 0 ANSI: 5
[    5.409056] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    5.409392] usb 5-7: configuration #1 chosen from 1 choice
[    5.409617] hub 5-7:1.0: USB hub found
[    5.409852] hub 5-7:1.0: 4 ports detected
[    5.567744] ACPI: PCI Interrupt 0000:00:1f.2[b] -> GSI 23 (level, low) -> IRQ 23
[    5.567756] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    5.567773] ata5: SATA max UDMA/133 cmd 0x0001e400 ctl 0x0001e082 bmdma 0x0001d880 irq 23
[    5.567787] ata6: SATA max UDMA/133 cmd 0x0001e000 ctl 0x0001dc02 bmdma 0x0001d888 irq 23
[    5.567796] scsi4 : ata_piix
[    5.732217] ata5.00: ata_hpa_resize 1: sectors = 145226112, hpa_sectors = 145226112
[    5.732220] ata5.00: ATA-7: WDC WD740ADFD-00NLR1, 20.07P20, max UDMA/133
[    5.732222] ata5.00: 145226112 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    5.744186] ata5.00: ata_hpa_resize 1: sectors = 145226112, hpa_sectors = 145226112
[    5.744189] ata5.00: configured for UDMA/133
[    5.744192] scsi5 : ata_piix
[    5.755320] usb 2-1: new low speed USB device using uhci_hcd and address 3
[    5.935081] usb 2-1: configuration #1 chosen from 1 choice
[    5.938996] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80000ef23f5]
[    6.146731] usb 5-7.3: new high speed USB device using ehci_hcd and address 4
[    6.252682] usb 5-7.3: configuration #1 chosen from 1 choice
[    6.254502] usbcore: registered new interface driver hiddev
[    6.268399] input: Logitech USB Receiver as /class/input/input1
[    6.268409] input: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.1-1
[    6.298347] input: Logitech USB Receiver as /class/input/input2
[    6.298369] input: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-1
[    6.298377] usbcore: registered new interface driver usbhid
[    6.298380] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[    6.406208] ata6.00: ATA-6: Config  Disk, RGL10364, max UDMA/133
[    6.406210] ata6.00: 640 sectors, multi 1: LBA 
[    6.406212] ata6.00: Drive reports diagnostics failure. This may indicate a drive
[    6.406213] ata6.00: fault or invalid emulation. Contact drive vendor for information.
[    6.406521] ata6.00: configured for UDMA/133
[    6.406589] scsi 4:0:0:0: Direct-Access     ATA      WDC WD740ADFD-00 20.0 PQ: 0 ANSI: 5
[    6.406926] scsi 5:0:0:0: Direct-Access     ATA      Config  Disk     RGL1 PQ: 0 ANSI: 5
[    6.407270] PCI: Enabling device 0000:02:00.1 (0000 -> 0001)
[    6.407276] ACPI: PCI Interrupt 0000:02:00.1[b] -> GSI 16 (level, low) -> IRQ 16
[    6.407293] PCI: Setting latency timer of device 0000:02:00.1 to 64
[    6.407312] ata7: PATA max UDMA/100 cmd 0x00019c00 ctl 0x00019882 bmdma 0x00019400 irq 16
[    6.407332] ata8: PATA max UDMA/100 cmd 0x00019800 ctl 0x00019482 bmdma 0x00019408 irq 16
[    6.407345] scsi6 : pata_jmicron
[    6.411937] SCSI device sda: 145226112 512-byte hdwr sectors (74356 MB)
[    6.411945] sda: Write Protect is off
[    6.411946] sda: Mode Sense: 00 3a 00 00
[    6.411956] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.411985] SCSI device sda: 145226112 512-byte hdwr sectors (74356 MB)
[    6.411991] sda: Write Protect is off
[    6.411993] sda: Mode Sense: 00 3a 00 00
[    6.412002] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.412004]  sda:sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.416868] Uniform CD-ROM driver Revision: 3.20
[    6.416954] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    6.423138]  sda1 sda2 < sda5 >
[    6.436209] sd 4:0:0:0: Attached scsi disk sda
[    6.436300] SCSI device sdb: 640 512-byte hdwr sectors (0 MB)
[    6.436306] sdb: Write Protect is off
[    6.436307] sdb: Mode Sense: 00 3a 00 00
[    6.436317] SCSI device sdb: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    6.436340] SCSI device sdb: 640 512-byte hdwr sectors (0 MB)
[    6.436345] sdb: Write Protect is off
[    6.436347] sdb: Mode Sense: 00 3a 00 00
[    6.436356] SCSI device sdb: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    6.436358]  sdb: unknown partition table
[    6.437026] sd 5:0:0:0: Attached scsi disk sdb
[    6.439690] sr 2:0:0:0: Attached scsi generic sg0 type 5
[    6.439702] sd 4:0:0:0: Attached scsi generic sg1 type 0
[    6.439717] sd 5:0:0:0: Attached scsi generic sg2 type 0
[    6.568496] Attempting manual resume
[    6.568498] swsusp: Resume From Partition 8:5
[    6.568499] PM: Checking swsusp image.
[    6.568608] PM: Resume from disk failed.
[    6.580370] kjournald starting.  Commit interval 5 seconds
[    6.580378] EXT3-fs: mounted filesystem with ordered data mode.
[   12.405423] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.703171] intel_rng: FWH not detected
[   12.752491] input: PC Speaker as /class/input/input3
[   12.816584] iTCO_vendor_support: vendor-support=0
[   12.873356] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   12.873405] iTCO_wdt: Found a ICH7 or ICH7R TCO device (Version=2, TCOBASE=0x0860)
[   12.873426] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   13.168640] wmaster0: Selected rate control algorithm 'simple'
[   13.214713] wiphy0: hwaddr 00:15:af:0b:c0:b3, rtl8187 V1 + rtl8225z2
[   13.214720] usbcore: registered new interface driver rtl8187
[   13.574292] ata7: port is slow to respond, please be patient (Status 0xd0)
[   16.592150] wmaster0: Does not support passive scan, disabled
[   17.687783] NET: Registered protocol family 17
[   36.571600] ata7: port failed to respond (30 secs, Status 0xd0)
[   36.583398] ATA: abnormal status 0xD0 on port 0x00019c07
[   36.583412] scsi7 : pata_jmicron
[   36.750433] ATA: abnormal status 0x7F on port 0x00019807
```

Any help would be greatly appreciated as 74GB can be filled up quite quickly

---

### Post by DealerMan on 2007-06-06
You need to format the drive with gparted.  You can use Add/Remove Software to install it and then format to your liking, along with mounting.

---

### Post by MCSE_Crossover on 2007-06-13
did you ever get this working? I had similar work arounds that I had to do to get my Asus P5W Deluxe mobo working and recognizing all my drives. I can help if necssary

---

