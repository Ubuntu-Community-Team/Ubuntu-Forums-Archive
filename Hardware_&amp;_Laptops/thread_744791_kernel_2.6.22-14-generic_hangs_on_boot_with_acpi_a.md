---
title: "kernel 2.6.22-14-generic hangs on boot with acpi and smp enabled"
date: 2008-04-03
forum: Hardware &amp; Laptops
---

### Post by arrancaru on 2008-04-03
Hi. I got some problems here. I'm currently running ubuntu gutsy. The problem is when acpi and smp are both enabled the boot hangs. It only works with the cheats "nosmp noapic nolapic" (but with only one processor) or "acpi=off" (but without acpi support). Any help would be fully appreciated.

lspci output:
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:09.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
00:09.2 Generic system peripheral [0805]: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
00:09.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: ATI Technologies Inc M71 [Mobility Radeon X2100] (Secondary) (rev ce)

```

dmesg output:
```
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[    0.000000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fd90000 (usable)
[    0.000000]  BIOS-e820: 000000003fd90000 - 000000003fd9a000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003fd9a000 - 000000003fd9b000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fd9b000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 125MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f85a0
[    0.000000] Entering add_active_range(0, 0, 261520) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   261520
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   261520
[    0.000000] On node 0 totalpages: 261520
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 251 pages used for memmap
[    0.000000]   HighMem zone: 31893 pages, LIFO batch:7
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F8570 checksum 0
[    0.000000] ACPI: RSDP 000F8570, 0024 (r2 PTLTD )
[    0.000000] ACPI: XSDT 3FD917EC, 0064 (r1 kennex kennexpc  6040000  LTP        0)
[    0.000000] ACPI: FACP 3FD99B86, 00F4 (r3 SiS    671MX     6040000 PTL     F4240)
[    0.000000] ACPI: DSDT 3FD951CF, 4943 (r1 PTLTD       671  6040000 MSFT  3000000)
[    0.000000] ACPI: FACS 3FD9AFC0, 0040
[    0.000000] ACPI: APIC 3FD99C7A, 005E (r1 PTLTD       APIC    6040000  LTP        0)
[    0.000000] ACPI: SLIC 3FD99CD8, 0176 (r1 kennex kennexpc  6040000  LTP        0)
[    0.000000] ACPI: MCFG 3FD99E4E, 003C (r1 PTLTD    MCFG    6040000  LTP        0)
[    0.000000] ACPI: SLIC 3FD99E8A, 0176 (r1 kennex kennexpc  6040000  LTP        0)
[    0.000000] ACPI: SSDT 3FD92D10, 025F (r1  PmRef  Cpu0Tst     3000 INTL 20050228)
[    0.000000] ACPI: SSDT 3FD92C6A, 00A6 (r1  PmRef  Cpu1Tst     3000 INTL 20050228)
[    0.000000] ACPI: SSDT 3FD91850, 141A (r1  PmRef    CpuPm     3000 INTL 20050228)
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID: SiS      Product ID: 671MX        APIC at: 0xFEE00000
[    0.000000] Processor #0 6:14 APIC version 20
[    0.000000] Processor #1 6:14 APIC version 20
[    0.000000] I/O APIC #2 Version 20 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 2
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] Built 1 zonelists.  Total pages: 259477
[    0.000000] Kernel command line: root=/dev/sda3 ro noapic nolapic nosmp
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1733.494 MHz processor.
[   25.505183] Console: colour VGA+ 80x25
[   25.508310] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   25.509082] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   25.571377] Memory: 1023544k/1046080k available (2015k kernel code, 21912k reserved, 915k data, 364k init, 128576k highmem)
[   25.571462] virtual kernel memory layout:
[   25.571465]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   25.571468]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   25.571471]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   25.571473]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   25.571476]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   25.571479]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   25.571482]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   25.571892] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   25.572060] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   25.652054] Calibrating delay using timer specific routine.. 3469.86 BogoMIPS (lpj=6939724)
[   25.652199] Security Framework v1.0.0 initialized
[   25.652263] SELinux:  Disabled at boot.
[   25.652340] Mount-cache hash table entries: 512
[   25.652627] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000
[   25.652644] monitor/mwait feature present.
[   25.652700] using mwait in idle threads.
[   25.652757] CPU: L1 I cache: 32K, L1 D cache: 32K
[   25.652852] CPU: L2 cache: 1024K
[   25.652905] CPU: Physical Processor ID: 0
[   25.652958] CPU: Processor Core ID: 0
[   25.653012] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000
[   25.653033] Compat vDSO mapped to ffffe000.
[   25.653106] Checking 'hlt' instruction... OK.
[   25.668302] SMP alternatives: switching to UP code
[   25.669237] Early unpacking initramfs... done
[   26.508760] ACPI: Core revision 20070126
[   26.508920] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   26.513035] ACPI: setting ELCR to 0800 (from 0eb8)
[   26.919686] CPU0: Intel Genuine Intel(R) CPU           T2080  @ 1.73GHz stepping 0c
[   26.919880] SMP mode deactivated, forcing use of dummy APIC emulation.
[   26.919991] Brought up 1 CPUs
[   26.920235] Booting paravirtualized kernel on bare hardware
[   26.920370] Time:  0:05:59  Date: 03/04/108
[   26.920455] NET: Registered protocol family 16
[   26.920646] EISA bus registered
[   26.920703] ACPI: bus type pci registered
[   26.936170] PCI: PCI BIOS revision 3.00 entry at 0xfde55, last bus=3
[   26.936232] PCI: Using configuration type 1
[   26.936285] Setting up standard PCI resources
[   26.945054] ACPI: EC: Look up EC in DSDT
[   26.945988] ACPI: EC: GPE=0x13, ports=0x66, 0x62
[   36.938311] ACPI: Interpreter enabled
[   36.938367] ACPI: (supports S0 S3 S4 S5)
[   36.938641] ACPI: Using PIC for interrupt routing
[   36.947531] ACPI: EC: GPE=0x13, ports=0x66, 0x62
[   36.947679] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   36.947761] PCI: Probing PCI hardware (bus 00)
[   36.949299] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   36.966726] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *9 10 11)
[   36.967297] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 9 10 11)
[   36.967860] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 7 9 10 11)
[   36.968422] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 9 10 11)
[   36.969018] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11)
[   36.969582] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11)
[   36.970146] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 *7 9 10 11)
[   36.970737] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 11) *0, disabled.
[   36.971437] Linux Plug and Play Support v0.97 (c) Adam Belay
[   36.971506] pnp: PnP ACPI init
[   36.971567] ACPI: bus type pnp registered
[   36.975306] pnp: PnP ACPI: found 10 devices
[   36.975360] ACPI: ACPI bus type pnp unregistered
[   36.975417] PnPBIOS: Disabled by ACPI PNP
[   36.975553] PCI: Using ACPI for IRQ routing
[   36.975608] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   37.013091] NET: Registered protocol family 8
[   37.013151] NET: Registered protocol family 20
[   37.013367] pnp: 00:04: ioport range 0x8000-0x80be has been reserved
[   37.013425] pnp: 00:04: ioport range 0x8100-0x812f has been reserved
[   37.013481] pnp: 00:04: ioport range 0x4d0-0x4d1 has been reserved
[   37.013537] pnp: 00:04: ioport range 0xfe00-0xfe00 has been reserved
[   37.013597] pnp: 00:04: iomem range 0xe0000000-0xefffffff could not be reserved
[   37.013662] pnp: 00:04: iomem range 0xfec00000-0xfecfffff could not be reserved
[   37.013726] pnp: 00:04: iomem range 0xfee00000-0xfeefffff could not be reserved
[   37.013792] pnp: 00:04: iomem range 0xffb80000-0xffbfffff has been reserved
[   37.014297] Time: tsc clocksource has been installed.
[   37.044466] PCI: Bridge: 0000:00:01.0
[   37.044521]   IO window: 9000-9fff
[   37.044577]   MEM window: d8000000-d80fffff
[   37.044633]   PREFETCH window: d0000000-d7ffffff
[   37.044690] PCI: Bridge: 0000:00:06.0
[   37.044741]   IO window: disabled.
[   37.044796]   MEM window: disabled.
[   37.044850]   PREFETCH window: disabled.
[   37.044906] PCI: Bridge: 0000:00:07.0
[   37.044959]   IO window: 3000-4fff
[   37.045015]   MEM window: dc000000-dfffffff
[   37.045069]   PREFETCH window: disabled.
[   37.045153] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   37.045534] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 9
[   37.045590] PCI: setting IRQ 9 as level-triggered
[   37.045596] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
[   37.045744] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   37.045773] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
[   37.045919] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   37.045941] NET: Registered protocol family 2
[   37.082257] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   37.082401] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   37.084617] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   37.085437] TCP: Hash tables configured (established 131072 bind 65536)
[   37.085495] TCP reno registered
[   37.094478] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
[   37.910847]  it is
[   38.763169] Freeing initrd memory: 9004k freed
[   38.764026] audit: initializing netlink socket (disabled)
[   38.764098] audit(1207267570.556:1): initialized
[   38.764278] highmem bounce pool size: 64 pages
[   38.768014] VFS: Disk quotas dquot_6.5.1
[   38.768164] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   38.768382] io scheduler noop registered
[   38.768436] io scheduler anticipatory registered
[   38.768489] io scheduler deadline registered
[   38.768568] io scheduler cfq registered (default)
[   38.768681] Boot video device is 0000:01:00.0
[   38.768809] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   38.768867] assign_interrupt_mode Found MSI capability
[   38.768923] Allocate Port Service[0000:00:01.0:pcie00]
[   38.769068] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   38.769149] assign_interrupt_mode Found MSI capability
[   38.769204] Allocate Port Service[0000:00:06.0:pcie00]
[   38.769355] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   38.769436] assign_interrupt_mode Found MSI capability
[   38.769491] Allocate Port Service[0000:00:07.0:pcie00]
[   38.769550] Allocate Port Service[0000:00:07.0:pcie02]
[   38.769811] isapnp: Scanning for PnP cards...
[   39.123819] isapnp: No Plug & Play device found
[   39.169332] Real Time Clock Driver v1.12ac
[   39.169730] hpet_acpi_add: no address or irqs in _CRS
[   39.169810] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   39.172780] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   39.173198] input: Macintosh mouse button emulation as /class/input/input0
[   39.173397] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   39.177095] i8042.c: Detected active multiplexing controller, rev 1.1.
[   39.179539] serio: i8042 KBD port at 0x60,0x64 irq 1
[   39.179597] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   39.179652] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   39.179706] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   39.179760] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   39.180147] mice: PS/2 mouse device common for all mice
[   39.180575] EISA: Probing bus 0 at eisa.0
[   39.180637] Cannot allocate resource for EISA slot 1
[   39.180696] Cannot allocate resource for EISA slot 3
[   39.180750] Cannot allocate resource for EISA slot 4
[   39.180818] Cannot allocate resource for EISA slot 8
[   39.180871] EISA: Detected 0 cards.
[   39.181097] TCP cubic registered
[   39.181171] NET: Registered protocol family 1
[   39.181262] Using IPI No-Shortcut mode
[   39.181569]   Magic number: 4:794:50
[   39.182104] Freeing unused kernel memory: 364k freed
[   39.354465] input: AT Translated Set 2 keyboard as /class/input/input1
[   39.554698] fuse init (API version 7.8)
[   39.564636] Capability LSM initialized
[   39.582206] ACPI: SSDT 3FD9350C, 02C5 (r1  PmRef  Cpu0Ist     3000 INTL 20050228)
[   39.583994] ACPI: SSDT 3FD92F6F, 0518 (r1  PmRef  Cpu0Cst     3001 INTL 20050228)
[   39.584758] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   39.584974] ACPI: Processor [CPU0] (supports 8 throttling states)
[   39.585142] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   39.585297] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   39.585452] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   39.585606] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   39.585761] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   39.585916] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   39.586070] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   39.589158] ACPI: Thermal Zone [TZ01] (56 C)
[   40.532148] SCSI subsystem initialized
[   40.543201] libata version 2.21 loaded.
[   40.549131] pata_sis 0000:00:02.5: version 0.5.1
[   40.549175] ACPI: PCI Interrupt 0000:00:02.5[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
[   40.549488] scsi0 : pata_sis
[   40.549611] scsi1 : pata_sis
[   40.549797] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011080 irq 14
[   40.549863] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011088 irq 15
[   40.569735] usbcore: registered new interface driver usbfs
[   40.569837] usbcore: registered new interface driver hub
[   40.569927] usbcore: registered new device driver usb
[   40.571455] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   40.885077] ata1.00: ATAPI: TSSTcorpCD/DVDW TS-L632D, TI03, max UDMA/33
[   41.072869] ata1.00: configured for UDMA/33
[   41.072974] ata2: port disabled. ignoring.
[   41.088975] scsi 0:0:0:0: CD-ROM            TSSTcorp CD/DVDW TS-L632D TI03 PQ: 0 ANSI: 5
[   41.089691] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[   41.089749] PCI: setting IRQ 11 as level-triggered
[   41.089755] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[   41.089914] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   41.090249] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   41.090331] ohci_hcd 0000:00:03.0: irq 11, io mem 0xd8304000
[   41.146691] usb usb1: configuration #1 chosen from 1 choice
[   41.146804] hub 1-0:1.0: USB hub found
[   41.146867] hub 1-0:1.0: 4 ports detected
[   15.216000] Marking TSC unstable due to: possible TSC halt in C2.
[   15.220000] Time: acpi_pm clocksource has been installed.
[   15.260000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   15.260000] Uniform CD-ROM driver Revision: 3.20
[   15.260000] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   15.268000] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   15.296000] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 10
[   15.296000] PCI: setting IRQ 10 as level-triggered
[   15.296000] ACPI: PCI Interrupt 0000:00:03.1[B] -> Link [LNKF] -> GSI 10 (level, low) -> IRQ 10
[   15.296000] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   15.296000] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[   15.296000] ohci_hcd 0000:00:03.1: irq 10, io mem 0xd8305000
[   15.352000] usb usb2: configuration #1 chosen from 1 choice
[   15.352000] hub 2-0:1.0: USB hub found
[   15.352000] hub 2-0:1.0: 4 ports detected
[   15.456000] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 7
[   15.456000] PCI: setting IRQ 7 as level-triggered
[   15.456000] ACPI: PCI Interrupt 0000:00:03.3[C] -> Link [LNKG] -> GSI 7 (level, low) -> IRQ 7
[   15.456000] ehci_hcd 0000:00:03.3: EHCI Host Controller
[   15.456000] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 3
[   15.456000] ehci_hcd 0000:00:03.3: irq 7, io mem 0xd8306000
[   15.600000] usb 1-1: new low speed USB device using ohci_hcd and address 2
[   15.600000] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   15.600000] usb usb3: configuration #1 chosen from 1 choice
[   15.600000] hub 3-0:1.0: USB hub found
[   15.600000] hub 3-0:1.0: 8 ports detected
[   15.704000] PCI: Enabling device 0000:00:09.0 (0015 -> 0017)
[   15.704000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[   15.704000] PCI: setting IRQ 5 as level-triggered
[   15.704000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   15.756000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[5]  MMIO=[d8307000-d83077ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[   15.756000] sata_sis 0000:00:05.0: version 0.8
[   15.756000] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   15.756000] sata_sis 0000:00:05.0: Detected SiS 1183/966/966L/968/680 controller in PATA mode
[   15.756000] scsi2 : sata_sis
[   15.756000] scsi3 : sata_sis
[   15.756000] ata3: PATA max UDMA/133 cmd 0x000110c8 ctl 0x000110be bmdma 0x000110a0 irq 5
[   15.756000] ata4: PATA max UDMA/133 cmd 0x000110c0 ctl 0x000110ba bmdma 0x000110a8 irq 5
[   15.920000] ata3.00: ATA-7: TOSHIBA MK8037GSX, DL250J, max UDMA/100
[   15.920000] ata3.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   15.928000] ata3.00: configured for UDMA/100
[   16.096000] scsi 2:0:0:0: Direct-Access     ATA      TOSHIBA MK8037GS DL25 PQ: 0 ANSI: 5
[   16.096000] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[   16.112000] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   16.112000] sd 2:0:0:0: [sda] Write Protect is off
[   16.112000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   16.112000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.112000] sd 2:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   16.112000] sd 2:0:0:0: [sda] Write Protect is off
[   16.112000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   16.112000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   16.112000]  sda:<6>usb 3-3: new high speed USB device using ehci_hcd and address 3
[   16.468000]  sda1 sda2 sda3
[   16.492000] sd 2:0:0:0: [sda] Attached SCSI disk
[   16.636000] usb 3-3: configuration #1 chosen from 1 choice
[   16.860000] Attempting manual resume
[   16.860000] swsusp: Resume From Partition 8:2
[   16.860000] PM: Checking swsusp image.
[   16.860000] PM: Resume from disk failed.
[   16.880000] ReiserFS: sda3: found reiserfs format "3.6" with standard journal
[   16.880000] ReiserFS: sda3: using ordered data mode
[   16.900000] ReiserFS: sda3: journal params: device sda3, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   16.900000] ReiserFS: sda3: checking transaction log (sda3)
[   16.944000] usb 1-1: new low speed USB device using ohci_hcd and address 3
[   16.944000] ReiserFS: sda3: Using r5 hash to sort names
[   17.028000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00030d004109615d]
[   17.156000] usb 1-1: configuration #1 chosen from 1 choice
[   29.760000] sis190 Gigabit Ethernet driver 1.2 loaded.
[   29.760000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 3
[   29.760000] PCI: setting IRQ 3 as level-triggered
[   29.760000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LNKD] -> GSI 3 (level, low) -> IRQ 3
[   29.760000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   29.776000] 0000:00:04.0: Read MAC address from EEPROM
[   29.876000] 0000:00:04.0: Realtek PHY RTL8201 transceiver at address 1.
[   30.028000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   30.372000] 0000:00:04.0: Using transceiver at address 1 as default.
[   30.404000] 0000:00:04.0: SiS 191 PCI Gigabit Ethernet adapter at f895e800 (IRQ: 3), 00:03:0d:7a:90:00
[   30.404000] eth0: GMII mode.
[   30.404000] eth0: Enabling Auto-negotiation.
[   30.436000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   31.268000] input: PC Speaker as /class/input/input2
[   31.272000] sdhci: Secure Digital Host Controller Interface driver
[   31.272000] sdhci: Copyright(c) Pierre Ossman
[   31.272000] sdhci: SDHCI controller found at 0000:00:09.2 [1217:7120] (rev 2)
[   31.272000] ACPI: PCI Interrupt 0000:00:09.2[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[   31.272000] sdhci:slot0: Unknown controller version (2). You may experience problems.
[   31.272000] mmc0: SDHCI at 0xd8309c00 irq 5 DMA
[   31.904000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[   31.936000] Linux agpgart interface v0.102 (c) Dave Jones
[   31.944000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   32.208000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   32.252000] [fglrx] Maximum main memory to use for locked dma buffers: 926 MBytes.
[   32.256000] [fglrx] ASYNCIO init succeed!
[   32.256000] [fglrx] PAT is enabled successfully!
[   32.272000] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   32.828000] usbcore: registered new interface driver hiddev
[   32.836000] input: USB Optical Mouse USB Optical Mouse as /class/input/input4
[   32.836000] input: USB HID v1.10 Mouse [USB Optical Mouse USB Optical Mouse] on usb-0000:00:03.0-1
[   32.836000] usbcore: registered new interface driver usbhid
[   32.836000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   33.464000] ieee80211_init: failed to initialize WME (err=-17)
[   33.512000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_unregister
[   33.512000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_put
[   33.512000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_sta_info_get
[   33.512000] iwlwifi_rc80211_simple: Unknown symbol iwlwifi_ieee80211_rate_control_register
[   33.540000] wmaster0: Selected rate control algorithm 'simple'
[   33.648000] usbcore: registered new interface driver rt73usb
[   33.688000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 4
[   33.688000] PCI: setting IRQ 4 as level-triggered
[   33.688000] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LNKC] -> GSI 4 (level, low) -> IRQ 4
[   33.688000] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   33.896000] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   34.772000] lp: driver loaded but no devices found
[   35.020000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   35.020000] apm: overridden by ACPI.
[   35.136000] Adding 1172736k swap on /dev/sda2.  Priority:-1 extents:1 across:1172736k
[   49.220000] ACPI: AC Adapter [AC0] (on-line)
[   49.232000] No dock devices found.
[   49.324000] input: Power Button (FF) as /class/input/input5
[   49.336000] ACPI: Power Button (FF) [PWRF]
[   49.368000] input: Power Button (CM) as /class/input/input6
[   49.368000] ACPI: Power Button (CM) [PWRB]
[   49.384000] input: Sleep Button (CM) as /class/input/input7
[   49.384000] ACPI: Sleep Button (CM) [SLPB]
[   49.392000] input: Lid Switch as /class/input/input8
[   49.392000] ACPI: Lid Switch [LID0]
[   49.548000] ACPI: Battery Slot [BAT0] (battery present)
[   49.568000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   51.620000] ppdev: user-space parallel port driver
[   52.048000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   52.048000] apm: disabled on user request.
[   52.556000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 9 (level, low) -> IRQ 9
[   54.696000] [fglrx] Reserve Block - 0 offset =  0X7ffb000 length = 0X5000
[   54.696000] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
[   54.696000] [fglrx] Reserve Block - 2 offset =  0X7fbb000 length = 0X40000
[   61.060000] eth0: mii ext = 0000.
[   61.076000] eth0: mii lpa = 45e1 adv = 01e1.
[   61.076000] eth0: link on 100 Mbps Full Duplex mode.
[   63.732000] NET: Registered protocol family 17
[   65.904000] wlan0: Initial auth_alg=0
[   65.904000] wlan0: authenticate with AP 00:4f:62:07:ad:4b
[   66.104000] wlan0: authenticate with AP 00:4f:62:07:ad:4b
[   66.304000] wlan0: authenticate with AP 00:4f:62:07:ad:4b
[   66.504000] wlan0: authentication with AP 00:4f:62:07:ad:4b timed out
[   89.788000] usb 1-1: USB disconnect, address 3
[   94.264000] usb 1-1: new low speed USB device using ohci_hcd and address 4
[   94.476000] usb 1-1: configuration #1 chosen from 1 choice
[   94.504000] input: USB Optical Mouse USB Optical Mouse as /class/input/input9
[   94.504000] input: USB HID v1.10 Mouse [USB Optical Mouse USB Optical Mouse] on usb-0000:00:03.0-1
```

---

### Post by farbird on 2008-04-24
i have the same problem as yours when booting a gutsy kernel on an old centrino single processor laptop..

using edgy kernels solved the problem but I shall try the kernel cheats u provided..

This was because the wifi in edgy kernel didnt work...
But if i do the acpi=off in gutsy kernel, wifi will work but sound wouldnt..

---

### Post by arrancaru on 2008-04-24
My laptop is a dual core 1.73 ghz, not the new core 2 duo. I will test with old kernels like you said.

---

### Post by farbird on 2008-04-24
whadayaknow...

nosmp noapic nolapic works...

but i havent tested beyond booting up and getting sound..

my previous experience with noapic resulted in keypress bahving funnily..
single tap becomes delayed multiple taps..

will provide more results soon

---

### Post by arrancaru on 2008-05-05
Hey farbird try "noapic nolapic pci=assign-busses apicmaintimer idle=poll reboot=cold,hard ". Yes I'm happy cause acpi is working together with two cores support 8) . This week I test the wireless and other things, but til now almost everything is ok.

---

