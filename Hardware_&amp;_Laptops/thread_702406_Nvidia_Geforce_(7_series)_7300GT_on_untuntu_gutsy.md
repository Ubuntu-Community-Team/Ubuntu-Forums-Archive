---
title: "Nvidia Geforce (7 series) 7300GT on untuntu gutsy"
date: 2008-02-20
forum: Hardware &amp; Laptops
---

### Post by Dabblo on 2008-02-20
Hello folks, I need a hand lol, I purchased a new graphics card today.

System Pentium4: (Dell dimension 4550). 756Mb ram. Ubuntu gutsy 7.1. Anyway I got a Nvidia Geforce (7 series) 7300 GT to replace the existing old GeForce MX 420. I was able to enable the driver to use desktop effects on the MX 420 card. But this new card I can't make work I have tried enabling the driver through envy but nothing worked out. I seem to loose the resolution down to 800x600 (ADI M700 Microscan monitor). I am new to this ubuntu and did a fresh install on purchasing the new card. Any help would be appreciated. I have tried suggested drivers - Nvidia-glx and Nvidia-glx-new, Ubuntu the restarts but only in low-graphics mode. I even tried to manually configure monitor etc. I also tried installing the driver in terminal as akschnare suggested above from nvidia.com. Have tried everything I can think of.. I'm wondering If I screwed something up. So far I'm not winning guys ....Help

Regards Dai

P.s I am new to this :)

---

### Post by roaldz on 2008-02-20
Hey, you only have to post once.. You´ll be helped. I´m helping, right?

[http://ubuntuforums.org/showthread.php?t=702406](http://ubuntuforums.org/showthread.php?t=702406)
[http://ubuntuforums.org/showthread.php?p=4368380#post4368380](http://ubuntuforums.org/showthread.php?p=4368380#post4368380)
[http://ubuntuforums.org/showthread.php?p=4368280#post4368280](http://ubuntuforums.org/showthread.php?p=4368280#post4368280)
[http://ubuntuforums.org/showthread.php?p=4364994#post4364994](http://ubuntuforums.org/showthread.php?p=4364994#post4364994)

In some threads you posted the same message twice. In your hurry, you didn´t even spell Ubuntu right! You´re being impatient, I´m trying to help you, if you´d post you status on the problem, I´m glad to help you.
If it has to go this way, I´m loosing hope.
Post the output of these commands, and put them in [ CODE] [ /CODE] tags (the ¨#¨ button), so I can read them decently:

¨dmesg¨
¨cat /var/log/Xorg.0.log¨
¨lsmod¨
¨cat /etc/X11/Xorg.conf¨

Roald

---

### Post by Dabblo on 2008-02-20
[    0.000000] Linux version 2.6.22-14-386 (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 Tue Feb 12 07:12:19 UTC 2008 (Ubuntu 2.6.22-14.52-386)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002ff75000 (usable)
[    0.000000]  BIOS-e820: 000000002ff75000 - 000000002ff77000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000002ff77000 - 000000002ff98000 (ACPI data)
[    0.000000]  BIOS-e820: 000000002ff98000 - 0000000030000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 767MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fe710
[    0.000000] Entering add_active_range(0, 0, 196469) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   196469
[    0.000000]   HighMem    196469 ->   196469
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   196469
[    0.000000] On node 0 totalpages: 196469
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1502 pages used for memmap
[    0.000000]   Normal zone: 190871 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FEB90 checksum 0
[    0.000000] ACPI: RSDP 000FEB90, 0014 (r0 DELL  )
[    0.000000] ACPI: RSDT 000FD4F6, 0038 (r1 DELL    4550           6 ASL        61)
[    0.000000] ACPI: FACP 000FD52E, 0074 (r1 DELL    4550           6 ASL        61)
[    0.000000] ACPI: DSDT FFFCE77E, 22D0 (r1   DELL    dt_ex     1000 MSFT  100000D)
[    0.000000] ACPI: FACS 2FF75000, 0040
[    0.000000] ACPI: SSDT FFFD0A4E, 00A7 (r1   DELL    st_ex     1000 MSFT  100000D)
[    0.000000] ACPI: APIC 000FD5A2, 006C (r1 DELL    4550           6 ASL        61)
[    0.000000] ACPI: BOOT 000FD60E, 0028 (r1 DELL    4550           6 ASL        61)
[    0.000000] ACPI: ASF! 000FD636, 0067 (r16 DELL    4550           6 ASL        61)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:cec00000)
[    0.000000] Built 1 zonelists.  Total pages: 194935
[    0.000000] Kernel command line: root=UUID=e625ab2d-a39a-4508-8989-1bdcf9588c17 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2525.131 MHz processor.
[   21.262324] Console: colour VGA+ 80x25
[   21.263330] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   21.264336] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   21.286876] Memory: 768020k/785876k available (1929k kernel code, 17192k reserved, 876k data, 348k init, 0k highmem)
[   21.286886] virtual kernel memory layout:
[   21.286887]     fixmap  : 0xfffa8000 - 0xfffff000   ( 348 kB)
[   21.286888]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   21.286889]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
[   21.286890]     lowmem  : 0xc0000000 - 0xeff75000   ( 767 MB)
[   21.286891]       .init : 0xc03c0000 - 0xc0417000   ( 348 kB)
[   21.286892]       .data : 0xc02e2655 - 0xc03bda04   ( 876 kB)
[   21.286894]       .text : 0xc0100000 - 0xc02e2655   (1929 kB)
[   21.286897] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   21.286949] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   21.366865] Calibrating delay using timer specific routine.. 5053.70 BogoMIPS (lpj=10107400)
[   21.366888] Security Framework v1.0.0 initialized
[   21.366895] SELinux:  Disabled at boot.
[   21.366902] Mount-cache hash table entries: 512
[   21.367004] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[   21.367014] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   21.367016] CPU: L2 cache: 512K
[   21.367019] CPU: After all inits, caps: 3febfbff 00000000 00000000 0000b080 00000000 00000000 00000000
[   21.367029] Compat vDSO mapped to ffffe000.
[   21.367040] CPU: Intel(R) Pentium(R) 4 CPU 2.53GHz stepping 04
[   21.367046] Checking 'hlt' instruction... OK.
[   21.383505] Early unpacking initramfs... done
[   21.706272] ACPI: Core revision 20070126
[   21.718148] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   21.741742] ENABLING IO-APIC IRQs
[   21.741915] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   21.886288] Booting paravirtualized kernel on bare hardware
[   21.886359] Time: 14:26:52  Date: 01/20/108
[   21.886384] NET: Registered protocol family 16
[   21.886480] EISA bus registered
[   21.886494] ACPI: bus type pci registered
[   21.912433] PCI: PCI BIOS revision 2.10 entry at 0xfbe6d, last bus=2
[   21.912435] PCI: Using configuration type 1
[   21.912437] Setting up standard PCI resources
[   21.913776] ACPI: EC: Look up EC in DSDT
[   21.938366] ACPI: Interpreter enabled
[   21.938370] ACPI: (supports S0 S1 S3 S4 S5)
[   21.938390] ACPI: Using IOAPIC for interrupt routing
[   21.960877] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   21.960896] PCI: Probing PCI hardware (bus 00)
[   21.961269] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[   21.961270] * this clock source is slow. If you are sure your timer does not have
[   21.961272] * this bug, please use "acpi_pm_good" to disable the workaround
[   21.961314] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[   21.961317] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[   21.961675] PCI: Firmware left 0000:02:08.0 e100 interrupts enabled, disabling
[   21.961736] PCI: Transparent bridge - 0000:00:1e.0
[   21.961762] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   21.962245] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   21.990106] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[   21.990427] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[   21.990745] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[   21.991062] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[   21.991381] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[   21.991697] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   21.992015] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[   21.992334] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 9 10 11 12 15)
[   21.992465] Linux Plug and Play Support v0.97 (c) Adam Belay
[   21.992476] pnp: PnP ACPI init
[   21.992484] ACPI: bus type pnp registered
[   22.013765] pnp: PnP ACPI: found 12 devices
[   22.013768] ACPI: ACPI bus type pnp unregistered
[   22.013772] PnPBIOS: Disabled by ACPI PNP
[   22.013827] PCI: Using ACPI for IRQ routing
[   22.013831] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   22.020161] NET: Registered protocol family 8
[   22.020163] NET: Registered protocol family 20
[   22.020233] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
[   22.020236] pnp: 00:00: iomem range 0x100000-0xffffff could not be reserved
[   22.020239] pnp: 00:00: iomem range 0x1000000-0x2ff74fff could not be reserved
[   22.020242] pnp: 00:00: iomem range 0xf0000-0xfffff could not be reserved
[   22.020253] pnp: 00:0b: ioport range 0x800-0x85f has been reserved
[   22.020256] pnp: 00:0b: ioport range 0xc00-0xc7f has been reserved
[   22.020258] pnp: 00:0b: ioport range 0x860-0x8ff could not be reserved
[   22.022020] Time: tsc clocksource has been installed.
[   22.050530] PCI: Bridge: 0000:00:01.0
[   22.050532]   IO window: disabled.
[   22.050537]   MEM window: fb000000-fdffffff
[   22.050541]   PREFETCH window: e0000000-efffffff
[   22.050546] PCI: Bridge: 0000:00:1e.0
[   22.050549]   IO window: e000-efff
[   22.050554]   MEM window: fe100000-fe2fffff
[   22.050557]   PREFETCH window: disabled.
[   22.050573] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   22.050585] NET: Registered protocol family 2
[   22.089957] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   22.090178] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   22.091558] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[   22.092013] TCP: Hash tables configured (established 131072 bind 65536)
[   22.092017] TCP reno registered
[   22.102122] checking if image is initramfs... it is
[   22.553334] Switched to high resolution mode on CPU 0
[   22.739062] Freeing initrd memory: 6682k freed
[   22.739227] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[   22.739230] Simple Boot Flag at 0x7a set to 0x1
[   22.739486] audit: initializing netlink socket (disabled)
[   22.739507] audit(1203517612.344:1): initialized
[   22.741570] VFS: Disk quotas dquot_6.5.1
[   22.741585] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   22.741706] io scheduler noop registered
[   22.741709] io scheduler anticipatory registered
[   22.741710] io scheduler deadline registered
[   22.741728] io scheduler cfq registered (default)
[   22.741800] Boot video device is 0000:01:00.0
[   22.741960] isapnp: Scanning for PnP cards...
[   23.095479] isapnp: No Plug & Play device found
[   23.118733] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   23.118834] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.119595] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.119793] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 22 (level, low) -> IRQ 16
[   23.120791] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   23.121021] input: Macintosh mouse button emulation as /class/input/input0
[   23.121112] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[   23.124730] serio: i8042 KBD port at 0x60,0x64 irq 1
[   23.124737] serio: i8042 AUX port at 0x60,0x64 irq 12
[   23.124939] mice: PS/2 mouse device common for all mice
[   23.125054] EISA: Probing bus 0 at eisa.0
[   23.125091] EISA: Detected 0 cards.
[   23.125201] TCP cubic registered
[   23.125212] NET: Registered protocol family 1
[   23.125237] Using IPI Shortcut mode
[   23.125412]   Magic number: 12:336:435
[   23.126124] Freeing unused kernel memory: 348k freed
[   23.164518] input: AT Translated Set 2 keyboard as /class/input/input1
[   24.349663] fuse init (API version 7.8)
[   24.356647] Capability LSM initialized
[   24.971251] usbcore: registered new interface driver usbfs
[   24.971279] usbcore: registered new interface driver hub
[   24.971303] usbcore: registered new device driver usb
[   24.972263] USB Universal Host Controller Interface driver v3.0
[   24.972344] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 17
[   24.972357] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   24.972361] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   24.972545] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   24.972572] uhci_hcd 0000:00:1d.0: irq 17, io base 0x0000ff80
[   24.972693] usb usb1: configuration #1 chosen from 1 choice
[   24.972721] hub 1-0:1.0: USB hub found
[   24.972728] hub 1-0:1.0: 2 ports detected
[   25.029858] SCSI subsystem initialized
[   25.036464] libata version 2.21 loaded.
[   25.074036] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
[   25.074050] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   25.074054] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   25.074079] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   25.074107] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000ff60
[   25.074205] usb usb2: configuration #1 chosen from 1 choice
[   25.074233] hub 2-0:1.0: USB hub found
[   25.074240] hub 2-0:1.0: 2 ports detected
[   25.122506] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
[   25.122510] e100: Copyright(c) 1999-2006 Intel Corporation
[   25.166234] Floppy drive(s): fd0 is 1.44M
[   25.177946] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[   25.177959] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   25.177963] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   25.177989] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   25.178017] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000ff40
[   25.178125] usb usb3: configuration #1 chosen from 1 choice
[   25.178152] hub 3-0:1.0: USB hub found
[   25.178159] hub 3-0:1.0: 2 ports detected
[   25.210122] FDC 0 is a post-1991 82077
[   25.287173] ata_piix 0000:00:1f.1: version 2.11
[   25.287190] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   25.287197] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 19
[   25.287251] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   25.287354] scsi0 : ata_piix
[   25.287406] scsi1 : ata_piix
[   25.287433] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[   25.287436] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[   25.605409] ata1.00: ATAPI: PLEXTOR CD-R   PX-W1210A, 1.07, max MWDMA2
[   25.777161] ata1.00: configured for MWDMA2
[   25.941130] ata2.00: ATA-6: Maxtor 32049H2, YAH814Y0, max UDMA/100
[   25.941134] ata2.00: 40021632 sectors, multi 8: LBA 
[   25.957111] ata2.00: configured for UDMA/100
[   25.957904] scsi 0:0:0:0: CD-ROM            PLEXTOR  CD-R   PX-W1210A 1.07 PQ: 0 ANSI: 5
[   25.958357] scsi 1:0:0:0: Direct-Access     ATA      Maxtor 32049H2   YAH8 PQ: 0 ANSI: 5
[   25.958749] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 20
[   25.958765] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   25.958769] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   25.958928] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   25.958968] ehci_hcd 0000:00:1d.7: debug port 1
[   25.958975] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   25.958984] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfe300800
[   25.962874] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   25.963202] usb usb4: configuration #1 chosen from 1 choice
[   25.963339] hub 4-0:1.0: USB hub found
[   25.963346] hub 4-0:1.0: 6 ports detected
[   25.983578] sr0: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
[   25.983584] Uniform CD-ROM driver Revision: 3.20
[   25.983811] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   25.988708] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   25.988732] scsi 1:0:0:0: Attached scsi generic sg1 type 0
[   26.004392] sd 1:0:0:0: [sda] 40021632 512-byte hardware sectors (20491 MB)
[   26.004407] sd 1:0:0:0: [sda] Write Protect is off
[   26.004410] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   26.004425] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.004584] sd 1:0:0:0: [sda] 40021632 512-byte hardware sectors (20491 MB)
[   26.004593] sd 1:0:0:0: [sda] Write Protect is off
[   26.004595] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   26.004609] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.004625]  sda: sda1 sda2 sda3 <<6>ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 20 (level, low) -> IRQ 21
[   26.087459] e100: eth0: e100_probe: addr 0xfe1fe000, irq 21, MAC addr 00:07:E9:B8:1C:BB
[   26.088989]  sda5 >
[   26.089677] sd 1:0:0:0: [sda] Attached SCSI disk
[   26.494325] Attempting manual resume
[   26.494330] swsusp: Resume From Partition 8:5
[   26.494332] PM: Checking swsusp image.
[   26.494909] PM: Resume from disk failed.
[   26.541964] kjournald starting.  Commit interval 5 seconds
[   26.541978] EXT3-fs: mounted filesystem with ordered data mode.
[   39.405576] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   39.409265] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   39.460691] Linux agpgart interface v0.102 (c) Dave Jones
[   39.535443] agpgart: Detected an Intel 830M Chipset.
[   39.541782] agpgart: AGP aperture is 128M @ 0xf0000000
[   39.646879] intel_rng: Firmware space is locked read-only. <4>intel_rng: If you can't or
[   39.646882]  don't want to <4>intel_rng: disable this in firmware setup, and <4>intel_rng: if
[   39.646884]  you are certain that your <4>intel_rng: system has a functional
[   39.646885]  RNG, try<4>intel_rng: using the 'no_fwh_detect' option.
[   40.062047] iTCO_vendor_support: vendor-support=0
[   40.064046] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   40.064122] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0860)
[   40.064164] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   40.429948] Real Time Clock Driver v1.12ac
[   40.441824] input: PC Speaker as /class/input/input2
[   40.780464] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   40.792734] parport_pc 00:0a: reported by Plug and Play ACPI
[   40.792787] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   40.877911] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 22
[   40.877932] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   41.248045] intel8x0_measure_ac97_clock: measured 54917 usecs
[   41.248049] intel8x0: clocking to 48000
[   41.602593] loop: module loaded
[   41.621821] lp0: using parport0 (interrupt-driven).
[   41.720084] Adding 289128k swap on /dev/sda5.  Priority:-1 extents:1 across:289128k
[   42.126771] EXT3 FS on sda2, internal journal
[   43.456498] No dock devices found.
[   43.717252] input: Power Button (FF) as /class/input/input4
[   43.722073] ACPI: Power Button (FF) [PWRF]
[   43.761302] input: Power Button (CM) as /class/input/input5
[   43.766073] ACPI: Power Button (CM) [VBTN]
[   45.587301] ppdev: user-space parallel port driver
[   45.598294] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   45.920086] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   45.920093] apm: overridden by ACPI.
[   47.736721] Capability LSM initialized
[   48.245749] Bluetooth: Core ver 2.11
[   48.245878] NET: Registered protocol family 31
[   48.245881] Bluetooth: HCI device and connection manager initialized
[   48.245884] Bluetooth: HCI socket layer initialized
[   48.257724] Bluetooth: L2CAP ver 2.8
[   48.257730] Bluetooth: L2CAP socket layer initialized
[   48.328425] Bluetooth: RFCOMM socket layer initialized
[   48.328525] Bluetooth: RFCOMM TTY layer initialized
[   48.328527] Bluetooth: RFCOMM ver 1.8
[   52.684989] NET: Registered protocol family 17
[   57.627041] NET: Registered protocol family 10
[   57.627218] lo: Disabled Privacy Extensions
[   67.959765] eth0: no IPv6 routers present

        [31] -1 0       0x0000ff60 - 0x0000ff7f (0x20) IX[B]
        [32] -1 0       0x0000ff80 - 0x0000ff9f (0x20) IX[B]
        [33] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [34] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.2
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "GeForce 7600 GS"
(II) NV(0): Creating default Display subsection in Screen section
        "Default Screen" for depth/fbbpp 24/32
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 0.1.0
        ABI class: X.Org Video Driver, version 1.2
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xE0000000
(--) NV(0): MMIO registers at 0xFC000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for analog device on output A...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for analog device on output B...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: ADI  Model: 8830  Serial#: 2404
(II) NV(0): Year: 2000  Week: 29
(II) NV(0): EDID Version: 1.1
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) NV(0): Sync:  Separate
(II) NV(0): Max H-Image Size [cm]: horiz.: 32  vert.: 24
(II) NV(0): Gamma: 2.25
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): redX: 0.625 redY: 0.340   greenX: 0.310 greenY: 0.592
(II) NV(0): blueX: 0.150 blueY: 0.063   whiteX: 0.281 whiteY: 0.311
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) NV(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) NV(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 25.2 MHz   Image Size:  0 x 0 mm
(II) NV(0): h_active: 640  h_sync: 656  h_sync_end 752 h_blank_end 784 h_border: 8
(II) NV(0): v_active: 480  v_sync: 490  v_sync_end 492 v_blanking: 509 v_border: 8
(II) NV(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 70 kHz,
(II) NV(0): Serial No: 029LB0302404
(II) NV(0): Monitor name: ADI M700
(II) NV(0): EDID (in hex):
(II) NV(0):     00ffffffffffff000489308864090000
(II) NV(0):     1d0a01016820187de80692a0574f9726
(II) NV(0):     10484f254a0031594559818061590101
(II) NV(0):     010101010101d609809020e01d101060
(II) NV(0):     a20000000008081e000000fd0032a01e
(II) NV(0):     46ff000a202020202020000000ff0030
(II) NV(0):     32394c42303330323430340a000000fc
(II) NV(0):     00414449204d3730300a20202020004b
(II) NV(0): Probing for EDID on I2C bus B...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(II) NV(0): Unable to detect which CRTCNumber...
(==) NV(0): ...Defaulting to CRTCNumber 0
(II) NV(0): Using CRT on CRTC 0
(II) NV(0): Using hsync ranges from config file
(II) NV(0): Using vrefresh ranges from config file
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) NV(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) NV(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) NV(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) NV(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) NV(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) NV(0): Modeline "640x480"   35.00  640 664 728 816  480 483 487 507 -hsync +vsync
(II) NV(0): Modeline "800x600"   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync
(II) NV(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) NV(0): Modeline "1024x768"   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync
(II) NV(0): Modeline "640x480"   25.18  640 656 752 784  480 490 492 509 +hsync +vsync
(--) NV(0): VideoRAM: 262144 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): Generic Monitor: Using hsync range of 30.00-70.00 kHz
(II) NV(0): Generic Monitor: Using vrefresh range of 50.00-160.00 Hz
(II) NV(0): Estimated virtual size for aspect ratio 1.3333 is 1024x768
(II) NV(0): Clock range:  12.00 to 400.00 MHz
(II) NV(0): Not using default mode "1152x864" (width too large for virtual size)
(II) NV(0): Not using default mode "1280x960" (width too large for virtual size)
(II) NV(0): Not using default mode "1280x960" (width too large for virtual size)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) NV(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1280x768" (width too large for virtual size)
(II) NV(0): Not using default mode "1280x800" (width too large for virtual size)
(II) NV(0): Not using default mode "1152x768" (width too large for virtual size)
(II) NV(0): Not using default mode "1152x864" (width too large for virtual size)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1440x900" (width too large for virtual size)
(II) NV(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using driver mode "1280x1024" (width too large for virtual size)
(--) NV(0): Virtual size is 1024x768 (pitch 1024)
(**) NV(0): *Driver mode "1024x768": 94.5 MHz, 68.7 kHz, 84.9 Hz
(II) NV(0): Modeline "1024x768"   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync
(**) NV(0): *Driver mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) NV(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) NV(0): *Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) NV(0): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) NV(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
(**) NV(0): *Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) NV(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) NV(0): *Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) NV(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) NV(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) NV(0): *Default mode "1024x768": 44.9 MHz, 35.5 kHz, 86.9 Hz (I)
(II) NV(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync
(**) NV(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) NV(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) NV(0): *Driver mode "800x600": 56.8 MHz, 53.7 kHz, 84.9 Hz
(II) NV(0): Modeline "800x600"   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync
(**) NV(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) NV(0): *Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) NV(0): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) NV(0): Modeline "800x600"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
(**) NV(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) NV(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) NV(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) NV(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) NV(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) NV(0): *Default mode "840x525": 73.6 MHz, 65.2 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "840x525"   73.57  840 892 984 1128  525 525 527 543 doublescan
(**) NV(0): *Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "700x525"   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync
(**) NV(0): *Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x512"   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync
(**) NV(0): *Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(II) NV(0): Modeline "720x450"   54.42  720 736 940 956  450 459 463 473 doublescan +hsync +vsync
(**) NV(0): *Driver mode "640x480": 35.0 MHz, 42.9 kHz, 84.6 Hz
(II) NV(0): Modeline "640x480"   35.00  640 664 728 816  480 483 487 507 -hsync +vsync
(**) NV(0): *Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) NV(0): *Driver mode "640x480": 25.2 MHz, 32.1 kHz, 63.1 Hz
(II) NV(0): Modeline "640x480"   25.18  640 656 752 784  480 490 492 509 +hsync +vsync
(**) NV(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) NV(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) NV(0): *Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) NV(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 -hsync -vsync
(**) NV(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) NV(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) NV(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 -hsync -vsync
(**) NV(0): *Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x480"   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync
(**) NV(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) NV(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
(**) NV(0): *Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) NV(0): Modeline "720x400"   35.50  720 756 828 936  400 401 404 446 -hsync +vsync
(**) NV(0): *Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) NV(0): Modeline "640x400"   31.50  640 672 736 832  400 401 404 445 -hsync +vsync
(**) NV(0): *Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x400"   41.73  640 672 740 840  400 400 402 414 doublescan
(**) NV(0): *Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "576x432"   54.00  576 608 672 800  432 432 434 450 doublescan +hsync +vsync
(**) NV(0): *Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "640x384"   40.07  640 672 740 840  384 384 386 397 doublescan
(**) NV(0): *Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) NV(0): Modeline "640x350"   31.50  640 672 736 832  350 382 385 445 +hsync -vsync
(**) NV(0): *Default mode "576x384": 32.5 MHz, 44.2 kHz, 54.8 Hz (D)
(II) NV(0): Modeline "576x384"   32.50  576 589 657 736  384 385 388 403 doublescan +hsync +vsync
(**) NV(0): *Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(II) NV(0): Modeline "512x384"   47.25  512 536 584 688  384 384 386 404 doublescan +hsync +vsync
(**) NV(0): *Default mode "512x384": 39.4 MHz, 60.0 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "512x384"   39.38  512 520 568 656  384 384 386 400 doublescan +hsync +vsync
(**) NV(0): *Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) NV(0): Modeline "512x384"   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync
(**) NV(0): *Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "512x384"   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync
(**) NV(0): *Default mode "512x384": 22.4 MHz, 35.5 kHz, 86.6 Hz (D)
(II) NV(0): Modeline "512x384"   22.45  512 516 604 632  384 384 388 409 interlace doublescan +hsync +vsync
(**) NV(0): *Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) NV(0): Modeline "416x312"   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync
(**) NV(0): *Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "400x300"   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync
(**) NV(0): *Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) NV(0): Modeline "400x300"   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync
(**) NV(0): *Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) NV(0): Modeline "400x300"   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync
(**) NV(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) NV(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(**) NV(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) NV(0): Modeline "400x300"   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync
(**) NV(0): *Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(II) NV(0): Modeline "320x240"   18.00  320 348 376 416  240 240 242 254 doublescan -hsync -vsync
(**) NV(0): *Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "320x240"   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync
(**) NV(0): *Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(II) NV(0): Modeline "320x240"   15.75  320 332 352 416  240 244 246 260 doublescan -hsync -vsync
(**) NV(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "320x240"   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync
(**) NV(0): *Default mode "360x200": 17.8 MHz, 37.9 kHz, 85.0 Hz (D)
(II) NV(0): Modeline "360x200"   17.75  360 378 414 468  200 200 202 223 doublescan -hsync +vsync
(**) NV(0): *Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "320x200"   15.75  320 336 368 416  200 200 202 222 doublescan -hsync +vsync
(**) NV(0): *Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "320x175"   15.75  320 336 368 416  175 191 192 222 doublescan +hsync -vsync
(**) NV(0): Display dimensions: (320, 240) mm
(**) NV(0): DPI set to (81, 81)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.2.0
        ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] 0   0       0xfb000000 - 0xfbffffff (0x1000000) MX[B]
        [1] 0   0       0xe0000000 - 0xefffffff (0x10000000) MX[B]
        [2] 0   0       0xfc000000 - 0xfcffffff (0x1000000) MX[B]
        [3] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [4] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [5] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [6] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [7] -1  0       0xfe1fe000 - 0xfe1fefff (0x1000) MX[B]
        [8] -1  0       0xfe1ff000 - 0xfe1fffff (0x1000) MX[B]
        [9] -1  0       0xfe300000 - 0xfe3000ff (0x100) MX[B]
        [10] -1 0       0xfe300400 - 0xfe3005ff (0x200) MX[B]
        [11] -1 0       0x40000000 - 0x400003ff (0x400) MX[B]
        [12] -1 0       0xfe300800 - 0xfe300bff (0x400) MX[B]
        [13] -1 0       0xf0000000 - 0xefffffff (0x0) MX[B]O
        [14] -1 0       0xfd000000 - 0xfd01ffff (0x20000) MX[B](B)
        [15] -1 0       0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
        [16] -1 0       0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
        [17] -1 0       0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
        [18] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
        [19] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
        [20] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
        [21] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [22] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [23] -1 0       0x0000ec80 - 0x0000ecbf (0x40) IX[B]
        [24] -1 0       0x0000ecf0 - 0x0000ecff (0x10) IX[B]
        [25] -1 0       0x0000dc40 - 0x0000dc7f (0x40) IX[B]
        [26] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [27] -1 0       0x0000dc80 - 0x0000dc9f (0x20) IX[B]
        [28] -1 0       0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
        [29] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [30] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [31] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [32] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [33] -1 0       0x0000ff40 - 0x0000ff5f (0x20) IX[B]
        [34] -1 0       0x0000ff60 - 0x0000ff7f (0x20) IX[B]
        [35] -1 0       0x0000ff80 - 0x0000ff9f (0x20) IX[B]
        [36] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
        [37] 0  0       0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) NV(0): Write-combining range (0xe0000000,0x10000000)
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        8x8 mono pattern filled rectangles
        Indirect CPU to Screen color expansion
        Solid Lines
        Scanline Image Writes
        Offscreen Pixmaps
        Setting up tile and stipple cache:
                32 128x128 slots
                32 256x256 slots
                16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(**) Option "dpms"
