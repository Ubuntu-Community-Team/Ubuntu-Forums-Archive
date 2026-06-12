---
title: "Everething work except sound in Feisty"
date: 2007-05-04
forum: Hardware &amp; Laptops
---

### Post by obavjestenja on 2007-05-04
How can i make my sound to work with Feisty.
Please help but  in simple IT english:) .
Thanks.

---

### Post by obavjestenja on 2007-05-04
please help:(

---

### Post by Swankyman on 2007-05-04
Hey,

You need to give us a bit more information otherwise we cant make any suggestions. 

in a terminal type:

lspci

and 

dmesg

and 

attach them so we can have a look

:) 

rich

---

### Post by obavjestenja on 2007-05-04
pika@pika-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RS400 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 12)
08:00.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
08:00.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
08:00.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
08:00.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
08:02.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
pika@pika-laptop:~$ 



 0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000d0000 size: 0000000000004000 end: 00000000000d4000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e4000 size: 000000000001c000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 0000000037da0000 end: 0000000037ea0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 0000000037ea0000 size: 0000000000012000 end: 0000000037eb2000 type: 3
[    0.000000] copy_e820_map() start: 0000000037eb2000 size: 000000000004e000 end: 0000000037f00000 type: 4
[    0.000000] copy_e820_map() start: 0000000037f00000 size: 0000000000100000 end: 0000000038000000 type: 2
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff80000 size: 0000000000080000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d0000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000037ea0000 (usable)
[    0.000000]  BIOS-e820: 0000000037ea0000 - 0000000037eb2000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000037eb2000 - 0000000037f00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000037f00000 - 0000000038000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 894MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f70b0
[    0.000000] Entering add_active_range(0, 0, 229024) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229024
[    0.000000]   HighMem    229024 ->   229024
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   229024
[    0.000000] On node 0 totalpages: 229024
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1757 pages used for memmap
[    0.000000]   Normal zone: 223171 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f7120
[    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x37eac0c9
[    0.000000] ACPI: FADT (v001 LGE    DEBORAH  0x06040000 LGE  0x000f4240) @ 0x37eb1ef6
[    0.000000] ACPI: MADT (v001 PTLTD    APIC   0x06040000  LTP 0x00000000) @ 0x37eb1f6a
[    0.000000] ACPI: MCFG (v001 PTLTD    MCFG   0x06040000  LTP 0x00000000) @ 0x37eb1fc4
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Ist 0x00003000 INTL 0x20030224) @ 0x37eac522
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20030224) @ 0x37eac307
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20030224) @ 0x37eac105
[    0.000000] ACPI: DSDT (v001    LGE DEBORAH  0x06040000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ATI board detected. Disabling timer routing over 8254.
[    0.000000] ACPI: PM-Timer IO Port: 0x8008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:13 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 38000000:a8000000)
[    0.000000] Detected 1733.563 MHz processor.
[   11.600144] Built 1 zonelists.  Total pages: 227235
[   11.600149] Kernel command line: root=UUID=ff4a463a-bbf7-4bb6-b30e-348d85bc10f2 ro quiet splash
[   11.600312] mapped APIC to ffffd000 (fee00000)
[   11.600315] mapped IOAPIC to ffffc000 (fec00000)
[   11.600319] Enabling fast FPU save and restore... done.
[   11.600321] Enabling unmasked SIMD FPU exception support... done.
[   11.600334] Initializing CPU#0
[   11.600414] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   11.601413] Console: colour VGA+ 80x25
[   11.602100] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   11.602744] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   11.628467] Memory: 896832k/916096k available (1992k kernel code, 18672k reserved, 893k data, 328k init, 0k highmem)
[   11.628477] virtual kernel memory layout:
[   11.628478]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   11.628479]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   11.628480]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   11.628482]     lowmem  : 0xc0000000 - 0xf7ea0000   ( 894 MB)
[   11.628483]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   11.628484]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   11.628485]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   11.628489] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   11.708291] Calibrating delay using timer specific routine.. 3470.61 BogoMIPS (lpj=6941236)
[   11.708332] Security Framework v1.0.0 initialized
[   11.708340] SELinux:  Disabled at boot.
[   11.708356] Mount-cache hash table entries: 512
[   11.708492] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000 00000000
[   11.708504] CPU: L1 I cache: 32K, L1 D cache: 32K
[   11.708507] CPU: L2 cache: 2048K
[   11.708510] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002040 00000180 00000000 00000000
[   11.708520] Compat vDSO mapped to ffffe000.
[   11.708524] Remapping vsyscall page to ffffe000
[   11.708535] Checking 'hlt' instruction... OK.
[   11.724360] SMP alternatives: switching to UP code
[   11.724528] Freeing SMP alternatives: 11k freed
[   11.724697] Early unpacking initramfs... done
[   12.053738] ACPI: Core revision 20060707
[   12.065421] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   12.070575] CPU0: Intel(R) Pentium(R) M processor 1.73GHz stepping 08
[   12.070599] Total of 1 processors activated (3470.61 BogoMIPS).
[   12.070780] ENABLING IO-APIC IRQs
[   12.070980] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   12.110664] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   12.110709] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[   12.110712] ...trying to set up timer as Virtual Wire IRQ... works.
[   12.255669] Brought up 1 CPUs
[   12.255898] Booting paravirtualized kernel on bare hardware
[   12.255983] Time: 11:59:33  Date: 04/04/107
[   12.256009] NET: Registered protocol family 16
[   12.256089] EISA bus registered
[   12.256093] ACPI: bus type pci registered
[   12.256469] PCI: PCI BIOS revision 2.10 entry at 0xfd84d, last bus=14
[   12.256471] PCI: Using configuration type 1
[   12.256473] Setting up standard PCI resources
[   12.262022] ACPI: Interpreter enabled
[   12.262025] ACPI: Using IOAPIC for interrupt routing
[   12.262746] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   12.262752] PCI: Probing PCI hardware (bus 00)
[   12.264122] Boot video device is 0000:01:05.0
[   12.264847] PCI: Transparent bridge - 0000:00:14.4
[   12.264957] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   12.266595] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB7_._PRT]
[   12.267942] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[   12.268174] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[   12.268405] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[   12.268635] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[   12.268865] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[   12.269094] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[   12.269325] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[   12.269554] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[   12.367614] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[   12.367956] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[   12.368506] ACPI: Power Resource [CTHT] (off)
[   12.368582] Linux Plug and Play Support v0.97 (c) Adam Belay
[   12.368593] pnp: PnP ACPI init
[   12.370418] pnp: PnP ACPI: found 10 devices
[   12.370423] PnPBIOS: Disabled by ACPI PNP
[   12.370457] PCI: Using ACPI for IRQ routing
[   12.370460] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   12.407516] NET: Registered protocol family 8
[   12.407518] NET: Registered protocol family 20
[   12.407700] pnp: 00:08: ioport range 0x1080-0x1080 has been reserved
[   12.407703] pnp: 00:08: ioport range 0x40b-0x40b has been reserved
[   12.407705] pnp: 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   12.407708] pnp: 00:08: ioport range 0x4d6-0x4d6 has been reserved
[   12.407711] pnp: 00:08: ioport range 0xc00-0xc01 has been reserved
[   12.407961] PCI: Bridge: 0000:00:01.0
[   12.407964]   IO window: 9000-9fff
[   12.407967]   MEM window: c0100000-c01fffff
[   12.407971]   PREFETCH window: d0000000-dfffffff
[   12.407974] PCI: Bridge: 0000:00:07.0
[   12.407977]   IO window: a000-afff
[   12.407980]   MEM window: c0200000-c02fffff
[   12.407983]   PREFETCH window: disabled.
[   12.407989] PCI: Bus 9, cardbus bridge: 0000:08:00.0
[   12.407991]   IO window: 00002000-000020ff
[   12.407997]   IO window: 00002400-000024ff
[   12.408003]   PREFETCH window: 40000000-43ffffff
[   12.408010]   MEM window: 44000000-47ffffff
[   12.408015] PCI: Bridge: 0000:00:14.4
[   12.408019]   IO window: 2000-2fff
[   12.408026]   MEM window: c0300000-c03fffff
[   12.408031]   PREFETCH window: 40000000-43ffffff
[   12.408054] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   12.408083] ACPI: PCI Interrupt 0000:08:00.0[A] -> GSI 20 (level, low) -> IRQ 16
[   12.408108] NET: Registered protocol family 2
[   12.439469] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   12.439610] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   12.440428] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   12.441001] TCP: Hash tables configured (established 131072 bind 65536)
[   12.441005] TCP reno registered
[   12.451548] checking if image is initramfs... it is
[   13.109179] Freeing initrd memory: 7012k freed
[   13.109678] audit: initializing netlink socket (disabled)
[   13.109696] audit(1178279973.552:1): initialized
[   13.109835] VFS: Disk quotas dquot_6.5.1
[   13.109856] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   13.109912] io scheduler noop registered
[   13.109915] io scheduler anticipatory registered
[   13.109917] io scheduler deadline registered
[   13.109927] io scheduler cfq registered (default)
[   13.781977] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   13.782009] assign_interrupt_mode Found MSI capability
[   13.782013] Allocate Port Service[0000:00:07.0:pcie00]
[   13.782144] isapnp: Scanning for PnP cards...
[   14.136336] isapnp: No Plug & Play device found
[   14.159623] Real Time Clock Driver v1.12ac
[   14.159694] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   14.160388] mice: PS/2 mouse device common for all mice
[   14.160923] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   14.161163] input: Macintosh mouse button emulation as /class/input/input0
[   14.161193] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   14.161198] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   14.161513] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   14.163914] i8042.c: Detected active multiplexing controller, rev 1.1.
[   14.164873] serio: i8042 KBD port at 0x60,0x64 irq 1
[   14.164879] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   14.164881] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   14.164883] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   14.164886] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   14.164996] EISA: Probing bus 0 at eisa.0
[   14.165006] Cannot allocate resource for EISA slot 1
[   14.165008] Cannot allocate resource for EISA slot 2
[   14.165039] Cannot allocate resource for EISA slot 8
[   14.165041] EISA: Detected 0 cards.
[   14.195114] TCP cubic registered
[   14.195124] NET: Registered protocol family 1
[   14.195144] Using IPI No-Shortcut mode
[   14.195218] ACPI: (supports S0 S3 S4 S5)
[   14.195273]   Magic number: 7:899:983
[   14.195691] Freeing unused kernel memory: 328k freed
[   14.196190] input: AT Translated Set 2 keyboard as /class/input/input1
[   14.197275] Time: tsc clocksource has been installed.
[   15.385991] Capability LSM initialized
[   15.414446] ACPI: Transitioning device [FAN0] to D3
[   15.414450] ACPI: Transitioning device [FAN0] to D3
[   15.414453] ACPI: Fan [FAN0] (off)
[   15.418517] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   15.418522] ACPI: Processor [CPU0] (supports 8 throttling states)
[   15.418529] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   15.420085] ACPI: Thermal Zone [TZ1] (40 C)
[   15.713516] usbcore: registered new interface driver usbfs
[   15.713538] usbcore: registered new interface driver hub
[   15.713556] usbcore: registered new device driver usb
[   15.714218] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   15.714261] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 17
[   15.714275] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   15.714444] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   15.714464] ohci_hcd 0000:00:13.0: irq 17, io mem 0xc0004000
[   15.750275] SCSI subsystem initialized
[   15.767535] libata version 2.20 loaded.
[   15.794162] usb usb1: configuration #1 chosen from 1 choice
[   15.794189] hub 1-0:1.0: USB hub found
[   15.794201] hub 1-0:1.0: 4 ports detected
[   15.895386] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 17
[   15.895407] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   15.895429] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   15.895447] ohci_hcd 0000:00:13.1: irq 17, io mem 0xc0005000
[   15.909825] ieee1394: Initialized config rom entry `ip1394'
[   15.955311] usb usb2: configuration #1 chosen from 1 choice
[   15.955340] hub 2-0:1.0: USB hub found
[   15.955352] hub 2-0:1.0: 4 ports detected
[    3.636000] Time: acpi_pm clocksource has been installed.
[    3.696000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 17
[    3.696000] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    3.696000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[    3.696000] ehci_hcd 0000:00:13.2: irq 17, io mem 0xc0006000
[    3.696000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.696000] usb usb3: configuration #1 chosen from 1 choice
[    3.696000] hub 3-0:1.0: USB hub found
[    3.696000] hub 3-0:1.0: 8 ports detected
[    3.800000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[    3.800000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 18
[    3.800000] ATIIXP: chipset revision 128
[    3.800000] ATIIXP: not 100% native mode: will probe irqs later
[    3.800000]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:pio
[    3.800000]     ide1: BM-DMA at 0x8418-0x841f, BIOS settings: hdc:DMA, hdd:pio
[    3.800000] Probing IDE interface ide0...
[    4.088000] hda: FUJITSU MHV2060AT, ATA DISK drive
[    4.380000] usb 1-1: new low speed USB device using ohci_hcd and address 3
[    4.584000] usb 1-1: configuration #1 chosen from 1 choice
[    4.596000] usbcore: registered new interface driver hiddev
[    4.600000] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input2
[    4.600000] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:13.0-1
[    4.600000] usbcore: registered new interface driver usbhid
[    4.600000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[    4.760000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[    4.836000] Probing IDE interface ide1...
[    5.572000] hdc: TSSTcorpCD/DVDW TS-L632B, ATAPI CD/DVD-ROM drive
[    5.908000] ide1 at 0x170-0x177,0x376 on irq 15
[    5.912000] ACPI: PCI Interrupt 0000:08:00.2[A] -> GSI 20 (level, low) -> IRQ 16
[    5.964000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[c0309000-c03097ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    5.968000] hda: max request size: 128KiB
[    5.976000] hda: 117210240 sectors (60011 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
[    5.980000] hda: cache flushes supported
[    5.980000]  hda: hda1 hda2 < hda5 >
[    6.064000] hdc: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[    6.064000] Uniform CD-ROM driver Revision: 3.20
[    6.200000] Attempting manual resume
[    6.200000] swsusp: Resume From Partition 3:5
[    6.200000] PM: Checking swsusp image.
[    6.204000] PM: Resume from disk failed.
[    6.212000] EXT3-fs: INFO: recovery required on readonly filesystem.
[    6.212000] EXT3-fs: write access will be enabled during recovery.
[    7.236000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e091040351230d]
[    7.984000] kjournald starting.  Commit interval 5 seconds
[    7.984000] EXT3-fs: recovery complete.
[    7.984000] EXT3-fs: mounted filesystem with ordered data mode.
[   19.204000] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   19.228000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   19.232000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   19.856000] Linux agpgart interface v0.102 (c) Dave Jones
[   19.924000] ACPI: PCI Interrupt 0000:08:00.3[A] -> GSI 20 (level, low) -> IRQ 16
[   20.112000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 19 (level, low) -> IRQ 17
[   20.112000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   20.112000] sky2 0000:02:00.0: v1.13 addr 0xc0200000 irq 17 Yukon-FE (0xb7) rev 1
[   20.112000] sky2 eth0: addr 00:e0:91:13:49:a1
[   20.124000] sdhci: Secure Digital Host Controller Interface driver
[   20.124000] sdhci: Copyright(c) Pierre Ossman
[   20.124000] sdhci: SDHCI controller found at 0000:08:00.4 [104c:8034] (rev 0)
[   20.124000] ACPI: PCI Interrupt 0000:08:00.4[A] -> GSI 20 (level, low) -> IRQ 16
[   20.128000] mmc0: SDHCI at 0xc030a000 irq 16 DMA
[   20.132000] mmc1: SDHCI at 0xc0309c00 irq 16 DMA
[   20.132000] mmc2: SDHCI at 0xc0309800 irq 16 DMA
[   20.208000] Yenta: CardBus bridge found at 0000:08:00.0 [1854:0023]
[   20.208000] Yenta: Using INTVAL to route CSC interrupts to PCI
[   20.208000] Yenta: Routing CardBus interrupts to PCI
[   20.208000] Yenta TI: socket 0000:08:00.0, mfunc 0x01001002, devctl 0x64
[   20.212000] input: PC Speaker as /class/input/input3
[   20.440000] Yenta: ISA IRQ mask 0x0ef8, PCI irq 16
[   20.440000] Socket status: 30000006
[   20.440000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   20.440000] cs: IO port probe 0x2000-0x2fff: clean.
[   20.440000] pcmcia: parent PCI bridge Memory window: 0xc0300000 - 0xc03fffff
[   20.440000] pcmcia: parent PCI bridge Memory window: 0x40000000 - 0x43ffffff
[   20.444000] ACPI: PCI Interrupt 0000:08:02.0[A] -> GSI 22 (level, low) -> IRQ 19
[   20.444000] rt2500 1.1.0 BETA4 2006/06/18 [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
[   20.564000] rt2500 EEPROM:  1  2  3  4  5  6  7  8  9 10 11 12 13 14  Channel
[   20.564000] rt2500 EEPROM:  7  7  7  7  7  8  8  8  8  8  8  8  7  7  dBm Maximum
[   20.692000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x23aeb3, caps: 0xa04713/0x10008
[   20.732000] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[   20.848000] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 18
[   20.900000] cs: IO port probe 0x100-0x3af: clean.
[   20.900000] cs: IO port probe 0x3e0-0x4ff: clean.
[   20.904000] cs: IO port probe 0x820-0x8ff: excluding 0x878-0x87f
[   20.904000] cs: IO port probe 0xc00-0xcf7: excluding 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[   20.904000] cs: IO port probe 0xa00-0xaff: clean.
[   21.272000] fuse init (API version 7.8)
[   21.348000] lp: driver loaded but no devices found
[   21.392000] Adding 2441840k swap on /dev/disk/by-uuid/a1c2dfd2-a804-4b7e-a541-7a3447c08611.  Priority:-1 extents:1 across:2441840k
[   21.540000] EXT3 FS on hda1, internal journal
[   21.856000] NET: Registered protocol family 17
[   21.960000] NET: Registered protocol family 10
[   21.960000] lo: Disabled Privacy Extensions
[   26.768000] ACPI: Battery Slot [CMB0] (battery present)
[   26.824000] ibm_acpi: ec object not found
[   26.844000] ACPI: AC Adapter [AC] (on-line)
[   26.852000] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
[   26.904000] Using specific hotkey driver
[   26.912000] No dock devices found.
[   26.952000] input: Power Button (FF) as /class/input/input5
[   26.956000] ACPI: Power Button (FF) [PWRF]
[   26.988000] input: Lid Switch as /class/input/input6
[   26.988000] ACPI: Lid Switch [LID0]
[   27.020000] input: Sleep Button (CM) as /class/input/input7
[   27.024000] ACPI: Sleep Button (CM) [SLPB]
[   27.056000] input: Power Button (CM) as /class/input/input8
[   27.060000] ACPI: Power Button (CM) [PWRB]
[   27.080000] pcc_acpi: loading...
[   27.084000] wmi_add device=f693a000
[   27.084000] calling WQBA
[   29.776000] sky2 eth0: enabling interface
[   29.780000] sky2 eth0: ram buffer 4K
[   29.780000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   31.608000] ppdev: user-space parallel port driver
[   32.360000] apm: BIOS not found.
[   32.536000] Bluetooth: Core ver 2.11
[   32.536000] NET: Registered protocol family 31
[   32.536000] Bluetooth: HCI device and connection manager initialized
[   32.536000] Bluetooth: HCI socket layer initialized
[   32.572000] Bluetooth: L2CAP ver 2.8
[   32.572000] Bluetooth: L2CAP socket layer initialized
[   32.628000] Bluetooth: RFCOMM socket layer initialized
[   32.628000] Bluetooth: RFCOMM TTY layer initialized
[   32.628000] Bluetooth: RFCOMM ver 1.8
[   32.912000] ra0: no IPv6 routers present
pika@pika-laptop:~$ 


this ?

---

### Post by obavjestenja on 2007-05-04
im going back to vista, to much sound problems  with this final release.

---

### Post by fulvio6900 on 2007-05-04
Same problem here!

I'm on a BENQ Joybook 7000 notebook and I can't make sound work.

Here's my lspci output:
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 21)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 21)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
02:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller

and here's my dmesg output:
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fef0000 end: 000000003fff0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003fff0000 size: 000000000000ffc0 end: 000000003fffffc0 type: 3
[    0.000000] copy_e820_map() start: 000000003fffffc0 size: 0000000000000040 end: 0000000040000000 type: 4
[    0.000000] copy_e820_map() start: 00000000ffb80000 size: 0000000000080000 end: 00000000ffc00000 type: 2
[    0.000000] copy_e820_map() start: 00000000fff80000 size: 0000000000080000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fffffc0 (ACPI data)
[    0.000000]  BIOS-e820: 000000003fffffc0 - 0000000040000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] 127MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 262128) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   262128
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   262128
[    0.000000] On node 0 totalpages: 262128
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 255 pages used for memmap
[    0.000000]   HighMem zone: 32497 pages, LIFO batch:7
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 OID_00                                ) @ 0x000e6010
[    0.000000] ACPI: RSDT (v001 INSYDE RSDT_000 0x00000001 _CSI 0x00010101) @ 0x3fffb9b6
[    0.000000] ACPI: FADT (v001 TOSINV FACP_000 0x00000100 _CSI 0x00010101) @ 0x3ffffb00
[    0.000000] ACPI: BOOT (v001 INSYDE SYS_BOOT 0x00000100 _CSI 0x00010101) @ 0x3ffffb90
[    0.000000] ACPI: DBGP (v001 INSYDE DBGP_000 0x00000100 _CSI 0x00010101) @ 0x3ffffbc0
[    0.000000] ACPI: SSDT (v001 INSYDE   GV3Ref 0x00001001 INTL 0x02012044) @ 0x3fffb9ea
[    0.000000] ACPI: DSDT (v001 INSYDE    Intel 0x00001004 INTL 0x02002036) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bfb80000)
[    0.000000] Detected 1594.897 MHz processor.
[   20.110248] Built 1 zonelists.  Total pages: 260081
[   20.110253] Kernel command line: root=UUID=56ecf4e1-364f-4350-be55-bb99d0024ada ro quiet splash locale=it_IT
[   20.110437] Local APIC disabled by BIOS -- you can enable it with "lapic"
[   20.110447] mapped APIC to ffffd000 (0180c000)
[   20.110451] Enabling fast FPU save and restore... done.
[   20.110454] Enabling unmasked SIMD FPU exception support... done.
[   20.110467] Initializing CPU#0
[   20.110544] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   20.111743] Console: colour VGA+ 80x25
[   20.112372] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   20.112989] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   20.148842] Memory: 1028060k/1048512k available (1992k kernel code, 19684k reserved, 893k data, 328k init, 131008k highmem)
[   20.148852] virtual kernel memory layout:
[   20.148854]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   20.148855]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   20.148856]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   20.148858]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   20.148859]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   20.148860]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   20.148862]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   20.148865] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   20.226542] Calibrating delay using timer specific routine.. 3191.89 BogoMIPS (lpj=6383796)
[   20.226583] Security Framework v1.0.0 initialized
[   20.226591] SELinux:  Disabled at boot.
[   20.226608] Mount-cache hash table entries: 512
[   20.226746] CPU: After generic identify, caps: afe9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
[   20.226758] CPU: L1 I cache: 32K, L1 D cache: 32K
[   20.226761] CPU: L2 cache: 2048K
[   20.226764] CPU: After all inits, caps: afe9f9bf 00000000 00000000 00002040 00000180 00000000 00000000
[   20.226774] Compat vDSO mapped to ffffe000.
[   20.226778] Remapping vsyscall page to ffffe000
[   20.226789] Checking 'hlt' instruction... OK.
[   20.242637] SMP alternatives: switching to UP code
[   20.242839] Freeing SMP alternatives: 11k freed
[   20.243024] Early unpacking initramfs... done
[   20.602402] ACPI: Core revision 20060707
[   20.602522] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   20.604240] ACPI: setting ELCR to 0200 (from 0c80)
[   20.622408] CPU0: Intel(R) Pentium(R) M processor 1.60GHz stepping 06
[   20.622414] SMP motherboard not detected.
[   20.622416] Local APIC not detected. Using dummy APIC emulation.
[   20.622452] Brought up 1 CPUs
[   20.622705] Booting paravirtualized kernel on bare hardware
[   20.622774] Time:  8:41:41  Date: 04/04/107
[   20.622804] NET: Registered protocol family 16
[   20.622884] EISA bus registered
[   20.622889] ACPI: bus type pci registered
[   20.622923] PCI: PCI BIOS revision 2.10 entry at 0xe94d4, last bus=2
[   20.622925] PCI: Using configuration type 1
[   20.622927] Setting up standard PCI resources
[   20.625357] ACPI: Interpreter enabled
[   20.625359] ACPI: Using PIC for interrupt routing
[   20.625992] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   20.625997] PCI: Probing PCI hardware (bus 00)
[   20.626126] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[   20.626634] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[   20.626638] PCI quirk: region 1300-133f claimed by ICH4 GPIO
[   20.626839] Boot video device is 0000:01:00.0
[   20.627141] PCI: Transparent bridge - 0000:00:1e.0
[   20.627193] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
[   20.627196] Please report the result to linux-kernel to fix this permanently
[   20.627215] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   20.628620] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[   20.629785] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 6 *10 11)
[   20.630016] ACPI: PCI Interrupt Link [LNKB] (IRQs 6) *10
[   20.630245] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 6 10 *11)
[   20.630476] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 6 10 *11)
[   20.630701] ACPI: PCI Interrupt Link [LNKE] (IRQs 5 6 *10 11)
[   20.630921] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 5 *7 10 11)
[   20.631125] ACPI: PCI Interrupt Link [LNKG] (IRQs 5 6 10 11) *0, disabled.
[   20.631333] ACPI: PCI Interrupt Link [LNKH] (IRQs 5 6 10 11) *0, disabled.
[   20.632400] ACPI: Power Resource [PUT2] (on)
[   20.632500] ACPI: Power Resource [PFA1] (off)
[   20.632584] ACPI: Power Resource [PFA0] (off)
[   20.632751] Linux Plug and Play Support v0.97 (c) Adam Belay
[   20.632764] pnp: PnP ACPI init
[   20.634990] pnp: PnP ACPI: found 11 devices
[   20.634995] PnPBIOS: Disabled by ACPI PNP
[   20.635030] PCI: Using ACPI for IRQ routing
[   20.635033] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   20.637915] NET: Registered protocol family 8
[   20.637917] NET: Registered protocol family 20
[   20.637997] pnp: 00:07: ioport range 0x680-0x6ff has been reserved
[   20.638000] pnp: 00:07: ioport range 0x200-0x20f has been reserved
[   20.638003] pnp: 00:07: ioport range 0x300-0x301 has been reserved
[   20.638006] pnp: 00:07: ioport range 0x310-0x31f has been reserved
[   20.638285] PCI: Bridge: 0000:00:01.0
[   20.638288]   IO window: c000-dfff
[   20.638292]   MEM window: e0000000-efffffff
[   20.638295]   PREFETCH window: a0000000-afffffff
[   20.638301] PCI: Bus 3, cardbus bridge: 0000:02:09.0
[   20.638304]   IO window: 0000a400-0000a4ff
[   20.638308]   IO window: 0000a800-0000a8ff
[   20.638312]   PREFETCH window: 90000000-93ffffff
[   20.638316]   MEM window: d4000000-d7ffffff
[   20.638320] PCI: Bridge: 0000:00:1e.0
[   20.638323]   IO window: a000-bfff
[   20.638328]   MEM window: d0000000-dfffffff
[   20.638332]   PREFETCH window: 90000000-9fffffff
[   20.638347] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   20.638567] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[   20.638570] PCI: setting IRQ 10 as level-triggered
[   20.638573] ACPI: PCI Interrupt 0000:02:09.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   20.638599] NET: Registered protocol family 2
[   20.670573] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   20.670692] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   20.671704] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   20.672425] TCP: Hash tables configured (established 131072 bind 65536)
[   20.672429] TCP reno registered
[   20.682678] checking if image is initramfs... it is
[   21.395821] Freeing initrd memory: 6997k freed
[   21.396078] Simple Boot Flag at 0x37 set to 0x1
[   21.396276] audit: initializing netlink socket (disabled)
[   21.396293] audit(1178268102.456:1): initialized
[   21.396374] highmem bounce pool size: 64 pages
[   21.396445] VFS: Disk quotas dquot_6.5.1
[   21.396467] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   21.396525] io scheduler noop registered
[   21.396528] io scheduler anticipatory registered
[   21.396531] io scheduler deadline registered
[   21.396542] io scheduler cfq registered (default)
[   21.396951] isapnp: Scanning for PnP cards...
[   21.750798] isapnp: No Plug & Play device found
[   21.775322] Real Time Clock Driver v1.12ac
[   21.775384] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   21.776306] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 6
[   21.776310] PCI: setting IRQ 6 as level-triggered
[   21.776314] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 6 (level, low) -> IRQ 6
[   21.776324] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[   21.776414] mice: PS/2 mouse device common for all mice
[   21.776974] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   21.777198] input: Macintosh mouse button emulation as /class/input/input0
[   21.777234] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   21.777238] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   21.777474] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   21.781586] serio: i8042 KBD port at 0x60,0x64 irq 1
[   21.781591] serio: i8042 AUX port at 0x60,0x64 irq 12
[   21.781712] EISA: Probing bus 0 at eisa.0
[   21.781722] Cannot allocate resource for EISA slot 1
[   21.781751] EISA: Detected 0 cards.
[   21.811855] TCP cubic registered
[   21.811864] NET: Registered protocol family 1
[   21.811886] Using IPI No-Shortcut mode
[   21.811945] ACPI: (supports S0 S3 S4 S5)
[   21.811991]   Magic number: 7:272:674
[   21.812368] Freeing unused kernel memory: 328k freed
[   21.813880] input: AT Translated Set 2 keyboard as /class/input/input1
[   21.814444] Time: tsc clocksource has been installed.
[   23.024229] Capability LSM initialized
[   23.054222] ACPI: Transitioning device [FAN0] to D3
[   23.054225] ACPI: Transitioning device [FAN0] to D3
[   23.054229] ACPI: Fan [FAN0] (off)
[   23.054289] ACPI: Transitioning device [FAN1] to D3
[   23.054291] ACPI: Transitioning device [FAN1] to D3
[   23.054294] ACPI: Fan [FAN1] (off)
[   23.057741] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   23.057745] ACPI: Processor [CPU0] (supports 8 throttling states)
[    2.948000] Time: acpi_pm clocksource has been installed.
[    2.956000] ACPI: Thermal Zone [THZN] (44 C)
[    2.956000] ACPI: Thermal Zone [THZV] (25 C)
[    3.300000] usbcore: registered new interface driver usbfs
[    3.300000] usbcore: registered new interface driver hub
[    3.300000] usbcore: registered new device driver usb
[    3.300000] USB Universal Host Controller Interface driver v3.0
[    3.304000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[    3.304000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.304000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.304000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    3.304000] uhci_hcd 0000:00:1d.0: irq 10, io base 0x00001200
[    3.304000] usb usb1: configuration #1 chosen from 1 choice
[    3.304000] hub 1-0:1.0: USB hub found
[    3.304000] hub 1-0:1.0: 2 ports detected
[    3.364000] SCSI subsystem initialized
[    3.368000] libata version 2.20 loaded.
[    3.408000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    3.408000] PCI: setting IRQ 11 as level-triggered
[    3.408000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[    3.408000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.408000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.408000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    3.408000] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001220
[    3.408000] usb usb2: configuration #1 chosen from 1 choice
[    3.408000] hub 2-0:1.0: USB hub found
[    3.408000] hub 2-0:1.0: 2 ports detected
[    3.492000] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    3.512000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    3.512000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[    3.512000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.512000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.512000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    3.512000] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001240
[    3.512000] usb usb3: configuration #1 chosen from 1 choice
[    3.512000] hub 3-0:1.0: USB hub found
[    3.512000] hub 3-0:1.0: 2 ports detected
[    3.512000] ieee1394: Initialized config rom entry `ip1394'
[    3.616000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[    3.616000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[    3.616000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.616000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.616000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    3.616000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.616000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.616000] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xf4000000
[    3.620000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.620000] usb usb4: configuration #1 chosen from 1 choice
[    3.620000] hub 4-0:1.0: USB hub found
[    3.620000] hub 4-0:1.0: 6 ports detected
[    3.648000] usb 1-2: new low speed USB device using uhci_hcd and address 2
[    3.724000] ata_piix 0000:00:1f.1: version 2.10ac1
[    3.724000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[    3.724000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[    3.724000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    3.724000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011100 irq 14
[    3.740000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011108 irq 15
[    3.740000] scsi0 : ata_piix
[    3.904000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
[    3.904000] ata1.00: ATA-7: ST96023A, 3.04, max UDMA/100
[    3.904000] ata1.00: 117210240 sectors, multi 16: LBA48 
[    3.912000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
[    3.912000] ata1.00: configured for UDMA/100
[    3.912000] scsi1 : ata_piix
[    4.152000] usb 1-2: new low speed USB device using uhci_hcd and address 3
[    4.232000] ata2.00: ATAPI, max UDMA/33
[    4.328000] usb 1-2: configuration #1 chosen from 1 choice
[    4.356000] usbcore: registered new interface driver hiddev
[    4.368000] input: Microsoft Microsoft(R) Compact Optical Mouse as /class/input/input2
[    4.368000] input: USB HID v1.10 Mouse [Microsoft Microsoft(R) Compact Optical Mouse] on usb-0000:00:1d.0-2
[    4.368000] usbcore: registered new interface driver usbhid
[    4.368000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[    4.396000] ata2.00: configured for UDMA/33
[    4.396000] scsi 0:0:0:0: Direct-Access     ATA      ST96023A         3.04 PQ: 0 ANSI: 5
[    4.396000] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-840S  1.50 PQ: 0 ANSI: 5
[    4.396000] 8139cp 0000:02:07.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    4.396000] 8139cp 0000:02:07.0: Try the "8139too" driver instead.
[    4.400000] 8139too Fast Ethernet driver 0.9.28
[    4.400000] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 7
[    4.400000] PCI: setting IRQ 7 as level-triggered
[    4.400000] ACPI: PCI Interrupt 0000:02:07.0[A] -> Link [LNKF] -> GSI 7 (level, low) -> IRQ 7
[    4.400000] eth0: RealTek RTL8139 at 0xf88ae300, 00:03:9d:75:46:b6, IRQ 7
[    4.400000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    4.400000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
[    4.400000] ACPI: PCI Interrupt 0000:02:09.2[C] -> Link [LNKE] -> GSI 10 (level, low) -> IRQ 10
[    4.452000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[febff800-febfffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.464000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[    4.464000] sda: Write Protect is off
[    4.464000] sda: Mode Sense: 00 3a 00 00
[    4.464000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.464000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[    4.464000] sda: Write Protect is off
[    4.464000] sda: Mode Sense: 00 3a 00 00
[    4.464000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.464000]  sda: sda1 sda2 sda3
[    4.500000] sd 0:0:0:0: Attached scsi disk sda
[    4.504000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.504000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    4.520000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.520000] Uniform CD-ROM driver Revision: 3.20
[    4.520000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.824000] Attempting manual resume
[    4.824000] swsusp: Resume From Partition 8:3
[    4.824000] PM: Checking swsusp image.
[    4.828000] PM: Resume from disk failed.
[    4.864000] kjournald starting.  Commit interval 5 seconds
[    4.864000] EXT3-fs: mounted filesystem with ordered data mode.
[    6.072000] irq 11: nobody cared (try booting with the "irqpoll" option)
[    6.072000]  [<c0154394>] __report_bad_irq+0x24/0x80
[    6.072000]  [<c015464e>] note_interrupt+0x25e/0x290
[    6.072000]  [<f8881f32>] usb_hcd_irq+0x22/0x60 [usbcore]
[    6.072000]  [<c01538c0>] handle_IRQ_event+0x30/0x60
[    6.072000]  [<c01551cb>] handle_level_irq+0xeb/0x120
[    6.072000]  [<c0105b70>] do_IRQ+0x40/0x80
[    6.072000]  [<c0104233>] common_interrupt+0x23/0x30
[    6.072000]  [<c01538a0>] handle_IRQ_event+0x10/0x60
[    6.072000]  [<c015516d>] handle_level_irq+0x8d/0x120
[    6.072000]  [<c0105b70>] do_IRQ+0x40/0x80
[    6.072000]  [<c0104233>] common_interrupt+0x23/0x30
[    6.072000]  [<c0137314>] run_workqueue+0xa4/0x140
[    6.072000]  [<f896f600>] delayed_reset_bus+0x0/0xe0 [ieee1394]
[    6.072000]  [<c0137d87>] worker_thread+0x147/0x170
[    6.072000]  [<c0120b40>] default_wake_function+0x0/0x10
[    6.072000]  [<c0137c40>] worker_thread+0x0/0x170
[    6.072000]  [<c013ac3a>] kthread+0xba/0xf0
[    6.072000]  [<c013ab80>] kthread+0x0/0xf0
[    6.072000]  [<c01044c7>] kernel_thread_helper+0x7/0x10
[    6.072000]  =======================
[    6.072000] handlers:
[    6.072000] [<f8881f10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[    6.072000] [<f8881f10>] (usb_hcd_irq+0x0/0x60 [usbcore])
[    6.072000] Disabling IRQ #11
[    6.344000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00039d039d7546b6]
[   14.548000] eth0: link up, 100Mbps, half-duplex, lpa 0x40A1
[   15.612000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   15.676000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.780000] iTCO_vendor_support: vendor-support=0
[   15.780000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   15.780000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   15.780000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   15.796000] intel_rng: FWH not detected
[   15.856000] NET: Registered protocol family 17
[   16.300000] Linux agpgart interface v0.102 (c) Dave Jones
[   16.320000] ieee80211_crypt: registered algorithm 'NULL'
[   16.344000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   16.344000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   16.368000] Yenta: CardBus bridge found at 0000:02:09.0 [17ff:5005]
[   16.368000] Yenta: Enabling burst memory read transactions
[   16.368000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   16.368000] Yenta: Routing CardBus interrupts to PCI
[   16.368000] Yenta TI: socket 0000:02:09.0, mfunc 0x01aa1b22, devctl 0x66
[   16.380000] input: PC Speaker as /class/input/input3
[   16.408000] agpgart: Detected an Intel 855PM Chipset.
[   16.412000] agpgart: AGP aperture is 64M @ 0xb0000000
[   16.444000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   16.444000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   16.600000] Yenta: ISA IRQ mask 0x0038, PCI irq 10
[   16.600000] Socket status: 30000006
[   16.600000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   16.600000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xbfff
[   16.600000] cs: IO port probe 0xa000-0xbfff: clean.
[   16.600000] pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xdfffffff
[   16.600000] pcmcia: parent PCI bridge Memory window: 0x90000000 - 0x9fffffff
[   16.612000] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [LNKB] -> GSI 6 (level, low) -> IRQ 6
[   16.612000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   16.668000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x926eb1, caps: 0x804719/0x0
[   16.720000] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[   17.048000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   17.048000] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 11
[   17.048000] ACPI: PCI Interrupt 0000:02:09.3[D] -> Link [LNKG] -> GSI 11 (level, low) -> IRQ 11
[   17.060000] irda_init()
[   17.060000] NET: Registered protocol family 23
[   17.232000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 6 (level, low) -> IRQ 6
[   17.232000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   17.392000] cs: IO port probe 0x100-0x3af: excluding 0x320-0x327
[   17.396000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   17.396000] cs: IO port probe 0x820-0x8ff: clean.
[   17.396000] cs: IO port probe 0xc00-0xcf7: clean.
[   17.396000] cs: IO port probe 0xa00-0xaff: clean.
[   18.056000] intel8x0_measure_ac97_clock: measured 55452 usecs
[   18.056000] intel8x0: clocking to 48000
[   18.196000] fuse init (API version 7.8)
[   18.248000] lp: driver loaded but no devices found
[   18.288000] Adding 1510100k swap on /dev/disk/by-uuid/396388a8-e569-41f6-a912-32ddb588067b.  Priority:-1 extents:1 across:1510100k
[   18.452000] EXT3 FS on sda2, internal journal
[   18.636000] NTFS driver 2.1.28 [Flags: R/O MODULE].
[   18.696000] NTFS volume version 3.1.
[   19.664000] NET: Registered protocol family 10
[   19.664000] lo: Disabled Privacy Extensions
[   23.020000] ibm_acpi: ec object not found
[   23.084000] input: Power Button (FF) as /class/input/input5
[   23.088000] ACPI: Power Button (FF) [PWRF]
[   23.128000] input: Sleep Button (CM) as /class/input/input6
[   23.132000] ACPI: Sleep Button (CM) [SLPB]
[   23.172000] input: Lid Switch as /class/input/input7
[   23.172000] ACPI: Lid Switch [LID]
[   23.216000] input: Power Button (CM) as /class/input/input8
[   23.216000] ACPI: Power Button (CM) [PBTN]
[   23.232000] ACPI: Battery Slot [BAT1] (battery absent)
[   23.252000] Using specific hotkey driver
[   23.324000] ACPI: AC Adapter [AC] (on-line)
[   23.344000] No dock devices found.
[   23.432000] pcc_acpi: loading...
[   27.984000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   27.992000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
[   27.992000] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0
[   28.024000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   28.420000] ppdev: user-space parallel port driver
[   30.576000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   30.576000] apm: overridden by ACPI.
[   30.764000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[   30.764000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[   30.764000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
[   30.768000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   30.768000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   30.768000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   30.768000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[   30.772000] [fglrx] total      GART = 67108864
[   30.772000] [fglrx] free       GART = 51113984
[   30.772000] [fglrx] max single GART = 51113984
[   30.772000] [fglrx] total      LFB  = 67108864
[   30.772000] [fglrx] free       LFB  = 53211136
[   30.772000] [fglrx] max single LFB  = 53211136
[   30.772000] [fglrx] total      Inv  = 0
[   30.772000] [fglrx] free       Inv  = 0
[   30.772000] [fglrx] max single Inv  = 0
[   30.772000] [fglrx] total      TIM  = 0
[   40.768000] eth0: no IPv6 routers present
[ 1542.052000] tun: Universal TUN/TAP device driver, 1.6
[ 1542.052000] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[ 1704.772000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[ 1704.772000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[ 1704.772000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
[ 1704.776000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[ 1704.776000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[ 1704.776000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[ 1704.776000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[ 1704.780000] [fglrx] total      GART = 67108864
[ 1704.780000] [fglrx] free       GART = 51113984
[ 1704.780000] [fglrx] max single GART = 51113984
[ 1704.780000] [fglrx] total      LFB  = 67108864
[ 1704.780000] [fglrx] free       LFB  = 53211136
[ 1704.780000] [fglrx] max single LFB  = 53211136
[ 1704.780000] [fglrx] total      Inv  = 0
[ 1704.780000] [fglrx] free       Inv  = 0
[ 1704.780000] [fglrx] max single Inv  = 0
[ 1704.780000] [fglrx] total      TIM  = 0
[ 4703.592000] usb 1-1: new full speed USB device using uhci_hcd and address 4
[ 4703.784000] usb 1-1: configuration #1 chosen from 2 choices
[ 4703.960000] usbcore: registered new interface driver libusual
[ 4703.964000] Initializing USB Mass Storage driver...
[ 4703.980000] scsi2 : SCSI emulation for USB Mass Storage devices
[ 4703.988000] usbcore: registered new interface driver usb-storage
[ 4703.988000] USB Mass Storage support registered.
[ 4703.988000] usb-storage: device found at 4
[ 4703.988000] usb-storage: waiting for device to settle before scanning
[ 4708.988000] usb-storage: device scan complete
[ 4709.328000] scsi 2:0:0:0: Direct-Access     Motorola Motorola Phone   2.31 PQ: 0 ANSI: 2
[ 4709.352000] SCSI device sdb: 122625 512-byte hdwr sectors (63 MB)
[ 4709.364000] sdb: Write Protect is off
[ 4709.364000] sdb: Mode Sense: 0b 00 00 08
[ 4709.364000] sdb: assuming drive cache: write through
[ 4709.416000] SCSI device sdb: 122625 512-byte hdwr sectors (63 MB)
[ 4709.428000] sdb: Write Protect is off
[ 4709.428000] sdb: Mode Sense: 0b 00 00 08
[ 4709.428000] sdb: assuming drive cache: write through
[ 4709.428000]  sdb: sdb1
[ 4709.460000] sd 2:0:0:0: Attached scsi removable disk sdb
[ 4709.460000] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 8093.256000] usb 1-1: USB disconnect, address 4
[ 8093.400000] scsi 2:0:0:0: rejecting I/O to dead device
[ 8104.080000] usb 1-1: new full speed USB device using uhci_hcd and address 5
[ 8104.276000] usb 1-1: configuration #1 chosen from 2 choices
[ 8104.400000] scsi3 : SCSI emulation for USB Mass Storage devices
[ 8104.404000] usb-storage: device found at 5
[ 8104.404000] usb-storage: waiting for device to settle before scanning
[ 8109.404000] usb-storage: device scan complete
[ 8110.248000] scsi 3:0:0:0: Direct-Access     Motorola Motorola Phone   2.31 PQ: 0 ANSI: 2
[ 8110.280000] SCSI device sdb: 122625 512-byte hdwr sectors (63 MB)
[ 8110.292000] sdb: Write Protect is off
[ 8110.292000] sdb: Mode Sense: 0b 00 00 08
[ 8110.292000] sdb: assuming drive cache: write through
[ 8110.344000] SCSI device sdb: 122625 512-byte hdwr sectors (63 MB)
[ 8110.356000] sdb: Write Protect is off
[ 8110.356000] sdb: Mode Sense: 0b 00 00 08
[ 8110.356000] sdb: assuming drive cache: write through
[ 8110.356000]  sdb: sdb1
[ 8110.392000] sd 3:0:0:0: Attached scsi removable disk sdb
[ 8110.392000] sd 3:0:0:0: Attached scsi generic sg2 type 0
[11187.980000] atkbd.c: Unknown key pressed (translated set 2, code 0xee on isa0060/serio0).
[11187.980000] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
[11188.028000] atkbd.c: Unknown key released (translated set 2, code 0xee on isa0060/serio0).
[11188.028000] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
[11188.208000] atkbd.c: Unknown key pressed (translated set 2, code 0xee on isa0060/serio0).
[11188.208000] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
[11188.288000] atkbd.c: Unknown key released (translated set 2, code 0xee on isa0060/serio0).
[11188.288000] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
[11188.424000] atkbd.c: Unknown key pressed (translated set 2, code 0xee on isa0060/serio0).
[11188.424000] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
[11188.500000] atkbd.c: Unknown key released (translated set 2, code 0xee on isa0060/serio0).
[11188.500000] atkbd.c: Use 'setkeycodes e06e <keycode>' to make it known.
[13958.052000] usb 1-1: USB disconnect, address 5
[13958.144000] scsi 3:0:0:0: rejecting I/O to dead device

On the same notebook everything works fine with Ubuntu 6.10. I have another hd with the old installation and if I connect it the sound system works properly!

Any useful idea? :confused:

---

### Post by Swankyman on 2007-05-04
hey if your still here with us then try this in the terminal:

sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel probe_mask=8 model=auto

if that makes it work then put : 

options snd-hda-intel probe_mask=8 model=auto

at the end of this file using:

sudo gedit /etc/modprobe.d/alsa-base

Rich

p.s taken from here:

[http://ubuntuforums.org/showthread.php?t=415821&page=2](http://ubuntuforums.org/showthread.php?t=415821&page=2)

:)

---

### Post by Swankyman on 2007-05-04
woops that last reply was to obavjestenja

---

### Post by Swankyman on 2007-05-04
to solve yours fulvio6900  

you could try adding 

acpi=ht 

to your boot options as discussed on this thread:

[http://ubuntuforums.org/showthread.php?t=349231](http://ubuntuforums.org/showthread.php?t=349231)

rich

:)

---

### Post by fulvio6900 on 2007-05-04
I've tried with:

acpi=ht and restart -> no result
noapic (as shown here [http://ubuntuforums.org/showthread.php?p=2563598](http://ubuntuforums.org/showthread.php?p=2563598)) and restart -> no result

:(

---

### Post by Swankyman on 2007-05-04
can you paste your /boot/grub/menu.lst please

rich

---

### Post by fulvio6900 on 2007-05-04
Here it is:

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=56ecf4e1-364f-4350-be55-bb99d0024ada ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash locale=it_IT

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=56ecf4e1-364f-4350-be55-bb99d0024ada ro quiet splash locale=it_IT
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=56ecf4e1-364f-4350-be55-bb99d0024ada ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1



and here is where I added the coptions:

.
.
.
## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=56ecf4e1-364f-4350-be55-bb99d0024ada ro quiet splash locale=it_IT     <===
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault
.
.
.

---

### Post by obavjestenja on 2007-05-04
> **Swankyman said:**
> hey if your still here with us then try this in the terminal:

sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel probe_mask=8 model=auto

if that makes it work then put : 

options snd-hda-intel probe_mask=8 model=auto

at the end of this file using:

sudo gedit /etc/modprobe.d/alsa-base

Rich

p.s taken from here:

[http://ubuntuforums.org/showthread.php?t=415821&page=2](http://ubuntuforums.org/showthread.php?t=415821&page=2)

:)


THAT WORK !!!!!!

THANKS!!!!!!!!!!!!!!

I HAVE SOUND NOW .

---

### Post by Swankyman on 2007-05-04
Hi 
Im not sure if the boot/grub/menu.lst file you pasted is the original or modified. If the modified porition is the end block after the ´## ## End Default Options ##´ then you need to  put :

acpi=ht 

at the end of the kernel line and give that block a differnet title, thus change that whole end block to this:

title Ubuntu, kernel 2.6.20-15-generic-acpi=ht 
root (hd0,1)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=56ecf4e1-364f-4350-be55-bb99d0024ada ro quiet splash locale=it_IT acpi=ht 
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

then you can select it in grub when booting :)

if you had already done this then, not sure where to go form here :(

rich

---

### Post by karaju on 2007-05-05
Hello
I have installed feisty recently dual booting with winxp.  sound doesnt work for me at all.  I tried every thing suggested by almost every page of google search results to no avail.  I have via8237 sound card.
please help me.  I am already frustrated with linux.

---

### Post by Swankyman on 2007-05-05
hi,

we need a bit of information though.

can you attach the output of these commands from the terminal:

dmesg
lsmod
lspci
 
rich

---

### Post by karaju on 2007-05-05
thanks for the reply
this is what i got from the terminal

[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000000def0000 end: 000000000dff0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000dff0000 size: 0000000000003000 end: 000000000dff3000 type: 4
[    0.000000] copy_e820_map() start: 000000000dff3000 size: 000000000000d000 end: 000000000e000000 type: 3
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000001000 end: 00000000fec01000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000ffff0000 size: 0000000000010000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000000dff0000 (usable)
[    0.000000]  BIOS-e820: 000000000dff0000 - 000000000dff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000000dff3000 - 000000000e000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 223MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f4d70
[    0.000000] Entering add_active_range(0, 0, 57328) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    57328
[    0.000000]   HighMem     57328 ->    57328
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    57328
[    0.000000] On node 0 totalpages: 57328
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 415 pages used for memmap
[    0.000000]   Normal zone: 52817 pages, LIFO batch:15
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 GBT                                   ) @ 0x000f6770
[    0.000000] ACPI: RSDT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x0dff3000
[    0.000000] ACPI: FADT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x0dff3040
[    0.000000] ACPI: MADT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x0dff7600
[    0.000000] ACPI: DSDT (v001 GBT    AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:8 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 10000000 (gap: 0e000000:f0c00000)
[    0.000000] Detected 1010.049 MHz processor.
[   22.980019] Built 1 zonelists.  Total pages: 56881
[   22.980025] Kernel command line: root=UUID=0143b661-b8e3-492c-a6c1-123af66212da ro quiet splash
[   22.980345] mapped APIC to ffffd000 (fee00000)
[   22.980350] mapped IOAPIC to ffffc000 (fec00000)
[   22.980356] Enabling fast FPU save and restore... done.
[   22.980361] Enabling unmasked SIMD FPU exception support... done.
[   22.980380] Initializing CPU#0
[   22.980478] PID hash table entries: 1024 (order: 10, 4096 bytes)
[   22.981799] Console: colour VGA+ 80x25
[   22.982157] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[   22.982413] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[   22.993255] Memory: 216128k/229312k available (1992k kernel code, 12696k reserved, 893k data, 328k init, 0k highmem)
[   22.993275] virtual kernel memory layout:
[   22.993277]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   22.993279]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   22.993282]     vmalloc : 0xce800000 - 0xff7fe000   ( 783 MB)
[   22.993284]     lowmem  : 0xc0000000 - 0xcdff0000   ( 223 MB)
[   22.993287]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   22.993289]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   22.993292]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   22.993298] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   23.072407] Calibrating delay using timer specific routine.. 2022.19 BogoMIPS (lpj=4044384)
[   23.072490] Security Framework v1.0.0 initialized
[   23.072502] SELinux:  Disabled at boot.
[   23.072534] Mount-cache hash table entries: 512
[   23.072810] CPU: After generic identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
[   23.072828] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   23.072833] CPU: L2 Cache: 256K (64 bytes/line)
[   23.072838] CPU: After all inits, caps: 0383fbff c1cbfbff 00000000 00000420 00000000 00000000 00000000
[   23.072858] Compat vDSO mapped to ffffe000.
[   23.072868] Remapping vsyscall page to ffffe000
[   23.072886] Checking 'hlt' instruction... OK.
[   23.088616] SMP alternatives: switching to UP code
[   23.089064] Freeing SMP alternatives: 11k freed
[   23.089527] Early unpacking initramfs... done
[   23.695177] ACPI: Core revision 20060707
[   23.699376] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   23.713079] CPU0: AMD Athlon(tm)  stepping 01
[   23.713123] Total of 1 processors activated (2022.19 BogoMIPS).
[   23.713877] ENABLING IO-APIC IRQs
[   23.714194] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   23.859828] Brought up 1 CPUs
[   23.860303] Booting paravirtualized kernel on bare hardware
[   23.860433] Time: 19:25:29  Date: 04/05/107
[   23.860495] NET: Registered protocol family 16
[   23.860678] EISA bus registered
[   23.860686] ACPI: bus type pci registered
[   23.868987] PCI: PCI BIOS revision 2.10 entry at 0xfa410, last bus=1
[   23.868992] PCI: Using configuration type 1
[   23.868996] Setting up standard PCI resources
[   23.880702] ACPI: Interpreter enabled
[   23.880713] ACPI: Using IOAPIC for interrupt routing
[   23.881811] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   23.881821] PCI: Probing PCI hardware (bus 00)
[   23.882893] Boot video device is 0000:01:00.0
[   23.882953] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   23.929503] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 6 7 10 *11 12)
[   23.930126] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 6 7 10 11 12) *5
[   23.930748] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 6 7 *10 11 12)
[   23.931345] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   23.931915] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   23.932453] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   23.932985] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   23.933519] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 6 7 10 11 12) *0, disabled.
[   23.934279] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0, disabled.
[   23.935034] ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0, disabled.
[   23.935841] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0, disabled.
[   23.936594] ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0, disabled.
[   23.941725] Linux Plug and Play Support v0.97 (c) Adam Belay
[   23.941763] pnp: PnP ACPI init
[   23.949382] pnp: PnP ACPI: found 14 devices
[   23.949392] PnPBIOS: Disabled by ACPI PNP
[   23.949510] PCI: Using ACPI for IRQ routing
[   23.949518] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   23.976773] NET: Registered protocol family 8
[   23.976778] NET: Registered protocol family 20
[   23.977453] pnp: 00:02: ioport range 0x4000-0x407f could not be reserved
[   23.977460] pnp: 00:02: ioport range 0x40f0-0x40ff could not be reserved
[   23.977466] pnp: 00:02: ioport range 0x5000-0x500f has been reserved
[   23.978027] PCI: Bridge: 0000:00:01.0
[   23.978031]   IO window: disabled.
[   23.978039]   MEM window: dc000000-ddffffff
[   23.978045]   PREFETCH window: d8000000-dbffffff
[   23.978071] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   23.978123] NET: Registered protocol family 2
[   24.015769] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[   24.015924] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[   24.016103] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[   24.016197] TCP: Hash tables configured (established 8192 bind 4096)
[   24.016203] TCP reno registered
[   24.027821] checking if image is initramfs... it is
[   25.180436] Freeing initrd memory: 7009k freed
[   25.181361] audit: initializing netlink socket (disabled)
[   25.181390] audit(1178393131.272:1): initialized
[   25.181601] VFS: Disk quotas dquot_6.5.1
[   25.181641] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   25.181732] io scheduler noop registered
[   25.181737] io scheduler anticipatory registered
[   25.181742] io scheduler deadline registered
[   25.181756] io scheduler cfq registered (default)
[   25.181838] PCI: Bypassing VIA 8237 APIC De-Assert Message
[   25.182218] isapnp: Scanning for PnP cards...
[   25.536008] isapnp: No Plug & Play device found
[   25.595290] Real Time Clock Driver v1.12ac
[   25.595386] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   25.595561] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.595939] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   25.597134] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.597701] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   25.598364] mice: PS/2 mouse device common for all mice
[   25.599387] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   25.599865] input: Macintosh mouse button emulation as /class/input/input0
[   25.599931] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   25.599939] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   25.600301] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   25.600673] serio: i8042 KBD port at 0x60,0x64 irq 1
[   25.600683] serio: i8042 AUX port at 0x60,0x64 irq 12
[   25.600918] EISA: Probing bus 0 at eisa.0
[   25.600949] Cannot allocate resource for EISA slot 4
[   25.600954] Cannot allocate resource for EISA slot 5
[   25.600973] EISA: Detected 0 cards.
[   25.631115] TCP cubic registered
[   25.631129] NET: Registered protocol family 1
[   25.631172] Using IPI No-Shortcut mode
[   25.631303] ACPI: (supports S0 S1 S4 S5)
[   25.631391]   Magic number: 7:757:444
[   25.632387] Freeing unused kernel memory: 328k freed
[   25.634240] Time: tsc clocksource has been installed.
[   25.651342] input: AT Translated Set 2 keyboard as /class/input/input1
[   27.124480] Capability LSM initialized
[   28.162297] SCSI subsystem initialized
[   28.172015] libata version 2.20 loaded.
[   28.179934] VP_IDE: IDE controller at PCI slot 0000:00:0f.0
[   28.180712] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
[   28.180719] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[   28.180735] ACPI: PCI Interrupt 0000:00:0f.0[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 16
[   28.180756] VP_IDE: chipset revision 6
[   28.180760] VP_IDE: not 100% native mode: will probe irqs later
[   28.180777] VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.0
[   28.180791]     ide0: BM-DMA at 0xd000-0xd007, BIOS settings: hda:DMA, hdb:pio
[   28.180813]     ide1: BM-DMA at 0xd008-0xd00f, BIOS settings: hdc:DMA, hdd:pio
[   28.180827] Probing IDE interface ide0...
[   28.206534] usbcore: registered new interface driver usbfs
[   28.206583] usbcore: registered new interface driver hub
[   28.206629] usbcore: registered new device driver usb
[   28.208483] USB Universal Host Controller Interface driver v3.0
[   28.313941] via-rhine.c:v1.10-LK1.4.2 Sept-11-2006 Written by Donald Becker
[   28.568652] Floppy drive(s): fd0 is 1.44M
[   28.595585] FDC 0 is a post-1991 82077
[   28.643407] hda: ST340016A, ATA DISK drive
[   29.315128] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   29.318857] Probing IDE interface ide1...
[   30.185977] hdc: LITE-ON LTR-16101B, ATAPI CD/DVD-ROM drive
[   30.521869] ide1 at 0x170-0x177,0x376 on irq 15
[   30.524036] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 0, using IRQ 21
[   30.524045] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 21
[   30.524062] ACPI: PCI Interrupt 0000:00:10.0[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   30.524084] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   30.524623] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   30.524672] uhci_hcd 0000:00:10.0: irq 17, io base 0x0000d400
[   30.525804] usb usb1: configuration #1 chosen from 1 choice
[   30.526234] hub 1-0:1.0: USB hub found
[   30.526260] hub 1-0:1.0: 2 ports detected
[   30.540384] hda: max request size: 128KiB
[   30.563029] hda: Host Protected Area detected.
[   30.563034]  current capacity is 78163247 sectors (40019 MB)
[   30.563037]  native  capacity is 78165360 sectors (40020 MB)
[   30.563374] hda: Host Protected Area disabled.
[   30.563381] hda: 78165360 sectors (40020 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(33)
[   30.563392] hda: cache flushes not supported
[   30.563494]  hda: hda1 hda2 < hda5 hda6 hda7 hda8<6>ACPI: PCI Interrupt 0000:00:10.1[A] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   30.633752] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   30.633799] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   30.633834] uhci_hcd 0000:00:10.1: irq 17, io base 0x0000d800
[   30.634030] usb usb2: configuration #1 chosen from 1 choice
[   30.634094] hub 2-0:1.0: USB hub found
[   30.634112] hub 2-0:1.0: 2 ports detected
[   30.646075]  hda9 >
[   30.666295] hdc: ATAPI 40X CD-ROM CD-R/RW drive, 2048kB Cache, DMA
[   30.666312] Uniform CD-ROM driver Revision: 3.20
[   30.741613] ACPI: PCI Interrupt 0000:00:10.2[B] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   30.741638] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   30.741691] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   30.741727] uhci_hcd 0000:00:10.2: irq 17, io base 0x0000dc00
[   30.741926] usb usb3: configuration #1 chosen from 1 choice
[   30.741994] hub 3-0:1.0: USB hub found
[   30.742012] hub 3-0:1.0: 2 ports detected
[   30.849698] ACPI: PCI Interrupt 0000:00:10.4[C] -> Link [ALKB] -> GSI 21 (level, low) -> IRQ 17
[   30.849726] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   30.849778] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 4
[   30.849872] ehci_hcd 0000:00:10.4: irq 17, io mem 0xde008000
[   30.849883] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   30.850052] usb usb4: configuration #1 chosen from 1 choice
[   30.850104] hub 4-0:1.0: USB hub found
[   30.850120] hub 4-0:1.0: 6 ports detected
[   30.873267] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   30.958350] ACPI: PCI Interrupt Link [ALKD] BIOS reported IRQ 0, using IRQ 23
[   30.958360] ACPI: PCI Interrupt Link [ALKD] enabled at IRQ 23
[   30.958376] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKD] -> GSI 23 (level, low) -> IRQ 18
[   30.958535] eth0: VIA Rhine II at 0x1e400, 00:14:85:93:0b:24, IRQ 18.
[   30.959304] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 41e1.
[   31.084969] Attempting manual resume
[   31.084978] swsusp: Resume From Partition 3:9
[   31.084981] PM: Checking swsusp image.
[   31.096504] PM: Resume from disk failed.
[   31.146917] kjournald starting.  Commit interval 5 seconds
[   31.146942] EXT3-fs: mounted filesystem with ordered data mode.
[   32.132098] usb 1-1: new full speed USB device using uhci_hcd and address 3
[   32.327015] usb 1-1: configuration #1 chosen from 1 choice
[   41.787143] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   42.159402] NET: Registered protocol family 10
[   42.159595] lo: Disabled Privacy Extensions
[   45.846731] Linux agpgart interface v0.102 (c) Dave Jones
[   45.881294] agpgart: Detected VIA KM400/KM400A chipset
[   45.892835] agpgart: AGP aperture is 128M @ 0xd0000000
[   46.402402] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   46.654388] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   47.285405] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 19
[   47.302596] input: PC Speaker as /class/input/input2
[   47.359525] Linux video capture interface: v2.00
[   47.530379] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   47.530735] parport: PnPBIOS parport detected.
[   47.530787] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   47.603824] ubuntu/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(SPCA500+unknown CCD)
[   47.605157] usbcore: registered new interface driver gspca
[   47.605168] ubuntu/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
[   48.177411] ACPI: PCI interrupt for device 0000:00:09.0 disabled
[   48.177435] Yamaha DS-1 PCI: probe of 0000:00:09.0 failed with error -16
[   48.178668] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 0, using IRQ 22
[   48.178675] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[   48.178693] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 20
[   48.178852] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   48.980071] fuse init (API version 7.8)
[   49.025148] lp0: using parport0 (interrupt-driven).
[   49.089217] Adding 433712k swap on /dev/disk/by-uuid/f71fd86b-f943-b0b3-e377-25463d049a9a.  Priority:-1 extents:1 across:433712k
[   49.397671] EXT3 FS on hda8, internal journal
[   52.153483] eth0: no IPv6 routers present
[   63.505390] NET: Registered protocol family 17
[   67.879034] PPP generic driver version 2.4.2
[   68.592214] ibm_acpi: ec object not found
[   68.718229] input: Power Button (FF) as /class/input/input4
[   68.718701] ACPI: Power Button (FF) [PWRF]
[   68.758226] input: Power Button (CM) as /class/input/input5
[   68.758718] ACPI: Power Button (CM) [PWRB]
[   68.855585] No dock devices found.
[   68.930418] Using specific hotkey driver
[   69.309388] pcc_acpi: loading...
[   77.208545] [drm] Initialized drm 1.1.0 20060810
[   77.249745] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 21
[   77.255936] [drm] Initialized via 2.11.0 20061227 on minor 0
[   77.302071] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   77.302715] agpgart: Device is in legacy mode, falling back to 2.x
[   77.303146] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   77.303774] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   77.312117] [drm:via_mem_alloc] *ERROR* Attempt to allocate from uninitialized memory manager.
[   77.626764] ppdev: user-space parallel port driver
[   78.701958] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   78.701971] apm: overridden by ACPI.
[   78.972953] Bluetooth: Core ver 2.11
[   78.973083] NET: Registered protocol family 31
[   78.973087] Bluetooth: HCI device and connection manager initialized
[   78.973095] Bluetooth: HCI socket layer initialized
[   79.040188] Bluetooth: L2CAP ver 2.8
[   79.040198] Bluetooth: L2CAP socket layer initialized
[   79.129462] Bluetooth: RFCOMM socket layer initialized
[   79.129498] Bluetooth: RFCOMM TTY layer initialized
[   79.129502] Bluetooth: RFCOMM ver 1.8
raju@raju-desktop:~$ ismod
bash: ismod: command not found
raju@raju-desktop:~$ ispci
bash: ispci: command not found
raju@raju-desktop:~$ 

