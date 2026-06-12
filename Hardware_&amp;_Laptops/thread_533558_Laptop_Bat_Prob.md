---
title: "Laptop Bat Prob"
date: 2007-08-24
forum: Hardware &amp; Laptops
---

### Post by neilcavendish on 2007-08-24
Hi all I have a Hi Grade C5514 laptop and when i had a older version of ubuntu on here everything worked great. Since version 6.10 it has not been working. I have been hoping it may have got fixed by now but i have installed the gusty tribe 4 and still no luck. Can some one help me diagnose the problem. I have tryed changing the battery with a brand new one and that also did not work. 

The code line below says there is no file or directory

```
watch cat /proc/acpi/battery/CMB0/state

```

The code line below dose not produce anything

```
acpi -b

```

I also am putting in my dmesg

> 
[    0.000000] Linux version 2.6.22-10-generic (buildd@palmer) (gcc version 4.1.3 20070812 (prerelease) (Ubuntu 4.1.2-15ubuntu2)) #1 SMP Wed Aug 22 08:11:52 GMT 2007 (Ubuntu 2.6.22-10.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000dfd0000 (usable)
[    0.000000]  BIOS-e820: 000000000dfd0000 - 000000000dfdf000 (ACPI data)
[    0.000000]  BIOS-e820: 000000000dfdf000 - 000000000e000000 (ACPI NVS)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 223MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 57296) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    57296
[    0.000000]   HighMem     57296 ->    57296
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    57296
[    0.000000] On node 0 totalpages: 57296
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 415 pages used for memmap
[    0.000000]   Normal zone: 52785 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP 000F59F0, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 0DFD0000, 0030 (r1 A M I  OEMRSDT   1000521 MSFT       97)
[    0.000000] ACPI: FACP 0DFD0200, 0081 (r2 A M I  OEMFACP   1000521 MSFT       97)
[    0.000000] ACPI: DSDT 0DFD0390, 36E9 (r1  0ABCM 0ABCM008        8 INTL  2002026)
[    0.000000] ACPI: FACS 0DFDF000, 0040
[    0.000000] ACPI: OEMB 0DFDF040, 0076 (r1 A M I  AMI_OEM   1000521 MSFT       97)
[    0.000000] ACPI: SSDT 0DFD3A80, 0392 (r1    AMI   CPU1PM        1 INTL  2002026)
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] Allocating PCI resources starting at 10000000 (gap: 0e000000:f2000000)
[    0.000000] Built 1 zonelists.  Total pages: 56849
[    0.000000] Kernel command line: root=UUID=42c94767-7751-4104-b8c3-c9246c58bae3 ro quiet splash
[    0.000000] Found and enabled local APIC!
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 1024 (order: 10, 4096 bytes)
[    0.000000] Detected 1600.105 MHz processor.
[   15.922496] Console: colour VGA+ 80x25
[   15.922625] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   15.922731] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   15.927724] Memory: 215700k/229184k available (2010k kernel code, 12904k reserved, 917k data, 364k init, 0k highmem)
[   15.927734] virtual kernel memory layout:
[   15.927735]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   15.927737]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   15.927738]     vmalloc : 0xce800000 - 0xff7fe000   ( 783 MB)
[   15.927740]     lowmem  : 0xc0000000 - 0xcdfd0000   ( 223 MB)
[   15.927741]       .init : 0xc03e1000 - 0xc043c000   ( 364 kB)
[   15.927742]       .data : 0xc02f69c6 - 0xc03dbe64   ( 917 kB)
[   15.927744]       .text : 0xc0100000 - 0xc02f69c6   (2010 kB)
[   15.927748] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   15.927806] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   16.007715] Calibrating delay using timer specific routine.. 3202.60 BogoMIPS (lpj=6405204)
[   16.007754] Security Framework v1.0.0 initialized
[   16.007768] SELinux:  Disabled at boot.
[   16.007786] Mount-cache hash table entries: 512
[   16.007976] CPU: After generic identify, caps: afe9fbbf 00000000 00000000 00000000 00000180 00000000 00000000
[   16.007993] CPU: L1 I cache: 32K, L1 D cache: 32K
[   16.007996] CPU: L2 cache: 2048K
[   16.008000] CPU: After all inits, caps: afe9fbbf 00000000 00000000 00002040 00000180 00000000 00000000
[   16.008012] Compat vDSO mapped to ffffe000.
[   16.008031] Checking 'hlt' instruction... OK.
[   16.023823] SMP alternatives: switching to UP code
[   16.024096] Freeing SMP alternatives: 11k freed
[   16.024410] Early unpacking initramfs... done
[   16.393230] ACPI: Core revision 20070126
[   16.393304] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   16.395115] ACPI: setting ELCR to 0200 (from 0c00)
[   16.490823] CPU0: Intel(R) Pentium(R) M processor 1.60GHz stepping 06
[   16.490830] SMP motherboard not detected.
[   16.594908] Brought up 1 CPUs
[   16.595043] Booting paravirtualized kernel on bare hardware
[   16.595116] Time:  7:22:14  Date: 07/24/107
[   16.595140] NET: Registered protocol family 16
[   16.595235] EISA bus registered
[   16.595250] ACPI: bus type pci registered
[   16.596501] PCI: Using configuration type 1
[   16.596503] Setting up standard PCI resources
[   16.606408] ACPI: EC: Look up EC in DSDT
[   16.607170] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
[   16.608789] ACPI: Interpreter enabled
[   16.608792] ACPI: (supports S0 S1 S3 S4 S5)
[   16.608811] ACPI: Using PIC for interrupt routing
[   16.620995] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
[   16.621087] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   16.621099] PCI: Probing PCI hardware (bus 00)
[   16.621578] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[   16.621582] PCI quirk: region 0500-053f claimed by ICH4 GPIO
[   16.621972] PCI: Transparent bridge - 0000:00:1e.0
[   16.622025] PCI: Bus #02 (-#05) is hidden behind transparent bridge #01 (-#01) (try 'pci=assign-busses')
[   16.622028] Please report the result to linux-kernel to fix this permanently
[   16.622045] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   16.622173] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   16.624029] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12)
[   16.624175] ACPI: PCI Interrupt Link [LNKB] (IRQs *11)
[   16.624315] ACPI: PCI Interrupt Link [LNKC] (IRQs *10)
[   16.624454] ACPI: PCI Interrupt Link [LNKD] (IRQs *10)
[   16.624592] ACPI: PCI Interrupt Link [LNKE] (IRQs 11) *0, disabled.
[   16.624732] ACPI: PCI Interrupt Link [LNKF] (IRQs *11)
[   16.624870] ACPI: PCI Interrupt Link [LNKG] (IRQs *11)
[   16.625009] ACPI: PCI Interrupt Link [LNKH] (IRQs *10)
[   16.625113] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.625124] pnp: PnP ACPI init
[   16.625131] ACPI: bus type pnp registered
[   16.631485] pnp: PnP ACPI: found 13 devices
[   16.631487] ACPI: ACPI bus type pnp unregistered
[   16.631491] PnPBIOS: Disabled by ACPI PNP
[   16.631535] PCI: Using ACPI for IRQ routing
[   16.631538] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.631607] NET: Registered protocol family 8
[   16.631610] NET: Registered protocol family 20
[   16.631666] pnp: 00:08: ioport range 0x600-0x67f has been reserved
[   16.631673] pnp: 00:0a: ioport range 0x6a0-0x6a0 has been reserved
[   16.631676] pnp: 00:0a: ioport range 0x1100-0x113f has been reserved
[   16.631679] pnp: 00:0a: ioport range 0x1254-0x1254 has been reserved
[   16.631682] pnp: 00:0a: ioport range 0x12d4-0x12d4 has been reserved
[   16.631685] pnp: 00:0a: ioport range 0x1300-0x1375 has been reserved
[   16.631688] pnp: 00:0a: ioport range 0x1377-0x137f has been reserved
[   16.631691] pnp: 00:0a: ioport range 0x1376-0x1376 has been reserved
[   16.631695] pnp: 00:0a: iomem range 0xfff00000-0xffffffff has been reserved
[   16.631698] pnp: 00:0a: iomem range 0xffb00000-0xffbfffff has been reserved
[   16.631701] pnp: 00:0a: iomem range 0x0-0x0 could not be reserved
[   16.631704] pnp: 00:0a: iomem range 0x0-0x0 could not be reserved
[   16.631710] pnp: 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   16.631713] pnp: 00:0c: iomem range 0xc0000-0xdffff could not be reserved
[   16.631716] pnp: 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[   16.631720] pnp: 00:0c: iomem range 0x100000-0xdffffff could not be reserved
[   16.634813] Time: tsc clocksource has been installed.
[   16.661952] PCI: Bus 2, cardbus bridge: 0000:01:04.0
[   16.661954]   IO window: 0000c000-0000c0ff
[   16.661959]   IO window: 0000c400-0000c4ff
[   16.661963]   PREFETCH window: 10000000-13ffffff
[   16.661968]   MEM window: 18000000-1bffffff
[   16.661972] PCI: Bridge: 0000:00:1e.0
[   16.661975]   IO window: c000-cfff
[   16.661981]   MEM window: e0000000-e00fffff
[   16.661986]   PREFETCH window: 10000000-13ffffff
[   16.662000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   16.662197] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[   16.662200] PCI: setting IRQ 11 as level-triggered
[   16.662204] ACPI: PCI Interrupt 0000:01:04.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[   16.662211] PCI: Setting latency timer of device 0000:01:04.0 to 64
[   16.662222] NET: Registered protocol family 2
[   16.698753] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   16.698796] TCP established hash table entries: 8192 (order: 4, 98304 bytes)
[   16.698891] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   16.698953] TCP: Hash tables configured (established 8192 bind 8192)
[   16.698956] TCP reno registered
[   16.710818] checking if image is initramfs... it is
[   17.162053] Switched to high resolution mode on CPU 0
[   17.422623] Freeing initrd memory: 7043k freed
[   17.423096] audit: initializing netlink socket (disabled)
[   17.423118] audit(1187940134.012:1): initialized
[   17.425063] VFS: Disk quotas dquot_6.5.1
[   17.425112] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   17.425216] io scheduler noop registered
[   17.425219] io scheduler anticipatory registered
[   17.425221] io scheduler deadline registered
[   17.425237] io scheduler cfq registered (default)
[   17.425254] Boot video device is 0000:00:02.0
[   17.425500] isapnp: Scanning for PnP cards...
[   17.778781] isapnp: No Plug & Play device found
[   17.802979] Real Time Clock Driver v1.12ac
[   17.803103] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   17.804016] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[   17.804021] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   17.804030] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[   17.804588] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   17.804813] input: Macintosh mouse button emulation as /class/input/input0
[   17.804892] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f12:PS2M] at 0x60,0x64 irq 1,12
[   17.812728] i8042.c: Detected active multiplexing controller, rev 1.1.
[   17.816680] serio: i8042 KBD port at 0x60,0x64 irq 1
[   17.816685] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   17.816688] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   17.816691] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   17.816693] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   17.816860] mice: PS/2 mouse device common for all mice
[   17.817351] EISA: Probing bus 0 at eisa.0
[   17.817389] EISA: Detected 0 cards.
[   17.817499] TCP cubic registered
[   17.817518] NET: Registered protocol family 1
[   17.817572] Testing NMI watchdog ... OK.
[   17.896884] Using IPI No-Shortcut mode
[   17.897055]   Magic number: 3:379:370
[   17.897405] Freeing unused kernel memory: 364k freed
[   18.061567] input: AT Translated Set 2 keyboard as /class/input/input1
[   19.092076] AppArmor: AppArmor initialized
[   19.092085] audit(1187940135.512:2): AppArmor initialized
[   19.092086] 
[   19.095233] AppArmor: Registered secondary security module: capability.
[   19.095236] Capability LSM initialized as secondary
[   19.102698] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   19.102704] ACPI: Processor [CPU1] (supports 8 throttling states)
[   19.491123] usbcore: registered new interface driver usbfs
[   19.491149] usbcore: registered new interface driver hub
[   19.491169] usbcore: registered new device driver usb
[   19.491985] USB Universal Host Controller Interface driver v3.0
[   19.492316] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[   19.492320] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   19.492332] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   19.492336] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   19.492550] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   19.492573] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000d800
[   19.492678] usb usb1: configuration #1 chosen from 1 choice
[   19.492701] hub 1-0:1.0: USB hub found
[   19.492705] hub 1-0:1.0: 2 ports detected
[   19.556436] SCSI subsystem initialized
[   19.561885] libata version 2.21 loaded.
[   19.594595] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[   19.594600] PCI: setting IRQ 10 as level-triggered
[   19.594604] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[   19.594616] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   19.594620] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   19.594649] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   19.594674] uhci_hcd 0000:00:1d.1: irq 10, io base 0x0000d880
[   19.594768] usb usb2: configuration #1 chosen from 1 choice
[   19.594792] hub 2-0:1.0: USB hub found
[   19.594798] hub 2-0:1.0: 2 ports detected
[   19.691118] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   19.698461] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[   19.698466] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   19.698479] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   19.698483] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   19.698508] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   19.698532] uhci_hcd 0000:00:1d.2: irq 10, io base 0x0000dc00
[   19.698638] usb usb3: configuration #1 chosen from 1 choice
[   19.698664] hub 3-0:1.0: USB hub found
[   19.698670] hub 3-0:1.0: 2 ports detected
[   19.802715] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[   19.802722] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[   19.802737] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   19.802741] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   19.802769] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[   19.802802] ehci_hcd 0000:00:1d.7: debug port 1
[   19.802809] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   19.802817] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xe037f400
[   19.806686] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   19.806772] usb usb4: configuration #1 chosen from 1 choice
[   19.806802] hub 4-0:1.0: USB hub found
[   19.806809] hub 4-0:1.0: 6 ports detected
[   19.909926] ata_piix 0000:00:1f.1: version 2.11
[   19.909942] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[   19.909952] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   19.909985] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   19.910074] scsi0 : ata_piix
[   19.923449] scsi1 : ata_piix
[   19.923494] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001ffa0 irq 14
[   19.923499] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001ffa8 irq 15
[    3.880000] Marking TSC unstable due to: possible TSC halt in C2.
[    3.904000] Time: acpi_pm clocksource has been installed.
[    3.968000] ata1.00: ATA-6: IC25N040ATMR04-0, MO2OAD4A, max UDMA/100
[    3.968000] ata1.00: 78140160 sectors, multi 16: LBA48 
[    3.968000] ata1.00: limited to UDMA/33 due to 40-wire cable
[    3.984000] ata1.00: configured for UDMA/33
[    4.304000] ata2.00: ATAPI: SONY CD-RW/DVD-ROM CRX830E, JYK3, max UDMA/33
[    4.476000] ata2.00: configured for UDMA/33
[    4.476000] scsi 0:0:0:0: Direct-Access     ATA      IC25N040ATMR04-0 MO2O PQ: 0 ANSI: 5
[    4.476000] scsi 1:0:0:0: CD-ROM            SONY     CD-RW  CRX830E   JYK3 PQ: 0 ANSI: 5
[    4.476000] 8139cp 0000:01:03.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    4.476000] 8139cp 0000:01:03.0: Try the "8139too" driver instead.
[    4.480000] 8139too Fast Ethernet driver 0.9.28
[    4.480000] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 11
[    4.480000] ACPI: PCI Interrupt 0000:01:03.0[A] -> Link [LNKG] -> GSI 11 (level, low) -> IRQ 11
[    4.480000] eth0: RealTek RTL8139 at 0xce82e400, 00:11:5b:46:ce:68, IRQ 11
[    4.480000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    4.480000] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 11
[    4.480000] ACPI: PCI Interrupt 0000:01:04.1[B] -> Link [LNKF] -> GSI 11 (level, low) -> IRQ 11
[    4.532000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[11]  MMIO=[e00ff800-e00fffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.556000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    4.556000] sd 0:0:0:0: [sda] Write Protect is off
[    4.556000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.556000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.556000] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[    4.556000] sd 0:0:0:0: [sda] Write Protect is off
[    4.556000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.556000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.556000]  sda: sda1 sda2 < sda5 >
[    4.608000] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.612000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.612000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.624000] sr0: scsi3-mmc drive: 0x/24x writer cd/rw xa/form2 cdda tray
[    4.624000] Uniform CD-ROM driver Revision: 3.20
[    4.624000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.876000] Attempting manual resume
[    4.876000] swsusp: Resume From Partition 8:5
[    4.876000] PM: Checking swsusp image.
[    4.876000] PM: Resume from disk failed.
[    4.888000] EXT3-fs: INFO: recovery required on readonly filesystem.
[    4.888000] EXT3-fs: write access will be enabled during recovery.
[    5.812000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00000ae6ff2496fd]
[    7.788000] kjournald starting.  Commit interval 5 seconds
[    7.788000] EXT3-fs: recovery complete.
[    7.792000] EXT3-fs: mounted filesystem with ordered data mode.
[   20.268000] eth0: link down
[   21.304000] Linux agpgart interface v0.102 (c) Dave Jones
[   21.348000] agpgart: Detected an Intel 855GM Chipset.
[   21.348000] agpgart: Detected 32636K stolen memory.
[   21.356000] agpgart: AGP aperture is 128M @ 0xd8000000
[   21.536000] iTCO_vendor_support: vendor-support=0
[   21.556000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   21.556000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x0460)
[   21.556000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   21.752000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   21.756000] NET: Registered protocol family 17
[   22.032000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   22.060000] intel_rng: FWH not detected
[   22.544000] input: PC Speaker as /class/input/input2
[   22.792000] ieee80211_crypt: registered algorithm 'NULL'
[   22.816000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   22.816000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   22.860000] Yenta: CardBus bridge found at 0000:01:04.0 [1019:0f44]
[   22.940000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   22.940000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   22.992000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x1d6eb1, caps: 0xa04713/0x4006
[   23.020000] Yenta: ISA IRQ mask 0x0038, PCI irq 11
[   23.020000] Socket status: 30000006
[   23.020000] Yenta: Raising subordinate bus# of parent bus (#01) from #01 to #05
[   23.020000] pcmcia: parent PCI bridge I/O window: 0xc000 - 0xcfff
[   23.020000] cs: IO port probe 0xc000-0xcfff: clean.
[   23.020000] pcmcia: parent PCI bridge Memory window: 0xe0000000 - 0xe00fffff
[   23.020000] pcmcia: parent PCI bridge Memory window: 0x10000000 - 0x13ffffff
[   23.020000] ACPI: PCI Interrupt 0000:01:02.0[A] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   23.020000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   23.036000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   23.040000] parport_pc 00:07: reported by Plug and Play ACPI
[   23.040000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   23.268000] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)
[   23.640000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   23.640000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   23.692000] cs: IO port probe 0x100-0x3af: clean.
[   23.696000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   23.696000] cs: IO port probe 0x820-0x8ff: clean.
[   23.696000] cs: IO port probe 0xc00-0xcf7: clean.
[   23.696000] cs: IO port probe 0xa00-0xaff: clean.
[   24.468000] intel8x0_measure_ac97_clock: measured 55394 usecs
[   24.468000] intel8x0: clocking to 48000
[   24.536000] Clocksource tsc unstable (delta = -132003972 ns)
[   25.020000] fuse init (API version 7.8)
[   25.048000] lp0: using parport0 (interrupt-driven).
[   25.132000] Adding 650592k swap on /dev/sda5.  Priority:-1 extents:1 across:650592k
[   25.436000] EXT3 FS on sda1, internal journal
[   25.640000] AppArmor: Unregistered secondary security module: capability
[   29.760000] ACPI: Battery Slot [BAT0] (battery absent)
[   30.368000] No dock devices found.
[   30.476000] input: Power Button (FF) as /class/input/input4
[   30.476000] ACPI: Power Button (FF) [PWRF]
[   30.544000] input: Power Button (CM) as /class/input/input5
[   30.548000] ACPI: Power Button (CM) [PWRB]
[   30.588000] input: Lid Switch as /class/input/input6
[   30.588000] ACPI: Lid Switch [LID0]
[   30.600000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   30.632000] ACPI: AC Adapter [ADP0] (on-line)
[   32.620000] ppdev: user-space parallel port driver
[   33.048000] audit(1187940166.983:3): REJECTING m access to /etc/passwd (cupsd(4687) profile /usr/sbin/cupsd active /usr/sbin/cupsd)
[   33.052000] audit(1187940166.983:4): REJECTING m access to /etc/group (cupsd(4687) profile /usr/sbin/cupsd active /usr/sbin/cupsd)
[   33.052000] audit(1187940166.983:5): REJECTING m access to /etc/group (cupsd(4687) profile /usr/sbin/cupsd active /usr/sbin/cupsd)
[   33.240000] audit(1187940166.983:6): REJECTING w access to /dev/tty (cupsd(4687) profile /usr/sbin/cupsd active /usr/sbin/cupsd)
[   33.376000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   33.376000] apm: overridden by ACPI.
[   33.556000] AppArmor: Registered secondary security module: capability.
[   33.556000] Capability LSM initialized as secondary
[   33.864000] Bluetooth: Core ver 2.11
[   33.864000] NET: Registered protocol family 31
[   33.864000] Bluetooth: HCI device and connection manager initialized
[   33.864000] Bluetooth: HCI socket layer initialized
[   33.916000] Bluetooth: L2CAP ver 2.8
[   33.916000] Bluetooth: L2CAP socket layer initialized
[   34.080000] Bluetooth: RFCOMM socket layer initialized
[   34.080000] Bluetooth: RFCOMM TTY layer initialized
[   34.080000] Bluetooth: RFCOMM ver 1.8
[   35.636000] [drm] Initialized drm 1.1.0 20060810
[   35.640000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   35.640000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   35.644000] [drm] Initialized i915 1.6.0 20060119 on minor 1
[   62.852000] NET: Registered protocol family 10
[   62.852000] lo: Disabled Privacy Extensions
[   62.852000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   73.248000] eth1: no IPv6 routers present
[  202.180000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  211.824000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  231.464000] eth1: no IPv6 routers present
[  349.256000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  349.256000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  368.500000] eth0: no IPv6 routers present
[  568.608000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1387.316000] eth0: link down
[ 1390.664000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1390.664000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1392.732000] eth0: link down
[ 1394.384000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[ 1394.388000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1412.136000] eth0: no IPv6 routers present


If anymore information is needed please ask cheers in advance.

---