(**) NV(0): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "gb"
(**) Generic Keyboard: XkbLayout: "gb"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded

Module                  Size  Used by
ipv6                  257700  8 
af_packet              21896  2 
rfcomm                 38684  2 
l2cap                  22788  11 rfcomm
bluetooth              52324  4 rfcomm,l2cap
capability              5000  0 
ppdev                   9348  0 
speedstep_lib           5380  0 
cpufreq_powersave       1792  0 
cpufreq_ondemand        8084  0 
cpufreq_stats           5508  0 
cpufreq_userspace       4116  0 
freq_table              4740  2 cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     6560  0 
button                  8080  0 
ac                      5252  0 
container               4608  0 
video                  17164  0 
sbs                    18568  0 
dock                    9476  0 
battery                10116  0 
lp                     11460  0 
loop                   17796  0 
snd_intel8x0           33564  1 
snd_ac97_codec         99492  1 snd_intel8x0
ac97_bus                2304  1 snd_ac97_codec
snd_pcm_oss            43264  0 
snd_mixer_oss          16640  1 snd_pcm_oss
snd_pcm                77320  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           3844  0 
snd_seq_oss            31872  0 
snd_seq_midi            8704  0 
snd_rawmidi            24832  1 snd_seq_midi
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
snd_seq                50416  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22916  2 snd_pcm,snd_seq
snd_seq_device          8332  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             36132  1 
parport                35656  3 ppdev,lp,parport_pc
serio_raw               7044  0 
pcspkr                  3072  0 
rtc                    13208  0 
snd                    52356  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7520  1 snd
snd_page_alloc         10504  2 snd_intel8x0,snd_pcm
psmouse                38672  0 
iTCO_wdt               10656  0 
iTCO_vendor_support     3972  1 iTCO_wdt
i2c_core               25104  0 
intel_agp              24596  1 
agpgart                33584  1 intel_agp
shpchp                 33556  0 
pci_hotplug            31288  1 shpchp
evdev                  10240  3 
ext3                  129928  1 
jbd                    53416  1 ext3
mbcache                 8324  1 ext3
sg                     36124  0 
sd_mod                 29200  3 
sr_mod                 16548  0 
cdrom                  36512  1 sr_mod
ata_piix               16644  2 
floppy                 58500  0 
e100                   36364  0 
mii                     5632  1 e100
ehci_hcd               35084  0 
ata_generic             7556  0 
libata                125040  2 ata_piix,ata_generic
scsi_mod              146828  4 sg,sd_mod,sr_mod,libata
uhci_hcd               25232  0 
usbcore               136088  3 ehci_hcd,uhci_hcd
thermal                13448  0 
processor              23984  1 thermal
fan                     4868  0 
commoncap               7424  1 capability
fuse                   44948  1

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

I hope this is the output you require. Sorry about the multiple replies. I'm such a newbie - find this quite confusing :)

---