now to the next step in helping me please
thanks

---

### Post by Swankyman on 2007-05-05
hi,

do these again:
 
lspci 

and 

lsmod

but copy and paste to terminal because you typed them wrong :) the first letters are l not a i

rich

---

### Post by karaju on 2007-05-05
Hello again,
Thank you for your kind response.  I am starting to regain my confidence in ubuntu because of your prompt attention and help.

here is what i got with those two commands:

raju@raju-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:09.0 Multimedia audio controller: Yamaha Corporation YMF-724 (rev 05)
00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)
raju@raju-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
via                    44160  2 
drm                    81044  3 via
cpufreq_conservative     8200  0 
cpufreq_stats           7360  0 
cpufreq_ondemand        9228  0 
cpufreq_userspace       5408  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
tc1100_wmi              8068  0 
sony_acpi               6284  0 
pcc_acpi               13184  0 
dev_acpi               12292  0 
sbs                    15652  0 
ac                      6020  0 
container               5248  0 
i2c_ec                  5888  1 sbs
battery                10756  0 
asus_acpi              17308  0 
video                  16388  0 
dock                   10268  0 
button                  8720  0 
backlight               7040  1 asus_acpi
ppp_generic            29076  0 
slhc                    7680  1 ppp_generic
af_packet              23816  2 
nls_iso8859_1           5120  4 
nls_cp437               6784  4 
vfat                   14208  4 
fat                    53916  1 vfat
lp                     12452  0 
fuse                   46612  0 
serio_raw               7940  0 
gspca                 607824  0 
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
videodev               28160  1 gspca
v4l2_common            25216  1 videodev
v4l1_compat            15236  1 videodev
snd_via82xx            29208  2 
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
psmouse                38920  0 
pcspkr                  4224  0 
snd_seq_midi            9600  0 
snd_ymfpci             62368  0 
gameport               16520  2 snd_via82xx,snd_ymfpci
snd_ac97_codec         98336  2 snd_via82xx,snd_ymfpci
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  5 snd_via82xx,snd_ymfpci,snd_ac97_codec,snd_pcm_oss
snd_opl3_lib           11520  1 snd_ymfpci
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_hwdep               9988  1 snd_opl3_lib
snd_page_alloc         10888  3 snd_via82xx,snd_ymfpci,snd_pcm
snd_mpu401_uart         9472  2 snd_via82xx,snd_ymfpci
snd_timer              23684  4 snd_ymfpci,snd_pcm,snd_opl3_lib,snd_seq
snd_rawmidi            25472  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          9100  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_opl3_lib,snd_seq,snd_rawmidi
via_agp                11264  1 
i2c_viapro             10132  0 
i2c_core               22784  2 i2c_ec,i2c_viapro
agpgart                35400  2 drm,via_agp
snd                    54020  17 snd_via82xx,snd_seq_oss,snd_ymfpci,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_seq,snd_hwdep,snd_mpu401_uart,snd_timer,snd_rawmidi,snd_seq_device
soundcore               8672  1 snd
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
evdev                  11008  3 
tsdev                   8768  0 
ipv6                  268704  10 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
ide_cd                 32672  0 
cdrom                  37664  1 ide_cd
ide_disk               17024  7 
via82cxxx              10372  0 [permanent]
generic                 5124  0 [permanent]
floppy                 59524  0 
via_rhine              25608  0 
mii                     6528  1 via_rhine
ata_generic             9092  0 
libata                125720  1 ata_generic
scsi_mod              142348  1 libata
ehci_hcd               34188  0 
uhci_hcd               25360  0 
usbcore               134280  4 gspca,ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability
raju@raju-desktop:~$ 

