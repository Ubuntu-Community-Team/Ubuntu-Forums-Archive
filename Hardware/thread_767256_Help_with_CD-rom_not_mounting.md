---
title: "Help with CD-rom not mounting"
date: 2008-04-25
forum: Hardware
---

### Post by MinMaxMcgee on 2008-04-25
When I click the CD-ROM 1 icon
I get the message
"Unable to mount image.  
mount: special device /dev/scd0 does not exist"  

After looking at a couple of other threads I found that this information may help you help me.  

The computer is a Compaq Presario V5207 laptop 

```
[    0.000000] Linux version 2.6.22-14-generic (buildd@palmer) (gcc version 4.1.
3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:05:12 GMT
 2007 (Ubuntu 2.6.22-14.46-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000005f680000 (usable)
[    0.000000]  BIOS-e820: 000000005f680000 - 000000005f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000005f700000 - 0000000060000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 630MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f65b0
[    0.000000] Entering add_active_range(0, 0, 390784) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   390784
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   390784
[    0.000000] On node 0 totalpages: 390784
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1261 pages used for memmap
[    0.000000]   HighMem zone: 160147 pages, LIFO batch:31
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6580 checksum 0
[    0.000000] ACPI: RSDP 000F6580, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 5F68D153, 0048 (r1 PTLTD  Capell00  6040000  LTP      
  0)
[    0.000000] ACPI: FACP 5F693DFC, 0074 (r1 HP     NISSAN    6040000 LOHR      
 5A)
[    0.000000] ACPI: DSDT 5F68DA7B, 6381 (r1 HP     NISSAN    6040000 INTL 20060
217)
[    0.000000] ACPI: FACS 5F694FC0, 0040
[    0.000000] ACPI: APIC 5F693E70, 0068 (r1 HP     NISSAN    6040000 LOHR      
 5A)
[    0.000000] ACPI: HPET 5F693ED8, 0038 (r1 HP     NISSAN    6040000 LOHR      
 5A)
[    0.000000] ACPI: MCFG 5F693F10, 003C (r1 HP     NISSAN    6040000 LOHR      
 5A)
[    0.000000] ACPI: BOOT 5F693FD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP      
  1)
[    0.000000] ACPI: APIC 5F693F7E, 005A (r1 PTLTD       APIC    6040000  LTP   
     0)
[    0.000000] ACPI: SSDT 5F68D86D, 020A (r1 SataRe SataAhci     1000 INTL 20060
217)
[    0.000000] ACPI: SSDT 5F68D691, 01DC (r1  PmRef  Cpu0Cst     3001 INTL 20060
217)
[    0.000000] ACPI: SSDT 5F68D19B, 04F6 (r1  PmRef    CpuPm     3000 INTL 20060
217)
[    0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
[    0.000000] ACPI: If "acpi_apic_instance=2" works better, notify linux-acpi@v
ger.kernel.org
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:14 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 68000000 (gap: 60000000:8000
0000)
[    0.000000] Built 1 zonelists.  Total pages: 387731
[    0.000000] Kernel command line: root=UUID=e1eb9190-8eaa-4682-aecd-ddf6d46a6e
40 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1463.184 MHz processor.
[   13.955126] Console: colour VGA+ 80x25
[   13.955418] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   13.955845] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   14.044040] Memory: 1537608k/1563136k available (2015k kernel code, 24256k re
served, 916k data, 364k init, 645632k highmem)
[   14.044052] virtual kernel memory layout:
[   14.044053]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   14.044055]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   14.044056]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   14.044058]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   14.044059]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   14.044061]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   14.044062]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   14.044067] Checking if this processor honours the WP bit even in supervisor 
mode... Ok.
[   14.044112] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, N
odes=1
[   14.044282] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   14.044288] hpet0: 3 64-bit timers, 14318180 Hz
[   14.125203] Calibrating delay using timer specific routine.. 2929.39 BogoMIPS
 (lpj=5858782)
[   14.125231] Security Framework v1.0.0 initialized
[   14.125242] SELinux:  Disabled at boot.
[   14.125258] Mount-cache hash table entries: 512
[   14.125411] CPU: After generic identify, caps: afe9fbff 00100000 00000000 000
00000 0000c109 00000000 00000000
[   14.125421] monitor/mwait feature present.
[   14.125423] using mwait in idle threads.
[   14.125428] CPU: L1 I cache: 32K, L1 D cache: 32K
[   14.125431] CPU: L2 cache: 1024K
[   14.125436] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002940 0
000c109 00000000 00000000
[   14.125447] Compat vDSO mapped to ffffe000.
[   14.125462] Checking 'hlt' instruction... OK.
[   14.141323] SMP alternatives: switching to UP code
[   14.141568] Freeing SMP alternatives: 11k freed
[   14.141892] Early unpacking initramfs... done
[   14.554329] ACPI: Core revision 20070126
[   14.554410] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not 
found.
[   14.590112] CPU0: Intel(R) Celeron(R) M CPU        410  @ 1.46GHz stepping 08
[   14.590143] Total of 1 processors activated (2929.39 BogoMIPS).
[   14.590341] ENABLING IO-APIC IRQs
[   14.590552] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   14.736426] Brought up 1 CPUs
[   14.736546] Booting paravirtualized kernel on bare hardware
[   14.736637] Time: 17:59:09  Date: 03/25/108
[   14.736663] NET: Registered protocol family 16
[   14.736750] EISA bus registered
[   14.736755] ACPI: bus type pci registered
[   14.736896] PCI: PCI BIOS revision 2.10 entry at 0xfd873, last bus=8
[   14.736899] PCI: Using configuration type 1
[   14.736901] Setting up standard PCI resources
[   14.739435] ACPI: EC: Look up EC in DSDT
[   14.740184] ACPI: EC: GPE=0x19, ports=0x66, 0x62
[   14.741599] ACPI: System BIOS is requesting _OSI(Linux)
[   14.741602] ACPI: Please test with "acpi_osi=!Linux"
[   14.741603] Please send dmidecode to linux-acpi@vger.kernel.org
[   14.742085] ACPI: Interpreter enabled
[   14.742089] ACPI: (supports S0 S3 S4 S5)
[   14.742107] ACPI: Using IOAPIC for interrupt routing
[   14.789630] ACPI: EC: GPE=0x19, ports=0x66, 0x62
[   14.789690] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   14.789705] PCI: Probing PCI hardware (bus 00)
[   14.790491] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   14.790496] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   14.791346] PCI: Firmware left 0000:08:08.0 e100 interrupts enabled, disablin
g
[   14.791441] PCI: Transparent bridge - 0000:00:1e.0
[   14.791521] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   14.791884] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   14.792026] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   14.792166] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   14.792327] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   14.795606] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *1
1
[   14.795715] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 *4 5 6 7 11 12 14 15)
[   14.795820] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[   14.795923] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *1
0
[   14.796026] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 *6 7 10 12 14 15)
[   14.796129] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0
, disabled.
[   14.796233] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[   14.796342] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[   14.796459] Linux Plug and Play Support v0.97 (c) Adam Belay
[   14.796475] pnp: PnP ACPI init
[   14.796486] ACPI: bus type pnp registered
[   14.816926] pnp: PnP ACPI: found 10 devices
[   14.816928] ACPI: ACPI bus type pnp unregistered
[   14.816933] PnPBIOS: Disabled by ACPI PNP
[   14.816981] PCI: Using ACPI for IRQ routing
[   14.816984] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, 
post a report
[   14.816989] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[   14.817056] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[   14.817120] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[   14.817183] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[   14.817246] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[   14.817310] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[   14.817412] PCI: Cannot allocate resource region 0 of device 0000:06:00.0
[   14.838078] NET: Registered protocol family 8
[   14.838081] NET: Registered protocol family 20
[   14.838139] pnp: 00:01: iomem range 0xe0000000-0xefffffff could not be reserv
ed
[   14.838144] pnp: 00:01: iomem range 0xfed14000-0xfed17fff could not be reserv
ed
[   14.838148] pnp: 00:01: iomem range 0xfed18000-0xfed18fff could not be reserv
ed
[   14.838151] pnp: 00:01: iomem range 0xfed19000-0xfed19fff could not be reserv
ed
[   14.838159] pnp: 00:04: iomem range 0xfed00000-0xfed003ff could not be reserv
ed
[   14.840248] Time: tsc clocksource has been installed.
[   14.840265] Switched to high resolution mode on CPU 0
[   14.868477] PCI: Bridge: 0000:00:1c.0
[   14.868479]   IO window: disabled.
[   14.868486]   MEM window: disabled.
[   14.868491]   PREFETCH window: disabled.
[   14.868497] PCI: Bridge: 0000:00:1c.1
[   14.868498]   IO window: disabled.
[   14.868504]   MEM window: disabled.
[   14.868509]   PREFETCH window: disabled.
[   14.868529] PCI: Bridge: 0000:00:1c.2
[   14.868530]   IO window: disabled.
[   14.868537]   MEM window: 68000000-680fffff
[   14.868542]   PREFETCH window: disabled.
[   14.868549] PCI: Bridge: 0000:00:1e.0
[   14.868552]   IO window: 2000-2fff
[   14.868558]   MEM window: d0100000-d01fffff
[   14.868563]   PREFETCH window: disabled.
[   14.868595] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ
 16
[   14.868604] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   14.868631] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ
 17
[   14.868639] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   14.868663] PCI: Enabling device 0000:00:1c.2 (0100 -> 0102)
[   14.868668] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ
 18
[   14.868676] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   14.868691] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   14.868706] NET: Registered protocol family 2
[   14.908163] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   14.908233] TCP established hash table entries: 131072 (order: 8, 1572864 byt
es)
[   14.909602] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   14.910127] TCP: Hash tables configured (established 131072 bind 65536)
[   14.910131] TCP reno registered
[   14.920302] checking if image is initramfs... it is
[   15.733268] Freeing initrd memory: 7347k freed
[   15.733406] Simple Boot Flag at 0x36 set to 0x1
[   15.733797] audit: initializing netlink socket (disabled)
[   15.733812] audit(1209146349.160:1): initialized
[   15.733889] highmem bounce pool size: 64 pages
[   15.735952] VFS: Disk quotas dquot_6.5.1
[   15.736010] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   15.736109] io scheduler noop registered
[   15.736112] io scheduler anticipatory registered
[   15.736115] io scheduler deadline registered
[   15.736132] io scheduler cfq registered (default)
[   15.736147] Boot video device is 0000:00:02.0
[   23.725013] 0000:00:1d.7 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[   23.725227] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   23.725287] assign_interrupt_mode Found MSI capability
[   23.725291] Allocate Port Service[0000:00:1c.0:pcie00]
[   23.725327] Allocate Port Service[0000:00:1c.0:pcie02]
[   23.725430] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   23.725490] assign_interrupt_mode Found MSI capability
[   23.725493] Allocate Port Service[0000:00:1c.1:pcie00]
[   23.725525] Allocate Port Service[0000:00:1c.1:pcie02]
[   23.725625] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   23.725684] assign_interrupt_mode Found MSI capability
[   23.725687] Allocate Port Service[0000:00:1c.2:pcie00]
[   23.725723] Allocate Port Service[0000:00:1c.2:pcie02]
[   23.725888] isapnp: Scanning for PnP cards...
[   24.079888] isapnp: No Plug & Play device found
[   24.106305] Real Time Clock Driver v1.12ac
[   24.106535] hpet_resources: 0xfed00000 is busy
[   24.106561] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing 
enabled
[   24.107842] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 bloc
ksize
[   24.108073] input: Macintosh mouse button emulation as /class/input/input0
[   24.108160] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq
 1,12
[   24.128197] i8042.c: Detected active multiplexing controller, rev 1.1.
[   24.146061] serio: i8042 KBD port at 0x60,0x64 irq 1
[   24.146067] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   24.146071] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   24.146074] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   24.146077] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   24.146288] mice: PS/2 mouse device common for all mice
[   24.148632] EISA: Probing bus 0 at eisa.0
[   24.148640] Cannot allocate resource for EISA slot 1
[   24.148644] Cannot allocate resource for EISA slot 2
[   24.148671] EISA: Detected 0 cards.
[   24.148779] TCP cubic registered
[   24.148796] NET: Registered protocol family 1
[   24.148822] Using IPI No-Shortcut mode
[   24.148986]   Magic number: 4:113:998
[   24.149012]   hash matches device ttyae
[   24.149185]   hash matches device 00:00
[   24.149364] Freeing unused kernel memory: 364k freed
[   24.203778] input: AT Translated Set 2 keyboard as /class/input/input1
[   25.395651] AppArmor: AppArmor initialized<5>audit(1209146359.160:2):  type=1
505 info="AppArmor initialized" pid=1212
[   25.402410] fuse init (API version 7.8)
[   25.407437] Failure registering capabilities with primary security module.
[   25.428272] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   25.428280] ACPI: Processor [CPU0] (supports 8 throttling states)
[   25.428293] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Dev
ice is not present [20070126]
[   25.440809] ACPI: Thermal Zone [TZ01] (36 C)
[   25.440949] ACPI: Thermal Zone [TZ02] (27 C)
[   26.027719] usbcore: registered new interface driver usbfs
[   26.027745] usbcore: registered new interface driver hub
[   26.027767] usbcore: registered new device driver usb
[   26.028681] USB Universal Host Controller Interface driver v3.0
[   26.028753] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ
 19
[   26.028765] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   26.028770] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   26.028958] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus numbe
r 1
[   26.028994] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001820
[   26.029122] usb usb1: configuration #1 chosen from 1 choice
[   26.029150] hub 1-0:1.0: USB hub found
[   26.029157] hub 1-0:1.0: 2 ports detected
[   26.122337] SCSI subsystem initialized
[   26.128497] libata version 2.21 loaded.
[   26.130386] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ
 20
[   26.130399] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   26.130404] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   26.130434] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus numbe
r 2
[   26.130470] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001840
[   26.130576] usb usb2: configuration #1 chosen from 1 choice
[   26.130604] hub 2-0:1.0: USB hub found
[   26.130611] hub 2-0:1.0: 2 ports detected
[   26.155705] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k4-NAPI
[   26.155709] e100: Copyright(c) 1999-2006 Intel Corporation
[   26.233999] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ
 18
[   26.234014] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   26.234018] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   26.234048] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus numbe
r 3
[   26.234086] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[   26.234196] usb usb3: configuration #1 chosen from 1 choice
[   26.234225] hub 3-0:1.0: USB hub found
[   26.234231] hub 3-0:1.0: 2 ports detected
[   12.160000] Marking TSC unstable due to: possible TSC halt in C2.
[   12.164000] Time: hpet clocksource has been installed.
[   12.172000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ
 17
[   12.172000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   12.172000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   12.172000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus numbe
r 4
[   12.172000] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[   12.172000] usb usb4: configuration #1 chosen from 1 choice
[   12.172000] hub 4-0:1.0: USB hub found
[   12.172000] hub 4-0:1.0: 2 ports detected
[   12.276000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ
 19
[   12.276000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   12.276000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   12.276000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus numbe
r 5
[   12.276000] ehci_hcd 0000:00:1d.7: debug port 1
[   12.276000] PCI: cache line size of 32 is not supported by device 0000:00:1d.
7
[   12.276000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xd0544000
[   12.280000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 
2004
[   12.280000] usb usb5: configuration #1 chosen from 1 choice
[   12.280000] hub 5-0:1.0: USB hub found
[   12.280000] hub 5-0:1.0: 8 ports detected
[   12.384000] ata_piix 0000:00:1f.1: version 2.11
[   12.384000] ACPI: PCI Interrupt 0000:00:1f.1[B] -> GSI 19 (level, low) -> IRQ
 20
[   12.384000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   12.384000] scsi0 : ata_piix
[   12.384000] scsi1 : ata_piix
[   12.384000] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000
11810 irq 14
[   12.384000] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x000
11818 irq 15
[   12.500000] Clocksource tsc unstable (delta = -127315813 ns)
[   12.552000] ata2: port disabled. ignoring.
[   12.552000] ahci 0000:00:1f.2: version 2.2
[   12.552000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ
 20
[   13.556000] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 1.5 Gbps 0xf i
mpl SATA mode
[   13.556000] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[   13.556000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   13.556000] scsi2 : ahci
[   13.556000] scsi3 : ahci
[   13.556000] scsi4 : ahci
[   13.556000] scsi5 : ahci
[   13.556000] ata3: SATA max UDMA/133 cmd 0xf8846500 ctl 0x00000000 bmdma 0x000
00000 irq 20
[   13.556000] ata4: SATA max UDMA/133 cmd 0xf8846580 ctl 0x00000000 bmdma 0x000
00000 irq 20
[   13.556000] ata5: SATA max UDMA/133 cmd 0xf8846600 ctl 0x00000000 bmdma 0x000
00000 irq 20
[   13.556000] ata6: SATA max UDMA/133 cmd 0xf8846680 ctl 0x00000000 bmdma 0x000
00000 irq 20
[   14.040000] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   14.040000] ata3.00: ATA-7: ST96812AS, 7.24, max UDMA/100
[   14.040000] ata3.00: 117231408 sectors, multi 16: LBA48 
[   14.040000] ata3.00: configured for UDMA/100
[   14.352000] ata4: SATA link down (SStatus 0 SControl 0)
[   14.664000] ata5: SATA link down (SStatus 0 SControl 300)
[   14.976000] ata6: SATA link down (SStatus 0 SControl 0)
[   14.976000] scsi 2:0:0:0: Direct-Access     ATA      ST96812AS        7.24 PQ
: 0 ANSI: 5
[   14.976000] ACPI: PCI Interrupt 0000:08:08.0[A] -> GSI 20 (level, low) -> IRQ
 21
[   15.004000] e100: eth0: e100_probe: addr 0xd0100000, irq 21, MAC addr 00:16:D
4:3B:BF:DD
[   15.016000] sd 2:0:0:0: [sda] 117231408 512-byte hardware sectors (60022 MB)
[   15.016000] sd 2:0:0:0: [sda] Write Protect is off
[   15.016000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   15.016000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, does
n't support DPO or FUA
[   15.016000] sd 2:0:0:0: [sda] 117231408 512-byte hardware sectors (60022 MB)
[   15.016000] sd 2:0:0:0: [sda] Write Protect is off
[   15.016000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   15.016000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, does
n't support DPO or FUA
[   15.016000]  sda: sda1 sda2 < sda5 >
[   15.044000] sd 2:0:0:0: [sda] Attached SCSI disk
[   15.048000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   15.360000] Attempting manual resume
[   15.360000] swsusp: Resume From Partition 8:5
[   15.360000] PM: Checking swsusp image.
[   15.360000] PM: Resume from disk failed.
[   15.412000] kjournald starting.  Commit interval 5 seconds
[   15.412000] EXT3-fs: mounted filesystem with ordered data mode.
[   23.236000] Linux agpgart interface v0.102 (c) Dave Jones
[   23.416000] agpgart: Detected an Intel 945GM Chipset.
[   23.416000] agpgart: Detected 7932K stolen memory.
[   23.432000] agpgart: AGP aperture is 256M @ 0xc0000000
[   24.072000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   24.076000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   24.104000] intel_rng: FWH not detected
[   24.136000] iTCO_vendor_support: vendor-support=0
[   24.136000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   24.136000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   24.136000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   25.132000] ieee80211_crypt: registered algorithm 'NULL'
[   25.148000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa0471
3/0x200000
[   25.152000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   25.152000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@li
nux.intel.com>
[   25.208000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[   25.436000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ
 22
[   25.436000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   25.456000] bcm43xx driver
[   25.640000] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 18 (level, low) -> IRQ
 18
[   25.640000] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   26.024000] lp: driver loaded but no devices found
[   26.080000] Adding 2433808k swap on /dev/sda5.  Priority:-1 extents:1 across:
2433808k
[   26.452000] EXT3 FS on sda1, internal journal

```

---