### Post by roaldz on 2008-02-20
Comeon! That is not even half WHAT I asked, and not even provided the way I asked. This is not of any use for me. So again:
Post the output of these commands, and put them in [ CODE] [ /CODE] tags (the ¨#¨ button). This means the first [ code] tag (without spaces and capitalized) had to become before the text, and the second [ /code] tag has to become after the text (without spaces and capitalized). It will look like this:
```
blablabla, your text
```

run these commands in a terminal and post them like I said:
¨dmesg¨
¨cat /var/log/Xorg.0.log¨
¨lsmod¨
¨cat /etc/X11/Xorg.conf¨

Roald

Edit: Okay, I will look at it

---

### Post by roaldz on 2008-02-20
Open up /etc/X11/Xorg.conf as a superuser (root):

```
gksu gedit /etc/X11/Xorg.conf
```

Find this:```

Section "Device"
Identifier "Generic Video Card"
Driver "nv"
BusID "PCI:1:0:0"
EndSection
```

Change ¨nv¨ to ¨nvidia¨

Then reboot,
Then post the output of 
```
cat /var/log/Xorg.o.log 
``` and PLEASE put it between [ code][ /code] tags! (without spaces.)

---

### Post by Dabblo on 2008-02-20
```
 [    0.000000] Linux version 2.6.22-14-386 (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 Tue Feb 12 07:12:19 UTC 2008 (Ubuntu 2.6.22-14.52-386)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002ff75000 (usable)
[    0.000000]  BIOS-e820: 000000002ff75000 - 000000002ff77000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000002ff77000 - 000000002ff98000 (ACPI data)
[    0.000000]  BIOS-e820: 000000002ff98000 - 0000000030000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 767MB LOWMEM available.
[    0.000000] found SMP MP-table at 000fe710
[    0.000000] Entering add_active_range(0, 0, 196469) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   196469
[    0.000000]   HighMem    196469 ->   196469
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   196469
[    0.000000] On node 0 totalpages: 196469
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1502 pages used for memmap
[    0.000000]   Normal zone: 190871 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00FEB90 checksum 0
[    0.000000] ACPI: RSDP 000FEB90, 0014 (r0 DELL  )
[    0.000000] ACPI: RSDT 000FD4F6, 0038 (r1 DELL    4550           6 ASL        61)
[    0.000000] ACPI: FACP 000FD52E, 0074 (r1 DELL    4550           6 ASL        61)
[    0.000000] ACPI: DSDT FFFCE77E, 22D0 (r1   DELL    dt_ex     1000 MSFT  100000D)
[    0.000000] ACPI: FACS 2FF75000, 0040
[    0.000000] ACPI: SSDT FFFD0A4E, 00A7 (r1   DELL    st_ex     1000 MSFT  100000D)
[    0.000000] ACPI: APIC 000FD5A2, 006C (r1 DELL    4550           6 ASL        61)
[    0.000000] ACPI: BOOT 000FD60E, 0028 (r1 DELL    4550           6 ASL        61)
[    0.000000] ACPI: ASF! 000FD636, 0067 (r16 DELL    4550           6 ASL        61)
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 30000000:cec00000)
[    0.000000] Built 1 zonelists.  Total pages: 194935
[    0.000000] Kernel command line: root=UUID=e625ab2d-a39a-4508-8989-1bdcf9588c17 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2525.131 MHz processor.
[   21.262324] Console: colour VGA+ 80x25
[   21.263330] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   21.264336] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   21.286876] Memory: 768020k/785876k available (1929k kernel code, 17192k reserved, 876k data, 348k init, 0k highmem)
[   21.286886] virtual kernel memory layout:
[   21.286887]     fixmap  : 0xfffa8000 - 0xfffff000   ( 348 kB)
[   21.286888]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   21.286889]     vmalloc : 0xf0800000 - 0xff7fe000   ( 239 MB)
[   21.286890]     lowmem  : 0xc0000000 - 0xeff75000   ( 767 MB)
[   21.286891]       .init : 0xc03c0000 - 0xc0417000   ( 348 kB)
[   21.286892]       .data : 0xc02e2655 - 0xc03bda04   ( 876 kB)
[   21.286894]       .text : 0xc0100000 - 0xc02e2655   (1929 kB)
[   21.286897] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   21.286949] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   21.366865] Calibrating delay using timer specific routine.. 5053.70 BogoMIPS (lpj=10107400)
[   21.366888] Security Framework v1.0.0 initialized
[   21.366895] SELinux:  Disabled at boot.
[   21.366902] Mount-cache hash table entries: 512
[   21.367004] CPU: After generic identify, caps: 3febfbff 00000000 00000000 00000000 00000000 00000000 00000000
[   21.367014] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   21.367016] CPU: L2 cache: 512K
[   21.367019] CPU: After all inits, caps: 3febfbff 00000000 00000000 0000b080 00000000 00000000 00000000
[   21.367029] Compat vDSO mapped to ffffe000.
[   21.367040] CPU: Intel(R) Pentium(R) 4 CPU 2.53GHz stepping 04
[   21.367046] Checking 'hlt' instruction... OK.
[   21.383505] Early unpacking initramfs... done
[   21.706272] ACPI: Core revision 20070126
[   21.718148] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   21.741742] ENABLING IO-APIC IRQs
[   21.741915] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   21.886288] Booting paravirtualized kernel on bare hardware
[   21.886359] Time: 14:26:52  Date: 01/20/108
[   21.886384] NET: Registered protocol family 16
[   21.886480] EISA bus registered
[   21.886494] ACPI: bus type pci registered
[   21.912433] PCI: PCI BIOS revision 2.10 entry at 0xfbe6d, last bus=2
[   21.912435] PCI: Using configuration type 1
[   21.912437] Setting up standard PCI resources
[   21.913776] ACPI: EC: Look up EC in DSDT
[   21.938366] ACPI: Interpreter enabled
[   21.938370] ACPI: (supports S0 S1 S3 S4 S5)
[   21.938390] ACPI: Using IOAPIC for interrupt routing
[   21.960877] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   21.960896] PCI: Probing PCI hardware (bus 00)
[   21.961269] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[   21.961270] * this clock source is slow. If you are sure your timer does not have
[   21.961272] * this bug, please use "acpi_pm_good" to disable the workaround
[   21.961314] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[   21.961317] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[   21.961675] PCI: Firmware left 0000:02:08.0 e100 interrupts enabled, disabling
[   21.961736] PCI: Transparent bridge - 0000:00:1e.0
[   21.961762] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   21.962245] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   21.990106] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[   21.990427] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[   21.990745] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 15)
[   21.991062] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 15)
[   21.991381] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[   21.991697] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 15) *0, disabled.
[   21.992015] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 *11 12 15)
[   21.992334] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 6 7 9 10 11 12 15)
[   21.992465] Linux Plug and Play Support v0.97 (c) Adam Belay
[   21.992476] pnp: PnP ACPI init
[   21.992484] ACPI: bus type pnp registered
[   22.013765] pnp: PnP ACPI: found 12 devices
[   22.013768] ACPI: ACPI bus type pnp unregistered
[   22.013772] PnPBIOS: Disabled by ACPI PNP
[   22.013827] PCI: Using ACPI for IRQ routing
[   22.013831] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   22.020161] NET: Registered protocol family 8
[   22.020163] NET: Registered protocol family 20
[   22.020233] pnp: 00:00: iomem range 0x0-0x9ffff could not be reserved
[   22.020236] pnp: 00:00: iomem range 0x100000-0xffffff could not be reserved
[   22.020239] pnp: 00:00: iomem range 0x1000000-0x2ff74fff could not be reserved
[   22.020242] pnp: 00:00: iomem range 0xf0000-0xfffff could not be reserved
[   22.020253] pnp: 00:0b: ioport range 0x800-0x85f has been reserved
[   22.020256] pnp: 00:0b: ioport range 0xc00-0xc7f has been reserved
[   22.020258] pnp: 00:0b: ioport range 0x860-0x8ff could not be reserved
[   22.022020] Time: tsc clocksource has been installed.
[   22.050530] PCI: Bridge: 0000:00:01.0
[   22.050532]   IO window: disabled.
[   22.050537]   MEM window: fb000000-fdffffff
[   22.050541]   PREFETCH window: e0000000-efffffff
[   22.050546] PCI: Bridge: 0000:00:1e.0
[   22.050549]   IO window: e000-efff
[   22.050554]   MEM window: fe100000-fe2fffff
[   22.050557]   PREFETCH window: disabled.
[   22.050573] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   22.050585] NET: Registered protocol family 2
[   22.089957] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   22.090178] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   22.091558] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[   22.092013] TCP: Hash tables configured (established 131072 bind 65536)
[   22.092017] TCP reno registered
[   22.102122] checking if image is initramfs... it is
[   22.553334] Switched to high resolution mode on CPU 0
[   22.739062] Freeing initrd memory: 6682k freed
[   22.739227] Simple Boot Flag value 0x87 read from CMOS RAM was invalid
[   22.739230] Simple Boot Flag at 0x7a set to 0x1
[   22.739486] audit: initializing netlink socket (disabled)
[   22.739507] audit(1203517612.344:1): initialized
[   22.741570] VFS: Disk quotas dquot_6.5.1
[   22.741585] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   22.741706] io scheduler noop registered
[   22.741709] io scheduler anticipatory registered
[   22.741710] io scheduler deadline registered
[   22.741728] io scheduler cfq registered (default)
[   22.741800] Boot video device is 0000:01:00.0
[   22.741960] isapnp: Scanning for PnP cards...
[   23.095479] isapnp: No Plug & Play device found
[   23.118733] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   23.118834] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.119595] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   23.119793] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 22 (level, low) -> IRQ 16
[   23.120791] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   23.121021] input: Macintosh mouse button emulation as /class/input/input0
[   23.121112] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[   23.124730] serio: i8042 KBD port at 0x60,0x64 irq 1
[   23.124737] serio: i8042 AUX port at 0x60,0x64 irq 12
[   23.124939] mice: PS/2 mouse device common for all mice
[   23.125054] EISA: Probing bus 0 at eisa.0
[   23.125091] EISA: Detected 0 cards.
[   23.125201] TCP cubic registered
[   23.125212] NET: Registered protocol family 1
[   23.125237] Using IPI Shortcut mode
[   23.125412]   Magic number: 12:336:435
[   23.126124] Freeing unused kernel memory: 348k freed
[   23.164518] input: AT Translated Set 2 keyboard as /class/input/input1
[   24.349663] fuse init (API version 7.8)
[   24.356647] Capability LSM initialized
[   24.971251] usbcore: registered new interface driver usbfs
[   24.971279] usbcore: registered new interface driver hub
[   24.971303] usbcore: registered new device driver usb
[   24.972263] USB Universal Host Controller Interface driver v3.0
[   24.972344] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 17
[   24.972357] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   24.972361] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   24.972545] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   24.972572] uhci_hcd 0000:00:1d.0: irq 17, io base 0x0000ff80
[   24.972693] usb usb1: configuration #1 chosen from 1 choice
[   24.972721] hub 1-0:1.0: USB hub found
[   24.972728] hub 1-0:1.0: 2 ports detected
[   25.029858] SCSI subsystem initialized
[   25.036464] libata version 2.21 loaded.
[   25.074036] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 18
[   25.074050] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   25.074054] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   25.074079] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   25.074107] uhci_hcd 0000:00:1d.1: irq 18, io base 0x0000ff60
[   25.074205] usb usb2: configuration #1 chosen from 1 choice
[   25.074233] hub 2-0:1.0: USB hub found
[   25.074240] hub 2-0:1.0: 2 ports detected
[   25.122506] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
[   25.122510] e100: Copyright(c) 1999-2006 Intel Corporation
[   25.166234] Floppy drive(s): fd0 is 1.44M
[   25.177946] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 19
[   25.177959] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   25.177963] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   25.177989] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   25.178017] uhci_hcd 0000:00:1d.2: irq 19, io base 0x0000ff40
[   25.178125] usb usb3: configuration #1 chosen from 1 choice
[   25.178152] hub 3-0:1.0: USB hub found
[   25.178159] hub 3-0:1.0: 2 ports detected
[   25.210122] FDC 0 is a post-1991 82077
[   25.287173] ata_piix 0000:00:1f.1: version 2.11
[   25.287190] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   25.287197] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 19
[   25.287251] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   25.287354] scsi0 : ata_piix
[   25.287406] scsi1 : ata_piix
[   25.287433] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[   25.287436] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[   25.605409] ata1.00: ATAPI: PLEXTOR CD-R   PX-W1210A, 1.07, max MWDMA2
[   25.777161] ata1.00: configured for MWDMA2
[   25.941130] ata2.00: ATA-6: Maxtor 32049H2, YAH814Y0, max UDMA/100
[   25.941134] ata2.00: 40021632 sectors, multi 8: LBA 
[   25.957111] ata2.00: configured for UDMA/100
[   25.957904] scsi 0:0:0:0: CD-ROM            PLEXTOR  CD-R   PX-W1210A 1.07 PQ: 0 ANSI: 5
[   25.958357] scsi 1:0:0:0: Direct-Access     ATA      Maxtor 32049H2   YAH8 PQ: 0 ANSI: 5
[   25.958749] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 20
[   25.958765] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   25.958769] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   25.958928] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   25.958968] ehci_hcd 0000:00:1d.7: debug port 1
[   25.958975] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   25.958984] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfe300800
[   25.962874] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   25.963202] usb usb4: configuration #1 chosen from 1 choice
[   25.963339] hub 4-0:1.0: USB hub found
[   25.963346] hub 4-0:1.0: 6 ports detected
[   25.983578] sr0: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
[   25.983584] Uniform CD-ROM driver Revision: 3.20
[   25.983811] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   25.988708] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   25.988732] scsi 1:0:0:0: Attached scsi generic sg1 type 0
[   26.004392] sd 1:0:0:0: [sda] 40021632 512-byte hardware sectors (20491 MB)
[   26.004407] sd 1:0:0:0: [sda] Write Protect is off
[   26.004410] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   26.004425] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.004584] sd 1:0:0:0: [sda] 40021632 512-byte hardware sectors (20491 MB)
[   26.004593] sd 1:0:0:0: [sda] Write Protect is off
[   26.004595] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   26.004609] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.004625]  sda: sda1 sda2 sda3 <<6>ACPI: PCI Interrupt 0000:02:08.0[A] -> GSI 20 (level, low) -> IRQ 21
[   26.087459] e100: eth0: e100_probe: addr 0xfe1fe000, irq 21, MAC addr 00:07:E9:B8:1C:BB
[   26.088989]  sda5 >
[   26.089677] sd 1:0:0:0: [sda] Attached SCSI disk
[   26.494325] Attempting manual resume
[   26.494330] swsusp: Resume From Partition 8:5
[   26.494332] PM: Checking swsusp image.
[   26.494909] PM: Resume from disk failed.
[   26.541964] kjournald starting.  Commit interval 5 seconds
[   26.541978] EXT3-fs: mounted filesystem with ordered data mode.
[   39.405576] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   39.409265] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   39.460691] Linux agpgart interface v0.102 (c) Dave Jones
[   39.535443] agpgart: Detected an Intel 830M Chipset.
[   39.541782] agpgart: AGP aperture is 128M @ 0xf0000000
[   39.646879] intel_rng: Firmware space is locked read-only. <4>intel_rng: If you can't or
[   39.646882]  don't want to <4>intel_rng: disable this in firmware setup, and <4>intel_rng: if
[   39.646884]  you are certain that your <4>intel_rng: system has a functional
[   39.646885]  RNG, try<4>intel_rng: using the 'no_fwh_detect' option.
[   40.062047] iTCO_vendor_support: vendor-support=0
[   40.064046] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   40.064122] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0860)
[   40.064164] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   40.429948] Real Time Clock Driver v1.12ac
[   40.441824] input: PC Speaker as /class/input/input2
[   40.780464] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   40.792734] parport_pc 00:0a: reported by Plug and Play ACPI
[   40.792787] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[   40.877911] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 22
[   40.877932] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   41.248045] intel8x0_measure_ac97_clock: measured 54917 usecs
[   41.248049] intel8x0: clocking to 48000
[   41.602593] loop: module loaded
[   41.621821] lp0: using parport0 (interrupt-driven).
[   41.720084] Adding 289128k swap on /dev/sda5.  Priority:-1 extents:1 across:289128k
[   42.126771] EXT3 FS on sda2, internal journal
[   43.456498] No dock devices found.
[   43.717252] input: Power Button (FF) as /class/input/input4
[   43.722073] ACPI: Power Button (FF) [PWRF]
[   43.761302] input: Power Button (CM) as /class/input/input5
[   43.766073] ACPI: Power Button (CM) [VBTN]
[   45.587301] ppdev: user-space parallel port driver
[   45.598294] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   45.920086] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   45.920093] apm: overridden by ACPI.
[   47.736721] Capability LSM initialized
[   48.245749] Bluetooth: Core ver 2.11
[   48.245878] NET: Registered protocol family 31
[   48.245881] Bluetooth: HCI device and connection manager initialized
[   48.245884] Bluetooth: HCI socket layer initialized
[   48.257724] Bluetooth: L2CAP ver 2.8
[   48.257730] Bluetooth: L2CAP socket layer initialized
[   48.328425] Bluetooth: RFCOMM socket layer initialized
[   48.328525] Bluetooth: RFCOMM TTY layer initialized
[   48.328527] Bluetooth: RFCOMM ver 1.8
[   52.684989] NET: Registered protocol family 17
[   57.627041] NET: Registered protocol family 10
[   57.627218] lo: Disabled Privacy Extensions
[   67.959765] eth0: no IPv6 routers present


       [31] -1 0       0x0000ff60 - 0x0000ff7f (0x20) IX[B]
        [32] -1 0       0x0000ff80 - 0x0000ff9f (0x20) IX[B]
        [33] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [34] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.2
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "GeForce 7600 GS"
(II) NV(0): Creating default Display subsection in Screen section
        "Default Screen" for depth/fbbpp 24/32
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 0.1.0
        ABI class: X.Org Video Driver, version 1.2
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xE0000000
(--) NV(0): MMIO registers at 0xFC000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for analog device on output A...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for analog device on output B...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: ADI  Model: 8830  Serial#: 2404
(II) NV(0): Year: 2000  Week: 29
(II) NV(0): EDID Version: 1.1
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) NV(0): Sync:  Separate
(II) NV(0): Max H-Image Size [cm]: horiz.: 32  vert.: 24
(II) NV(0): Gamma: 2.25
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): redX: 0.625 redY: 0.340   greenX: 0.310 greenY: 0.592
(II) NV(0): blueX: 0.150 blueY: 0.063   whiteX: 0.281 whiteY: 0.311
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) NV(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) NV(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 25.2 MHz   Image Size:  0 x 0 mm
(II) NV(0): h_active: 640  h_sync: 656  h_sync_end 752 h_blank_end 784 h_border: 8
(II) NV(0): v_active: 480  v_sync: 490  v_sync_end 492 v_blanking: 509 v_border: 8
(II) NV(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 70 kHz,
(II) NV(0): Serial No: 029LB0302404
(II) NV(0): Monitor name: ADI M700
(II) NV(0): EDID (in hex):
(II) NV(0):     00ffffffffffff000489308864090000
(II) NV(0):     1d0a01016820187de80692a0574f9726
(II) NV(0):     10484f254a0031594559818061590101
(II) NV(0):     010101010101d609809020e01d101060
(II) NV(0):     a20000000008081e000000fd0032a01e
(II) NV(0):     46ff000a202020202020000000ff0030
(II) NV(0):     32394c42303330323430340a000000fc
(II) NV(0):     00414449204d3730300a20202020004b
(II) NV(0): Probing for EDID on I2C bus B...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(II) NV(0): Unable to detect which CRTCNumber...
(==) NV(0): ...Defaulting to CRTCNumber 0
(II) NV(0): Using CRT on CRTC 0
(II) NV(0): Using hsync ranges from config file
(II) NV(0): Using vrefresh ranges from config file
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) NV(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) NV(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) NV(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) NV(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) NV(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) NV(0): Modeline "640x480"   35.00  640 664 728 816  480 483 487 507 -hsync +vsync
(II) NV(0): Modeline "800x600"   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync
(II) NV(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) NV(0): Modeline "1024x768"   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync
(II) NV(0): Modeline "640x480"   25.18  640 656 752 784  480 490 492 509 +hsync +vsync
(--) NV(0): VideoRAM: 262144 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): Generic Monitor: Using hsync range of 30.00-70.00 kHz
(II) NV(0): Generic Monitor: Using vrefresh range of 50.00-160.00 Hz
(II) NV(0): Estimated virtual size for aspect ratio 1.3333 is 1024x768
(II) NV(0): Clock range:  12.00 to 400.00 MHz
(II) NV(0): Not using default mode "1152x864" (width too large for virtual size)
(II) NV(0): Not using default mode "1280x960" (width too large for virtual size)
(II) NV(0): Not using default mode "1280x960" (width too large for virtual size)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) NV(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1280x768" (width too large for virtual size)
(II) NV(0): Not using default mode "1280x800" (width too large for virtual size)
(II) NV(0): Not using default mode "1152x768" (width too large for virtual size)
(II) NV(0): Not using default mode "1152x864" (width too large for virtual size)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1440x900" (width too large for virtual size)
(II) NV(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using driver mode "1280x1024" (width too large for virtual size)
(--) NV(0): Virtual size is 1024x768 (pitch 1024)
(**) NV(0): *Driver mode "1024x768": 94.5 MHz, 68.7 kHz, 84.9 Hz
(II) NV(0): Modeline "1024x768"   94.50  1024 1096 1200 1376  768 771 775 809 -hsync +vsync
(**) NV(0): *Driver mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) NV(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) NV(0): *Driver mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) NV(0): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) NV(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
(**) NV(0): *Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) NV(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) NV(0): *Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) NV(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) NV(0): *Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) NV(0): *Default mode "1024x768": 44.9 MHz, 35.5 kHz, 86.9 Hz (I)
(II) NV(0): Modeline "1024x768"   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync
(**) NV(0): *Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) NV(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) NV(0): *Driver mode "800x600": 56.8 MHz, 53.7 kHz, 84.9 Hz
(II) NV(0): Modeline "800x600"   56.75  800 848 928 1056  600 603 607 633 -hsync +vsync
(**) NV(0): *Driver mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) NV(0): *Driver mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) NV(0): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) NV(0): Modeline "800x600"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
(**) NV(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) NV(0): *Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) NV(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) NV(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) NV(0): *Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) NV(0): *Default mode "840x525": 73.6 MHz, 65.2 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "840x525"   73.57  840 892 984 1128  525 525 527 543 doublescan
(**) NV(0): *Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "700x525"   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync
(**) NV(0): *Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x512"   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync
(**) NV(0): *Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(II) NV(0): Modeline "720x450"   54.42  720 736 940 956  450 459 463 473 doublescan +hsync +vsync
(**) NV(0): *Driver mode "640x480": 35.0 MHz, 42.9 kHz, 84.6 Hz
(II) NV(0): Modeline "640x480"   35.00  640 664 728 816  480 483 487 507 -hsync +vsync
(**) NV(0): *Driver mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) NV(0): *Driver mode "640x480": 25.2 MHz, 32.1 kHz, 63.1 Hz
(II) NV(0): Modeline "640x480"   25.18  640 656 752 784  480 490 492 509 +hsync +vsync
(**) NV(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) NV(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) NV(0): *Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) NV(0): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 -hsync -vsync
(**) NV(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) NV(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) NV(0): Modeline "640x480"   31.50  640 664 704 832  480 489 492 520 -hsync -vsync
(**) NV(0): *Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x480"   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync
(**) NV(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) NV(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
(**) NV(0): *Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(II) NV(0): Modeline "720x400"   35.50  720 756 828 936  400 401 404 446 -hsync +vsync
(**) NV(0): *Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) NV(0): Modeline "640x400"   31.50  640 672 736 832  400 401 404 445 -hsync +vsync
(**) NV(0): *Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x400"   41.73  640 672 740 840  400 400 402 414 doublescan
(**) NV(0): *Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "576x432"   54.00  576 608 672 800  432 432 434 450 doublescan +hsync +vsync
(**) NV(0): *Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "640x384"   40.07  640 672 740 840  384 384 386 397 doublescan
(**) NV(0): *Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(II) NV(0): Modeline "640x350"   31.50  640 672 736 832  350 382 385 445 +hsync -vsync
(**) NV(0): *Default mode "576x384": 32.5 MHz, 44.2 kHz, 54.8 Hz (D)
(II) NV(0): Modeline "576x384"   32.50  576 589 657 736  384 385 388 403 doublescan +hsync +vsync
(**) NV(0): *Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(II) NV(0): Modeline "512x384"   47.25  512 536 584 688  384 384 386 404 doublescan +hsync +vsync
(**) NV(0): *Default mode "512x384": 39.4 MHz, 60.0 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "512x384"   39.38  512 520 568 656  384 384 386 400 doublescan +hsync +vsync
(**) NV(0): *Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(II) NV(0): Modeline "512x384"   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync
(**) NV(0): *Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "512x384"   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync
(**) NV(0): *Default mode "512x384": 22.4 MHz, 35.5 kHz, 86.6 Hz (D)
(II) NV(0): Modeline "512x384"   22.45  512 516 604 632  384 384 388 409 interlace doublescan +hsync +vsync
(**) NV(0): *Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(II) NV(0): Modeline "416x312"   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync
(**) NV(0): *Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "400x300"   28.15  400 416 448 524  300 300 302 315 doublescan +hsync +vsync
(**) NV(0): *Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(II) NV(0): Modeline "400x300"   24.75  400 408 448 528  300 300 302 312 doublescan +hsync +vsync
(**) NV(0): *Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(II) NV(0): Modeline "400x300"   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync
(**) NV(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) NV(0): Modeline "400x300"   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync
(**) NV(0): *Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(II) NV(0): Modeline "400x300"   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync
(**) NV(0): *Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(II) NV(0): Modeline "320x240"   18.00  320 348 376 416  240 240 242 254 doublescan -hsync -vsync
(**) NV(0): *Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "320x240"   15.75  320 328 360 420  240 240 242 250 doublescan -hsync -vsync
(**) NV(0): *Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(II) NV(0): Modeline "320x240"   15.75  320 332 352 416  240 244 246 260 doublescan -hsync -vsync
(**) NV(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "320x240"   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync
(**) NV(0): *Default mode "360x200": 17.8 MHz, 37.9 kHz, 85.0 Hz (D)
(II) NV(0): Modeline "360x200"   17.75  360 378 414 468  200 200 202 223 doublescan -hsync +vsync
(**) NV(0): *Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "320x200"   15.75  320 336 368 416  200 200 202 222 doublescan -hsync +vsync
(**) NV(0): *Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NV(0): Modeline "320x175"   15.75  320 336 368 416  175 191 192 222 doublescan +hsync -vsync
(**) NV(0): Display dimensions: (320, 240) mm
(**) NV(0): DPI set to (81, 81)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.2.0
        ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] 0   0       0xfb000000 - 0xfbffffff (0x1000000) MX[B]
        [1] 0   0       0xe0000000 - 0xefffffff (0x10000000) MX[B]
        [2] 0   0       0xfc000000 - 0xfcffffff (0x1000000) MX[B]
        [3] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [4] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [5] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [6] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [7] -1  0       0xfe1fe000 - 0xfe1fefff (0x1000) MX[B]
        [8] -1  0       0xfe1ff000 - 0xfe1fffff (0x1000) MX[B]
        [9] -1  0       0xfe300000 - 0xfe3000ff (0x100) MX[B]
        [10] -1 0       0xfe300400 - 0xfe3005ff (0x200) MX[B]
        [11] -1 0       0x40000000 - 0x400003ff (0x400) MX[B]
        [12] -1 0       0xfe300800 - 0xfe300bff (0x400) MX[B]
        [13] -1 0       0xf0000000 - 0xefffffff (0x0) MX[B]O
        [14] -1 0       0xfd000000 - 0xfd01ffff (0x20000) MX[B](B)
        [15] -1 0       0xfb000000 - 0xfbffffff (0x1000000) MX[B](B)
        [16] -1 0       0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
        [17] -1 0       0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
        [18] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
        [19] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
        [20] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
        [21] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [22] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [23] -1 0       0x0000ec80 - 0x0000ecbf (0x40) IX[B]
        [24] -1 0       0x0000ecf0 - 0x0000ecff (0x10) IX[B]
        [25] -1 0       0x0000dc40 - 0x0000dc7f (0x40) IX[B]
        [26] -1 0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [27] -1 0       0x0000dc80 - 0x0000dc9f (0x20) IX[B]
        [28] -1 0       0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
        [29] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [30] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [31] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [32] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
EndSection

        [33] -1 0       0x0000ff40 - 0x0000ff5f (0x20) IX[B]
        [34] -1 0       0x0000ff60 - 0x0000ff7f (0x20) IX[B]
        [35] -1 0       0x0000ff80 - 0x0000ff9f (0x20) IX[B]
        [36] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
        [37] 0  0       0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) NV(0): Write-combining range (0xe0000000,0x10000000)
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        8x8 mono pattern filled rectangles
        Indirect CPU to Screen color expansion
        Solid Lines
        Scanline Image Writes
        Offscreen Pixmaps
        Setting up tile and stipple cache:
                32 128x128 slots
                32 256x256 slots
                16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(**) Option "dpms"
(**) NV(0): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "gb"
(**) Generic Keyboard: XkbLayout: "gb"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
 

Module                  Size  Used by
ipv6                  257700  8 
af_packet              21896  2 
rfcomm                 38684  2 
l2cap                  22788  11 rfcomm
bluetooth              52324  4 rfcomm,l2cap
capability              5000  0 
ppdev                   9348  0 
speedstep_lib           5380  0 
cpufreq_powersave       1792  0 
cpufreq_ondemand        8084  0 
cpufreq_stats           5508  0 
cpufreq_userspace       4116  0 
freq_table              4740  2 cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     6560  0 
button                  8080  0 
ac                      5252  0 
container               4608  0 
video                  17164  0 
sbs                    18568  0 
dock                    9476  0 
battery                10116  0 
lp                     11460  0 
loop                   17796  0 
snd_intel8x0           33564  1 
snd_ac97_codec         99492  1 snd_intel8x0
ac97_bus                2304  1 snd_ac97_codec
snd_pcm_oss            43264  0 
snd_mixer_oss          16640  1 snd_pcm_oss
snd_pcm                77320  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           3844  0 
snd_seq_oss            31872  0 
snd_seq_midi            8704  0 
snd_rawmidi            24832  1 snd_seq_midi
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
snd_seq                50416  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22916  2 snd_pcm,snd_seq
snd_seq_device          8332  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
parport_pc             36132  1 
parport                35656  3 ppdev,lp,parport_pc
serio_raw               7044  0 
pcspkr                  3072  0 
rtc                    13208  0 
snd                    52356  12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7520  1 snd
snd_page_alloc         10504  2 snd_intel8x0,snd_pcm
psmouse                38672  0 
iTCO_wdt               10656  0 
iTCO_vendor_support     3972  1 iTCO_wdt
i2c_core               25104  0 
intel_agp              24596  1 
agpgart                33584  1 intel_agp
shpchp                 33556  0 
pci_hotplug            31288  1 shpchp
evdev                  10240  3 
ext3                  129928  1 
jbd                    53416  1 ext3
mbcache                 8324  1 ext3
sg                     36124  0 
sd_mod                 29200  3 
sr_mod                 16548  0 
cdrom                  36512  1 sr_mod
ata_piix               16644  2 
floppy                 58500  0 
e100                   36364  0 
mii                     5632  1 e100
ehci_hcd               35084  0 
ata_generic             7556  0 
libata                125040  2 ata_piix,ata_generic
scsi_mod              146828  4 sg,sd_mod,sr_mod,libata
uhci_hcd               25232  0 
usbcore               136088  3 ehci_hcd,uhci_hcd
thermal                13448  0 
processor              23984  1 thermal
fan                     4868  0 
commoncap               7424  1 capability
fuse                   44948  1 

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
EndSection
 
```

---

### Post by Dabblo on 2008-02-20
Hey that and a instaling drivers over has fixed it unexpectedly, I now have all desktop effects working thanks.

Regards Dai

---

### Post by roaldz on 2008-02-21
> **Dabblo said:**
> Hey that and a instaling drivers over has fixed it unexpectedly, I now have all desktop effects working thanks.

Regards Dai

You´re welcome

---

### Post by shadowfirebird on 2008-03-09
.

---

### Post by ftmichael on 2008-03-15
I'm having this same problem, and from searching the forums, it seems that a lot of other people are, too.  I bought my new motherboard (with onboard graphics) because several people told me that nVidia is excellent with Ubuntu, but this whole experience has seriously soured me on nVidia.  My motherboard is an [nforce 630i from XFX](http://www.newegg.com/Product/Product.aspx?Item=N82E16813141008), and the onboard graphics card is an **nVidia geforce 7100**.  I have **nvidia-glx-new** installed, after nvidia-glx didn't work - switching to nvidia-glx-new hasn't changed a thing, but it's what's still installed.

As seems to be the case with so many folks, X keeps starting in low graphics mode.  It informs me that it couldn't properly detect my graphics card or screen, and gives me the option of manually configuring them.  I do so, telling it to use the nvidia driver and that my monitor is 1024x768, and I click OK; it immediately decides to ignore what I've just told it and boots into 800x600, which it had started to do anyway.  Going to System->Preferences->Screen Resolution shows me that it won't allow me to choose any resolution above 800x600; going to System->Administration->Screens and Graphics shows me that it's back using the vesa driver (which is the default in low graphics mode) and thinks I'm using a Plug n' Play monitor that only supports 800x600 resolution.

I have run **dpkg-configure xserver-xorg** more times than I can count and am sure everything is as it should be; no joy.

My xorg.conf (remember I was in low graphics mode when I ran this - I don't know if that makes a difference):
```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "Files"
EndSection

Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc101"
	Option		"XkbLayout"	"uk"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"vesa"
	Busid		"PCI:0:16:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Generic CRT Display"
	Modelname	"Monitor 1024x768"
	Horizsync	31.5-61.0
	Vertrefresh	50-75
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	960
		Modes		"1024x768@75"	"1024x768@70"	"832x624@75"	"1024x768@60"	"800x600@60"	"1280x960@60"	"800x600@75"	"800x600@72"	"800x600@56"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection
Section "ServerFlags"
EndSection
```


My Xorg.0.log (remember I was in low graphics mode when I ran this - I don't know if that makes a difference):
```
X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux jeezychreezy 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686
Build Date: 18 January 2008
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Mar 15 14:20:46 2008
(==) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Failsafe Monitor"
(**) |   |-->Device "Failsafe Device"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81e9800
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 9

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,07c1 card 10de,cb73 rev a2 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,07cb card 10de,cb73 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:01:0: chip 10de,07cd card 10de,cb73 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:1: chip 10de,07ce card 10de,cb73 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:2: chip 10de,07cf card 10de,cb73 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:3: chip 10de,07d0 card 10de,cb73 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:4: chip 10de,07d1 card 10de,cb73 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:5: chip 10de,07d2 card 10de,cb73 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:6: chip 10de,07d3 card 10de,cb73 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:02:0: chip 10de,07d6 card 10de,cb73 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:03:0: chip 10de,07d7 card 10de,cb73 rev a2 class 06,01,00 hdr 80
(II) PCI: 00:03:1: chip 10de,07d8 card 10de,cb73 rev a1 class 0c,05,00 hdr 80
(II) PCI: 00:03:2: chip 10de,07d9 card 10de,cb73 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:03:3: chip 10de,07da card 10de,cb73 rev a2 class 0b,40,00 hdr 80
(II) PCI: 00:03:4: chip 10de,07c8 card 10de,cb73 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:04:0: chip 10de,07fe card 10de,cb73 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:04:1: chip 10de,056a card 10de,cb73 rev a1 class 0c,03,20 hdr 80
(II) PCI: 00:08:0: chip 10de,056c card 10de,cb73 rev a1 class 01,01,8a hdr 00
(II) PCI: 00:09:0: chip 10de,07fc card 10de,07fc rev a1 class 04,03,00 hdr 00
(II) PCI: 00:0a:0: chip 10de,056d card 0000,0000 rev a1 class 06,04,01 hdr 01
(II) PCI: 00:0b:0: chip 10de,056e card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:0c:0: chip 10de,056f card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 10de,056f card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,07f0 card 10de,cb73 rev a2 class 01,01,85 hdr 00
(II) PCI: 00:10:0: chip 10de,07e1 card 10de,cb73 rev a2 class 03,00,00 hdr 00
(II) PCI: 03:00:0: chip 11ab,4364 card 11ab,00ba rev 14 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:3:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:10:0), (0,1,1), BCTRL: 0x0200 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000b000 - 0x0000bfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xef800000 - 0xef8fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xef700000 - 0xef7fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:11:0), (0,2,2), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xefe00000 - 0xefefffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xefd00000 - 0xefdfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:12:0), (0,3,3), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xefc00000 - 0xefcfffff (0x100000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0xefb00000 - 0xefbfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:13:0), (0,4,4), BCTRL: 0x0000 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xefa00000 - 0xefafffff (0x100000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xef900000 - 0xef9fffff (0x100000) MX[B]
(--) PCI:*(0:16:0) nVidia Corporation unknown chipset (0x07e1) rev 162, Mem @ 0xed000000/24, 0xd0000000/28, 0xee000000/24
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xefcfc000 - 0xefcfffff (0x4000) MX[B]
	[1] -1	0	0xefffc000 - 0xefffdfff (0x2000) MX[B]
	[2] -1	0	0xefff8000 - 0xefffbfff (0x4000) MX[B]
	[3] -1	0	0xefffe000 - 0xefffe0ff (0x100) MX[B]
	[4] -1	0	0xeffff000 - 0xefffffff (0x1000) MX[B]
	[5] -1	0	0xee000000 - 0xeeffffff (0x1000000) MX[B](B)
	[6] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[7] -1	0	0xed000000 - 0xedffffff (0x1000000) MX[B](B)
	[8] -1	0	0xeff00000 - 0xeff7ffff (0x80000) MX[B]
	[9] -1	0	0x0000df00 - 0x0000dfff (0x100) IX[B]
	[10] -1	0	0x0000f700 - 0x0000f70f (0x10) IX[B]
	[11] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[12] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[13] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[14] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[15] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[16] -1	0	0x00001c80 - 0x00001cbf (0x40) IX[B]
	[17] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[18] -1	0	0x0000ff00 - 0x0000ff3f (0x40) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xefcfc000 - 0xefcfffff (0x4000) MX[B]
	[1] -1	0	0xefffc000 - 0xefffdfff (0x2000) MX[B]
	[2] -1	0	0xefff8000 - 0xefffbfff (0x4000) MX[B]
	[3] -1	0	0xefffe000 - 0xefffe0ff (0x100) MX[B]
	[4] -1	0	0xeffff000 - 0xefffffff (0x1000) MX[B]
	[5] -1	0	0xee000000 - 0xeeffffff (0x1000000) MX[B](B)
	[6] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[7] -1	0	0xed000000 - 0xedffffff (0x1000000) MX[B](B)
	[8] -1	0	0xeff00000 - 0xeff7ffff (0x80000) MX[B]
	[9] -1	0	0x0000df00 - 0x0000dfff (0x100) IX[B]
	[10] -1	0	0x0000f700 - 0x0000f70f (0x10) IX[B]
	[11] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[12] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[13] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[14] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[15] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[16] -1	0	0x00001c80 - 0x00001cbf (0x40) IX[B]
	[17] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[18] -1	0	0x0000ff00 - 0x0000ff3f (0x40) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xefcfc000 - 0xefcfffff (0x4000) MX[B]
	[5] -1	0	0xefffc000 - 0xefffdfff (0x2000) MX[B]
	[6] -1	0	0xefff8000 - 0xefffbfff (0x4000) MX[B]
	[7] -1	0	0xefffe000 - 0xefffe0ff (0x100) MX[B]
	[8] -1	0	0xeffff000 - 0xefffffff (0x1000) MX[B]
	[9] -1	0	0xee000000 - 0xeeffffff (0x1000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xed000000 - 0xedffffff (0x1000000) MX[B](B)
	[12] -1	0	0xeff00000 - 0xeff7ffff (0x80000) MX[B]
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000df00 - 0x0000dfff (0x100) IX[B]
	[16] -1	0	0x0000f700 - 0x0000f70f (0x10) IX[B]
	[17] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[18] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[19] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[20] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[21] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[22] -1	0	0x00001c80 - 0x00001cbf (0x40) IX[B]
	[23] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[24] -1	0	0x0000ff00 - 0x0000ff3f (0x40) IX[B]
(WW) "dbe" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "dri" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "glx" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "vbe" will not be loaded unless you've specified it to be loaded elsewhere.
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 00:10:0
(--) Chipset vesa found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xefcfc000 - 0xefcfffff (0x4000) MX[B]
	[5] -1	0	0xefffc000 - 0xefffdfff (0x2000) MX[B]
	[6] -1	0	0xefff8000 - 0xefffbfff (0x4000) MX[B]
	[7] -1	0	0xefffe000 - 0xefffe0ff (0x100) MX[B]
	[8] -1	0	0xeffff000 - 0xefffffff (0x1000) MX[B]
	[9] -1	0	0xee000000 - 0xeeffffff (0x1000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xed000000 - 0xedffffff (0x1000000) MX[B](B)
	[12] -1	0	0xeff00000 - 0xeff7ffff (0x80000) MX[B]
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000df00 - 0x0000dfff (0x100) IX[B]
	[16] -1	0	0x0000f700 - 0x0000f70f (0x10) IX[B]
	[17] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[18] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[19] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[20] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[21] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[22] -1	0	0x00001c80 - 0x00001cbf (0x40) IX[B]
	[23] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[24] -1	0	0x0000ff00 - 0x0000ff3f (0x40) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xefcfc000 - 0xefcfffff (0x4000) MX[B]
	[5] -1	0	0xefffc000 - 0xefffdfff (0x2000) MX[B]
	[6] -1	0	0xefff8000 - 0xefffbfff (0x4000) MX[B]
	[7] -1	0	0xefffe000 - 0xefffe0ff (0x100) MX[B]
	[8] -1	0	0xeffff000 - 0xefffffff (0x1000) MX[B]
	[9] -1	0	0xee000000 - 0xeeffffff (0x1000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xed000000 - 0xedffffff (0x1000000) MX[B](B)
	[12] -1	0	0xeff00000 - 0xeff7ffff (0x80000) MX[B]
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000df00 - 0x0000dfff (0x100) IX[B]
	[19] -1	0	0x0000f700 - 0x0000f70f (0x10) IX[B]
	[20] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[21] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[22] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[23] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[24] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[25] -1	0	0x00001c80 - 0x00001cbf (0x40) IX[B]
	[26] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[27] -1	0	0x0000ff00 - 0x0000ff3f (0x40) IX[B]
	[28] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[29] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 65536 kB
(II) VESA(0): VESA VBE OEM: NVIDIA
(II) VESA(0): VESA VBE OEM Software Rev: 5.115
(II) VESA(0): VESA VBE OEM Vendor: Build    071004.1


(II) VESA(0): VESA VBE OEM Product: MCP73 - mcp73-80
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
(**) VESA(0): Depth 16, (--) framebuffer bpp 16
(==) VESA(0): RGB weight 565
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level none
(II) VESA(0): VESA VBE DDC transfer in appr. 0 sec.
(II) VESA(0): VESA VBE DDC read failed
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 100 (640x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009cc9
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 101 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009cc9
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 10
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 10
	LinNumberOfImagePages: 10
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 102 (800x600)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009cc9
	BytesPerScanline: 100
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 100
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 103 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009cc9
	BytesPerScanline: 800
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 800
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 104 (1024x768)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009cc9
	BytesPerScanline: 128
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 128
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 105 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009cc9
	BytesPerScanline: 1024
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 106 (1280x1024)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009cc9
	BytesPerScanline: 160
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 160
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 107 (1280x1024)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009cc9
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 10e (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009cc9
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 30
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 10f (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009cc9
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
*Mode: 111 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009cc9
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 112 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009cc9
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
*Mode: 114 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009cc9
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 115 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009cc9
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
*Mode: 117 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009cc9
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 118 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009cc9
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
*Mode: 11a (1280x1024)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009cc9
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 11b (1280x1024)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009cc9
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 130 (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009cc9
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 62
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 62
	LinNumberOfImagePages: 62
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 131 (320x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009cc9
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 30
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 132 (320x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009cc9
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 133 (320x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009cc9
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 134 (320x240)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009cc9
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 30
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 135 (320x240)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009cc9
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 19
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 19
	LinNumberOfImagePages: 19
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 136 (320x240)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009cc9
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 10
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 10
	LinNumberOfImagePages: 10
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
*Mode: 13d (640x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009cc9
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 13e (640x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009cc9
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 145 (1600x1200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009cc9
	BytesPerScanline: 1600
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 146 (1600x1200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009cc9
	BytesPerScanline: 3200
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 147 (1400x1050)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009cc9
	BytesPerScanline: 1400
	XResolution: 1400
	YResolution: 1050
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 1400
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 148 (1400x1050)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009cc9
	BytesPerScanline: 2800
	XResolution: 1400
	YResolution: 1050
	XCharSize: 8
	YCharSize: 14
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 2800
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 152 (2048x1536)
	ModeAttributes: 0x3db
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0009cc9
	BytesPerScanline: 8192
	XResolution: 2048
	YResolution: 1536
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd0000000
	LinBytesPerScanLine: 8192
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000

(II) VESA(0): Total Memory: 1024 64KB banks (65536kB)
(II) VESA(0): Failsafe Monitor: Using default hsync range of 31.50-37.90 kHz
(II) VESA(0): Failsafe Monitor: Using default vrefresh range of 50.00-70.00 Hz
(II) VESA(0): Not using built-in mode "1600x1200" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "1400x1050" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "1280x1024" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "1024x768" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "640x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x240" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x200" (hsync out of range)
(--) VESA(0): Virtual size is 800x600 (pitch 800)
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0):  Built-in mode "640x480"
(==) VESA(0): DPI set to (100, 100)
(II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (114)
(II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (111)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xefcfc000 - 0xefcfffff (0x4000) MX[B]
	[5] -1	0	0xefffc000 - 0xefffdfff (0x2000) MX[B]
	[6] -1	0	0xefff8000 - 0xefffbfff (0x4000) MX[B]
	[7] -1	0	0xefffe000 - 0xefffe0ff (0x100) MX[B]
	[8] -1	0	0xeffff000 - 0xefffffff (0x1000) MX[B]
	[9] -1	0	0xee000000 - 0xeeffffff (0x1000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xed000000 - 0xedffffff (0x1000000) MX[B](B)
	[12] -1	0	0xeff00000 - 0xeff7ffff (0x80000) MX[B]
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000df00 - 0x0000dfff (0x100) IX[B]
	[19] -1	0	0x0000f700 - 0x0000f70f (0x10) IX[B]
	[20] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[21] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[22] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[23] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[24] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[25] -1	0	0x00001c80 - 0x00001cbf (0x40) IX[B]
	[26] -1	0	0x00001c00 - 0x00001c3f (0x40) IX[B]
	[27] -1	0	0x0000ff00 - 0x0000ff3f (0x40) IX[B]
	[28] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[29] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 65536 kB
(II) VESA(0): VESA VBE OEM: NVIDIA
(II) VESA(0): VESA VBE OEM Software Rev: 5.115
(II) VESA(0): VESA VBE OEM Vendor: Build    071004.1


(II) VESA(0): VESA VBE OEM Product: MCP73 - mcp73-80
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
(==) VESA(0): Write-combining range (0xd0000000,0x4000000)
(II) VESA(0): virtual address = 0xb3af6000,
	physical address = 0xd0000000, size = 67108864
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(**) Option "dpms"
(**) VESA(0): DPMS enabled
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc101"
(**) Generic Keyboard: XkbModel: "pc101"
(**) Option "XkbLayout" "uk"
(**) Generic Keyboard: XkbLayout: "uk"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetClientVersion: 0 9
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
```


My results from **lsmod** (remember I was in low graphics mode when I ran this - I don't know if that makes a difference):
```
Module                  Size  Used by
af_packet              24840  2 
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
nfsd                  220912  13 
exportfs                7040  1 nfsd
lockd                  67592  2 nfsd
sunrpc                172412  8 nfsd,lockd
ppdev                  10244  0 
ipv6                  273892  22 
cpufreq_conservative     8072  0 
cpufreq_stats           7232  0 
cpufreq_userspace       5280  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
video                  18060  0 
container               5504  0 
ac                      6148  0 
sbs                    19592  0 
dock                   10656  0 
button                  8976  0 
battery                11012  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
gspca                 608336  0 
sg                     36764  0 
nvidia               6221648  0 
videodev               29312  1 gspca
v4l2_common            18432  1 videodev
v4l1_compat            15364  1 videodev
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sky2                   46852  0 
agpgart                35016  1 nvidia
serio_raw               8068  0 
i2c_core               26112  1 nvidia
pcspkr                  4224  0 
psmouse                39952  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
evdev                  11136  3 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
ide_disk               18560  3 
ahci                   23300  0 
ata_generic             8452  0 
libata                125168  2 ahci,ata_generic
scsi_mod              147084  3 sg,sr_mod,libata
ohci_hcd               22916  0 
amd74xx                15260  0 [permanent]
ide_core              116804  2 ide_disk,amd74xx
ehci_hcd               36492  0 
usbcore               138632  4 gspca,ohci_hcd,ehci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor
```

I tried running **dmesg** and it scrolled so far that I couldn't see the beginning anymore.  Should I post just as much as is left in my terminal?

Also, my sound isn't working either.  Is that a function of low graphics mode for some reason, or am I going to have to troubleshoot that separately?  At the moment I'm more concerned with sorting out the graphics, but the missing sound is an annoyance as well.  Going to System->Preferences->Sound, selecting the Devices tab, and clicking any of the Test buttons gets me this error message:

audiotestsrc wave=sine freq=512 !
audioconvert ! audioresample !
gconfaudiosink: Could not open source for writing.


**ETA:** I tried Envy, and it told me that my video card is not compatible with any version of the driver. wtf?

**ETA2:** I found the appropriate driver version on nVidia's website and used Envy to manually install it. I've rebooted and all seems well now! Now to deal with the sound issue. Any help on that?

Michael

---

### Post by sabhain on 2008-03-31
Hello,

I'm running into similar issues for an integrated nvidia card.  It's a 7100 on an MSI motherboard (P6-NGM).  It appears you may know what to look for .. so I thought I'd reply to exactly what you asked the other user for ..

FYI, I have been able to get the nvidia open source drivers to work, but they don't play perfectly well with mythtv, so I'm making a go at trying to get the proprietary drivers to load correctly.  I've done a complete scrub and have only been configuring / reconfiguring based on the proprietary package (nvidia-glx-new).

Here's the dmesg output:
```
[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000006ff90000 (usable)
[    0.000000]  BIOS-e820: 000000006ff90000 - 000000006ff9e000 (ACPI data)
[    0.000000]  BIOS-e820: 000000006ff9e000 - 000000006ffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000006ffe0000 - 000000006ffee000 (reserved)
[    0.000000]  BIOS-e820: 000000006fff0000 - 0000000070000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 895MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 458640) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   458640
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   458640
[    0.000000] On node 0 totalpages: 458640
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1791 pages used for memmap
[    0.000000]   HighMem zone: 227473 pages, LIFO batch:31
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F9960 checksum 0
[    0.000000] ACPI: RSDP 000F9960, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 6FF90000, 0040 (r1 102507 RSDT1721 20071025 MSFT       97)
[    0.000000] ACPI: FACP 6FF90200, 0084 (r1 102507 FACP1721 20071025 MSFT       97)
[    0.000000] ACPI: DSDT 6FF904A0, 56C6 (r1  1ADSY 1ADSY002        2 INTL 20051117)
[    0.000000] ACPI: FACS 6FF9E000, 0040
[    0.000000] ACPI: APIC 6FF90390, 0080 (r1 102507 APIC1721 20071025 MSFT       97)
[    0.000000] ACPI: MCFG 6FF90410, 003C (r1 102507 OEMMCFG  20071025 MSFT       97)
[    0.000000] ACPI: WDRT 6FF90450, 0047 (r1 102507 NV-WDRT  20071025 MSFT       97)
[    0.000000] ACPI: OEMB 6FF9E040, 0071 (r1 102507 OEMB1721 20071025 MSFT       97)
[    0.000000] ACPI: NVHD 6FF9E0C0, 0554 (r1 102507  NVHDCP  20071025 MSFT       97)
[    0.000000] ACPI: SSDT 6FF9EF40, 0A7C (r1 DpgPmm    CpuPm       12 INTL 20051117)
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:15 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 70000000:8ec00000)
[    0.000000] Built 1 zonelists.  Total pages: 455057
[    0.000000] Kernel command line: root=UUID=1b5eb33b-d09d-4955-a313-f6c5293acd90 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1800.028 MHz processor.
[   14.289567] spurious 8259A interrupt: IRQ7.
[   14.292277] Console: colour VGA+ 80x25
[   14.292642] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   14.292953] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   14.362793] Memory: 1807124k/1834560k available (2015k kernel code, 26112k reserved, 915k data, 364k init, 917056k highmem)
[   14.362801] virtual kernel memory layout:
[   14.362802]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   14.362803]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   14.362804]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   14.362805]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   14.362807]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   14.362808]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[   14.362809]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[   14.362811] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   14.362846] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   14.442750] Calibrating delay using timer specific routine.. 3604.06 BogoMIPS (lpj=7208127)
[   14.442775] Security Framework v1.0.0 initialized
[   14.442780] SELinux:  Disabled at boot.
[   14.442793] Mount-cache hash table entries: 512
[   14.442909] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e39d 00000000 00000001
[   14.442916] monitor/mwait feature present.
[   14.442918] using mwait in idle threads.
[   14.442922] CPU: L1 I cache: 32K, L1 D cache: 32K
[   14.442924] CPU: L2 cache: 1024K
[   14.442926] CPU: Physical Processor ID: 0
[   14.442928] CPU: Processor Core ID: 0
[   14.442930] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e39d 00000000 00000001
[   14.442940] Compat vDSO mapped to ffffe000.
[   14.442951] Checking 'hlt' instruction... OK.
[   14.458850] SMP alternatives: switching to UP code
[   14.459245] Early unpacking initramfs... done
[   14.761870] ACPI: Core revision 20070126
[   14.761912] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   14.764732] CPU0: Intel(R) Pentium(R) Dual  CPU  E2160  @ 1.80GHz stepping 0d
[   14.764746] SMP alternatives: switching to SMP code
[   14.764821] Booting processor 1/1 eip 3000
[   14.774882] Initializing CPU#1
[   14.854116] Calibrating delay using timer specific routine.. 3600.16 BogoMIPS (lpj=7200339)
[   14.854122] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e39d 00000000 00000001
[   14.854127] monitor/mwait feature present.
[   14.854129] CPU: L1 I cache: 32K, L1 D cache: 32K
[   14.854131] CPU: L2 cache: 1024K
[   14.854133] CPU: Physical Processor ID: 0
[   14.854134] CPU: Processor Core ID: 1
[   14.854136] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e39d 00000000 00000001
[   14.854521] CPU1: Intel(R) Pentium(R) Dual  CPU  E2160  @ 1.80GHz stepping 0d
[   14.854541] Total of 2 processors activated (7204.23 BogoMIPS).
[   14.854737] ENABLING IO-APIC IRQs
[   14.854937] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   15.001979] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   15.021961] Brought up 2 CPUs
[   15.042391] migration_cost=16
[   15.042498] Booting paravirtualized kernel on bare hardware
[   15.042564] Time:  4:02:10  Date: 02/31/108
[   15.042580] NET: Registered protocol family 16
[   15.042652] EISA bus registered
[   15.042656] ACPI: bus type pci registered
[   15.042812] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[   15.042813] PCI: Using configuration type 1
[   15.042815] Setting up standard PCI resources
[   15.049526] ACPI: EC: Look up EC in DSDT
[   15.054597] ACPI: Interpreter enabled
[   15.054600] ACPI: (supports S0 S1 S3 S4 S5)
[   15.054617] ACPI: Using IOAPIC for interrupt routing
[   15.054780] Error attaching device data
[   15.054817] Error attaching device data
[   15.054855] Error attaching device data
[   15.054891] Error attaching device data
[   15.062915] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   15.062921] PCI: Probing PCI hardware (bus 00)
[   15.064580] PCI: Transparent bridge - 0000:00:0a.0
[   15.065079] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   15.065292] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   15.065430] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR10._PRT]
[   15.065528] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR11._PRT]
[   15.065626] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR12._PRT]
[   15.076400] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *11
[   15.076635] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *10
[   15.076866] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[   15.077096] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[   15.077325] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *0, disabled.
[   15.077553] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
[   15.077782] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
[   15.078048] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
[   15.078281] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *10
[   15.078513] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *11
[   15.078744] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *7
[   15.078976] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *7
[   15.079208] ACPI: PCI Interrupt Link [SGRU] (IRQs 20 21 22 23) *10
[   15.079471] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
[   15.079717] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *7
[   15.079951] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *5
[   15.080224] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[   15.080328] Linux Plug and Play Support v0.97 (c) Adam Belay
[   15.080337] pnp: PnP ACPI init
[   15.080345] ACPI: bus type pnp registered
[   15.084473] pnp: PnP ACPI: found 12 devices
[   15.084475] ACPI: ACPI bus type pnp unregistered
[   15.084478] PnPBIOS: Disabled by ACPI PNP
[   15.084523] PCI: Using ACPI for IRQ routing
[   15.084525] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   15.104993] NET: Registered protocol family 8
[   15.104995] NET: Registered protocol family 20
[   15.105045] pnp: 00:05: iomem range 0x0-0x0 could not be reserved
[   15.105048] pnp: 00:05: iomem range 0xfed02000-0xfed03fff has been reserved
[   15.105051] pnp: 00:05: iomem range 0xfed04000-0xfed04fff has been reserved
[   15.105054] pnp: 00:05: iomem range 0xfee01000-0xfeefffff has been reserved
[   15.105060] pnp: 00:07: iomem range 0xfec00000-0xfec00fff could not be reserved
[   15.105063] pnp: 00:07: iomem range 0xfee00000-0xfee00fff could not be reserved
[   15.105068] pnp: 00:09: ioport range 0xa00-0xadf has been reserved
[   15.105071] pnp: 00:09: ioport range 0xae0-0xaef has been reserved
[   15.105075] pnp: 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
[   15.105080] pnp: 00:0b: iomem range 0x0-0x9ffff could not be reserved
[   15.105083] pnp: 00:0b: iomem range 0xc0000-0xcffff could not be reserved
[   15.105086] pnp: 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[   15.105088] pnp: 00:0b: iomem range 0x100000-0x7fffffff could not be reserved
[   15.105749] Time: tsc clocksource has been installed.
[   15.135318] PCI: Bridge: 0000:01:06.0
[   15.135319]   IO window: disabled.
[   15.135324]   MEM window: disabled.
[   15.135329]   PREFETCH window: f4000000-fbffffff
[   15.135334] PCI: Bridge: 0000:00:0a.0
[   15.135335]   IO window: disabled.
[   15.135339]   MEM window: feb00000-febfffff
[   15.135343]   PREFETCH window: f4000000-fbffffff
[   15.135347] PCI: Bridge: 0000:00:0b.0
[   15.135348]   IO window: disabled.
[   15.135351]   MEM window: disabled.
[   15.135354]   PREFETCH window: disabled.
[   15.135357] PCI: Bridge: 0000:00:0c.0
[   15.135358]   IO window: disabled.
[   15.135361]   MEM window: disabled.
[   15.135364]   PREFETCH window: disabled.
[   15.135367] PCI: Bridge: 0000:00:0d.0
[   15.135368]   IO window: disabled.
[   15.135372]   MEM window: disabled.
[   15.135374]   PREFETCH window: disabled.
[   15.135386] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   15.135407] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   15.135417] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   15.135427] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   15.135436] NET: Registered protocol family 2
[   15.177780] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   15.177873] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   15.178641] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   15.178999] TCP: Hash tables configured (established 131072 bind 65536)
[   15.179001] TCP reno registered
[   15.189939] checking if image is initramfs... it is
[   15.633177] Switched to high resolution mode on CPU 1
[   15.637076] Switched to high resolution mode on CPU 0
[   15.789191] Freeing initrd memory: 7048k freed
[   15.789677] audit: initializing netlink socket (disabled)
[   15.789691] audit(1206936130.124:1): initialized
[   15.789776] highmem bounce pool size: 64 pages
[   15.791467] VFS: Disk quotas dquot_6.5.1
[   15.791510] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   15.791587] io scheduler noop registered
[   15.791589] io scheduler anticipatory registered
[   15.791591] io scheduler deadline registered
[   15.791603] io scheduler cfq registered (default)
[   15.813919] Boot video device is 0000:00:10.0
[   15.814008] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   15.814045] assign_interrupt_mode Found MSI capability
[   15.814047] Allocate Port Service[0000:00:0b.0:pcie00]
[   15.814124] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   15.814160] assign_interrupt_mode Found MSI capability
[   15.814162] Allocate Port Service[0000:00:0c.0:pcie00]
[   15.814231] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   15.814267] assign_interrupt_mode Found MSI capability
[   15.814269] Allocate Port Service[0000:00:0d.0:pcie00]
[   15.814401] isapnp: Scanning for PnP cards...
[   16.166796] isapnp: No Plug & Play device found
[   16.186580] Real Time Clock Driver v1.12ac
[   16.186673] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   16.186765] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.187306] 00:04: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   16.187928] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   16.188076] input: Macintosh mouse button emulation as /class/input/input0
[   16.188139] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   16.188141] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   16.190504] serio: i8042 KBD port at 0x60,0x64 irq 1
[   16.190508] serio: i8042 AUX port at 0x60,0x64 irq 12
[   16.190653] mice: PS/2 mouse device common for all mice
[   16.190755] EISA: Probing bus 0 at eisa.0
[   16.190770] Cannot allocate resource for EISA slot 4
[   16.190783] EISA: Detected 0 cards.
[   16.190861] TCP cubic registered
[   16.190873] NET: Registered protocol family 1
[   16.190892] Using IPI No-Shortcut mode
[   16.191046]   Magic number: 0:693:10
[   16.191306] Freeing unused kernel memory: 364k freed
[   16.208875] input: AT Translated Set 2 keyboard as /class/input/input1
[   17.379320] AppArmor: AppArmor initialized<5>audit(1206936131.624:2):  type=1505 info="AppArmor initialized" pid=1237
[   17.386582] fuse init (API version 7.8)
[   17.390829] Failure registering capabilities with primary security module.
[   17.430185] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  28, should be 27 [20070126]
[   17.430193] ACPI: SSDT 6FF9E620, 01F3 (r1 DpgPmm  P001Ist       11 INTL 20051117)
[   17.430437] ACPI: Processor [P001] (supports 8 throttling states)
[   17.430646] ACPI: SSDT 6FF9EAB0, 01F3 (r1 DpgPmm  P002Ist       12 INTL 20051117)
[   17.430858] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   17.430868] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   17.872833] usbcore: registered new interface driver usbfs
[   17.872853] usbcore: registered new interface driver hub
[   17.872871] usbcore: registered new device driver usb
[   17.873500] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   17.873897] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 23
[   17.873903] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LUB0] -> GSI 23 (level, low) -> IRQ 16
[   17.873914] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   17.873917] ohci_hcd 0000:00:04.0: OHCI Host Controller
[   17.874023] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 1
[   17.874036] ohci_hcd 0000:00:04.0: irq 16, io mem 0xfea7f000
[   17.935907] usb usb1: configuration #1 chosen from 1 choice
[   17.935932] hub 1-0:1.0: USB hub found
[   17.935940] hub 1-0:1.0: 10 ports detected
[   17.978359] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.60.
[   17.991909] SCSI subsystem initialized
[   18.001101] libata version 2.21 loaded.
[   18.037869] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 19
[   18.037882] ACPI: PCI Interrupt 0000:01:07.0[A] -> Link [LNKB] -> GSI 19 (level, low) -> IRQ 17
[   18.038704] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 22
[   18.038709] ACPI: PCI Interrupt 0000:00:04.1[B] -> Link [LUB2] -> GSI 22 (level, low) -> IRQ 18
[   18.038720] PCI: Setting latency timer of device 0000:00:04.1 to 64
[   18.038724] ehci_hcd 0000:00:04.1: EHCI Host Controller
[   18.038852] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[   18.038876] ehci_hcd 0000:00:04.1: debug port 1
[   18.038881] PCI: cache line size of 32 is not supported by device 0000:00:04.1
[   18.038890] ehci_hcd 0000:00:04.1: irq 18, io mem 0xfea7ec00
[   18.038898] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   18.039175] usb usb2: configuration #1 chosen from 1 choice
[   18.039298] hub 2-0:1.0: USB hub found
[   18.039304] hub 2-0:1.0: 10 ports detected
[   18.087581] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[febff000-febff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   18.186722] ohci1394: fw-host0: Get PHY Reg timeout [0x02e30000/0x00000000/100]
[   18.285866] ohci1394: fw-host0: Get PHY Reg timeout [0x02e30000/0x00000000/100]
[   18.385011] ohci1394: fw-host0: Get PHY Reg timeout [0x02e30000/0x00000000/100]
[   18.385716] ahci 0000:00:0e.0: version 2.2
[   18.386090] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 21
[   18.386096] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LSA0] -> GSI 21 (level, low) -> IRQ 19
[   18.907653] usb 1-4: new low speed USB device using ohci_hcd and address 2
[   19.122003] usb 1-4: configuration #1 chosen from 1 choice
[   19.133832] usbcore: registered new interface driver hiddev
[   19.139107] input: Microsoft Basic Optical Mouse as /class/input/input2
[   19.139127] input: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:04.0-4
[   19.139139] usbcore: registered new interface driver usbhid
[   19.139142] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   19.382930] ieee1394: received packet during reset; ignoring
[   19.382935] ieee1394: received packet during reset; ignoring
[   19.382938] ieee1394: received packet during reset; ignoring
[   19.382940] ieee1394: received packet during reset; ignoring
[   19.382943] ieee1394: received packet during reset; ignoring
[   19.382945] ieee1394: received packet during reset; ignoring
[   19.382948] ieee1394: received packet during reset; ignoring
[   19.382950] ieee1394: received packet during reset; ignoring
[   19.382953] ieee1394: received packet during reset; ignoring
[   19.382955] ieee1394: received packet during reset; ignoring
[   19.382958] ieee1394: received packet during reset; ignoring
[   19.382960] ieee1394: received packet during reset; ignoring
[   19.382963] ieee1394: received packet during reset; ignoring
[   19.382965] ieee1394: received packet during reset; ignoring
[   19.382968] ieee1394: received packet during reset; ignoring
[   19.382970] ieee1394: received packet during reset; ignoring
[   19.382973] ieee1394: received packet during reset; ignoring
[   19.382975] ieee1394: received packet during reset; ignoring
[   19.382978] ieee1394: received packet during reset; ignoring
[   19.382980] ieee1394: received packet during reset; ignoring
[   19.382983] ieee1394: received packet during reset; ignoring
[   19.382985] ieee1394: received packet during reset; ignoring
[   19.382988] ieee1394: received packet during reset; ignoring
[   19.382991] ieee1394: received packet during reset; ignoring
[   19.382993] ieee1394: received packet during reset; ignoring
[   19.382996] ieee1394: received packet during reset; ignoring
[   19.382998] ieee1394: received packet during reset; ignoring
[   19.383001] ieee1394: received packet during reset; ignoring
[   19.383003] ieee1394: received packet during reset; ignoring
[   19.383006] ieee1394: received packet during reset; ignoring
[   19.383008] ieee1394: received packet during reset; ignoring
[   19.383011] ieee1394: received packet during reset; ignoring
[   19.383013] ieee1394: received packet during reset; ignoring
[   19.383016] ieee1394: received packet during reset; ignoring
[   19.383018] ieee1394: received packet during reset; ignoring
[   19.383021] ieee1394: received packet during reset; ignoring
[   19.383023] ieee1394: received packet during reset; ignoring
[   19.383026] ieee1394: received packet during reset; ignoring
[   19.383028] ieee1394: received packet during reset; ignoring
[   19.383031] ieee1394: received packet during reset; ignoring
[   19.383033] ieee1394: received packet during reset; ignoring
[   19.383036] ieee1394: received packet during reset; ignoring
[   19.383038] ieee1394: received packet during reset; ignoring
[   19.383041] ieee1394: received packet during reset; ignoring
[   19.383043] ieee1394: received packet during reset; ignoring
[   19.383046] ieee1394: received packet during reset; ignoring
[   19.383048] ieee1394: received packet during reset; ignoring
[   19.383051] ieee1394: received packet during reset; ignoring
[   19.383054] ieee1394: received packet during reset; ignoring
[   19.383056] ieee1394: received packet during reset; ignoring
[   19.383064] ieee1394: received packet during reset; ignoring
[   19.383066] ieee1394: received packet during reset; ignoring
[   19.383068] ieee1394: received packet during reset; ignoring
[   19.383070] ieee1394: received packet during reset; ignoring
[   19.383071] ieee1394: received packet during reset; ignoring
[   19.383073] ieee1394: received packet during reset; ignoring
[   19.383075] ieee1394: received packet during reset; ignoring
[   19.383076] ieee1394: received packet during reset; ignoring
[   19.383078] ieee1394: received packet during reset; ignoring
[   19.383080] ieee1394: received packet during reset; ignoring
[   19.383081] ieee1394: received packet during reset; ignoring
[   19.383083] ieee1394: received packet during reset; ignoring
[   19.383085] ieee1394: received packet during reset; ignoring
[   19.383086] ieee1394: received packet during reset; ignoring
[   19.383088] ieee1394: received packet during reset; ignoring
[   19.383090] ieee1394: received packet during reset; ignoring
[   19.383091] ieee1394: received packet during reset; ignoring
[   19.383093] ieee1394: received packet during reset; ignoring
[   19.383095] ieee1394: received packet during reset; ignoring
[   19.383096] ieee1394: received packet during reset; ignoring
[   19.383098] ieee1394: received packet during reset; ignoring
[   19.383100] ieee1394: received packet during reset; ignoring
[   19.383101] ieee1394: received packet during reset; ignoring
[   19.383103] ieee1394: received packet during reset; ignoring
[   19.383105] ieee1394: received packet during reset; ignoring
[   19.383106] ieee1394: received packet during reset; ignoring
[   19.383108] ieee1394: received packet during reset; ignoring
[   19.383110] ieee1394: received packet during reset; ignoring
[   19.383111] ieee1394: received packet during reset; ignoring
[   19.383113] ieee1394: received packet during reset; ignoring
[   19.383115] ieee1394: received packet during reset; ignoring
[   19.383117] ieee1394: received packet during reset; ignoring
[   19.383118] ieee1394: received packet during reset; ignoring
[   19.383120] ieee1394: received packet during reset; ignoring
[   19.383122] ieee1394: received packet during reset; ignoring
[   19.383123] ieee1394: received packet during reset; ignoring
[   19.383125] ieee1394: received packet during reset; ignoring
[   19.383127] ieee1394: received packet during reset; ignoring
[   19.383128] ieee1394: received packet during reset; ignoring
[   19.383130] ieee1394: received packet during reset; ignoring
[   19.383132] ieee1394: received packet during reset; ignoring
[   19.383133] ieee1394: received packet during reset; ignoring
[   19.383135] ieee1394: received packet during reset; ignoring
[   19.383137] ieee1394: received packet during reset; ignoring
[   19.383139] ieee1394: received packet during reset; ignoring
[   19.383140] ieee1394: received packet during reset; ignoring
[   19.383142] ieee1394: received packet during reset; ignoring
[   19.383144] ieee1394: received packet during reset; ignoring
[   19.383145] ieee1394: received packet during reset; ignoring
[   19.383147] ieee1394: received packet during reset; ignoring
[   19.383149] ieee1394: received packet during reset; ignoring
[   19.383150] ieee1394: received packet during reset; ignoring
[   19.383152] ieee1394: received packet during reset; ignoring
[   19.383158] ohci1394: fw-host0: Error in reception of SelfID packets [0xffffffff/0x0001214c] (count: 0)
[   19.482395] ohci1394: fw-host0: Set PHY Reg timeout [0xffffffff/0x00004000/100]
[   19.482474] ahci 0000:00:0e.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[   19.482478] ahci 0000:00:0e.0: flags: 64bit led clo pmp pio 
[   19.482482] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   19.482720] scsi0 : ahci
[   19.482770] scsi1 : ahci
[   19.482799] scsi2 : ahci
[   19.482832] scsi3 : ahci
[   19.482904] ata1: SATA max UDMA/133 cmd 0xf885c100 ctl 0x00000000 bmdma 0x00000000 irq 19
[   19.482907] ata2: SATA max UDMA/133 cmd 0xf885c180 ctl 0x00000000 bmdma 0x00000000 irq 19
[   19.482910] ata3: SATA max UDMA/133 cmd 0xf885c200 ctl 0x00000000 bmdma 0x00000000 irq 19
[   19.482913] ata4: SATA max UDMA/133 cmd 0xf885c280 ctl 0x00000000 bmdma 0x00000000 irq 19
[   19.965974] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   19.966523] ata1.00: ATA-7: WDC WD2500KS-00MJB0, 02.01C03, max UDMA/133
[   19.966527] ata1.00: 488397168 sectors, multi 16: LBA48 
[   19.967134] ata1.00: configured for UDMA/133
[   20.277449] ata2: SATA link down (SStatus 0 SControl 300)
[   20.588949] ata3: SATA link down (SStatus 0 SControl 300)
[   20.900451] ata4: SATA link down (SStatus 0 SControl 300)
[   20.900576] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500KS-00M 02.0 PQ: 0 ANSI: 5
[   20.902184] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[   20.902190] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [LMAC] -> GSI 20 (level, low) -> IRQ 20
[   20.902196] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[   20.902204] forcedeth: using HIGHDMA
[   21.420279] eth0: forcedeth.c: subsystem: 01462:366c bound to 0000:00:0f.0
[   21.425370] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   21.425375] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   21.425969] NFORCE-MCP73: IDE controller at PCI slot 0000:00:08.0
[   21.425989] NFORCE-MCP73: chipset revision 161
[   21.425991] NFORCE-MCP73: not 100% native mode: will probe irqs later
[   21.425998] NFORCE-MCP73: 0000:00:08.0 (rev a1) UDMA133 controller
[   21.426006]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[   21.426015] Probing IDE interface ide0...
[   21.435700] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   21.435712] sd 0:0:0:0: [sda] Write Protect is off
[   21.435714] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.435728] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.435771] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   21.435780] sd 0:0:0:0: [sda] Write Protect is off
[   21.435782] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   21.435795] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   21.435799]  sda: sda1 sda2 < sda5 >
[   21.467133] sd 0:0:0:0: [sda] Attached SCSI disk
[   21.470313] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   21.614062] Attempting manual resume
[   21.614065] swsusp: Resume From Partition 8:5
[   21.614067] PM: Checking swsusp image.
[   21.614169] PM: Resume from disk failed.
[   21.651324] kjournald starting.  Commit interval 5 seconds
[   21.651335] EXT3-fs: mounted filesystem with ordered data mode.
[   22.158528] hda: Optiarc DVD RW AD-7190A, ATAPI CD/DVD-ROM drive
[   22.830086] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   27.665123] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   27.675309] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   27.829145] input: PC Speaker as /class/input/input3
[   27.867441] Linux video capture interface: v2.00
[   27.881927] Linux agpgart interface v0.102 (c) Dave Jones
[   27.956011] nvidia: module license 'NVIDIA' taints kernel.
[   28.208617] ACPI: PCI Interrupt Link [SGRU] enabled at IRQ 23
[   28.208621] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [SGRU] -> GSI 23 (level, low) -> IRQ 16
[   28.208630] PCI: Setting latency timer of device 0000:00:10.0 to 64
[   28.208757] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.19  Wed Sep 12 14:12:24 PDT 2007
[   28.265039] hda: ATAPI 12X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   28.265049] Uniform CD-ROM driver Revision: 3.20
[   28.273532] ivtv:  ==================== START INIT IVTV ====================
[   28.273535] ivtv:  version 1.0.0 (2.6.22-14-generic SMP mod_unload 586 ) loading
[   28.273604] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   28.279760] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 18
[   28.279767] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKA] -> GSI 18 (level, low) -> IRQ 21
[   28.574766] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[   28.574770] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LAZA] -> GSI 22 (level, low) -> IRQ 18
[   28.574787] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   28.606827] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   28.932259] ivtv0: loaded v4l-cx2341x-enc.fw firmware (3751102016 bytes)
[   29.147219] ivtv0: Encoder revision: 0x02050032
[   29.147222] ivtv0: Recommended firmware version is 0x02060039.
[   29.206271] tveeprom 0-0050: Hauppauge model 23552, rev E592, serial# 10470122
[   29.206274] tveeprom 0-0050: tuner model is Philips FQ1236A MK4 (idx 92, type 57)
[   29.206277] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   29.206279] tveeprom 0-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[   29.206282] tveeprom 0-0050: audio processor is CX25843 (idx 37)
[   29.206284] tveeprom 0-0050: decoder processor is CX25843 (idx 30)
[   29.206286] tveeprom 0-0050: has radio, has no IR receiver, has no IR transmitter
[   29.206289] ivtv0: Autodetected WinTV PVR 500 (unit #1)
[   29.223039] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   29.223069] tda9887 0-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   29.226932] tuner 0-0060: TEA5767 detected.
[   29.226934] tuner 0-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[   29.226945] tuner 0-0060: type set to 62 (Philips TEA5767HN FM Radio)
[   29.227189] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   29.249681] cx25840 0-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   32.705675] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   32.806849] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   32.854563] tuner 0-0061: type set to 57 (Philips FQ1236A MK4)
[   33.174783] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   33.175028] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   33.175301] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   33.175471] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   33.175764] ivtv0: Registered device radio0 for encoder radio
[   33.200929] ivtv0: Initialized WinTV PVR 500 (unit #1), card #0
[   33.200971] ivtv:  ======================  NEXT CARD  ======================
[   33.200974] ivtv1: Autodetected Hauppauge card (cx23416 based)
[   33.201028] ACPI: PCI Interrupt 0000:02:09.0[A] -> Link [LNKB] -> GSI 19 (level, low) -> IRQ 17
[   33.832127] ivtv1: loaded v4l-cx2341x-enc.fw firmware (3751102520 bytes)
[   34.047346] ivtv1: Encoder revision: 0x02050032
[   34.047349] ivtv1: Recommended firmware version is 0x02060039.
[   34.052224] tuner 1-0043: chip found @ 0x86 (ivtv i2c driver #1)
[   34.052237] tda9887 1-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   34.055428] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[   34.071548] cx25840 1-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #1)
[   37.528168] cx25840 1-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   37.605249] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #1)
[   37.672002] tveeprom 1-0050: Hauppauge model 23552, rev E592, serial# 10470122
[   37.672005] tveeprom 1-0050: tuner model is Philips FQ1236A MK4 (idx 92, type 57)
[   37.672007] tveeprom 1-0050: TV standards NTSC(M) (eeprom 0x08)
[   37.672010] tveeprom 1-0050: second tuner model is Philips TEA5768HL FM Radio (idx 101, type 62)
[   37.672012] tveeprom 1-0050: audio processor is CX25843 (idx 37)
[   37.672014] tveeprom 1-0050: decoder processor is CX25843 (idx 30)
[   37.672017] tveeprom 1-0050: has radio, has no IR receiver, has no IR transmitter
[   37.672020] ivtv1: Correcting tveeprom data: no radio present on second unit
[   37.672022] ivtv1: Autodetected WinTV PVR 500 (unit #2)
[   37.727332] tuner 1-0061: type set to 57 (Philips FQ1236A MK4)
[   38.046943] ivtv1: Registered device video1 for encoder MPEG (4 MB)
[   38.047102] ivtv1: Registered device video33 for encoder YUV (2 MB)
[   38.047287] ivtv1: Registered device vbi1 for encoder VBI (1 MB)
[   38.047367] ivtv1: Registered device video25 for encoder PCM audio (1 MB)
[   38.071483] ivtv1: Initialized WinTV PVR 500 (unit #2), card #1
[   38.071798] ivtv:  ====================  END INIT IVTV  ====================
[   38.568066] lp: driver loaded but no devices found
[   38.622713] Adding 5317472k swap on /dev/sda5.  Priority:-1 extents:1 across:5317472k
[   38.955454] EXT3 FS on sda1, internal journal
[   39.864419] input: Power Button (FF) as /class/input/input4
[   39.864438] ACPI: Power Button (FF) [PWRF]
[   39.864522] input: Power Button (CM) as /class/input/input5
[   39.864539] ACPI: Power Button (CM) [PWRB]
[   39.904151] No dock devices found.
[   41.032163] ppdev: user-space parallel port driver
[   41.186690] audit(1206936156.621:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4970 profile="/usr/sbin/cupsd"
[   41.243407] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   41.243411] apm: disabled - APM is not SMP safe.
[   42.186002] Failure registering capabilities with primary security module.
[   42.384199] Bluetooth: Core ver 2.11
[   42.384267] NET: Registered protocol family 31
[   42.384270] Bluetooth: HCI device and connection manager initialized
[   42.384275] Bluetooth: HCI socket layer initialized
[   42.406452] Bluetooth: L2CAP ver 2.8
[   42.406458] Bluetooth: L2CAP socket layer initialized
[   42.452672] Bluetooth: RFCOMM socket layer initialized
[   42.452688] Bluetooth: RFCOMM TTY layer initialized
[   42.452691] Bluetooth: RFCOMM ver 1.8
[   44.519418] NVRM: RmInitAdapter failed! (0x23:0xffffffff:682)
[   44.519431] NVRM: rm_init_adapter(0) failed
[   46.520477] NET: Registered protocol family 17
[   48.579868] NVRM: RmInitAdapter failed! (0x23:0xffffffff:682)
[   48.579881] NVRM: rm_init_adapter(0) failed
[   50.710804] NET: Registered protocol family 10
[   50.710910] lo: Disabled Privacy Extensions
[   52.637128] NVRM: RmInitAdapter failed! (0x23:0xffffffff:682)
[   52.637139] NVRM: rm_init_adapter(0) failed
[   61.016728] eth0: no IPv6 routers present
[  215.679355] NVRM: RmInitAdapter failed! (0x23:0xffffffff:682)
[  215.679365] NVRM: rm_init_adapter(0) failed

```

Here's the output of "cat /var/log/Xorg.0.log"
```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux Core7989 2.6.22-14-generic #1 SMP Tue Feb 12 07:
42:25 UTC 2008 i686
Build Date: 18 January 2008
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Mar 31 00:04:20 2008
(==) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Failsafe Monitor"
(**) |   |-->Device "Failsafe Device"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
        Entry deleted from font path.
(==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81e9800
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.3
        X.Org Video Driver: 1.2
        X.Org XInput driver : 0.7
        X.Org Server Extension : 0.3
        X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.2
(++) using VT number 9

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,07c1 card 1462,7366 rev a2 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,07cb card 1462,7366 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:01:0: chip 10de,07cd card 1462,7366 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:1: chip 10de,07ce card 1462,7366 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:2: chip 10de,07cf card 1462,7366 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:3: chip 10de,07d0 card 1462,7366 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:4: chip 10de,07d1 card 1462,7366 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:5: chip 10de,07d2 card 1462,7366 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:6: chip 10de,07d3 card 1462,7366 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:02:0: chip 10de,07d6 card 1462,7366 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:03:0: chip 10de,07d7 card 1462,7366 rev a2 class 06,01,00 hdr 80
(II) PCI: 00:03:1: chip 10de,07d8 card 1462,7366 rev a1 class 0c,05,00 hdr 80
(II) PCI: 00:03:2: chip 10de,07d9 card 1462,7366 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:03:3: chip 10de,07da card 1462,7366 rev a2 class 0b,40,00 hdr 80
(II) PCI: 00:03:4: chip 10de,07c8 card 0000,0000 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:04:0: chip 10de,07fe card 1462,7366 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:04:1: chip 10de,056a card 1462,7366 rev a1 class 0c,03,20 hdr 80
(II) PCI: 00:08:0: chip 10de,056c card 1462,7366 rev a1 class 01,01,8a hdr 00

(II) PCI: 00:09:0: chip 10de,07fc card 1462,7366 rev a1 class 04,03,00 hdr 00
(II) PCI: 00:0a:0: chip 10de,056d card 0000,0000 rev a1 class 06,04,01 hdr 01
(II) PCI: 00:0b:0: chip 10de,056e card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:0c:0: chip 10de,056f card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 10de,056f card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,07f0 card 1462,7366 rev a2 class 01,01,85 hdr 00
(II) PCI: 00:0f:0: chip 10de,07dc card 1462,366c rev a2 class 02,00,00 hdr 00
(II) PCI: 00:10:0: chip 10de,07e1 card 1462,7366 rev a2 class 03,00,00 hdr 00
(II) PCI: 01:06:0: chip 3388,0021 card 0000,0000 rev 11 class 06,04,00 hdr 01
(II) PCI: 01:07:0: chip 104c,8024 card 0000,0000 rev 00 class 0c,00,10 hdr 00
(II) PCI: 02:08:0: chip 4444,0016 card 0070,e807 rev 01 class 04,00,00 hdr 00
(II) PCI: 02:09:0: chip 4444,0016 card 0070,e817 rev 01 class 04,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:3:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:10:0), (0,1,2), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Bus 1 non-prefetchable memory range:
        [0] -1  0       0xfeb00000 - 0xfebfffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
        [0] -1  0       0xf4000000 - 0xfbffffff (0x8000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:11:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:12:0), (0,4,4), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:13:0), (0,5,5), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (1:6:0), (1,2,2), BCTRL: 0x0007 (VGA_EN is cleared)
(II) Bus 2 prefetchable memory range:
        [0] -1  0       0xf4000000 - 0xfbffffff (0x8000000) MX[B]
(--) PCI:*(0:16:0) nVidia Corporation unknown chipset (0x07e1) rev 162, Mem @ 0x
fd000000/24, 0xd0000000/28, 0xfc000000/24, BIOS @ 0xfea40000/17
(--) PCI: (2:8:0) unknown vendor (0x4444) unknown chipset (0x0016) rev 1, Mem @ 
0xf8000000/26
(--) PCI: (2:9:0) unknown vendor (0x4444) unknown chipset (0x0016) rev 1, Mem @ 
0xf4000000/26
(II) Addressable bus resource ranges are
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
        [1] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
        [0] -1  0       0xfebf8000 - 0xfebfbfff (0x4000) MX[B]
        [1] -1  0       0xfebff000 - 0xfebfffff (0x1000) MX[B]
        [2] -1  0       0xfea7e400 - 0xfea7e40f (0x10) MX[B]
        [3] -1  0       0xfea7e800 - 0xfea7e8ff (0x100) MX[B]
        [4] -1  0       0xfea77000 - 0xfea77fff (0x1000) MX[B]
        [5] -1  0       0xfea7c000 - 0xfea7dfff (0x2000) MX[B]
        [6] -1  0       0xfea78000 - 0xfea7bfff (0x4000) MX[B]
        [7] -1  0       0xfea7ec00 - 0xfea7ecff (0x100) MX[B]
        [8] -1  0       0xfea7f000 - 0xfea7ffff (0x1000) MX[B]
        [9] -1  0       0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
        [10] -1 0       0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
        [11] -1 0       0xfea40000 - 0xfea5ffff (0x20000) MX[B](B)
        [12] -1 0       0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
        [13] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
        [14] -1 0       0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
        [15] -1 0       0xfea80000 - 0xfeafffff (0x80000) MX[B]
        [16] -1 0       0x0000d880 - 0x0000d887 (0x8) IX[B]
        [17] -1 0       0x0000dc00 - 0x0000dc0f (0x10) IX[B]
        [18] -1 0       0x0000e000 - 0x0000e003 (0x4) IX[B]
        [19] -1 0       0x0000e080 - 0x0000e087 (0x8) IX[B]
        [20] -1 0       0x0000e400 - 0x0000e403 (0x4) IX[B]
        [21] -1 0       0x0000e480 - 0x0000e487 (0x8) IX[B]
        [22] -1 0       0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
        [23] -1 0       0x00004e00 - 0x00004e3f (0x40) IX[B]
        [24] -1 0       0x00004d00 - 0x00004d3f (0x40) IX[B]
        [25] -1 0       0x00004900 - 0x0000493f (0x40) IX[B]
        [26] -1 0       0x00004f00 - 0x00004fff (0x100) IX[B]
(II) Active PCI resource ranges after removing overlaps:
        [0] -1  0       0xfebf8000 - 0xfebfbfff (0x4000) MX[B]
        [1] -1  0       0xfebff000 - 0xfebfffff (0x1000) MX[B]
        [2] -1  0       0xfea7e400 - 0xfea7e40f (0x10) MX[B]
        [3] -1  0       0xfea7e800 - 0xfea7e8ff (0x100) MX[B]
        [4] -1  0       0xfea77000 - 0xfea77fff (0x1000) MX[B]
        [5] -1  0       0xfea7c000 - 0xfea7dfff (0x2000) MX[B]
        [6] -1  0       0xfea78000 - 0xfea7bfff (0x4000) MX[B]
        [7] -1  0       0xfea7ec00 - 0xfea7ecff (0x100) MX[B]
        [8] -1  0       0xfea7f000 - 0xfea7ffff (0x1000) MX[B]
        [9] -1  0       0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
        [10] -1 0       0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
        [11] -1 0       0xfea40000 - 0xfea5ffff (0x20000) MX[B](B)
        [12] -1 0       0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
        [13] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
        [14] -1 0       0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
        [15] -1 0       0xfea80000 - 0xfeafffff (0x80000) MX[B]
        [16] -1 0       0x0000d880 - 0x0000d887 (0x8) IX[B]
        [17] -1 0       0x0000dc00 - 0x0000dc0f (0x10) IX[B]
        [18] -1 0       0x0000e000 - 0x0000e003 (0x4) IX[B]
        [19] -1 0       0x0000e080 - 0x0000e087 (0x8) IX[B]
        [20] -1 0       0x0000e400 - 0x0000e403 (0x4) IX[B]
        [21] -1 0       0x0000e480 - 0x0000e487 (0x8) IX[B]
        [22] -1 0       0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
        [23] -1 0       0x00004e00 - 0x00004e3f (0x40) IX[B]
        [24] -1 0       0x00004d00 - 0x00004d3f (0x40) IX[B]
        [25] -1 0       0x00004900 - 0x0000493f (0x40) IX[B]
        [26] -1 0       0x00004f00 - 0x00004fff (0x100) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xfebf8000 - 0xfebfbfff (0x4000) MX[B]
        [5] -1  0       0xfebff000 - 0xfebfffff (0x1000) MX[B]
        [6] -1  0       0xfea7e400 - 0xfea7e40f (0x10) MX[B]
        [7] -1  0       0xfea7e800 - 0xfea7e8ff (0x100) MX[B]
        [8] -1  0       0xfea77000 - 0xfea77fff (0x1000) MX[B]
        [9] -1  0       0xfea7c000 - 0xfea7dfff (0x2000) MX[B]
        [10] -1 0       0xfea78000 - 0xfea7bfff (0x4000) MX[B]
        [11] -1 0       0xfea7ec00 - 0xfea7ecff (0x100) MX[B]
        [12] -1 0       0xfea7f000 - 0xfea7ffff (0x1000) MX[B]
        [13] -1 0       0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
        [14] -1 0       0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
        [15] -1 0       0xfea40000 - 0xfea5ffff (0x20000) MX[B](B)
        [16] -1 0       0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
        [17] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
        [18] -1 0       0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
        [19] -1 0       0xfea80000 - 0xfeafffff (0x80000) MX[B]
        [20] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [21] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [22] -1 0       0x0000d880 - 0x0000d887 (0x8) IX[B]
        [23] -1 0       0x0000dc00 - 0x0000dc0f (0x10) IX[B]
        [24] -1 0       0x0000e000 - 0x0000e003 (0x4) IX[B]
        [25] -1 0       0x0000e080 - 0x0000e087 (0x8) IX[B]
        [26] -1 0       0x0000e400 - 0x0000e403 (0x4) IX[B]
        [27] -1 0       0x0000e480 - 0x0000e487 (0x8) IX[B]
        [28] -1 0       0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
        [29] -1 0       0x00004e00 - 0x00004e3f (0x40) IX[B]
        [30] -1 0       0x00004d00 - 0x00004d3f (0x40) IX[B]
        [31] -1 0       0x00004900 - 0x0000493f (0x40) IX[B]
        [32] -1 0       0x00004f00 - 0x00004fff (0x100) IX[B]
(WW) "dbe" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "dri" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "glx" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "vbe" will not be loaded unless you've specified it to be loaded elsewhere.
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 1.3.0, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.13.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.3.0
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.2.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.2.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.7
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 00:10:0
(--) Chipset vesa found
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xfebf8000 - 0xfebfbfff (0x4000) MX[B]
        [5] -1  0       0xfebff000 - 0xfebfffff (0x1000) MX[B]
        [6] -1  0       0xfea7e400 - 0xfea7e40f (0x10) MX[B]
        [7] -1  0       0xfea7e800 - 0xfea7e8ff (0x100) MX[B]
        [8] -1  0       0xfea77000 - 0xfea77fff (0x1000) MX[B]
        [9] -1  0       0xfea7c000 - 0xfea7dfff (0x2000) MX[B]
        [10] -1 0       0xfea78000 - 0xfea7bfff (0x4000) MX[B]
        [11] -1 0       0xfea7ec00 - 0xfea7ecff (0x100) MX[B]
        [12] -1 0       0xfea7f000 - 0xfea7ffff (0x1000) MX[B]
        [13] -1 0       0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
        [14] -1 0       0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
        [15] -1 0       0xfea40000 - 0xfea5ffff (0x20000) MX[B](B)
        [16] -1 0       0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
        [17] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
        [18] -1 0       0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
        [19] -1 0       0xfea80000 - 0xfeafffff (0x80000) MX[B]
        [20] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [21] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [22] -1 0       0x0000d880 - 0x0000d887 (0x8) IX[B]
        [23] -1 0       0x0000dc00 - 0x0000dc0f (0x10) IX[B]
        [24] -1 0       0x0000e000 - 0x0000e003 (0x4) IX[B]
        [25] -1 0       0x0000e080 - 0x0000e087 (0x8) IX[B]
        [26] -1 0       0x0000e400 - 0x0000e403 (0x4) IX[B]
        [27] -1 0       0x0000e480 - 0x0000e487 (0x8) IX[B]
        [28] -1 0       0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
        [29] -1 0       0x00004e00 - 0x00004e3f (0x40) IX[B]
        [30] -1 0       0x00004d00 - 0x00004d3f (0x40) IX[B]
        [31] -1 0       0x00004900 - 0x0000493f (0x40) IX[B]
        [32] -1 0       0x00004f00 - 0x00004fff (0x100) IX[B]
(II) resource ranges after probing:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xfebf8000 - 0xfebfbfff (0x4000) MX[B]
        [5] -1  0       0xfebff000 - 0xfebfffff (0x1000) MX[B]
        [6] -1  0       0xfea7e400 - 0xfea7e40f (0x10) MX[B]
        [7] -1  0       0xfea7e800 - 0xfea7e8ff (0x100) MX[B]
        [8] -1  0       0xfea77000 - 0xfea77fff (0x1000) MX[B]
        [9] -1  0       0xfea7c000 - 0xfea7dfff (0x2000) MX[B]
        [10] -1 0       0xfea78000 - 0xfea7bfff (0x4000) MX[B]
        [11] -1 0       0xfea7ec00 - 0xfea7ecff (0x100) MX[B]
        [12] -1 0       0xfea7f000 - 0xfea7ffff (0x1000) MX[B]
        [13] -1 0       0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
        [14] -1 0       0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
        [15] -1 0       0xfea40000 - 0xfea5ffff (0x20000) MX[B](B)
        [16] -1 0       0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
        [17] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
        [18] -1 0       0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
        [19] -1 0       0xfea80000 - 0xfeafffff (0x80000) MX[B]
        [20] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [21] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [22] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [23] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [24] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [25] -1 0       0x0000d880 - 0x0000d887 (0x8) IX[B]
        [26] -1 0       0x0000dc00 - 0x0000dc0f (0x10) IX[B]
        [27] -1 0       0x0000e000 - 0x0000e003 (0x4) IX[B]
        [28] -1 0       0x0000e080 - 0x0000e087 (0x8) IX[B]
        [29] -1 0       0x0000e400 - 0x0000e403 (0x4) IX[B]
        [30] -1 0       0x0000e480 - 0x0000e487 (0x8) IX[B]
        [31] -1 0       0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
        [32] -1 0       0x00004e00 - 0x00004e3f (0x40) IX[B]
        [33] -1 0       0x00004d00 - 0x00004d3f (0x40) IX[B]
        [34] -1 0       0x00004900 - 0x0000493f (0x40) IX[B]
        [35] -1 0       0x00004f00 - 0x00004fff (0x100) IX[B]
        [36] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [37] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.1.0
        ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.2
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 262144 kB
(II) VESA(0): VESA VBE OEM: NVIDIA
(II) VESA(0): VESA VBE OEM Software Rev: 5.115
(II) VESA(0): VESA VBE OEM Vendor: Build    071004.1

(II) VESA(0): VESA VBE OEM Product: MCP73 - mcp73-81
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
(**) VESA(0): Depth 16, (--) framebuffer bpp 16
(==) VESA(0): RGB weight 565
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level none
(II) VESA(0): VESA VBE DDC transfer in appr. 0 sec.
(II) VESA(0): VESA VBE DDC read failed
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 100 (640x400)
        ModeAttributes: 0x39f
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc0009cc3
        BytesPerScanline: 640
        XResolution: 640
        YResolution: 400
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 8
        NumberOfBanks: 1
        MemoryModel: 4
        BankSize: 0
        NumberOfImages: 14
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0xd0000000
        LinBytesPerScanLine: 640
        BnkNumberOfImagePages: 14
        LinNumberOfImagePages: 14
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 229500000
Mode: 101 (640x480)
        ModeAttributes: 0x39f
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc0009cc3
        BytesPerScanline: 640
        XResolution: 640
        YResolution: 480
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 8
        NumberOfBanks: 1
        MemoryModel: 4
        BankSize: 0
        NumberOfImages: 10
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0xd0000000
        LinBytesPerScanLine: 640
        BnkNumberOfImagePages: 10
        LinNumberOfImagePages: 10
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 229500000
Mode: 102 (800x600)
        ModeAttributes: 0x31f
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc0009cc3
        BytesPerScanline: 100
        XResolution: 800
        YResolution: 600
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 4
        BitsPerPixel: 4
        NumberOfBanks: 1
        MemoryModel: 3
        BankSize: 0
        NumberOfImages: 14
        RedMaskSize: 0
        RedFieldPosition: 0
        GreenMaskSize: 0
        GreenFieldPosition: 0
        BlueMaskSize: 0
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0x0
        LinBytesPerScanLine: 100
        BnkNumberOfImagePages: 14
        LinNumberOfImagePages: 14
        LinRedMaskSize: 0
        LinRedFieldPosition: 0
        LinGreenMaskSize: 0
        LinGreenFieldPosition: 0
        LinBlueMaskSize: 0
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 108500000

***** BUNCH OF SIMILAR MODE DEF'S SNIPPED ****

*Mode: 148 (1400x1050)
        ModeAttributes: 0x39f
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc0009cc3
        BytesPerScanline: 2800
        XResolution: 1400
        YResolution: 1050
        XCharSize: 8
        YCharSize: 14
        NumberOfPlanes: 1
        BitsPerPixel: 16
        NumberOfBanks: 1
        MemoryModel: 6
        BankSize: 0
        NumberOfImages: 1
        RedMaskSize: 5
        RedFieldPosition: 11
        GreenMaskSize: 6
        GreenFieldPosition: 5
        BlueMaskSize: 5
        BlueFieldPosition: 0
        RsvdMaskSize: 0
        RsvdFieldPosition: 0
        DirectColorModeInfo: 0
        PhysBasePtr: 0xd0000000
        LinBytesPerScanLine: 2800
        BnkNumberOfImagePages: 1
        LinNumberOfImagePages: 1
        LinRedMaskSize: 5
        LinRedFieldPosition: 11
        LinGreenMaskSize: 6
        LinGreenFieldPosition: 5
        LinBlueMaskSize: 5
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 0
        LinRsvdFieldPosition: 0
        MaxPixelClock: 229500000
Mode: 152 (2048x1536)
        ModeAttributes: 0x3db
        WinAAttributes: 0x7
        WinBAttributes: 0x0
        WinGranularity: 64
        WinSize: 64
        WinASegment: 0xa000
        WinBSegment: 0x0
        WinFuncPtr: 0xc0009cc3
        BytesPerScanline: 8192
        XResolution: 2048
        YResolution: 1536
        XCharSize: 8
        YCharSize: 16
        NumberOfPlanes: 1
        BitsPerPixel: 32
        NumberOfBanks: 1
        MemoryModel: 6
        BankSize: 0
        NumberOfImages: 0
        RedMaskSize: 8
        RedFieldPosition: 16
        GreenMaskSize: 8
        GreenFieldPosition: 8
        BlueMaskSize: 8
        BlueFieldPosition: 0
        RsvdMaskSize: 8
        RsvdFieldPosition: 24
        DirectColorModeInfo: 0
        PhysBasePtr: 0xd0000000
        LinBytesPerScanLine: 8192
        BnkNumberOfImagePages: 0
        LinNumberOfImagePages: 0
        LinRedMaskSize: 8
        LinRedFieldPosition: 16
        LinGreenMaskSize: 8
        LinGreenFieldPosition: 8
        LinBlueMaskSize: 8
        LinBlueFieldPosition: 0
        LinRsvdMaskSize: 8
        LinRsvdFieldPosition: 24
        MaxPixelClock: 229500000

(II) VESA(0): Total Memory: 4096 64KB banks (262144kB)
(II) VESA(0): Failsafe Monitor: Using default hsync range of 31.50-37.90 kHz
(II) VESA(0): Failsafe Monitor: Using default vrefresh range of 50.00-70.00 Hz
(II) VESA(0): Not using built-in mode "1600x1200" (width too large for virtual s
ize)
(II) VESA(0): Not using built-in mode "1400x1050" (width too large for virtual s
ize)
(II) VESA(0): Not using built-in mode "1280x1024" (width too large for virtual s
ize)
(II) VESA(0): Not using built-in mode "1024x768" (width too large for virtual si
ze)
(II) VESA(0): Not using built-in mode "640x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x400" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x240" (hsync out of range)
(II) VESA(0): Not using built-in mode "320x200" (hsync out of range)
(--) VESA(0): Virtual size is 800x600 (pitch 800)
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0):  Built-in mode "640x480"
(==) VESA(0): DPI set to (100, 100)
(II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (114)
(II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (111)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.1.0
        ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.3
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xfebf8000 - 0xfebfbfff (0x4000) MX[B]
        [5] -1  0       0xfebff000 - 0xfebfffff (0x1000) MX[B]
        [6] -1  0       0xfea7e400 - 0xfea7e40f (0x10) MX[B]
        [7] -1  0       0xfea7e800 - 0xfea7e8ff (0x100) MX[B]
        [8] -1  0       0xfea77000 - 0xfea77fff (0x1000) MX[B]
        [9] -1  0       0xfea7c000 - 0xfea7dfff (0x2000) MX[B]
        [10] -1 0       0xfea78000 - 0xfea7bfff (0x4000) MX[B]
        [11] -1 0       0xfea7ec00 - 0xfea7ecff (0x100) MX[B]
        [12] -1 0       0xfea7f000 - 0xfea7ffff (0x1000) MX[B]
        [13] -1 0       0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
        [14] -1 0       0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
        [15] -1 0       0xfea40000 - 0xfea5ffff (0x20000) MX[B](B)
        [16] -1 0       0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
        [17] -1 0       0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
        [18] -1 0       0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
        [19] -1 0       0xfea80000 - 0xfeafffff (0x80000) MX[B]
        [20] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [21] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [22] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [23] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [24] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [25] -1 0       0x0000d880 - 0x0000d887 (0x8) IX[B]
        [26] -1 0       0x0000dc00 - 0x0000dc0f (0x10) IX[B]
        [27] -1 0       0x0000e000 - 0x0000e003 (0x4) IX[B]
        [28] -1 0       0x0000e080 - 0x0000e087 (0x8) IX[B]
        [29] -1 0       0x0000e400 - 0x0000e403 (0x4) IX[B]
        [30] -1 0       0x0000e480 - 0x0000e487 (0x8) IX[B]
        [31] -1 0       0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
        [32] -1 0       0x00004e00 - 0x00004e3f (0x40) IX[B]
        [33] -1 0       0x00004d00 - 0x00004d3f (0x40) IX[B]
        [34] -1 0       0x00004900 - 0x0000493f (0x40) IX[B]
        [35] -1 0       0x00004f00 - 0x00004fff (0x100) IX[B]
        [36] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [37] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 262144 kB
(II) VESA(0): VESA VBE OEM: NVIDIA
(II) VESA(0): VESA VBE OEM Software Rev: 5.115
(II) VESA(0): VESA VBE OEM Vendor: Build    071004.1

(II) VESA(0): VESA VBE OEM Product: MCP73 - mcp73-81
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
(==) VESA(0): Write-combining range (0xd0000000,0x10000000)
(II) VESA(0): virtual address = 0xa7afe000,
        physical address = 0xd0000000, size = 268435456
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(**) Option "dpms"
(**) VESA(0): DPMS enabled
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9
SetClientVersion: 0 9
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Configured Mouse: ps2EnableDataReporting: succeeded

```

Here's the output of 'lsmod'
```

Module                  Size  Used by
ipv6                  273892  10 
af_packet              24840  2 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
acpi_cpufreq           10568  0 
cpufreq_stats           7232  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5280  0 
cpufreq_conservative     8072  0 
cpufreq_ondemand        9612  2 
freq_table              5792  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
container               5504  0 
ac                      6148  0 
sbs                    19592  0 
dock                   10656  0 
button                  8976  0 
video                  18060  0 
battery                11012  0 
sbp2                   24072  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
wm8775                  7180  0 
cx25840                26640  0 
tuner                  63144  0 
snd_hda_intel         349848  1 
snd_pcm_oss            42784  0 
snd_mixer_oss          18048  2 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11656  2 snd_hda_intel,snd_pcm
snd_hwdep              10628  1 snd_hda_intel
snd_seq_oss            35712  0 
snd_seq_midi_event      8704  1 snd_seq_oss
snd_seq                54480  4 snd_seq_oss,snd_seq_midi_event
ivtv                  134928  0 
ide_cd                 32672  0 
cdrom                  37536  1 ide_cd
i2c_algo_bit            7428  1 ivtv
snd_timer              25092  2 snd_pcm,snd_seq
snd_seq_device          9740  2 snd_seq_oss,snd_seq
nvidia               6221648  0 
cx2341x                13316  1 ivtv
tveeprom               16784  1 ivtv
agpgart                35016  1 nvidia
videodev               29312  1 ivtv
v4l2_common            18432  6 wm8775,cx25840,tuner,ivtv,cx2341x,videodev
v4l1_compat            15364  2 ivtv,videodev
psmouse                39952  0 
serio_raw               8068  0 
pcspkr                  4224  0 
i2c_core               26112  7 wm8775,cx25840,tuner,ivtv,i2c_algo_bit,nvidia,tveeprom
snd                    59940  9 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
soundcore               8800  2 snd
evdev                  11136  3 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  3 
amd74xx                15260  0 [permanent]
ide_core              116804  2 ide_cd,amd74xx
usbhid                 29536  0 
hid                    28928  1 usbhid
ata_generic             8452  0 
ahci                   23300  2 
libata                125168  2 ata_generic,ahci
scsi_mod              147084  4 sbp2,sg,sd_mod,libata
forcedeth              51592  0 
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
ehci_hcd               36492  0 
ohci_hcd               22916  0 
usbcore               138632  4 usbhid,ehci_hcd,ohci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

```

Here's the 'cat /etc/X11/xorg.conf'
```

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "nVidia Corporation NVIDIA Default Card"
        Driver          "nvidia"
        BusID           "PCI:0:16:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-72
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NVIDIA Default Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1440x900" "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
EndSection

```

and now for a couple of other things: 

output of lspci:
```

00:00.0 Host bridge: nVidia Corporation Unknown device 07c1 (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)
00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:03.0 ISA bridge: nVidia Corporation Unknown device 07d7 (rev a2)
00:03.1 SMBus: nVidia Corporation Unknown device 07d8 (rev a1)
00:03.2 RAM memory: nVidia Corporation Unknown device 07d9 (rev a1)
00:03.3 Co-processor: nVidia Corporation Unknown device 07da (rev a2)
00:03.4 RAM memory: nVidia Corporation Unknown device 07c8 (rev a1)
00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i (rev a1)
00:04.1 USB Controller: nVidia Corporation GeForce 7100/nForce 630i (rev a1)
00:08.0 IDE interface: nVidia Corporation Unknown device 056c (rev a1)
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
00:0a.0 PCI bridge: nVidia Corporation Unknown device 056d (rev a1)
00:0b.0 PCI bridge: nVidia Corporation Unknown device 056e (rev a1)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 056f (rev a1)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 056f (rev a1)
00:0e.0 IDE interface: nVidia Corporation Unknown device 07f0 (rev a2)
00:0f.0 Ethernet controller: nVidia Corporation MCP73 Ethernet (rev a2)
00:10.0 VGA compatible controller: nVidia Corporation GeForce 7100/nForce 630i (rev a2)
01:06.0 PCI bridge: Hint Corp HB6 Universal PCI-PCI bridge (non-transparent mode) (rev 11)
01:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
02:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
02:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)

```

And output of lspci -n | grep 0300
[Code]
00:10.0 0300: 10de:07e1 (rev a2)
[Code]

The odd thing  is that when I run "startx" from a shell login .. I get different errors .. mainly that there are no screens found for use with the nvidia graphics .. and that the nvidia driver failed to initialize.  I don't know how to grab those errors and paste them here .. I would have thought the logs might have them .. but these appear to be different.

Others have posted issues with this MB related to both video and sound.  I've been able to get the sound easily fixed using the Realtek drivers .. and I CAN get the nvidia.com drivers to work, both individually .. and using envy.

But I'm hoping that someone here can tell me what the trick is to getting the proprietary driver to fly.  I'd like to use XvMC w/ Mythtv .. and this may be my best hope.

Thanks in advance for your interest and recommendations.

---

### Post by sabhain on 2008-03-31
Ok .. I've captured the  log file obtained by running startx at the command line .. this would seem to me to mean that I'm really close and need to kick my monitor manual around for some valid modes?   But I'm unsure as to why these log files would be so different.  This one at least seems to be trying the nvidia / glx stuff.

```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux Core7989 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686
Build Date: 18 January 2008
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Mar 31 00:38:30 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "nVidia Corporation NVIDIA Default Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81e9800
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,07c1 card 1462,7366 rev a2 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,07cb card 1462,7366 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:01:0: chip 10de,07cd card 1462,7366 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:1: chip 10de,07ce card 1462,7366 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:2: chip 10de,07cf card 1462,7366 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:3: chip 10de,07d0 card 1462,7366 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:4: chip 10de,07d1 card 1462,7366 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:5: chip 10de,07d2 card 1462,7366 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:6: chip 10de,07d3 card 1462,7366 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:02:0: chip 10de,07d6 card 1462,7366 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:03:0: chip 10de,07d7 card 1462,7366 rev a2 class 06,01,00 hdr 80
(II) PCI: 00:03:1: chip 10de,07d8 card 1462,7366 rev a1 class 0c,05,00 hdr 80
(II) PCI: 00:03:2: chip 10de,07d9 card 1462,7366 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:03:3: chip 10de,07da card 1462,7366 rev a2 class 0b,40,00 hdr 80
(II) PCI: 00:03:4: chip 10de,07c8 card 0000,0000 rev a1 class 05,00,00 hdr 80
(II) PCI: 00:04:0: chip 10de,07fe card 1462,7366 rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:04:1: chip 10de,056a card 1462,7366 rev a1 class 0c,03,20 hdr 80
(II) PCI: 00:08:0: chip 10de,056c card 1462,7366 rev a1 class 01,01,8a hdr 00
(II) PCI: 00:09:0: chip 10de,07fc card 1462,7366 rev a1 class 04,03,00 hdr 00
(II) PCI: 00:0a:0: chip 10de,056d card 0000,0000 rev a1 class 06,04,01 hdr 01
(II) PCI: 00:0b:0: chip 10de,056e card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:0c:0: chip 10de,056f card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 10de,056f card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,07f0 card 1462,7366 rev a2 class 01,01,85 hdr 00
(II) PCI: 00:0f:0: chip 10de,07dc card 1462,366c rev a2 class 02,00,00 hdr 00
(II) PCI: 00:10:0: chip 10de,07e1 card 1462,7366 rev a2 class 03,00,00 hdr 00
(II) PCI: 01:06:0: chip 3388,0021 card 0000,0000 rev 11 class 06,04,00 hdr 01
(II) PCI: 01:07:0: chip 104c,8024 card 0000,0000 rev 00 class 0c,00,10 hdr 00
(II) PCI: 02:08:0: chip 4444,0016 card 0070,e807 rev 01 class 04,00,00 hdr 00
(II) PCI: 02:09:0: chip 4444,0016 card 0070,e817 rev 01 class 04,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:3:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:10:0), (0,1,2), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfeb00000 - 0xfebfffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xf4000000 - 0xfbffffff (0x8000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:11:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:12:0), (0,4,4), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:13:0), (0,5,5), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (1:6:0), (1,2,2), BCTRL: 0x0007 (VGA_EN is cleared)
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xf4000000 - 0xfbffffff (0x8000000) MX[B]
(--) PCI:*(0:16:0) nVidia Corporation unknown chipset (0x07e1) rev 162, Mem @ 0xfd000000/24, 0xd0000000/28, 0xfc000000/24, BIOS @ 0xfea40000/17
(--) PCI: (2:8:0) unknown vendor (0x4444) unknown chipset (0x0016) rev 1, Mem @ 0xf8000000/26
(--) PCI: (2:9:0) unknown vendor (0x4444) unknown chipset (0x0016) rev 1, Mem @ 0xf4000000/26
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xfebf8000 - 0xfebfbfff (0x4000) MX[B]
	[1] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[2] -1	0	0xfea7e400 - 0xfea7e40f (0x10) MX[B]
	[3] -1	0	0xfea7e800 - 0xfea7e8ff (0x100) MX[B]
	[4] -1	0	0xfea77000 - 0xfea77fff (0x1000) MX[B]
	[5] -1	0	0xfea7c000 - 0xfea7dfff (0x2000) MX[B]
	[6] -1	0	0xfea78000 - 0xfea7bfff (0x4000) MX[B]
	[7] -1	0	0xfea7ec00 - 0xfea7ecff (0x100) MX[B]
	[8] -1	0	0xfea7f000 - 0xfea7ffff (0x1000) MX[B]
	[9] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[10] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[11] -1	0	0xfea40000 - 0xfea5ffff (0x20000) MX[B](B)
	[12] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] -1	0	0xfea80000 - 0xfeafffff (0x80000) MX[B]
	[16] -1	0	0x0000d880 - 0x0000d887 (0x8) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[18] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[19] -1	0	0x0000e080 - 0x0000e087 (0x8) IX[B]
	[20] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[21] -1	0	0x0000e480 - 0x0000e487 (0x8) IX[B]
	[22] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[23] -1	0	0x00004e00 - 0x00004e3f (0x40) IX[B]
	[24] -1	0	0x00004d00 - 0x00004d3f (0x40) IX[B]
	[25] -1	0	0x00004900 - 0x0000493f (0x40) IX[B]
	[26] -1	0	0x00004f00 - 0x00004fff (0x100) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfebf8000 - 0xfebfbfff (0x4000) MX[B]
	[1] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[2] -1	0	0xfea7e400 - 0xfea7e40f (0x10) MX[B]
	[3] -1	0	0xfea7e800 - 0xfea7e8ff (0x100) MX[B]
	[4] -1	0	0xfea77000 - 0xfea77fff (0x1000) MX[B]
	[5] -1	0	0xfea7c000 - 0xfea7dfff (0x2000) MX[B]
	[6] -1	0	0xfea78000 - 0xfea7bfff (0x4000) MX[B]
	[7] -1	0	0xfea7ec00 - 0xfea7ecff (0x100) MX[B]
	[8] -1	0	0xfea7f000 - 0xfea7ffff (0x1000) MX[B]
	[9] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[10] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[11] -1	0	0xfea40000 - 0xfea5ffff (0x20000) MX[B](B)
	[12] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[15] -1	0	0xfea80000 - 0xfeafffff (0x80000) MX[B]
	[16] -1	0	0x0000d880 - 0x0000d887 (0x8) IX[B]
	[17] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[18] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[19] -1	0	0x0000e080 - 0x0000e087 (0x8) IX[B]
	[20] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[21] -1	0	0x0000e480 - 0x0000e487 (0x8) IX[B]
	[22] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[23] -1	0	0x00004e00 - 0x00004e3f (0x40) IX[B]
	[24] -1	0	0x00004d00 - 0x00004d3f (0x40) IX[B]
	[25] -1	0	0x00004900 - 0x0000493f (0x40) IX[B]
	[26] -1	0	0x00004f00 - 0x00004fff (0x100) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebf8000 - 0xfebfbfff (0x4000) MX[B]
	[5] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[6] -1	0	0xfea7e400 - 0xfea7e40f (0x10) MX[B]
	[7] -1	0	0xfea7e800 - 0xfea7e8ff (0x100) MX[B]
	[8] -1	0	0xfea77000 - 0xfea77fff (0x1000) MX[B]
	[9] -1	0	0xfea7c000 - 0xfea7dfff (0x2000) MX[B]
	[10] -1	0	0xfea78000 - 0xfea7bfff (0x4000) MX[B]
	[11] -1	0	0xfea7ec00 - 0xfea7ecff (0x100) MX[B]
	[12] -1	0	0xfea7f000 - 0xfea7ffff (0x1000) MX[B]
	[13] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[14] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[15] -1	0	0xfea40000 - 0xfea5ffff (0x20000) MX[B](B)
	[16] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[17] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[19] -1	0	0xfea80000 - 0xfeafffff (0x80000) MX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000d880 - 0x0000d887 (0x8) IX[B]
	[23] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[24] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[25] -1	0	0x0000e080 - 0x0000e087 (0x8) IX[B]
	[26] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[27] -1	0	0x0000e480 - 0x0000e487 (0x8) IX[B]
	[28] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[29] -1	0	0x00004e00 - 0x00004e3f (0x40) IX[B]
	[30] -1	0	0x00004d00 - 0x00004d3f (0x40) IX[B]
	[31] -1	0	0x00004900 - 0x0000493f (0x40) IX[B]
	[32] -1	0	0x00004f00 - 0x00004fff (0x100) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  100.14.19  Wed Sep 12 14:48:02 PDT 2007
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) NVIDIA dlloader X Driver  100.14.19  Wed Sep 12 14:14:20 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 00:10:0
(WW) NVIDIA: No matching Device section for instance (BusID PCI:0:3:3) found
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebf8000 - 0xfebfbfff (0x4000) MX[B]
	[5] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[6] -1	0	0xfea7e400 - 0xfea7e40f (0x10) MX[B]
	[7] -1	0	0xfea7e800 - 0xfea7e8ff (0x100) MX[B]
	[8] -1	0	0xfea77000 - 0xfea77fff (0x1000) MX[B]
	[9] -1	0	0xfea7c000 - 0xfea7dfff (0x2000) MX[B]
	[10] -1	0	0xfea78000 - 0xfea7bfff (0x4000) MX[B]
	[11] -1	0	0xfea7ec00 - 0xfea7ecff (0x100) MX[B]
	[12] -1	0	0xfea7f000 - 0xfea7ffff (0x1000) MX[B]
	[13] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[14] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[15] -1	0	0xfea40000 - 0xfea5ffff (0x20000) MX[B](B)
	[16] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[17] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[19] -1	0	0xfea80000 - 0xfeafffff (0x80000) MX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000d880 - 0x0000d887 (0x8) IX[B]
	[23] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[24] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[25] -1	0	0x0000e080 - 0x0000e087 (0x8) IX[B]
	[26] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[27] -1	0	0x0000e480 - 0x0000e487 (0x8) IX[B]
	[28] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[29] -1	0	0x00004e00 - 0x00004e3f (0x40) IX[B]
	[30] -1	0	0x00004d00 - 0x00004d3f (0x40) IX[B]
	[31] -1	0	0x00004900 - 0x0000493f (0x40) IX[B]
	[32] -1	0	0x00004f00 - 0x00004fff (0x100) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebf8000 - 0xfebfbfff (0x4000) MX[B]
	[5] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[6] -1	0	0xfea7e400 - 0xfea7e40f (0x10) MX[B]
	[7] -1	0	0xfea7e800 - 0xfea7e8ff (0x100) MX[B]
	[8] -1	0	0xfea77000 - 0xfea77fff (0x1000) MX[B]
	[9] -1	0	0xfea7c000 - 0xfea7dfff (0x2000) MX[B]
	[10] -1	0	0xfea78000 - 0xfea7bfff (0x4000) MX[B]
	[11] -1	0	0xfea7ec00 - 0xfea7ecff (0x100) MX[B]
	[12] -1	0	0xfea7f000 - 0xfea7ffff (0x1000) MX[B]
	[13] -1	0	0xf4000000 - 0xf7ffffff (0x4000000) MX[B](B)
	[14] -1	0	0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
	[15] -1	0	0xfea40000 - 0xfea5ffff (0x20000) MX[B](B)
	[16] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[17] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[19] -1	0	0xfea80000 - 0xfeafffff (0x80000) MX[B]
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000d880 - 0x0000d887 (0x8) IX[B]
	[26] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[27] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[28] -1	0	0x0000e080 - 0x0000e087 (0x8) IX[B]
	[29] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[30] -1	0	0x0000e480 - 0x0000e487 (0x8) IX[B]
	[31] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[32] -1	0	0x00004e00 - 0x00004e3f (0x40) IX[B]
	[33] -1	0	0x00004d00 - 0x00004d3f (0x40) IX[B]
	[34] -1	0	0x00004900 - 0x0000493f (0x40) IX[B]
	[35] -1	0	0x00004f00 - 0x00004fff (0x100) IX[B]
	[36] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[37] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:0:16:0. 
(EE) NVIDIA(0):     Please see the COMMON PROBLEMS section in the README for
(EE) NVIDIA(0):     additional information.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

---

### Post by ftmichael on 2008-03-31
> I've been able to get the sound easily fixed using the Realtek drivers .. and I CAN get the nvidia.com drivers to work, both individually .. and using envy.

Can you talk me through what you did to get your sound working?  I'm not sure where to get the drivers, or how to get them working, given that Gutsy isn't detecting my (onboard) sound card at all.

Michael

---

### Post by sabhain on 2008-03-31
Sure thing .. I'll do my best.

First, check the output of 'lspci' .. if your board is similar to mine (sounds like the same chipset anyway), you ought to see something like what is reported in:

[http://ubuntuforums.org/showthread.php?t=736933&highlight=nvidia+proprietary+driver]("http://ubuntuforums.org/showthread.php?t=736933&highlight=nvidia+proprietary+driver")

Like the user posted there, I did have to run:  'sudo update-pciids' to get a good list recognizing the nvidia chipsets .. etc.  Actually, my experience in this regard was EXACTLY the same as his/hers.

Don't worry about what the lspci says, and if it doesn't include Realtek .. just keep going.

Get the latest drivers from the realtek.com page for linux.  I think there's only one package for all distributions.

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false#2]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false#2")

Then either sudo or login as root .. extract the package and run the install (./install from within the directory that it extracts to).

You need to make sure you have build-essential installed.  You won't get far without:

```
sudo apt-get install build-essential
```

If yours is like mine, it will hang on the first attempt, due to some missing libraries.  My experience was that it was missing the package "ncurses5-dev" or something like that

so I needed to do a ```
apt-get install libncurses5-dev
``` and then reran the install.

After that, it seems to work pretty well .. goes through a bunch of configs/compiles and ultimately launches a text app interface to finish it out, and when it was done, I had sound with both OSS and ALSA mixers.

Good luck .. it's worth the try .. don't ditch the board.

---

### Post by ftmichael on 2008-03-31
I ran **sudo update-pciids'** and now lspci gives me:
```
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
```

I downloaded the Realtek driver and ran **./install**. It worked for a while, and near the end, I saw this:

```
test -z "/usr/include/alsa/sound" || mkdir -p -- "/usr/include/alsa/sound"
mkdir: cannot create directory `/usr/include/alsa': Permission denied
make[3]: *** [install-alsasoundincludeHEADERS] Error 1
make[3]: Leaving directory `/home/michael/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/include/sound'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/michael/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/include/sound'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/michael/Desktop/realtek-linux-audiopack-4.06a/alsa-lib-1.0.14/include'
make: *** [install-recursive] Error 1
Compile ALSA Utility......
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for cross-compiler... gcc
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for ALSA CFLAGS... 
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 1.0.12... not present.
configure: error: Sufficiently new version of libasound not found.
make: *** No targets specified and no makefile found. Stop.
make: *** No rule to make target `install'. Stop.
cp: cannot create link `/usr/lib64/libasound.so.2': Permission denied
cp: cannot create link `/usr/lib64/libasound.so.2.0.0': Permission denied
cp: cannot stat `/usr/lib/pkgconfig/alsa.pc': No such file or directory
ln: creating symbolic link `/dev/sndstat' to `/proc/asound/oss/sndstat': File exists
cp: cannot create regular file `/usr/share/sounds/alsa/test.wav': Permission denied
Remove Folder.....
./install: 102: alsaconf: not found
```

No text-app interface launched at the end; it just finished and did nothing more.

Running **alsamixer** still gives me:

```
alsamixer: function snd_ctl_open failed for default: No such device
```

Thoughts?

Michael

---

### Post by sabhain on 2008-03-31
are you running the install as root?  

it seems like you need to do:

sudo ./install

Those are permissions errors I think.

---

### Post by ftmichael on 2008-03-31
Silly me.  I re-ran as root; no permissions errors this time, but the last lines were:
```
checking for snd_ctl_open in -lasound... yes
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for initscr in -lncurses... no
checking for initscr in -lcurses... no
configure: error: this packages requires a curses library
make: *** No targets specified and no makefile found. Stop.
make: *** No rule to make target `install'. Stop.
Remove Folder.....
./install: 102: alsaconf: not found
```

(**build-essential** was already installed when I checked prior to installing the driver.)

Again, no text-app interface launched at the end; it just finished and did nothing more.

Running **alsamixer** still gives me:
```
alsamixer: function snd_ctl_open failed for default: No such device
```

---

### Post by sabhain on 2008-03-31
Alright .. you're right on the doorstep here.  This was the exact error I got earlier.

Do this:

```
sudo apt-get install libncurses5-dev
```

and then re-run the install (as sudo).

---

### Post by ftmichael on 2008-03-31
Okay, I did that, and the text-app config bit came up.  It couldn't find my sound card, so I told it to probe.  It told me that probing might make my system unstable, and I told it to go ahead.  It flickered, then gave me a grey box with **Ok** highlighted, but no other text.  I clicked the **Ok** and it took me back to the regular CLI in the terminal.  After all the **./install** output, the terminal had:

```
Remove Folder.....
Building card database..
modinfo: could not find module snd-opl3sa2
modinfo: could not find module snd-cs4236
modinfo: could not find module snd-cs4232
modinfo: could not find module snd-cs4231
modinfo: could not find module snd-es18xx
modinfo: could not find module snd-es1688
modinfo: could not find module snd-sb16
modinfo: could not find module snd-sb8
```

Michael

---

### Post by sabhain on 2008-03-31
Hmmm ...

You're in new territory for me here.  The probing you allowed it to do is for legacy ISA sound items, so you shouldn't have to worry about that.  I also think that the errors listed at the end are related to the ISA probe (just a guess).

And you've done a complete reboot .. no effect?

Very strange.  When the text thing came up, I was able to pick an Nvidia sound controller on that screen .. and then it all worked out.

I think you're really close ..

---

### Post by ftmichael on 2008-03-31
Yep, I rebooted.  No joy.

I thought I wanted **snd-hda-intel** anyway, not any of the modules listed, although I'm not actually certain.  How would I install those though?

Michael

---

### Post by sabhain on 2008-03-31
I'll tell you what .. I just got tired of fighting 7.10 on the graphics driver end of things, and tried the 8.04 beta .. and it found the sound & video right off & configured them correctly on the first install.

I'm not here to promote a beta in a production environment, but you might consider it.

Good luck regardless.

---

### Post by ftmichael on 2008-04-01
Brilliant!  I was hoping that would be the case.  I prefer to wait for the stable release, but I can live for another few weeks without sound as long as I know there's an end in sight!  I'll post back if I have any issues with Hardy.

Thanks so much for your help!

Michael

---