now please tell me what to do.   thanks

---

### Post by armornutz on 2007-05-06
Don't know if this will help, but go to Apps-Add/Remove-Sound&Video. Make sure that Alsamixergui and Alsamixer are checked. They were not on mine, checked them and that did the trick.

---

### Post by karaju on 2007-05-06
hello
the files u suggested are not in add/remove application but they are available in synaptic.  even after installing those two files, i am back to square one.  I think this  problem can not be solved at this time and it may need further development of linux/ubuntu.  thanks for the help anyway.  if u come across some solution to the problem,  please email me at [email]karaju8000@gmail.com[/email].

---

### Post by Swankyman on 2007-05-06
Hi

From the look of it your sound card is detected properly (unless it has a strange prbolem). Me and the previous post think your volume is too low. To check do this:

In a terminal type 

alsamixer

using the up and and left/right keys select each column and set each one to max ( a full bar)

then using the m button make sure each column has a green 00 at the bottom and not MM (meaning mute)

press esc to leave the program

then try playing something

rich

---

### Post by karaju on 2007-05-07
hello,
the files  you suggested are not in add/remove application but are available in synaptic.  Even after installing them, I could not get the sound.  I see lot of posts regarding sound problems in forums and I think it needs some   further development in ubuntu to make things work.  It is strange that the sound card is detected and set as default, no sound comes even after installing the drivers.  The sound is working fine in winxp.  Thanks for your kind help.

regards

---

### Post by Swankyman on 2007-05-07
hi

did you type alsamixer in the terminal like I suggested. and did you make sure your volumes using that program were at full.>????

alsamixer is installed by default so you dont need to install it

:confused: 

rich

---

### Post by luke411 on 2007-05-07
I tried every command and every post on here but these worked. You have to install the Also Mixer, as suggested. It IS in the add/remove programs. Then open it and making sure that all of the volumes are turned up, play with the small buttons at the bottom of the "pc speaker" slider and the "external amplifier" slider. Just click them off and on until you get sound, going from one to the other. I wish I could tell you which was on and which was off but the graphics are so screwed up in the program, that you really can't tell.

Thanks for the tip guys.

---

### Post by bertschollaert on 2007-05-08
Hello,

Looked at all the posts, still no mic recording, nor in sound recorder or krec. Also trying to open gnome-volume-control doesn't work, result is segmentation fault (core dumped). Alsamixer looks fine to me, all checked and unmuted. No idea anymore what to do next.
Thank you in advance for all help!

Here is result of lsmod:
bertaxelle@mshome:/proc$ lsmod
Module                  Size  Used by
isofs                  36284  1 
udf                    85252  0 
binfmt_misc            12680  1 
ipv6                  268704  14 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
ppdev                  10116  0 
radeon                124576  2 
drm                    81044  3 radeon
speedstep_lib           6148  0 
cpufreq_userspace       5408  0 
cpufreq_conservative     8200  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7360  0 
cpufreq_ondemand        9228  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
pcc_acpi               13184  0 
sony_acpi               6284  0 
dev_acpi               12292  0 
tc1100_wmi              8068  0 
video                  16388  0 
battery                10756  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
ac                      6020  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
button                  8720  0 
container               5248  0 
dock                   10268  0 
sbp2                   23812  0 
lp                     12452  0 
fuse                   46612  0 
saa7134_alsa           15392  0 
snd_intel8x0           34204  4 
snd_ac97_codec         98336  1 snd_intel8x0
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
tuner                  61864  0 
snd_pcm                79876  5 saa7134_alsa,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
xpad                    9988  0 
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
saa7134               122080  1 saa7134_alsa
video_buf              26116  2 saa7134_alsa,saa7134
compat_ioctl32          2304  1 saa7134
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
ir_kbd_i2c              9872  1 saa7134
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
i2c_core               22784  4 i2c_ec,tuner,saa7134,ir_kbd_i2c
snd_timer              23684  3 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ir_common              31236  2 saa7134,ir_kbd_i2c
snd                    54020  17 saa7134_alsa,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                38920  0 
videodev               28160  1 saa7134
v4l2_common            25216  3 tuner,saa7134,videodev
v4l1_compat            15236  2 saa7134,videodev
soundcore               8672  1 snd
usbhid                 26592  0 
serio_raw               7940  0 
snd_page_alloc         10888  2 snd_intel8x0,snd_pcm
hid                    27392  1 usbhid
pcspkr                  4224  0 
parport_pc             36388  1 
parport                36936  3 ppdev,lp,parport_pc
intel_agp              25116  1 
agpgart                35400  2 drm,intel_agp
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
af_packet              23816  6 
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
evdev                  11008  5 
tsdev                   8768  0 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sr_mod                 17060  1 
sd_mod                 23428  3 
cdrom                  37664  1 sr_mod
generic                 5124  0 [permanent]
ata_generic             9092  0 
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
ehci_hcd               34188  0 
floppy                 59524  0 
uhci_hcd               25360  0 
ata_piix               15492  3 
libata                125720  2 ata_generic,ata_piix
scsi_mod              142348  5 sbp2,sg,sr_mod,sd_mod,libata
via_rhine              25608  0 
mii                     6528  1 via_rhine
usbcore               134280  5 xpad,usbhid,ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability


Here is result of lspci:
bertaxelle@mshome:/proc$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 NJ [Radeon 9800 XT]
01:00.1 Display controller: ATI Technologies Inc RV350 NJ [Radeon 9800 XT] (Secondary)
02:00.0 Network controller: Intersil Corporation ISL3886 [Prism Javelin/Prism Xbow] (rev 01)
02:02.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
02:04.0 Communication controller: Intel Corporation 536EP Data Fax Modem
02:09.0 Ethernet controller: VIA Technologies, Inc. VT6105 [Rhine-III] (rev 8b)
02:0a.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)

Here is result of dmesg: 
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000f0000 size: 0000000000010000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fef0000 end: 000000001fff0000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001fff0000 size: 0000000000003000 end: 000000001fff3000 type: 4
[    0.000000] copy_e820_map() start: 000000001fff3000 size: 000000000000d000 end: 0000000020000000 type: 3
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000001400000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f5020
[    0.000000] Entering add_active_range(0, 0, 131056) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131056
[    0.000000]   HighMem    131056 ->   131056
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131056
[    0.000000] On node 0 totalpages: 131056
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125969 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 IntelR                                ) @ 0x000f6a90
[    0.000000] ACPI: RSDT (v001 IntelR AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3000
[    0.000000] ACPI: FADT (v001 IntelR AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff3040
[    0.000000] ACPI: MADT (v001 IntelR AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x1fff7180
[    0.000000] ACPI: DSDT (v001 INTELR AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:2 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:2 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] Detected 2992.647 MHz processor.
[   20.477265] Built 1 zonelists.  Total pages: 130033
[   20.477268] Kernel command line: root=UUID=83f40fa6-bd4f-4377-816e-55afcf196b87 ro quiet splash locale=nl_NL
[   20.477415] mapped APIC to ffffd000 (fee00000)
[   20.477418] mapped IOAPIC to ffffc000 (fec00000)
[   20.477420] Enabling fast FPU save and restore... done.
[   20.477423] Enabling unmasked SIMD FPU exception support... done.
[   20.477433] Initializing CPU#0
[   20.477504] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   20.478503] Console: colour VGA+ 80x25
[   20.478770] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   20.479003] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   20.487984] Memory: 508480k/524224k available (1992k kernel code, 15212k reserved, 893k data, 328k init, 0k highmem)
[   20.487993] virtual kernel memory layout:
[   20.487994]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   20.487995]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   20.487995]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   20.487996]     lowmem  : 0xc0000000 - 0xdfff0000   ( 511 MB)
[   20.487997]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   20.487998]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   20.487999]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   20.488002] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   20.565466] Calibrating delay using timer specific routine.. 5989.52 BogoMIPS (lpj=11979054)
[   20.565504] Security Framework v1.0.0 initialized
[   20.565510] SELinux:  Disabled at boot.
[   20.565526] Mount-cache hash table entries: 512
[   20.565659] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[   20.565670] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   20.565673] CPU: L2 cache: 512K
[   20.565675] CPU: Physical Processor ID: 0
[   20.565677] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003080 00004400 00000000 00000000
[   20.565689] Compat vDSO mapped to ffffe000.
[   20.565692] Remapping vsyscall page to ffffe000
[   20.565703] Checking 'hlt' instruction... OK.
[   20.581543] SMP alternatives: switching to UP code
[   20.581872] Early unpacking initramfs... done
[   20.844738] ACPI: Core revision 20060707
[   20.850171] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   20.853644] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09
[   20.853668] SMP alternatives: switching to SMP code
[   20.853852] Booting processor 1/1 eip 3000
[   20.864120] Initializing CPU#1
[   20.941279] Calibrating delay using timer specific routine.. 5985.43 BogoMIPS (lpj=11970868)
[   20.941287] CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
[   20.941297] CPU: Trace cache: 12K uops, L1 D cache: 8K
[   20.941300] CPU: L2 cache: 512K
[   20.941302] CPU: Physical Processor ID: 0
[   20.941304] CPU: After all inits, caps: bfebfbff 00000000 00000000 00003080 00004400 00000000 00000000
[   20.941460] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 09
[   20.941498] Total of 2 processors activated (11974.96 BogoMIPS).
[   20.941627] ENABLING IO-APIC IRQs
[   20.941805] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   21.089216] checking TSC synchronization across 2 CPUs: passed.
[    0.003998] Brought up 2 CPUs
[    0.061320] migration_cost=206
[    0.061615] Booting paravirtualized kernel on bare hardware
[    0.061698] Time: 20:15:33  Date: 04/08/107
[    0.061729] NET: Registered protocol family 16
[    0.061829] EISA bus registered
[    0.061834] ACPI: bus type pci registered
[    0.088743] PCI: PCI BIOS revision 2.10 entry at 0xfb270, last bus=2
[    0.088746] PCI: Using configuration type 1
[    0.088747] Setting up standard PCI resources
[    0.109235] ACPI: Interpreter enabled
[    0.109239] ACPI: Using IOAPIC for interrupt routing
[    0.109920] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.109926] PCI: Probing PCI hardware (bus 00)
[    0.110536] PCI quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[    0.110540] PCI quirk: region 0480-04bf claimed by ICH4 GPIO
[    0.110760] Boot video device is 0000:01:00.0
[    0.111145] PCI: Transparent bridge - 0000:00:1e.0
[    0.111170] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.119728] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.123697] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.123965] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.124212] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[    0.124457] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[    0.124698] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.124940] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.125189] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.125433] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.125702] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.125720] pnp: PnP ACPI init
[    0.129230] pnp: PnP ACPI: found 13 devices
[    0.129236] PnPBIOS: Disabled by ACPI PNP
[    0.129306] PCI: Using ACPI for IRQ routing
[    0.129310] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.146076] NET: Registered protocol family 8
[    0.146078] NET: Registered protocol family 20
[    0.146474] pnp: 00:0b: ioport range 0x400-0x4bf could not be reserved
[    0.146848] PCI: Bridge: 0000:00:01.0
[    0.146851]   IO window: a000-afff
[    0.146856]   MEM window: f8000000-f9ffffff
[    0.146860]   PREFETCH window: e8000000-f7ffffff
[    0.146865] PCI: Bridge: 0000:00:1e.0
[    0.146867]   IO window: b000-bfff
[    0.146872]   MEM window: fa000000-fa7fffff
[    0.146876]   PREFETCH window: disabled.
[    0.146892] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.146930] NET: Registered protocol family 2
[    0.199959] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.200047] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.200114] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.200148] TCP: Hash tables configured (established 16384 bind 8192)
[    0.200151] TCP reno registered
[    0.216004] checking if image is initramfs... it is
[    0.741985] Freeing initrd memory: 6995k freed
[    0.742439] audit: initializing netlink socket (disabled)
[    0.742453] audit(1178655334.436:1): initialized
[    0.742670] VFS: Disk quotas dquot_6.5.1
[    0.742693] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.742749] io scheduler noop registered
[    0.742752] io scheduler anticipatory registered
[    0.742754] io scheduler deadline registered
[    0.742766] io scheduler cfq registered (default)
[    0.743090] isapnp: Scanning for PnP cards...
[    1.096466] isapnp: No Plug & Play device found
[    1.123932] Real Time Clock Driver v1.12ac
[    1.123988] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    1.124099] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.124261] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a XScale
[    1.124882] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.125151] mice: PS/2 mouse device common for all mice
[    1.125846] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    1.126013] input: Macintosh mouse button emulation as /class/input/input0
[    1.126056] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    1.126060] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    1.126377] PNP: No PS/2 controller found. Probing ports directly.
[    1.128443] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.128449] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.128577] EISA: Probing bus 0 at eisa.0
[    1.128616] EISA: Detected 0 cards.
[    1.158702] TCP cubic registered
[    1.158710] NET: Registered protocol family 1
[    1.158737] Starting balanced_irq
[    1.158745] Using IPI No-Shortcut mode
[    1.158860] ACPI: (supports S0 S3 S4 S5)
[    1.158907]   Magic number: 7:435:295
[    1.158935]   hash matches device ttyz9
[    1.158948]   hash matches device ttywc
[    1.159057]   hash matches device tty28
[    1.159354] Freeing unused kernel memory: 328k freed
[    1.159419] Time: tsc clocksource has been installed.
[    2.377836] Capability LSM initialized
[    2.416975] ACPI: Fan [FAN] (on)
[    2.422436] ACPI: Thermal Zone [THRM] (40 C)
[    2.906994] usbcore: registered new interface driver usbfs
[    2.907031] usbcore: registered new interface driver hub
[    3.088869] usbcore: registered new device driver usb
[    3.091011] via-rhine.c:v1.10-LK1.4.2 Sept-11-2006 Written by Donald Becker
[    3.091435] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 20 (level, low) -> IRQ 16
[    3.096979] eth0: VIA Rhine III at 0x1b000, 00:0c:76:c4:37:8e, IRQ 16.
[    3.097705] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 0021.
[    3.105540] SCSI subsystem initialized
[    3.112626] libata version 2.20 loaded.
[    3.114534] ata_piix 0000:00:1f.1: version 2.10ac1
[    3.114560] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 17
[    3.114582] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    3.114652] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x0001f000 irq 14
[    3.140568] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x0001f008 irq 15
[    3.140604] USB Universal Host Controller Interface driver v3.0
[    3.141061] scsi0 : ata_piix
[    3.143803] Floppy drive(s): fd0 is 1.44M
[    3.153966] ieee1394: Initialized config rom entry `ip1394'
[    3.166071] FDC 0 is a post-1991 82077
[    3.650425] ata1.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[    3.650430] ata1.00: ATA-6: ST3200021A, 3.01, max UDMA/100
[    3.650433] ata1.00: 390721968 sectors, multi 16: LBA48 
[    3.650435] ata1.01: ATAPI, max UDMA/33
[    3.662411] ata1.00: ata_hpa_resize 1: sectors = 390721968, hpa_sectors = 390721968
[    3.662414] ata1.00: configured for UDMA/100
[    3.834152] ata1.01: configured for UDMA/33
[    3.834168] scsi1 : ata_piix
[    4.157990] ata2.00: ATAPI, max UDMA/33
[    4.325899] ata2.00: configured for UDMA/33
[    4.326034] scsi 0:0:0:0: Direct-Access     ATA      ST3200021A       3.01 PQ: 0 ANSI: 5
[    4.326356] scsi 0:0:1:0: CD-ROM            IDE      DVD-ROM 16X      7.92 PQ: 0 ANSI: 5
[    4.333281] scsi 1:0:0:0: CD-ROM            PIONEER  DVD RW  DVR-107D 1.05 PQ: 0 ANSI: 5
[    4.333707] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 18
[    4.333727] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    4.333733] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.334056] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    4.334091] uhci_hcd 0000:00:1d.0: irq 18, io base 0x0000cc00
[    4.335595] usb usb1: configuration #1 chosen from 1 choice
[    4.335819] hub 1-0:1.0: USB hub found
[    4.335830] hub 1-0:1.0: 2 ports detected
[    4.441784] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[    4.441804] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    4.441811] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.441845] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    4.441875] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000c000
[    4.442014] usb usb2: configuration #1 chosen from 1 choice
[    4.442066] hub 2-0:1.0: USB hub found
[    4.442085] hub 2-0:1.0: 2 ports detected
[    4.549717] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 17
[    4.549733] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    4.549738] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.549772] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    4.549802] uhci_hcd 0000:00:1d.2: irq 17, io base 0x0000c400
[    4.549950] usb usb3: configuration #1 chosen from 1 choice
[    4.550008] hub 3-0:1.0: USB hub found
[    4.550021] hub 3-0:1.0: 2 ports detected
[    4.657661] ACPI: PCI Interrupt 0000:00:1d.3[A] -> GSI 16 (level, low) -> IRQ 18
[    4.657676] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    4.657682] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    4.657720] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    4.657745] uhci_hcd 0000:00:1d.3: irq 18, io base 0x0000c800
[    4.657893] usb usb4: configuration #1 chosen from 1 choice
[    4.657958] hub 4-0:1.0: USB hub found
[    4.657971] hub 4-0:1.0: 2 ports detected
[    4.681517] usb 1-2: new low speed USB device using uhci_hcd and address 2
[    4.765776] ACPI: PCI Interrupt 0000:00:1d.7[D] -> GSI 23 (level, low) -> IRQ 20
[    4.765799] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.765804] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.765857] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    4.765913] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[    4.765928] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfa800000
[    4.769821] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.770011] usb usb5: configuration #1 chosen from 1 choice
[    4.770061] hub 5-0:1.0: USB hub found
[    4.770076] hub 5-0:1.0: 8 ports detected
[    4.877694] ACPI: PCI Interrupt 0000:02:0a.0[A] -> GSI 21 (level, low) -> IRQ 21
[    4.930535] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[fa404000-fa4047ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    4.954345] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[    4.954373] sda: Write Protect is off
[    4.954377] sda: Mode Sense: 00 3a 00 00
[    4.954413] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.954503] SCSI device sda: 390721968 512-byte hdwr sectors (200050 MB)
[    4.954523] sda: Write Protect is off
[    4.954528] sda: Mode Sense: 00 3a 00 00
[    4.956614] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.956623]  sda: sda1 sda2 sda3 sda4 < sda5 >
[    4.998727] sd 0:0:0:0: Attached scsi disk sda
[    5.001281] sr0: scsi3-mmc drive: 0x/48x cd/rw xa/form2 cdda tray
[    5.001287] Uniform CD-ROM driver Revision: 3.20
[    5.001376] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    5.004009] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    5.004040] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    5.004069] sr 1:0:0:0: Attached scsi generic sg2 type 5
[    5.014169] sr1: scsi3-mmc drive: 62x/62x writer cd/rw xa/form2 cdda tray
[    5.014514] sr 1:0:0:0: Attached scsi CD-ROM sr1
[    5.221223] usb 1-2: device not accepting address 2, error -71
[    5.288778] Attempting manual resume
[    5.288782] swsusp: Resume From Partition 8:5
[    5.288784] PM: Checking swsusp image.
[    5.289107] PM: Resume from disk failed.
[    5.314497] kjournald starting.  Commit interval 5 seconds
[    5.314511] EXT3-fs: mounted filesystem with ordered data mode.
[    6.216861] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc000057779c]
[    6.324643] usb 1-2: new low speed USB device using uhci_hcd and address 4
[    6.557620] usb 1-2: configuration #1 chosen from 1 choice
[    6.800383] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    6.924321] usb 2-1: device descriptor read/64, error -71
[    7.152196] usb 2-1: device descriptor read/64, error -71
[    7.368081] usb 2-1: new full speed USB device using uhci_hcd and address 3
[    7.492014] usb 2-1: device descriptor read/64, error -71
[    7.719894] usb 2-1: device descriptor read/64, error -71
[    7.935781] usb 2-1: new full speed USB device using uhci_hcd and address 4
[    8.351556] usb 2-1: device not accepting address 4, error -71
[    8.463500] usb 2-1: new full speed USB device using uhci_hcd and address 5
[    8.879284] usb 2-1: device not accepting address 5, error -71
[    9.119152] usb 4-1: new low speed USB device using uhci_hcd and address 2
[    9.309523] usb 4-1: configuration #1 chosen from 1 choice
[   13.560361] eth0: link up, 10Mbps, half-duplex, lpa 0x0021
[   14.818017] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.981750] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.997062] NET: Registered protocol family 17
[   15.017542] iTCO_vendor_support: vendor-support=0
[   15.019920] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   15.020051] iTCO_wdt: Found a ICH5 or ICH5R TCO device (Version=1, TCOBASE=0x0460)
[   15.020088] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   15.062077] Linux agpgart interface v0.102 (c) Dave Jones
[   15.071004] intel_rng: FWH not detected
[   15.082423] agpgart: Detected an Intel 865 Chipset.
[   15.088104] agpgart: AGP aperture is 128M @ 0xe0000000
[   15.568331] parport: PnPBIOS parport detected.
[   15.568384] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   15.585570] input: PC Speaker as /class/input/input1
[   15.951759] usbcore: registered new interface driver hiddev
[   16.046290] Linux video capture interface: v2.00
[   16.081721] input: Chicony USB Wireless HID Receiver as /class/input/input2
[   16.081775] input: USB HID v1.10 Keyboard [Chicony USB Wireless HID Receiver] on usb-0000:00:1d.0-2
[   16.195556] input: Chicony USB Wireless HID Receiver as /class/input/input3
[   16.195678] input,hiddev96: USB HID v1.10 Device [Chicony USB Wireless HID Receiver] on usb-0000:00:1d.0-2
[   16.220545] input: Chicony USB Wireless HID Receiver as /class/input/input4
[   16.220677] input: USB HID v1.10 Mouse [Chicony USB Wireless HID Receiver] on usb-0000:00:1d.0-2
[   16.282207] saa7130/34: v4l2 driver version 0.2.14 loaded
[   16.282285] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 18 (level, low) -> IRQ 17
[   16.282297] saa7134[0]: found at 0000:02:02.0, rev: 1, irq: 17, latency: 32, mmio: 0xfa402000
[   16.282305] saa7134[0]: subsystem: 16be:0003, board: Medion 7134 [card=12,autodetected]
[   16.282319] saa7134[0]: board init: gpio is 0
[   16.333517] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /class/input/input5
[   16.333647] input: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.3-1
[   16.333668] usbcore: registered new interface driver usbhid
[   16.333673] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   16.404836] usbcore: registered new interface driver xpad
[   16.404843] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[   16.451253] saa7134[0]: i2c eeprom 00: be 16 03 00 08 20 1c 55 43 43 a9 1c 55 43 43 a9
[   16.451274] saa7134[0]: i2c eeprom 10: ff ff ff ff 15 00 0e 01 0c c0 08 00 00 00 00 00
[   16.451292] saa7134[0]: i2c eeprom 20: 00 00 00 e3 ff ff ff ff ff ff ff ff ff ff ff ff
[   16.451310] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.451328] saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.451346] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.451364] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.451382] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.475242] saa7134[0] Tuner type is 38
[   16.567201] tuner 0-0043: chip found @ 0x86 (saa7134[0])
[   16.567280] tda9887 0-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   16.591181] tuner 0-0060: All bytes are equal. It is not a TEA5767
[   16.591187] tuner 0-0060: chip found @ 0xc0 (saa7134[0])
[   16.591241] tuner 0-0060: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[   16.591245] tuner 0-0060: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[   16.595253] saa7134[0]: registered device video0 [v4l2]
[   16.595284] saa7134[0]: registered device vbi0
[   16.595309] saa7134[0]: registered device radio0
[   16.595363] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 22
[   16.595408] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   16.617748] saa7134 ALSA driver for DMA sound loaded
[   16.617795] saa7134[0]/alsa: saa7134[0] at 0xfa402000 irq 17 registered as card -2
[   16.915000] intel8x0_measure_ac97_clock: measured 59176 usecs
[   16.915004] intel8x0: clocking to 48000
[   17.206472] fuse init (API version 7.8)
[   17.222285] lp0: using parport0 (interrupt-driven).
[   17.280385] Adding 1510068k swap on /dev/disk/by-uuid/8f0baf95-3c86-48c6-b174-9da00dd37e96.  Priority:-1 extents:1 across:1510068k
[   17.387384] EXT3 FS on sda2, internal journal
[   22.732205] No dock devices found.
[   22.757406] input: Power Button (FF) as /class/input/input6
[   22.757441] ACPI: Power Button (FF) [PWRF]
[   22.757501] input: Power Button (CM) as /class/input/input7
[   22.757533] ACPI: Power Button (CM) [PWRB]
[   22.757577] input: Sleep Button (CM) as /class/input/input8
[   22.757618] ACPI: Sleep Button (CM) [SLPB]
[   22.965771] ibm_acpi: ec object not found
[   23.047225] Using specific hotkey driver
[   23.119796] pcc_acpi: loading...
[   29.583299] [drm] Initialized drm 1.1.0 20060810
[   29.596898] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 18
[   29.597731] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[   30.289855] ppdev: user-space parallel port driver
[   31.539300] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   31.539498] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[   31.539692] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
[   31.586720] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   31.586727] apm: disabled - APM is not SMP safe.
[   31.843831] Bluetooth: Core ver 2.11
[   31.843926] NET: Registered protocol family 31
[   31.843929] Bluetooth: HCI device and connection manager initialized
[   31.843934] Bluetooth: HCI socket layer initialized
[   31.868798] [drm] Setting GART location based on new memory map
[   31.868811] [drm] Loading R300 Microcode
[   31.868854] [drm] writeback test succeeded in 1 usecs
[   31.952140] Bluetooth: L2CAP ver 2.8
[   31.952149] Bluetooth: L2CAP socket layer initialized
[   32.002987] usb 2-1: new full speed USB device using uhci_hcd and address 6
[   32.126922] usb 2-1: device descriptor read/64, error -71
[   32.354793] usb 2-1: device descriptor read/64, error -71
[   32.570671] usb 2-1: new full speed USB device using uhci_hcd and address 7
[   32.694606] usb 2-1: device descriptor read/64, error -71
[   32.922484] usb 2-1: device descriptor read/64, error -71
[   33.138373] usb 2-1: new full speed USB device using uhci_hcd and address 8
[   33.554154] usb 2-1: device not accepting address 8, error -71
[   33.666099] usb 2-1: new full speed USB device using uhci_hcd and address 9
[   34.081870] usb 2-1: device not accepting address 9, error -71
[   34.157574] Bluetooth: RFCOMM socket layer initialized
[   34.157594] Bluetooth: RFCOMM TTY layer initialized
[   34.157597] Bluetooth: RFCOMM ver 1.8
[   35.115671] NET: Registered protocol family 10
[   35.115810] lo: Disabled Privacy Extensions
[   46.031510] eth0: no IPv6 routers present
[  468.830679] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[  468.830706] agpgart: Putting AGP V3 device at 0000:00:00.0 into 4x mode
[  468.830741] agpgart: Putting AGP V3 device at 0000:01:00.0 into 4x mode
[  468.830783] [drm] Loading R300 Microcode

---

### Post by Swankyman on 2007-05-09
hi,

two more things to try

when you are in alsamixer press tab, this swaps between playback/capture/all. 
make sure the settings in capture are full too.

2)Right click on the volume control applet, select ´open volume control´ 
then in the file pull down menu select ´change device´ and select each device making sure all settings for each one is un muted and full

Rich

---

### Post by bertschollaert on 2007-05-09
Thank you very much for your response, Rich.
right clicking the applet and choosing "open volume control "unfortunately also doesn't work: for a few seconds I see the volume-control tab in the task bar, then it disappears (same behaviour as typing it in a console).
Here are some alsamixer screenshots. I can't seem to move up the mic volume in capture mode.
> [ATTACH]32166[/ATTACH]

[ATTACH]32167[/ATTACH]

[ATTACH]32168[/ATTACH]

Thanks in advance

---

### Post by stchman on 2007-05-09
> **obavjestenja said:**
> How can i make my sound to work with Feisty.
Please help but  in simple IT english:) .
Thanks.

The ATI SB450 sound supprt is buggy in Feisty.  I recommend using Edgy as it just works with that card.

---

### Post by Swankyman on 2007-05-10
Hi,

try running volume control from the terminal to see if it tells you why it dies
type:

gnome-volume-control

rich

---

### Post by bertschollaert on 2007-05-10
Well, that's what I mentioned before: I just get a "segmentation fault (core dumped)". In task bar I see it for a few seconds starting, then it disappears. Same behaviour I had also with edgy and with a fresh install from another cd of Feisty.

---

### Post by tinti on 2007-05-17
Try this:
acpi=noirq noapic

---

### Post by bertschollaert on 2007-05-17
Thank you for the response. Please tell me where exactly I have to type that. Thanks

---

