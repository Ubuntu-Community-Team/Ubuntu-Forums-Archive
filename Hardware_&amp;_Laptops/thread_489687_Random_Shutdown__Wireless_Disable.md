---
title: "Random Shutdown / Wireless Disable"
date: 2007-07-01
forum: Hardware &amp; Laptops
---

### Post by lookformeb on 2007-07-01
I am currently running Kubuntu Fiesty and having some issues I'm hoping to iron out.

----------------------------------
My laptop, when idle, will sometimes shut itself down.  I find this most common after I have been asleep wake up to a laptop that is off, even though I had tasks running all night.  This is extremely frustrating... more so than my wireless disabling (I'll discuss next).  My power management scheme is as follows:

General Settings: Lock screen on resume
Mains Powered: Do nothing
Batter powered: When battery remaining time drops below 5 min - Shutdown
When Laptop Lid Closed: Lock screen

 I've looked through KSytemLog and hadn't been able to find the issue there.  Can someone help point me in the right direction?
----------------------------------
Now, when my Laptop does this, I find the wireless disabled. The toggle switch doesn't work, and I can only get it back up my inserting a PCLinuxOS 2007 Live CD and setting up the network after the GUI boots.  I've tried the following suggestion as mentioned in the Networking & Wireless forums:

# sudo nano /etc/default/acpi-support
```
# Add services to this list to stop them before suspend and restart them in
# the resume process.
STOP_SERVICES="networking"
```----------------------------------

No luck.  Any help would be appreciated... this is very consistent and frustrating.

---

### Post by lookformeb on 2007-07-02
*bump*

---

### Post by Ayuthia on 2007-07-02
Do you see any messages when you type dmesg or /var/log/messages?

---

### Post by lookformeb on 2007-07-03
```
$ dmesg
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
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
[    0.000000] ACPI: RSDT (v001 INSYDE RSDT_000 0x00000001 _CSI 0x00010101) @ 0x3fffa7f0
[    0.000000] ACPI: FADT (v001 COMPAL DCL56    0x00000200 _CSI 0x00010101) @ 0x3ffffb00
[    0.000000] ACPI: BOOT (v001 INSYDE SYS_BOOT 0x00000100 _CSI 0x00010101) @ 0x3ffffb90
[    0.000000] ACPI: DBGP (v001 INSYDE DBGP_000 0x00000100 _CSI 0x00010101) @ 0x3ffffbc0
[    0.000000] ACPI: SSDT (v001 INSYDE   GV3Ref 0x00002000 INTL 0x20021002) @ 0x3fffa830
[    0.000000] ACPI: DSDT (v001 COMPAL   DCL561 0x00000006 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bfb80000)
[    0.000000] Detected 1993.693 MHz processor.
[    7.830555] Built 1 zonelists.  Total pages: 260081
[    7.830559] Kernel command line: root=UUID=f2db0809-08f4-4d50-bf89-177269e9374a ro quiet splash
[    7.830703] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    7.830712] mapped APIC to ffffd000 (0180c000)
[    7.830715] Enabling fast FPU save and restore... done.
[    7.830718] Enabling unmasked SIMD FPU exception support... done.
[    7.830729] Initializing CPU#0
[    7.830802] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    7.831994] Console: colour VGA+ 80x25
[    7.832544] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    7.833088] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    7.865939] Memory: 1028308k/1048512k available (1992k kernel code, 19468k reserved, 900k data, 328k init, 131008k highmem)
[    7.865947] virtual kernel memory layout:
[    7.865948]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[    7.865949]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    7.865951]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    7.865952]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    7.865953]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[    7.865954]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[    7.865955]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[    7.865958] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    7.942669] Calibrating delay using timer specific routine.. 3989.73 BogoMIPS (lpj=7979460)
[    7.942705] Security Framework v1.0.0 initialized
[    7.942712] SELinux:  Disabled at boot.
[    7.942726] Mount-cache hash table entries: 512
[    7.942848] CPU: After generic identify, caps: afe9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
[    7.942859] CPU: L1 I cache: 32K, L1 D cache: 32K
[    7.942861] CPU: L2 cache: 2048K
[    7.942863] CPU: After all inits, caps: afe9f9bf 00000000 00000000 00002040 00000180 00000000 00000000
[    7.942872] Compat vDSO mapped to ffffe000.
[    7.942875] Remapping vsyscall page to ffffe000
[    7.942885] Checking 'hlt' instruction... OK.
[    7.958736] SMP alternatives: switching to UP code
[    7.958928] Freeing SMP alternatives: 11k freed
[    7.959087] Early unpacking initramfs... done
[    8.242093] ACPI: Core revision 20060707
[    8.242198] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[    8.243763] ACPI: setting ELCR to 0200 (from 0c00)
[    8.250293] CPU0: Intel(R) Pentium(R) M processor 2.00GHz stepping 06
[    8.250298] SMP motherboard not detected.
[    8.250300] Local APIC not detected. Using dummy APIC emulation.
[    8.250332] Brought up 1 CPUs
[    8.250537] Booting paravirtualized kernel on bare hardware
[    8.250605] Time: 18:50:13  Date: 06/01/107
[    8.250630] NET: Registered protocol family 16
[    8.250702] EISA bus registered
[    8.250705] ACPI: bus type pci registered
[    8.250737] PCI: PCI BIOS revision 2.10 entry at 0xe97a4, last bus=2
[    8.250739] PCI: Using configuration type 1
[    8.250740] Setting up standard PCI resources
[    8.252864] ACPI: Interpreter enabled
[    8.252866] ACPI: Using PIC for interrupt routing
[    8.253198] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    8.253201] PCI: Probing PCI hardware (bus 00)
[    8.253988] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[    8.253992] PCI quirk: region 1300-133f claimed by ICH4 GPIO
[    8.254218] Boot video device is 0000:01:00.0
[    8.254467] PCI: Transparent bridge - 0000:00:1e.0
[    8.254513] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
[    8.254516] Please report the result to linux-kernel to fix this permanently
[    8.254531] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    8.259757] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[    8.259888] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB_._PRT]
[    8.260864] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 *10)
[    8.261033] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 10) *11
[    8.261201] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 10) *11
[    8.261369] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 10) *11
[    8.261546] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    8.261719] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    8.261893] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    8.262068] ACPI: PCI Interrupt Link [LNKH] (IRQs 5 10) *11
[    8.303314] Linux Plug and Play Support v0.97 (c) Adam Belay
[    8.303321] pnp: PnP ACPI init
[    8.326434] pnp: PnP ACPI: found 11 devices
[    8.326437] PnPBIOS: Disabled by ACPI PNP
[    8.326472] PCI: Using ACPI for IRQ routing
[    8.326475] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    8.326500] PCI: Cannot allocate resource region 0 of device 0000:02:03.0
[    8.329151] NET: Registered protocol family 8
[    8.329152] NET: Registered protocol family 20
[    8.329489] PCI: Bridge: 0000:00:01.0
[    8.329491]   IO window: c000-dfff
[    8.329494]   MEM window: e0000000-efffffff
[    8.329497]   PREFETCH window: a0000000-afffffff
[    8.329504] PCI: Bus 3, cardbus bridge: 0000:02:03.0
[    8.329506]   IO window: 0000a400-0000a4ff
[    8.329510]   IO window: 0000a800-0000a8ff
[    8.329514]   PREFETCH window: 90000000-93ffffff
[    8.329517]   MEM window: d4000000-d7ffffff
[    8.329521] PCI: Bridge: 0000:00:1e.0
[    8.329523]   IO window: a000-bfff
[    8.329528]   MEM window: d0000000-dfffffff
[    8.329532]   PREFETCH window: 90000000-9fffffff
[    8.329545] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    8.329684] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[    8.329686] PCI: setting IRQ 10 as level-triggered
[    8.329689] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[    8.329711] NET: Registered protocol family 2
[    8.362200] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    8.362320] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    8.363270] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    8.363932] TCP: Hash tables configured (established 131072 bind 65536)
[    8.363936] TCP reno registered
[    8.374287] checking if image is initramfs... it is
[    8.926956] Freeing initrd memory: 6772k freed
[    8.927209] Simple Boot Flag at 0x37 set to 0x1
[    8.927396] audit: initializing netlink socket (disabled)
[    8.927413] audit(1183315814.280:1): initialized
[    8.927485] highmem bounce pool size: 64 pages
[    8.927546] VFS: Disk quotas dquot_6.5.1
[    8.927566] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    8.927619] io scheduler noop registered
[    8.927622] io scheduler anticipatory registered
[    8.927624] io scheduler deadline registered
[    8.927634] io scheduler cfq registered (default)
[    8.927926] isapnp: Scanning for PnP cards...
[    9.281305] isapnp: No Plug & Play device found
[    9.302467] Real Time Clock Driver v1.12ac
[    9.302524] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    9.302720] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    9.303419] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[    9.303422] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[    9.303431] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[    9.303501] mice: PS/2 mouse device common for all mice
[    9.303991] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    9.304191] input: Macintosh mouse button emulation as /class/input/input0
[    9.304221] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    9.304224] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    9.304453] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    9.304717] i8042.c: Detected active multiplexing controller, rev 1.1.
[    9.304757] serio: i8042 KBD port at 0x60,0x64 irq 1
[    9.304761] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    9.304763] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    9.304765] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    9.304767] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    9.304861] EISA: Probing bus 0 at eisa.0
[    9.304868] Cannot allocate resource for EISA slot 1
[    9.304895] EISA: Detected 0 cards.
[    9.335024] TCP cubic registered
[    9.335036] NET: Registered protocol family 1
[    9.335057] Using IPI No-Shortcut mode
[    9.335112] ACPI: (supports S0 S1 S3 S4 S5)
[    9.335149]   Magic number: 15:775:846
[    9.335244]   hash matches device ptyrf
[    9.335566] Freeing unused kernel memory: 328k freed
[    9.336953] Time: tsc clocksource has been installed.
[    9.337155] input: AT Translated Set 2 keyboard as /class/input/input1
[   10.517280] Capability LSM initialized
[   10.546128] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[   10.546134] ACPI: Processor [CPU0] (supports 8 throttling states)
[   10.826778] usbcore: registered new interface driver usbfs
[   10.826799] usbcore: registered new interface driver hub
[   10.826820] usbcore: registered new device driver usb
[   10.827504] USB Universal Host Controller Interface driver v3.0
[   10.827746] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[   10.827749] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   10.827759] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   10.827762] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   10.827915] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   10.827937] uhci_hcd 0000:00:1d.0: irq 10, io base 0x00001200
[   10.828023] usb usb1: configuration #1 chosen from 1 choice
[   10.828041] hub 1-0:1.0: USB hub found
[   10.828046] hub 1-0:1.0: 2 ports detected
[   10.931310] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[   10.931315] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[   10.931326] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   10.931330] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   10.931354] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   10.931378] uhci_hcd 0000:00:1d.1: irq 10, io base 0x00001600
[   10.931465] usb usb2: configuration #1 chosen from 1 choice
[   10.931486] hub 2-0:1.0: USB hub found
[   10.931492] hub 2-0:1.0: 2 ports detected
[   10.969728] ieee1394: Initialized config rom entry `ip1394'
[   10.978957] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   11.034988] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   11.035001] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   11.035005] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   11.035023] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   11.035045] uhci_hcd 0000:00:1d.2: irq 10, io base 0x00001700
[   11.035124] usb usb3: configuration #1 chosen from 1 choice
[   11.035151] hub 3-0:1.0: USB hub found
[   11.035159] hub 3-0:1.0: 2 ports detected
[    3.264000] Time: acpi_pm clocksource has been installed.
[    3.312000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[    3.312000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[    3.312000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.312000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.312000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    3.312000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.312000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.312000] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xf4000000
[    3.316000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.316000] usb usb4: configuration #1 chosen from 1 choice
[    3.316000] hub 4-0:1.0: USB hub found
[    3.316000] hub 4-0:1.0: 6 ports detected
[    3.424000] SCSI subsystem initialized
[    3.428000] libata version 2.20 loaded.
[    3.432000] ata_piix 0000:00:1f.1: version 2.10ac1
[    3.432000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[    3.432000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[    3.432000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    3.432000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011100 irq 14
[    3.432000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011108 irq 15
[    3.432000] scsi0 : ata_piix
[    3.596000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
[    3.596000] ata1.00: ATA-6: HTE726060M9AT00, MH4OA6AA, max UDMA/100
[    3.596000] ata1.00: 117210240 sectors, multi 16: LBA48 
[    3.604000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240
[    3.604000] ata1.00: configured for UDMA/100
[    3.604000] scsi1 : ata_piix
[    3.964000] ata2.00: ATAPI, max UDMA/33
[    4.152000] ata2.00: configured for UDMA/33
[    4.152000] scsi 0:0:0:0: Direct-Access     ATA      HTE726060M9AT00  MH4O PQ: 0 ANSI: 5
[    4.156000] scsi 1:0:0:0: CD-ROM            TOSHIBA  ODD-DVD SD-R6372 1030 PQ: 0 ANSI: 5
[    4.156000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[    4.208000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[d0010800-d0010fff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.216000] 8139cp 0000:02:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[    4.216000] 8139cp 0000:02:01.0: Try the "8139too" driver instead.
[    4.216000] 8139too Fast Ethernet driver 0.9.28
[    4.216000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[    4.216000] eth0: RealTek RTL8139 at 0xf88a2000, 00:02:3f:09:99:a3, IRQ 10
[    4.216000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    4.228000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[    4.228000] sda: Write Protect is off
[    4.228000] sda: Mode Sense: 00 3a 00 00
[    4.228000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.228000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[    4.228000] sda: Write Protect is off
[    4.228000] sda: Mode Sense: 00 3a 00 00
[    4.228000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.228000]  sda: sda1 sda2 < sda5 > sda3
[    4.264000] sd 0:0:0:0: Attached scsi disk sda
[    4.264000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.264000] scsi 1:0:0:0: Attached scsi generic sg1 type 5
[    4.280000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.280000] Uniform CD-ROM driver Revision: 3.20
[    4.280000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.452000] Attempting manual resume
[    4.452000] swsusp: Resume From Partition 8:5
[    4.452000] PM: Checking swsusp image.
[    4.452000] PM: Resume from disk failed.
[    4.488000] kjournald starting.  Commit interval 5 seconds
[    4.488000] EXT3-fs: mounted filesystem with ordered data mode.
[    5.488000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f495240117e]
[   14.084000] iTCO_vendor_support: vendor-support=0
[   14.084000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   14.084000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)
[   14.084000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   14.096000] intel_rng: Firmware space is locked read-only. If you can't or
[   14.096000] intel_rng: don't want to disable this in firmware setup, and if
[   14.096000] intel_rng: you are certain that your system has a functional
[   14.096000] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   14.364000] Linux agpgart interface v0.102 (c) Dave Jones
[   14.528000] agpgart: Detected an Intel 855PM Chipset.
[   14.532000] agpgart: AGP aperture is 64M @ 0xb0000000
[   14.752000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   14.756000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.944000] input: PC Speaker as /class/input/input2
[   14.952000] wbsd: Winbond W83L51xD SD/MMC card interface driver
[   14.952000] wbsd: Copyright(c) Pierre Ossman
[   14.952000] pnp: Device 00:0a activated.
[   14.960000] mmc0: W83L51xD id 7112 at 0x248 irq 6 FIFO PnP
[   15.000000] ath_hal: module license 'Proprietary' taints kernel.
[   15.000000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   15.056000] parport: PnPBIOS parport detected.
[   15.056000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   15.084000] irda_init()
[   15.084000] NET: Registered protocol family 23
[   15.112000] Yenta: CardBus bridge found at 0000:02:03.0 [14c0:0012]
[   15.112000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   15.112000] Yenta: Routing CardBus interrupts to PCI
[   15.112000] Yenta TI: socket 0000:02:03.0, mfunc 0x001c1112, devctl 0x44
[   15.124000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x254ab1, caps: 0x804713/0x0
[   15.156000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   15.204000] wlan: 0.8.4.2 (0.9.3)
[   15.264000] ath_pci: 0.9.4.5 (0.9.3)
[   15.344000] Yenta: ISA IRQ mask 0x0818, PCI irq 10
[   15.344000] Socket status: 30000006
[   15.344000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   15.344000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xbfff
[   15.344000] cs: IO port probe 0xa000-0xbfff: clean.
[   15.344000] pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xdfffffff
[   15.344000] pcmcia: parent PCI bridge Memory window: 0x90000000 - 0x9fffffff
[   15.352000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[   15.596000] ath_rate_sample: 1.2 (0.9.3)
[   15.596000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   15.596000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   15.596000] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   15.596000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   15.596000] wifi0: mac 5.6 phy 4.1 radio 4.6
[   15.596000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   15.596000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   15.596000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   15.596000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   15.596000] wifi0: Use hw queue 8 for CAB traffic
[   15.596000] wifi0: Use hw queue 9 for beacons
[   15.612000] wifi0: Atheros 5212: mem=0xd0000000, irq=10
[   15.848000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   15.848000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   16.024000] cs: IO port probe 0x100-0x3af: excluding 0x230-0x237
[   16.028000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   16.028000] cs: IO port probe 0x820-0x8ff: clean.
[   16.028000] cs: IO port probe 0xc00-0xcf7: clean.
[   16.028000] cs: IO port probe 0xa00-0xaff: clean.
[   16.668000] intel8x0_measure_ac97_clock: measured 55258 usecs
[   16.668000] intel8x0: clocking to 48000
[   16.764000] fuse init (API version 7.8)
[   16.784000] lp0: using parport0 (interrupt-driven).
[   16.824000] Adding 2441840k swap on /dev/disk/by-uuid/f4d24f1c-a9d1-4889-88e5-bcbee8f6f6fb.  Priority:-1 extents:1 across:2441840k
[   16.992000] EXT3 FS on sda1, internal journal
[   17.204000] kjournald starting.  Commit interval 5 seconds
[   17.208000] EXT3 FS on sda3, internal journal
[   17.208000] EXT3-fs: mounted filesystem with ordered data mode.
[   17.668000] ACPI: Battery Slot [BAT1] (battery present)
[   17.708000] input: Power Button (FF) as /class/input/input4
[   17.712000] ACPI: Power Button (FF) [PWRF]
[   17.712000] ACPI Error (evxfevnt-0189): Could not enable SleepButton event [20060707]
[   17.712000] ACPI Warning (evxface-0146): Could not enable fixed event 3 [20060707]
[   17.740000] input: Lid Switch as /class/input/input5
[   17.744000] ACPI: Lid Switch [LID]
[   17.772000] input: Power Button (CM) as /class/input/input6
[   17.776000] ACPI: Power Button (CM) [PWRB]
[   17.884000] No dock devices found.
[   17.916000] Using specific hotkey driver
[   17.944000] ACPI: AC Adapter [ACAD] (off-line)
[   17.952000] ibm_acpi: ec object not found
[   17.980000] pcc_acpi: loading...
[   20.728000] eth0: link down
[   20.748000] ppdev: user-space parallel port driver
[   21.612000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   21.612000] apm: overridden by ACPI.
[   22.136000] Bluetooth: Core ver 2.11
[   22.136000] NET: Registered protocol family 31
[   22.136000] Bluetooth: HCI device and connection manager initialized
[   22.136000] Bluetooth: HCI socket layer initialized
[   22.180000] Bluetooth: L2CAP ver 2.8
[   22.180000] Bluetooth: L2CAP socket layer initialized
[   22.320000] Bluetooth: RFCOMM socket layer initialized
[   22.320000] Bluetooth: RFCOMM TTY layer initialized
[   22.320000] Bluetooth: RFCOMM ver 1.8
[   23.792000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
[   23.792000] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0
[   23.812000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[   26.160000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[   26.160000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[   26.160000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
[   26.160000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   26.160000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   26.160000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   26.160000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[   26.164000] [fglrx] total      GART = 67108864
[   26.164000] [fglrx] free       GART = 51113984
[   26.164000] [fglrx] max single GART = 51113984
[   26.164000] [fglrx] total      LFB  = 134217728
[   26.164000] [fglrx] free       LFB  = 96432128
[   26.164000] [fglrx] max single LFB  = 96432128
[   26.164000] [fglrx] total      Inv  = 0
[   26.164000] [fglrx] free       Inv  = 0
[   26.164000] [fglrx] max single Inv  = 0
[   26.164000] [fglrx] total      TIM  = 0
[   60.740000] NET: Registered protocol family 10
[   60.740000] lo: Disabled Privacy Extensions
[   60.740000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   71.208000] ath0: no IPv6 routers present
[   77.788000] NET: Registered protocol family 17
[   91.160000] ath0: no IPv6 routers present
[  505.408000] end_request: I/O error, dev sr0, sector 14424576
[  505.408000] Buffer I/O error on device sr0, logical block 1803072
[  505.452000] end_request: I/O error, dev sr0, sector 14424576
[  505.452000] Buffer I/O error on device sr0, logical block 1803072
[  505.596000] end_request: I/O error, dev sr0, sector 14424480
[  505.596000] Buffer I/O error on device sr0, logical block 1803060
[  505.656000] end_request: I/O error, dev sr0, sector 14424480
[  505.656000] Buffer I/O error on device sr0, logical block 1803060
[  506.264000] UDF-fs: Partition marked readonly; forcing readonly mount
[  506.304000] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'BUFFALO_SOLDIERS', timestamp 2003/11/12 14:56 (1ed4)
[ 7996.200000] loop: loaded (max 8 devices)
[ 7996.412000] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 7996.432000] ISOFS: changing to secondary root
[ 9255.524000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 9255.524000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 9255.584000] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[ 9255.584000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 9255.664000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 9255.664000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 9255.732000] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[ 9255.732000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 9255.812000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[ 9255.812000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[ 9255.872000] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[ 9255.872000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[15349.868000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[15359.836000] psmouse.c: TouchPad at isa0060/serio4/input0 - driver resynched.
[23976.540000] usb 4-3: new high speed USB device using ehci_hcd and address 2
[23977.412000] hub 4-0:1.0: Cannot enable port 3.  Maybe the USB cable is bad?
[23977.524000] usb 4-3: new high speed USB device using ehci_hcd and address 3
[23977.656000] usb 4-3: configuration #1 chosen from 1 choice
[23978.036000] usbcore: registered new interface driver libusual
[23978.080000] Initializing USB Mass Storage driver...
[23978.084000] scsi2 : SCSI emulation for USB Mass Storage devices
[23978.084000] usbcore: registered new interface driver usb-storage
[23978.084000] USB Mass Storage support registered.
[23978.084000] usb-storage: device found at 3
[23978.084000] usb-storage: waiting for device to settle before scanning
[23980.584000] usb 4-3: USB disconnect, address 3
[23980.824000] usb 4-3: new high speed USB device using ehci_hcd and address 4
[23980.956000] usb 4-3: configuration #1 chosen from 1 choice
[23980.956000] scsi3 : SCSI emulation for USB Mass Storage devices
[23980.956000] usb-storage: device found at 4
[23980.956000] usb-storage: waiting for device to settle before scanning
[23985.956000] usb-storage: device scan complete
[23985.956000] scsi 3:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  2.18 PQ: 0 ANSI: 2
[23985.956000] SCSI device sdb: 990865 512-byte hdwr sectors (507 MB)
[23985.956000] sdb: Write Protect is off
[23985.956000] sdb: Mode Sense: 03 00 00 00
[23985.956000] sdb: assuming drive cache: write through
[23985.960000] SCSI device sdb: 990865 512-byte hdwr sectors (507 MB)
[23985.960000] sdb: Write Protect is off
[23985.960000] sdb: Mode Sense: 03 00 00 00
[23985.960000] sdb: assuming drive cache: write through
[23985.960000]  sdb: sdb1
[23985.964000] sd 3:0:0:0: Attached scsi removable disk sdb
[23985.964000] sd 3:0:0:0: Attached scsi generic sg2 type 0
[24097.764000] usb 4-3: USB disconnect, address 4
[29354.180000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[29354.180000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[29354.180000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
[29354.184000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[29354.184000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[29354.184000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[29354.184000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[29354.192000] [fglrx] total      GART = 67108864
[29354.192000] [fglrx] free       GART = 51113984
[29354.192000] [fglrx] max single GART = 51113984
[29354.192000] [fglrx] total      LFB  = 134217728
[29354.192000] [fglrx] free       LFB  = 96432128
[29354.192000] [fglrx] max single LFB  = 96432128
[29354.192000] [fglrx] total      Inv  = 0
[29354.192000] [fglrx] free       Inv  = 0
[29354.192000] [fglrx] max single Inv  = 0
[29354.192000] [fglrx] total      TIM  = 0
[29398.036000] end_request: I/O error, dev sr0, sector 14424576
[29398.036000] Buffer I/O error on device sr0, logical block 1803072
[29398.076000] end_request: I/O error, dev sr0, sector 14424576
[29398.076000] Buffer I/O error on device sr0, logical block 1803072
[29398.224000] end_request: I/O error, dev sr0, sector 14424480
[29398.224000] Buffer I/O error on device sr0, logical block 1803060
[29398.284000] end_request: I/O error, dev sr0, sector 14424480
[29398.284000] Buffer I/O error on device sr0, logical block 1803060
[29398.872000] UDF-fs: Partition marked readonly; forcing readonly mount
[29398.912000] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'BUFFALO_SOLDIERS', timestamp 2003/11/12 14:56 (1ed4)
[31354.296000] usb 4-3: new high speed USB device using ehci_hcd and address 5
[31354.432000] usb 4-3: configuration #1 chosen from 1 choice
[31354.432000] scsi4 : SCSI emulation for USB Mass Storage devices
[31354.432000] usb-storage: device found at 5
[31354.432000] usb-storage: waiting for device to settle before scanning
[31359.432000] usb-storage: device scan complete
[31359.436000] scsi 4:0:0:0: Direct-Access     Lexar    JD Mercury       1100 PQ: 0 ANSI: 0 CCS
[31359.464000] SCSI device sdb: 1965056 512-byte hdwr sectors (1006 MB)
[31359.464000] sdb: Write Protect is off
[31359.464000] sdb: Mode Sense: 43 00 00 00
[31359.464000] sdb: assuming drive cache: write through
[31359.472000] SCSI device sdb: 1965056 512-byte hdwr sectors (1006 MB)
[31359.472000] sdb: Write Protect is off
[31359.472000] sdb: Mode Sense: 43 00 00 00
[31359.472000] sdb: assuming drive cache: write through
[31359.472000]  sdb: sdb1
[31359.472000] sd 4:0:0:0: Attached scsi removable disk sdb
[31359.472000] sd 4:0:0:0: Attached scsi generic sg2 type 0
[33711.012000] usb 4-3: USB disconnect, address 5
[48928.680000] NET: Registered protocol family 4
[48928.740000] NET: Registered protocol family 3
[48928.768000] NET: Registered protocol family 5
[81893.268000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[81893.268000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[81893.376000] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[81893.376000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[81893.596000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[81893.596000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[81893.680000] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[81893.680000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[81893.792000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[81893.792000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[81893.868000] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[81893.868000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[81893.972000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[81893.972000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[81894.036000] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[81894.036000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[81894.128000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[81894.128000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[81894.184000] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[81894.184000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[81894.432000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[81894.432000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[81894.456000] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[81894.456000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[81894.564000] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[81894.564000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[81894.592000] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[81894.592000] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[84088.760000] end_request: I/O error, dev sr0, sector 14424576
[84088.760000] Buffer I/O error on device sr0, logical block 1803072
[84088.800000] end_request: I/O error, dev sr0, sector 14424576
[84088.800000] Buffer I/O error on device sr0, logical block 1803072
[84088.928000] end_request: I/O error, dev sr0, sector 14424480
[84088.928000] Buffer I/O error on device sr0, logical block 1803060
[84088.968000] end_request: I/O error, dev sr0, sector 14424480
[84088.968000] Buffer I/O error on device sr0, logical block 1803060
[84089.576000] UDF-fs: Partition marked readonly; forcing readonly mount
[84089.620000] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'BUFFALO_SOLDIERS', timestamp 2003/11/12 14:56 (1ed4)
[103380.992000] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[103380.992000] ata2.00: (BMDMA stat 0x24)
[103380.992000] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0x4a data 8 in
[103380.992000]          res 58/00:02:00:00:00/00:00:00:00:00/a0 Emask 0x2 (HSM violation)
[103380.992000] ata2: soft resetting port
[103381.524000] ata2.00: configured for UDMA/33
[103381.524000] ata2: EH complete
[106977.988000] end_request: I/O error, dev sr0, sector 14424576
[106977.988000] Buffer I/O error on device sr0, logical block 1803072
[106978.052000] end_request: I/O error, dev sr0, sector 14424576
[106978.052000] Buffer I/O error on device sr0, logical block 1803072
[106978.204000] end_request: I/O error, dev sr0, sector 14424480
[106978.204000] Buffer I/O error on device sr0, logical block 1803060
[106978.260000] end_request: I/O error, dev sr0, sector 14424480
[106978.260000] Buffer I/O error on device sr0, logical block 1803060
[106978.892000] UDF-fs: Partition marked readonly; forcing readonly mount
[106978.940000] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'BUFFALO_SOLDIERS', timestamp 2003/11/12 14:56 (1ed4)
[119301.456000] ADDRCONF(NETDEV_UP): ath0: link is not ready
[119302.404000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[119316.380000] ath0: no IPv6 routers present
[120757.004000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[120757.072000] ADDRCONF(NETDEV_UP): ath0: link is not ready
[120760.304000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[120774.664000] ath0: no IPv6 routers present

```

The /var/log/messages has several thousand lines of output (over 400kb of .txt).  What are we looking for in there?

---

### Post by Austin_KW on 2007-07-03
random laptop shutdown is often due to overheating, clean the dust out by blowing air through the air outtakes, or vacuum the air intakes.

---

### Post by lookformeb on 2007-07-09
Ok.  Any idea why the wireless would remain disabled after this happens?  My laptop hasn't randomly rebooted for days now, yet after I shutdown and turned it back on the wireless was disabled... I had to boot to the PCLinuxOS 2007 Live CD again to re-enable.

---

### Post by Ayuthia on 2007-07-09
Sorry for the late reply, Sometimes /var/log/messages will get logged when something gets disabled.  However, I am unable to see anything in this one that points that it was disabled.  You might check this log when you shutdown and wireless does not start up.

---

### Post by lookformeb on 2007-08-14
My laptop doesn't randomly shutdown anymore... however, when the battery remaining time reaches 5 minutes and it shutsdown automatically (as set by the power manager policy) the wireless card is no longer active (light is off).

The system shutdown at 9:59 PM.  Here are the logs:

/var/logs/syslog
```
08/13/2007 09:59:45 PM	laptop	init	tty1 main process (4009) killed by TERM signal

08/13/2007 09:59:45 PM	laptop	init	tty2 main process (4007) killed by TERM signal

08/13/2007 09:59:45 PM	laptop	init	tty3 main process (4008) killed by TERM signal

08/13/2007 09:59:45 PM	laptop	init	tty4 main process (4002) killed by TERM signal

08/13/2007 09:59:45 PM	laptop	init	tty5 main process (4003) killed by TERM signal

08/13/2007 09:59:45 PM	laptop	init	tty6 main process (4010) killed by TERM signal

08/13/2007 09:59:54 PM	laptop	none	exiting on signal 15

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000]     0:        0 ->   262128

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] 127MB HIGHMEM available.

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] 896MB LOWMEM available.

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] ACPI: BOOT (v001 INSYDE SYS_BOOT 0x00000100 _CSI 0x00010101) @ 0x3ffffb90

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] ACPI: DBGP (v001 INSYDE DBGP_000 0x00000100 _CSI 0x00010101) @ 0x3ffffbc0

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] ACPI: DSDT (v001 COMPAL   DCL561 0x00000006 MSFT 0x0100000e) @ 0x00000000

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] ACPI: FADT (v001 COMPAL DCL56    0x00000200 _CSI 0x00010101) @ 0x3ffffb00

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] ACPI: PM-Timer IO Port: 0x1008

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] ACPI: RSDP (v000 OID_00                                ) @ 0x000e6010

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] ACPI: RSDT (v001 INSYDE RSDT_000 0x00000001 _CSI 0x00010101) @ 0x3fffa7f0

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] ACPI: SSDT (v001 INSYDE   GV3Ref 0x00002000 INTL 0x20021002) @ 0x3fffa830

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bfb80000)

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fffffc0 (ACPI data)

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000]  BIOS-e820: 000000003fffffc0 - 0000000040000000 (ACPI NVS)

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] BIOS-provided physical RAM map:

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fef0000 end: 000000003fff0000 type: 1

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] copy_e820_map() start: 000000003fff0000 size: 000000000000ffc0 end: 000000003fffffc0 type: 3

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] copy_e820_map() start: 000000003fffffc0 size: 0000000000000040 end: 0000000040000000 type: 4

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] copy_e820_map() start: 00000000ffb80000 size: 0000000000080000 end: 00000000ffc00000 type: 2

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] copy_e820_map() start: 00000000fff80000 size: 0000000000080000 end: 0000000100000000 type: 2

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] copy_e820_map() type is E820_RAM

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] copy_e820_map() type is E820_RAM

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] Detected 1993.689 MHz processor.

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000]   DMA             0 ->     4096

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000]   DMA zone: 0 pages reserved

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000]   DMA zone: 32 pages used for memmap

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000]   DMA zone: 4064 pages, LIFO batch:0

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] DMI 2.3 present.

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] early_node_map[1] active PFN ranges

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] Entering add_active_range(0, 0, 262128) 0 entries of 256 used

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000]   HighMem    229376 ->   262128

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000]   HighMem zone: 255 pages used for memmap

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000]   HighMem zone: 32497 pages, LIFO batch:7

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000]   Normal       4096 ->   229376

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000]   Normal zone: 1760 pages used for memmap

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000]   Normal zone: 223520 pages, LIFO batch:31

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] On node 0 totalpages: 262128

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] sanitize end

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] sanitize start

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] Zone PFN ranges:

08/13/2007 10:00:47 PM	laptop	kernel	[   10.028836] isapnp: No Plug & Play device found

08/13/2007 10:00:47 PM	laptop	kernel	[   10.050354] Real Time Clock Driver v1.12ac

08/13/2007 10:00:47 PM	laptop	kernel	[   10.050413] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled

08/13/2007 10:00:47 PM	laptop	kernel	[   10.050612] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A

08/13/2007 10:00:47 PM	laptop	kernel	[   10.051321] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10

08/13/2007 10:00:47 PM	laptop	kernel	[   10.051325] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:00:47 PM	laptop	kernel	[   10.051333] ACPI: PCI interrupt for device 0000:00:1f.6 disabled

08/13/2007 10:00:47 PM	laptop	kernel	[   10.051404] mice: PS/2 mouse device common for all mice

08/13/2007 10:00:47 PM	laptop	kernel	[   10.051894] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize

08/13/2007 10:00:47 PM	laptop	kernel	[   10.052096] input: Macintosh mouse button emulation as /class/input/input0

08/13/2007 10:00:47 PM	laptop	kernel	[   10.052127] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2

08/13/2007 10:00:47 PM	laptop	kernel	[   10.052130] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

08/13/2007 10:00:47 PM	laptop	kernel	[   10.052358] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12

08/13/2007 10:00:47 PM	laptop	kernel	[   10.052630] i8042.c: Detected active multiplexing controller, rev 1.1.

08/13/2007 10:00:47 PM	laptop	kernel	[   10.052671] serio: i8042 KBD port at 0x60,0x64 irq 1

08/13/2007 10:00:47 PM	laptop	kernel	[   10.052674] serio: i8042 AUX0 port at 0x60,0x64 irq 12

08/13/2007 10:00:47 PM	laptop	kernel	[   10.052676] serio: i8042 AUX1 port at 0x60,0x64 irq 12

08/13/2007 10:00:47 PM	laptop	kernel	[   10.052678] serio: i8042 AUX2 port at 0x60,0x64 irq 12

08/13/2007 10:00:47 PM	laptop	kernel	[   10.052680] serio: i8042 AUX3 port at 0x60,0x64 irq 12

08/13/2007 10:00:47 PM	laptop	kernel	[   10.052778] EISA: Probing bus 0 at eisa.0

08/13/2007 10:00:47 PM	laptop	kernel	[   10.052785] Cannot allocate resource for EISA slot 1

08/13/2007 10:00:47 PM	laptop	kernel	[   10.052812] EISA: Detected 0 cards.

08/13/2007 10:00:47 PM	laptop	kernel	[   10.082942] TCP cubic registered

08/13/2007 10:00:47 PM	laptop	kernel	[   10.082954] NET: Registered protocol family 1

08/13/2007 10:00:47 PM	laptop	kernel	[   10.082975] Using IPI No-Shortcut mode

08/13/2007 10:00:47 PM	laptop	kernel	[   10.083031] ACPI: (supports S0 S1 S3 S4 S5)

08/13/2007 10:00:47 PM	laptop	kernel	[   10.083068]   Magic number: 3:340:7

08/13/2007 10:00:47 PM	laptop	kernel	[   10.083485] Freeing unused kernel memory: 328k freed

08/13/2007 10:00:47 PM	laptop	kernel	[   10.084418] Time: tsc clocksource has been installed.

08/13/2007 10:00:47 PM	laptop	kernel	[   10.085076] input: AT Translated Set 2 keyboard as /class/input/input1

08/13/2007 10:00:47 PM	laptop	kernel	[   11.264784] Capability LSM initialized

08/13/2007 10:00:47 PM	laptop	kernel	[   11.293697] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])

08/13/2007 10:00:47 PM	laptop	kernel	[   11.293703] ACPI: Processor [CPU0] (supports 8 throttling states)

08/13/2007 10:00:47 PM	laptop	kernel	[   11.576455] usbcore: registered new interface driver usbfs

08/13/2007 10:00:47 PM	laptop	kernel	[   11.576477] usbcore: registered new interface driver hub

08/13/2007 10:00:47 PM	laptop	kernel	[   11.576498] usbcore: registered new device driver usb

08/13/2007 10:00:47 PM	laptop	kernel	[   11.577220] USB Universal Host Controller Interface driver v3.0

08/13/2007 10:00:47 PM	laptop	kernel	[   11.577466] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10

08/13/2007 10:00:47 PM	laptop	kernel	[   11.577469] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:00:47 PM	laptop	kernel	[   11.577479] PCI: Setting latency timer of device 0000:00:1d.0 to 64

08/13/2007 10:00:47 PM	laptop	kernel	[   11.577482] uhci_hcd 0000:00:1d.0: UHCI Host Controller

08/13/2007 10:00:47 PM	laptop	kernel	[   11.577644] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1

08/13/2007 10:00:47 PM	laptop	kernel	[   11.577667] uhci_hcd 0000:00:1d.0: irq 10, io base 0x00001200

08/13/2007 10:00:47 PM	laptop	kernel	[   11.577759] usb usb1: configuration #1 chosen from 1 choice

08/13/2007 10:00:47 PM	laptop	kernel	[   11.577777] hub 1-0:1.0: USB hub found

08/13/2007 10:00:47 PM	laptop	kernel	[   11.577783] hub 1-0:1.0: 2 ports detected

08/13/2007 10:00:47 PM	laptop	kernel	[   11.635016] ieee1394: Initialized config rom entry `ip1394'

08/13/2007 10:00:47 PM	laptop	kernel	[   11.644369] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)

08/13/2007 10:00:47 PM	laptop	kernel	[   11.678778] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10

08/13/2007 10:00:47 PM	laptop	kernel	[   11.678783] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:00:47 PM	laptop	kernel	[   11.678795] PCI: Setting latency timer of device 0000:00:1d.1 to 64

08/13/2007 10:00:47 PM	laptop	kernel	[   11.678799] uhci_hcd 0000:00:1d.1: UHCI Host Controller

08/13/2007 10:00:47 PM	laptop	kernel	[   11.678822] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2

08/13/2007 10:00:47 PM	laptop	kernel	[   11.678844] uhci_hcd 0000:00:1d.1: irq 10, io base 0x00001600

08/13/2007 10:00:47 PM	laptop	kernel	[   11.678933] usb usb2: configuration #1 chosen from 1 choice

08/13/2007 10:00:47 PM	laptop	kernel	[   11.678953] hub 2-0:1.0: USB hub found

08/13/2007 10:00:47 PM	laptop	kernel	[   11.678959] hub 2-0:1.0: 2 ports detected

08/13/2007 10:00:47 PM	laptop	kernel	[   11.782458] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:00:47 PM	laptop	kernel	[   11.782471] PCI: Setting latency timer of device 0000:00:1d.2 to 64

08/13/2007 10:00:47 PM	laptop	kernel	[   11.782476] uhci_hcd 0000:00:1d.2: UHCI Host Controller

08/13/2007 10:00:47 PM	laptop	kernel	[   11.782494] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3

08/13/2007 10:00:47 PM	laptop	kernel	[   11.782517] uhci_hcd 0000:00:1d.2: irq 10, io base 0x00001700

08/13/2007 10:00:47 PM	laptop	kernel	[   11.782597] usb usb3: configuration #1 chosen from 1 choice

08/13/2007 10:00:47 PM	laptop	kernel	[   11.782621] hub 3-0:1.0: USB hub found

08/13/2007 10:00:47 PM	laptop	kernel	[   11.782627] hub 3-0:1.0: 2 ports detected

08/13/2007 10:00:47 PM	laptop	kernel	[   14.676000] Linux agpgart interface v0.102 (c) Dave Jones

08/13/2007 10:00:47 PM	laptop	kernel	[   14.680000] iTCO_vendor_support: vendor-support=0

08/13/2007 10:00:47 PM	laptop	kernel	[   14.680000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)

08/13/2007 10:00:47 PM	laptop	kernel	[   14.680000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)

08/13/2007 10:00:47 PM	laptop	kernel	[   14.680000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)

08/13/2007 10:00:47 PM	laptop	kernel	[   14.692000] intel_rng: don't want to disable this in firmware setup, and if

08/13/2007 10:00:47 PM	laptop	kernel	[   14.692000] intel_rng: Firmware space is locked read-only. If you can't or

08/13/2007 10:00:47 PM	laptop	kernel	[   14.692000] intel_rng: RNG, try using the 'no_fwh_detect' option.

08/13/2007 10:00:47 PM	laptop	kernel	[   14.692000] intel_rng: you are certain that your system has a functional

08/13/2007 10:00:47 PM	laptop	kernel	[   15.160000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5

08/13/2007 10:00:47 PM	laptop	kernel	[   15.164000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4

08/13/2007 10:00:47 PM	laptop	kernel	[   15.328000] agpgart: Detected an Intel 855PM Chipset.

08/13/2007 10:00:47 PM	laptop	kernel	[   15.332000] agpgart: AGP aperture is 64M @ 0xb0000000

08/13/2007 10:00:47 PM	laptop	kernel	[   15.340000] input: PC Speaker as /class/input/input2

08/13/2007 10:00:47 PM	laptop	kernel	[   15.528000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]

08/13/2007 10:00:47 PM	laptop	kernel	[   15.528000] parport: PnPBIOS parport detected.

08/13/2007 10:00:47 PM	laptop	kernel	[   15.564000] irda_init()

08/13/2007 10:00:47 PM	laptop	kernel	[   15.564000] NET: Registered protocol family 23

08/13/2007 10:00:47 PM	laptop	kernel	[   15.600000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)

08/13/2007 10:00:47 PM	laptop	kernel	[   15.600000] ath_hal: module license 'Proprietary' taints kernel.

08/13/2007 10:00:47 PM	laptop	kernel	[   15.636000] Yenta: CardBus bridge found at 0000:02:03.0 [14c0:0012]

08/13/2007 10:00:47 PM	laptop	kernel	[   15.636000] Yenta: Routing CardBus interrupts to PCI

08/13/2007 10:00:47 PM	laptop	kernel	[   15.636000] Yenta TI: socket 0000:02:03.0, mfunc 0x001c1112, devctl 0x44

08/13/2007 10:00:47 PM	laptop	kernel	[   15.636000] Yenta: Using CSCINT to route CSC interrupts to PCI

08/13/2007 10:00:47 PM	laptop	kernel	[   15.740000] wlan: 0.8.4.2 (0.9.3.1)

08/13/2007 10:00:47 PM	laptop	kernel	[   15.744000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x254ab1, caps: 0x804713/0x0

08/13/2007 10:00:47 PM	laptop	kernel	[   15.776000] input: SynPS/2 Synaptics TouchPad as /class/input/input3

08/13/2007 10:00:47 PM	laptop	kernel	[   15.800000] ath_pci: 0.9.4.5 (0.9.3.1)

08/13/2007 10:00:47 PM	laptop	kernel	[   15.860000] pnp: Device 00:0a activated.

08/13/2007 10:00:47 PM	laptop	kernel	[   15.860000] wbsd: Copyright(c) Pierre Ossman

08/13/2007 10:00:47 PM	laptop	kernel	[   15.860000] wbsd: Winbond W83L51xD SD/MMC card interface driver

08/13/2007 10:00:47 PM	laptop	kernel	[   15.864000] mmc0: W83L51xD id 7112 at 0x248 irq 6 FIFO PnP

08/13/2007 10:00:47 PM	laptop	kernel	[   15.876000] cs: IO port probe 0xa000-0xbfff: clean.

08/13/2007 10:00:47 PM	laptop	kernel	[   15.876000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xbfff

08/13/2007 10:00:47 PM	laptop	kernel	[   15.876000] pcmcia: parent PCI bridge Memory window: 0x90000000 - 0x9fffffff

08/13/2007 10:00:47 PM	laptop	kernel	[   15.876000] pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xdfffffff

08/13/2007 10:00:47 PM	laptop	kernel	[   15.876000] Socket status: 30000006

08/13/2007 10:00:47 PM	laptop	kernel	[   15.876000] Yenta: ISA IRQ mask 0x0808, PCI irq 10

08/13/2007 10:00:47 PM	laptop	kernel	[   15.876000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06

08/13/2007 10:00:47 PM	laptop	kernel	[   15.888000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:00:47 PM	laptop	kernel	[   16.196000] ath_rate_sample: 1.2 (0.9.3.1)

08/13/2007 10:00:47 PM	laptop	kernel	[   16.196000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps

08/13/2007 10:00:47 PM	laptop	kernel	[   16.196000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps

08/13/2007 10:00:47 PM	laptop	kernel	[   16.196000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP

08/13/2007 10:00:47 PM	laptop	kernel	[   16.196000] wifi0: mac 5.6 phy 4.1 radio 4.6

08/13/2007 10:00:47 PM	laptop	kernel	[   16.196000] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps

08/13/2007 10:00:47 PM	laptop	kernel	[   16.196000] wifi0: Use hw queue 0 for WME_AC_BK traffic

08/13/2007 10:00:47 PM	laptop	kernel	[   16.196000] wifi0: Use hw queue 1 for WME_AC_BE traffic

08/13/2007 10:00:47 PM	laptop	kernel	[   16.196000] wifi0: Use hw queue 2 for WME_AC_VI traffic

08/13/2007 10:00:47 PM	laptop	kernel	[   16.196000] wifi0: Use hw queue 3 for WME_AC_VO traffic

08/13/2007 10:00:47 PM	laptop	kernel	[   16.196000] wifi0: Use hw queue 8 for CAB traffic

08/13/2007 10:00:47 PM	laptop	kernel	[   16.196000] wifi0: Use hw queue 9 for beacons

08/13/2007 10:00:47 PM	laptop	kernel	[   16.264000] wifi0: Atheros 5212: mem=0xd0000000, irq=10

08/13/2007 10:00:47 PM	laptop	kernel	[   16.396000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:00:47 PM	laptop	kernel	[   16.396000] PCI: Setting latency timer of device 0000:00:1f.5 to 64

08/13/2007 10:00:47 PM	laptop	kernel	[   16.532000] cs: IO port probe 0x100-0x3af: excluding 0x230-0x237

08/13/2007 10:00:47 PM	laptop	kernel	[   16.532000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7

08/13/2007 10:00:47 PM	laptop	kernel	[   16.536000] cs: IO port probe 0x820-0x8ff: clean.

08/13/2007 10:00:47 PM	laptop	kernel	[   16.536000] cs: IO port probe 0xa00-0xaff: clean.

08/13/2007 10:00:47 PM	laptop	kernel	[   16.536000] cs: IO port probe 0xc00-0xcf7: clean.

08/13/2007 10:00:47 PM	laptop	kernel	[   17.216000] intel8x0: clocking to 48000

08/13/2007 10:00:47 PM	laptop	kernel	[   17.216000] intel8x0_measure_ac97_clock: measured 55446 usecs

08/13/2007 10:00:47 PM	laptop	kernel	[   17.336000] fuse init (API version 7.8)

08/13/2007 10:00:47 PM	laptop	kernel	[   17.356000] lp0: using parport0 (interrupt-driven).

08/13/2007 10:00:47 PM	laptop	kernel	[   17.428000] NET: Registered protocol family 17

08/13/2007 10:00:47 PM	laptop	kernel	[   17.440000] ACPI: PCI Interrupt 0000:00:1f.3[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:00:47 PM	laptop	kernel	[   17.552000] Adding 2441840k swap on /dev/disk/by-uuid/f4d24f1c-a9d1-4889-88e5-bcbee8f6f6fb.  Priority:-1 extents:1 across:2441840k

08/13/2007 10:00:47 PM	laptop	kernel	[   17.724000] EXT3 FS on sda1, internal journal

08/13/2007 10:00:47 PM	laptop	kernel	[   17.916000] kjournald starting.  Commit interval 5 seconds

08/13/2007 10:00:47 PM	laptop	kernel	[   17.924000] EXT3-fs: mounted filesystem with ordered data mode.

08/13/2007 10:00:47 PM	laptop	kernel	[   17.924000] EXT3 FS on sda3, internal journal

08/13/2007 10:00:47 PM	laptop	kernel	[   18.600000] ACPI: Battery Slot [BAT1] (battery present)

08/13/2007 10:00:47 PM	laptop	kernel	[   18.640000] ACPI Error (evxfevnt-0189): Could not enable SleepButton event [20060707]

08/13/2007 10:00:47 PM	laptop	kernel	[   18.640000] ACPI: Power Button (FF) [PWRF]

08/13/2007 10:00:47 PM	laptop	kernel	[   18.640000] ACPI Warning (evxface-0146): Could not enable fixed event 3 [20060707]

08/13/2007 10:00:47 PM	laptop	kernel	[   18.640000] input: Power Button (FF) as /class/input/input4

08/13/2007 10:00:47 PM	laptop	kernel	[   18.672000] input: Lid Switch as /class/input/input5

08/13/2007 10:00:47 PM	laptop	kernel	[   18.676000] ACPI: Lid Switch [LID]

08/13/2007 10:00:47 PM	laptop	kernel	[   18.704000] input: Power Button (CM) as /class/input/input6

08/13/2007 10:00:47 PM	laptop	kernel	[   18.708000] ACPI: Power Button (CM) [PWRB]

08/13/2007 10:00:47 PM	laptop	kernel	[   18.804000] No dock devices found.

08/13/2007 10:00:47 PM	laptop	kernel	[   18.832000] Using specific hotkey driver

08/13/2007 10:00:47 PM	laptop	kernel	[   18.852000] ACPI: AC Adapter [ACAD] (off-line)

08/13/2007 10:00:47 PM	laptop	kernel	[   18.860000] ibm_acpi: ec object not found

08/13/2007 10:00:47 PM	laptop	kernel	[   18.888000] pcc_acpi: loading...

08/13/2007 10:00:47 PM	laptop	kernel	[    3.264000] Time: acpi_pm clocksource has been installed.

08/13/2007 10:00:47 PM	laptop	kernel	[    3.316000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:00:47 PM	laptop	kernel	[    3.316000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10

08/13/2007 10:00:47 PM	laptop	kernel	[    3.316000] ehci_hcd 0000:00:1d.7: debug port 1

08/13/2007 10:00:47 PM	laptop	kernel	[    3.316000] ehci_hcd 0000:00:1d.7: EHCI Host Controller

08/13/2007 10:00:47 PM	laptop	kernel	[    3.316000] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xf4000000

08/13/2007 10:00:47 PM	laptop	kernel	[    3.316000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4

08/13/2007 10:00:47 PM	laptop	kernel	[    3.316000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7

08/13/2007 10:00:47 PM	laptop	kernel	[    3.316000] PCI: Setting latency timer of device 0000:00:1d.7 to 64

08/13/2007 10:00:47 PM	laptop	kernel	[    3.320000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004

08/13/2007 10:00:47 PM	laptop	kernel	[    3.320000] hub 4-0:1.0: 6 ports detected

08/13/2007 10:00:47 PM	laptop	kernel	[    3.320000] hub 4-0:1.0: USB hub found

08/13/2007 10:00:47 PM	laptop	kernel	[    3.320000] usb usb4: configuration #1 chosen from 1 choice

08/13/2007 10:00:47 PM	laptop	kernel	[    3.428000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:00:47 PM	laptop	kernel	[    3.480000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[d0010800-d0010fff]  Max Packet=[2048]  IR/IT contexts=[4/4]

08/13/2007 10:00:47 PM	laptop	kernel	[    3.484000] 8139cp 0000:02:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip

08/13/2007 10:00:47 PM	laptop	kernel	[    3.484000] 8139cp 0000:02:01.0: Try the "8139too" driver instead.

08/13/2007 10:00:47 PM	laptop	kernel	[    3.492000] SCSI subsystem initialized

08/13/2007 10:00:47 PM	laptop	kernel	[    3.496000] libata version 2.20 loaded.

08/13/2007 10:00:47 PM	laptop	kernel	[    3.504000] 8139too Fast Ethernet driver 0.9.28

08/13/2007 10:00:47 PM	laptop	kernel	[    3.504000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:00:47 PM	laptop	kernel	[    3.504000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011100 irq 14

08/13/2007 10:00:47 PM	laptop	kernel	[    3.504000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011108 irq 15

08/13/2007 10:00:47 PM	laptop	kernel	[    3.504000] ata_piix 0000:00:1f.1: version 2.10ac1

08/13/2007 10:00:47 PM	laptop	kernel	[    3.504000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)

08/13/2007 10:00:47 PM	laptop	kernel	[    3.504000] PCI: Setting latency timer of device 0000:00:1f.1 to 64

08/13/2007 10:00:47 PM	laptop	kernel	[    3.504000] scsi0 : ata_piix

08/13/2007 10:00:47 PM	laptop	kernel	[    3.668000] ata1.00: 117210240 sectors, multi 16: LBA48 

08/13/2007 10:00:47 PM	laptop	kernel	[    3.668000] ata1.00: ATA-6: HTE726060M9AT00, MH4OA6AA, max UDMA/100

08/13/2007 10:00:47 PM	laptop	kernel	[    3.668000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240

08/13/2007 10:00:47 PM	laptop	kernel	[    3.676000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240

08/13/2007 10:00:47 PM	laptop	kernel	[    3.676000] ata1.00: configured for UDMA/100

08/13/2007 10:00:47 PM	laptop	kernel	[    3.676000] scsi1 : ata_piix

08/13/2007 10:00:47 PM	laptop	kernel	[    4.020000] ata2.00: ATAPI, max UDMA/33

08/13/2007 10:00:47 PM	laptop	kernel	[    4.208000] ata2.00: configured for UDMA/33

08/13/2007 10:00:47 PM	laptop	kernel	[    4.208000] scsi 0:0:0:0: Direct-Access     ATA      HTE726060M9AT00  MH4O PQ: 0 ANSI: 5

08/13/2007 10:00:47 PM	laptop	kernel	[    4.212000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:00:47 PM	laptop	kernel	[    4.212000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'

08/13/2007 10:00:47 PM	laptop	kernel	[    4.212000] eth0: RealTek RTL8139 at 0xf88a2000, 00:02:3f:09:99:a3, IRQ 10

08/13/2007 10:00:47 PM	laptop	kernel	[    4.212000] scsi 1:0:0:0: CD-ROM            TOSHIBA  ODD-DVD SD-R6372 1030 PQ: 0 ANSI: 5

08/13/2007 10:00:47 PM	laptop	kernel	[    4.224000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)

08/13/2007 10:00:47 PM	laptop	kernel	[    4.224000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)

08/13/2007 10:00:47 PM	laptop	kernel	[    4.224000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

08/13/2007 10:00:47 PM	laptop	kernel	[    4.224000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

08/13/2007 10:00:47 PM	laptop	kernel	[    4.224000] sda: Mode Sense: 00 3a 00 00

08/13/2007 10:00:47 PM	laptop	kernel	[    4.224000] sda: Mode Sense: 00 3a 00 00

08/13/2007 10:00:47 PM	laptop	kernel	[    4.224000]  sda: sda1 sda2 < sda5 > sda3 sda4

08/13/2007 10:00:47 PM	laptop	kernel	[    4.224000] sda: Write Protect is off

08/13/2007 10:00:47 PM	laptop	kernel	[    4.224000] sda: Write Protect is off

08/13/2007 10:00:47 PM	laptop	kernel	[    4.264000] sd 0:0:0:0: Attached scsi disk sda

08/13/2007 10:00:47 PM	laptop	kernel	[    4.268000] scsi 1:0:0:0: Attached scsi generic sg1 type 5

08/13/2007 10:00:47 PM	laptop	kernel	[    4.268000] sd 0:0:0:0: Attached scsi generic sg0 type 0

08/13/2007 10:00:47 PM	laptop	kernel	[    4.280000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray

08/13/2007 10:00:47 PM	laptop	kernel	[    4.280000] sr 1:0:0:0: Attached scsi CD-ROM sr0

08/13/2007 10:00:47 PM	laptop	kernel	[    4.280000] Uniform CD-ROM driver Revision: 3.20

08/13/2007 10:00:47 PM	laptop	kernel	[    4.492000] Attempting manual resume

08/13/2007 10:00:47 PM	laptop	kernel	[    4.492000] PM: Checking swsusp image.

08/13/2007 10:00:47 PM	laptop	kernel	[    4.492000] PM: Resume from disk failed.

08/13/2007 10:00:47 PM	laptop	kernel	[    4.492000] swsusp: Resume From Partition 8:5

08/13/2007 10:00:47 PM	laptop	kernel	[    4.524000] EXT3-fs: mounted filesystem with ordered data mode.

08/13/2007 10:00:47 PM	laptop	kernel	[    4.524000] kjournald starting.  Commit interval 5 seconds

08/13/2007 10:00:47 PM	laptop	kernel	[    4.756000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f495240117e]

08/13/2007 10:00:47 PM	laptop	kernel	[    8.578019] Built 1 zonelists.  Total pages: 260081

08/13/2007 10:00:47 PM	laptop	kernel	[    8.578023] Kernel command line: root=UUID=f2db0809-08f4-4d50-bf89-177269e9374a ro quiet splash

08/13/2007 10:00:47 PM	laptop	kernel	[    8.578167] Local APIC disabled by BIOS -- you can enable it with "lapic"

08/13/2007 10:00:47 PM	laptop	kernel	[    8.578175] mapped APIC to ffffd000 (0180c000)

08/13/2007 10:00:47 PM	laptop	kernel	[    8.578179] Enabling fast FPU save and restore... done.

08/13/2007 10:00:47 PM	laptop	kernel	[    8.578181] Enabling unmasked SIMD FPU exception support... done.

08/13/2007 10:00:47 PM	laptop	kernel	[    8.578192] Initializing CPU#0

08/13/2007 10:00:47 PM	laptop	kernel	[    8.578266] PID hash table entries: 4096 (order: 12, 16384 bytes)

08/13/2007 10:00:47 PM	laptop	kernel	[    8.579476] Console: colour VGA+ 80x25

08/13/2007 10:00:47 PM	laptop	kernel	[    8.580017] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)

08/13/2007 10:00:47 PM	laptop	kernel	[    8.580565] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)

08/13/2007 10:00:47 PM	laptop	kernel	[    8.613420] Memory: 1028308k/1048512k available (1992k kernel code, 19468k reserved, 900k data, 328k init, 131008k highmem)

08/13/2007 10:00:47 PM	laptop	kernel	[    8.613429] virtual kernel memory layout:

08/13/2007 10:00:47 PM	laptop	kernel	[    8.613430]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)

08/13/2007 10:00:47 PM	laptop	kernel	[    8.613431]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)

08/13/2007 10:00:47 PM	laptop	kernel	[    8.613432]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)

08/13/2007 10:00:47 PM	laptop	kernel	[    8.613433]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)

08/13/2007 10:00:47 PM	laptop	kernel	[    8.613434]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)

08/13/2007 10:00:47 PM	laptop	kernel	[    8.613435]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)

08/13/2007 10:00:47 PM	laptop	kernel	[    8.613436]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)

08/13/2007 10:00:47 PM	laptop	kernel	[    8.613439] Checking if this processor honours the WP bit even in supervisor mode... Ok.

08/13/2007 10:00:47 PM	laptop	kernel	[    8.690132] Calibrating delay using timer specific routine.. 3989.72 BogoMIPS (lpj=7979452)

08/13/2007 10:00:47 PM	laptop	kernel	[    8.690168] Security Framework v1.0.0 initialized

08/13/2007 10:00:47 PM	laptop	kernel	[    8.690175] SELinux:  Disabled at boot.

08/13/2007 10:00:47 PM	laptop	kernel	[    8.690189] Mount-cache hash table entries: 512

08/13/2007 10:00:47 PM	laptop	kernel	[    8.690312] CPU: After generic identify, caps: afe9f9bf 00000000 00000000 00000000 00000180 00000000 00000000

08/13/2007 10:00:47 PM	laptop	kernel	[    8.690323] CPU: L1 I cache: 32K, L1 D cache: 32K

08/13/2007 10:00:47 PM	laptop	kernel	[    8.690325] CPU: L2 cache: 2048K

08/13/2007 10:00:47 PM	laptop	kernel	[    8.690328] CPU: After all inits, caps: afe9f9bf 00000000 00000000 00002040 00000180 00000000 00000000

08/13/2007 10:00:47 PM	laptop	kernel	[    8.690336] Compat vDSO mapped to ffffe000.

08/13/2007 10:00:47 PM	laptop	kernel	[    8.690340] Remapping vsyscall page to ffffe000

08/13/2007 10:00:47 PM	laptop	kernel	[    8.690349] Checking 'hlt' instruction... OK.

08/13/2007 10:00:47 PM	laptop	kernel	[    8.706199] SMP alternatives: switching to UP code

08/13/2007 10:00:47 PM	laptop	kernel	[    8.706389] Freeing SMP alternatives: 11k freed

08/13/2007 10:00:47 PM	laptop	kernel	[    8.706548] Early unpacking initramfs... done

08/13/2007 10:00:47 PM	laptop	kernel	[    8.989522] ACPI: Core revision 20060707

08/13/2007 10:00:47 PM	laptop	kernel	[    8.989626] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.

08/13/2007 10:00:47 PM	laptop	kernel	[    8.991191] ACPI: setting ELCR to 0200 (from 0c00)

08/13/2007 10:00:47 PM	laptop	kernel	[    8.997478] CPU0: Intel(R) Pentium(R) M processor 2.00GHz stepping 06

08/13/2007 10:00:47 PM	laptop	kernel	[    8.997484] SMP motherboard not detected.

08/13/2007 10:00:47 PM	laptop	kernel	[    8.997486] Local APIC not detected. Using dummy APIC emulation.

08/13/2007 10:00:47 PM	laptop	kernel	[    8.997517] Brought up 1 CPUs

08/13/2007 10:00:47 PM	laptop	kernel	[    8.997726] Booting paravirtualized kernel on bare hardware

08/13/2007 10:00:47 PM	laptop	kernel	[    8.997800] Time:  3:00:28  Date: 07/14/107

08/13/2007 10:00:47 PM	laptop	kernel	[    8.997825] NET: Registered protocol family 16

08/13/2007 10:00:47 PM	laptop	kernel	[    8.997898] EISA bus registered

08/13/2007 10:00:47 PM	laptop	kernel	[    8.997901] ACPI: bus type pci registered

08/13/2007 10:00:47 PM	laptop	kernel	[    8.997932] PCI: PCI BIOS revision 2.10 entry at 0xe97a4, last bus=2

08/13/2007 10:00:47 PM	laptop	kernel	[    8.997934] PCI: Using configuration type 1

08/13/2007 10:00:47 PM	laptop	kernel	[    8.997936] Setting up standard PCI resources

08/13/2007 10:00:47 PM	laptop	kernel	[    9.000059] ACPI: Interpreter enabled

08/13/2007 10:00:47 PM	laptop	kernel	[    9.000061] ACPI: Using PIC for interrupt routing

08/13/2007 10:00:47 PM	laptop	kernel	[    9.000392] ACPI: PCI Root Bridge [PCI0] (0000:00)

08/13/2007 10:00:47 PM	laptop	kernel	[    9.000396] PCI: Probing PCI hardware (bus 00)

08/13/2007 10:00:47 PM	laptop	kernel	[    9.001183] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO

08/13/2007 10:00:47 PM	laptop	kernel	[    9.001186] PCI quirk: region 1300-133f claimed by ICH4 GPIO

08/13/2007 10:00:47 PM	laptop	kernel	[    9.001412] Boot video device is 0000:01:00.0

08/13/2007 10:00:47 PM	laptop	kernel	[    9.001645] PCI: Transparent bridge - 0000:00:1e.0

08/13/2007 10:00:47 PM	laptop	kernel	[    9.001691] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')

08/13/2007 10:00:47 PM	laptop	kernel	[    9.001693] Please report the result to linux-kernel to fix this permanently

08/13/2007 10:00:47 PM	laptop	kernel	[    9.001709] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]

08/13/2007 10:00:47 PM	laptop	kernel	[    9.006952] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]

08/13/2007 10:00:47 PM	laptop	kernel	[    9.007083] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB_._PRT]

08/13/2007 10:00:47 PM	laptop	kernel	[    9.008060] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 *10)

08/13/2007 10:00:47 PM	laptop	kernel	[    9.008228] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 10) *11

08/13/2007 10:00:47 PM	laptop	kernel	[    9.008395] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 10) *11

08/13/2007 10:00:47 PM	laptop	kernel	[    9.008564] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 10) *11

08/13/2007 10:00:47 PM	laptop	kernel	[    9.008740] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.

08/13/2007 10:00:47 PM	laptop	kernel	[    9.008914] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.

08/13/2007 10:00:47 PM	laptop	kernel	[    9.009088] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.

08/13/2007 10:00:47 PM	laptop	kernel	[    9.009263] ACPI: PCI Interrupt Link [LNKH] (IRQs 5 10) *11

08/13/2007 10:00:47 PM	laptop	kernel	[    9.050779] Linux Plug and Play Support v0.97 (c) Adam Belay

08/13/2007 10:00:47 PM	laptop	kernel	[    9.050786] pnp: PnP ACPI init

08/13/2007 10:00:47 PM	laptop	kernel	[    9.073898] pnp: PnP ACPI: found 11 devices

08/13/2007 10:00:47 PM	laptop	kernel	[    9.073901] PnPBIOS: Disabled by ACPI PNP

08/13/2007 10:00:47 PM	laptop	kernel	[    9.073936] PCI: Using ACPI for IRQ routing

08/13/2007 10:00:47 PM	laptop	kernel	[    9.073938] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report

08/13/2007 10:00:47 PM	laptop	kernel	[    9.073964] PCI: Cannot allocate resource region 0 of device 0000:02:03.0

08/13/2007 10:00:47 PM	laptop	kernel	[    9.076614] NET: Registered protocol family 8

08/13/2007 10:00:47 PM	laptop	kernel	[    9.076616] NET: Registered protocol family 20

08/13/2007 10:00:47 PM	laptop	kernel	[    9.076954] PCI: Bridge: 0000:00:01.0

08/13/2007 10:00:47 PM	laptop	kernel	[    9.076956]   IO window: c000-dfff

08/13/2007 10:00:47 PM	laptop	kernel	[    9.076959]   MEM window: e0000000-efffffff

08/13/2007 10:00:47 PM	laptop	kernel	[    9.076962]   PREFETCH window: a0000000-afffffff

08/13/2007 10:00:47 PM	laptop	kernel	[    9.076970] PCI: Bus 3, cardbus bridge: 0000:02:03.0

08/13/2007 10:00:47 PM	laptop	kernel	[    9.076971]   IO window: 0000a400-0000a4ff

08/13/2007 10:00:47 PM	laptop	kernel	[    9.076975]   IO window: 0000a800-0000a8ff

08/13/2007 10:00:47 PM	laptop	kernel	[    9.076979]   PREFETCH window: 90000000-93ffffff

08/13/2007 10:00:47 PM	laptop	kernel	[    9.076983]   MEM window: d4000000-d7ffffff

08/13/2007 10:00:47 PM	laptop	kernel	[    9.076986] PCI: Bridge: 0000:00:1e.0

08/13/2007 10:00:47 PM	laptop	kernel	[    9.076988]   IO window: a000-bfff

08/13/2007 10:00:47 PM	laptop	kernel	[    9.076993]   MEM window: d0000000-dfffffff

08/13/2007 10:00:47 PM	laptop	kernel	[    9.076997]   PREFETCH window: 90000000-9fffffff

08/13/2007 10:00:47 PM	laptop	kernel	[    9.077010] PCI: Setting latency timer of device 0000:00:1e.0 to 64

08/13/2007 10:00:47 PM	laptop	kernel	[    9.077149] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10

08/13/2007 10:00:47 PM	laptop	kernel	[    9.077151] PCI: setting IRQ 10 as level-triggered

08/13/2007 10:00:47 PM	laptop	kernel	[    9.077154] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:00:47 PM	laptop	kernel	[    9.077175] NET: Registered protocol family 2

08/13/2007 10:00:47 PM	laptop	kernel	[    9.109664] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)

08/13/2007 10:00:47 PM	laptop	kernel	[    9.109779] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)

08/13/2007 10:00:47 PM	laptop	kernel	[    9.110727] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)

08/13/2007 10:00:47 PM	laptop	kernel	[    9.111391] TCP: Hash tables configured (established 131072 bind 65536)

08/13/2007 10:00:47 PM	laptop	kernel	[    9.111394] TCP reno registered

08/13/2007 10:00:47 PM	laptop	kernel	[    9.121754] checking if image is initramfs... it is

08/13/2007 10:00:47 PM	laptop	kernel	[    9.674496] Freeing initrd memory: 6772k freed

08/13/2007 10:00:47 PM	laptop	kernel	[    9.674751] Simple Boot Flag at 0x37 set to 0x1

08/13/2007 10:00:47 PM	laptop	kernel	[    9.674938] audit: initializing netlink socket (disabled)

08/13/2007 10:00:47 PM	laptop	kernel	[    9.674954] audit(1187060429.284:1): initialized

08/13/2007 10:00:47 PM	laptop	kernel	[    9.675028] highmem bounce pool size: 64 pages

08/13/2007 10:00:47 PM	laptop	kernel	[    9.675090] VFS: Disk quotas dquot_6.5.1

08/13/2007 10:00:47 PM	laptop	kernel	[    9.675109] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)

08/13/2007 10:00:47 PM	laptop	kernel	[    9.675163] io scheduler noop registered

08/13/2007 10:00:47 PM	laptop	kernel	[    9.675166] io scheduler anticipatory registered

08/13/2007 10:00:47 PM	laptop	kernel	[    9.675168] io scheduler deadline registered

08/13/2007 10:00:47 PM	laptop	kernel	[    9.675178] io scheduler cfq registered (default)

08/13/2007 10:00:47 PM	laptop	kernel	[    9.675470] isapnp: Scanning for PnP cards...

08/13/2007 10:00:47 PM	laptop	kernel	Inspecting /boot/System.map-2.6.20-16-generic

08/13/2007 10:00:47 PM	laptop	kernel	Loaded 24977 symbols from /boot/System.map-2.6.20-16-generic.

08/13/2007 10:00:47 PM	laptop	kernel	No module symbols loaded - kernel modules not enabled. 

08/13/2007 10:00:47 PM	laptop	kernel	Symbols match kernel version 2.6.20.

08/13/2007 10:00:47 PM	laptop	syslogd 1.4.1#20ubuntu4	restart.

08/13/2007 10:00:49 PM	laptop	dhclient	DHCPREQUEST on ath0 to 255.255.255.255 port 67

08/13/2007 10:00:50 PM	laptop	anacron[4565]	Anacron 2.3 started on 2007-08-13

08/13/2007 10:00:50 PM	laptop	anacron[4565]	Normal exit (0 jobs run)

08/13/2007 10:00:50 PM	laptop	avahi-daemon[4597]	avahi-daemon 0.6.17 starting up.

08/13/2007 10:00:50 PM	laptop	avahi-daemon[4597]	Found user 'avahi' (UID 105) and group 'avahi' (GID 111).

08/13/2007 10:00:50 PM	laptop	avahi-daemon[4597]	Network interface enumeration completed.

08/13/2007 10:00:50 PM	laptop	avahi-daemon[4597]	No service found in /etc/avahi/services.

08/13/2007 10:00:50 PM	laptop	avahi-daemon[4597]	Registering HINFO record with values 'I686'/'LINUX'.

08/13/2007 10:00:50 PM	laptop	avahi-daemon[4597]	Server startup complete. Host name is laptop.local. Local service cookie is 1452931620.

08/13/2007 10:00:50 PM	laptop	avahi-daemon[4597]	Successfully called chroot().

08/13/2007 10:00:50 PM	laptop	avahi-daemon[4597]	Successfully dropped remaining capabilities.

08/13/2007 10:00:50 PM	laptop	avahi-daemon[4597]	Successfully dropped root privileges.

08/13/2007 10:00:50 PM	laptop	dhcdbd	Started up.

08/13/2007 10:00:50 PM	laptop	hpiod	1.7.3 accepting connections at 2208... 

08/13/2007 10:00:50 PM	laptop	kernel	[   21.708000] eth0: link down

08/13/2007 10:00:50 PM	laptop	kernel	[   21.892000] ppdev: user-space parallel port driver

08/13/2007 10:00:50 PM	laptop	NetworkManager	<debug info>^I[1187060450.506645] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_ODD_DVD_SD_R6372'). 

08/13/2007 10:00:50 PM	laptop	NetworkManager	<information>^Iath0: Device is fully-supported using driver 'ath_pci'. 

08/13/2007 10:00:50 PM	laptop	NetworkManager	<information>^IDeactivating device ath0. 

08/13/2007 10:00:50 PM	laptop	NetworkManager	<information>^IDeactivating device eth0. 

08/13/2007 10:00:50 PM	laptop	NetworkManager	<information>^Ieth0: Device is fully-supported using driver '8139too'. 

08/13/2007 10:00:50 PM	laptop	NetworkManager	<information>^Inm_device_init(): device's worker thread started, continuing. 

08/13/2007 10:00:50 PM	laptop	NetworkManager	<information>^Inm_device_init(): device's worker thread started, continuing. 

08/13/2007 10:00:50 PM	laptop	NetworkManager	<information>^Inm_device_init(): waiting for device's worker thread to start 

08/13/2007 10:00:50 PM	laptop	NetworkManager	<information>^Inm_device_init(): waiting for device's worker thread to start 

08/13/2007 10:00:50 PM	laptop	NetworkManager	<information>^INow managing wired Ethernet (802.3) device 'eth0'. 

08/13/2007 10:00:50 PM	laptop	NetworkManager	<information>^INow managing wireless (802.11) device 'ath0'. 

08/13/2007 10:00:50 PM	laptop	NetworkManager	<information>^Istarting... 

08/13/2007 10:00:51 PM	laptop	kernel	[   22.756000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)

08/13/2007 10:00:51 PM	laptop	kernel	[   22.756000] apm: overridden by ACPI.

08/13/2007 10:00:52 PM	laptop	anacron[4932]	Anacron 2.3 started on 2007-08-13

08/13/2007 10:00:52 PM	laptop	anacron[4932]	Normal exit (0 jobs run)

08/13/2007 10:00:52 PM	laptop	hcid[4893]	Bluetooth HCI daemon

08/13/2007 10:00:52 PM	laptop	hcid[4893]	Starting SDP server

08/13/2007 10:00:52 PM	laptop	kernel	[   23.624000] Bluetooth: Core ver 2.11

08/13/2007 10:00:52 PM	laptop	kernel	[   23.624000] Bluetooth: HCI device and connection manager initialized

08/13/2007 10:00:52 PM	laptop	kernel	[   23.624000] Bluetooth: HCI socket layer initialized

08/13/2007 10:00:52 PM	laptop	kernel	[   23.624000] NET: Registered protocol family 31

08/13/2007 10:00:52 PM	laptop	kernel	[   23.668000] Bluetooth: L2CAP socket layer initialized

08/13/2007 10:00:52 PM	laptop	kernel	[   23.668000] Bluetooth: L2CAP ver 2.8

08/13/2007 10:00:52 PM	laptop	kernel	[   23.804000] Bluetooth: RFCOMM socket layer initialized

08/13/2007 10:00:52 PM	laptop	kernel	[   23.804000] Bluetooth: RFCOMM TTY layer initialized

08/13/2007 10:00:52 PM	laptop	kernel	[   23.804000] Bluetooth: RFCOMM ver 1.8

08/13/2007 10:00:52 PM	laptop	NetworkManager	<debug info>^I[1187060452.149905] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 

08/13/2007 10:00:52 PM	laptop	/usr/sbin/cron[4959]	(CRON) INFO (pidfile fd = 3)

08/13/2007 10:00:52 PM	laptop	/usr/sbin/cron[4960]	(CRON) INFO (Running @reboot jobs)

08/13/2007 10:00:52 PM	laptop	/usr/sbin/cron[4960]	(CRON) STARTUP (fork ok)

08/13/2007 10:00:53 PM	laptop	kernel	[   25.104000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.

08/13/2007 10:00:53 PM	laptop	kernel	[   25.104000] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0

08/13/2007 10:00:53 PM	laptop	kernel	[   25.132000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:00:54 PM	laptop	dhclient	DHCPREQUEST on ath0 to 255.255.255.255 port 67

08/13/2007 10:00:55 PM	laptop	kernel	[   27.468000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.

08/13/2007 10:00:55 PM	laptop	kernel	[   27.468000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode

08/13/2007 10:00:55 PM	laptop	kernel	[   27.468000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode

08/13/2007 10:00:55 PM	laptop	kernel	[   27.468000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)

08/13/2007 10:00:55 PM	laptop	kernel	[   27.468000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)

08/13/2007 10:00:55 PM	laptop	kernel	[   27.468000] [fglrx] Have to use kernel AGP support to avoid conflicts.

08/13/2007 10:00:55 PM	laptop	kernel	[   27.468000] [fglrx] Internal AGP support requested, but kernel AGP support active.

08/13/2007 10:00:55 PM	laptop	kernel	[   27.476000] [fglrx] free       GART = 51113984

08/13/2007 10:00:55 PM	laptop	kernel	[   27.476000] [fglrx] free       Inv  = 0

08/13/2007 10:00:55 PM	laptop	kernel	[   27.476000] [fglrx] free       LFB  = 96432128

08/13/2007 10:00:55 PM	laptop	kernel	[   27.476000] [fglrx] max single GART = 51113984

08/13/2007 10:00:55 PM	laptop	kernel	[   27.476000] [fglrx] max single Inv  = 0

08/13/2007 10:00:55 PM	laptop	kernel	[   27.476000] [fglrx] max single LFB  = 96432128

08/13/2007 10:00:55 PM	laptop	kernel	[   27.476000] [fglrx] total      GART = 67108864

08/13/2007 10:00:55 PM	laptop	kernel	[   27.476000] [fglrx] total      Inv  = 0

08/13/2007 10:00:55 PM	laptop	kernel	[   27.476000] [fglrx] total      LFB  = 134217728

08/13/2007 10:00:55 PM	laptop	kernel	[   27.476000] [fglrx] total      TIM  = 0

08/13/2007 10:01:00 PM	laptop	kdm_greet[5079]	Can't open default user face

08/13/2007 10:01:07 PM	laptop	dhclient	DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8

08/13/2007 10:01:12 PM	laptop	init	tty1 main process (4024) killed by TERM signal

08/13/2007 10:01:12 PM	laptop	init	tty2 main process (4022) killed by TERM signal

08/13/2007 10:01:12 PM	laptop	init	tty3 main process (4023) killed by TERM signal

08/13/2007 10:01:12 PM	laptop	init	tty4 main process (4017) killed by TERM signal

08/13/2007 10:01:12 PM	laptop	init	tty5 main process (4018) killed by TERM signal

08/13/2007 10:01:12 PM	laptop	init	tty6 main process (4025) killed by TERM signal

08/13/2007 10:01:12 PM	laptop	kdm_greet[5079]	Internal error: memory corruption detected

08/13/2007 10:01:15 PM	laptop	dhclient	DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 18

08/13/2007 10:01:18 PM	laptop	kernel	[   49.692000] ip_tables: (C) 2000-2006 Netfilter Core Team

08/13/2007 10:01:18 PM	laptop	kernel	[   49.856000] Netfilter messages via NETLINK v0.30.

08/13/2007 10:01:18 PM	laptop	kernel	[   49.880000] nf_conntrack version 0.5.0 (8191 buckets, 65528 max)

08/13/2007 10:01:20 PM	laptop	none	exiting on signal 15

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000]     0:        0 ->   262128

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] 127MB HIGHMEM available.

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] 896MB LOWMEM available.

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] ACPI: BOOT (v001 INSYDE SYS_BOOT 0x00000100 _CSI 0x00010101) @ 0x3ffffb90

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] ACPI: DBGP (v001 INSYDE DBGP_000 0x00000100 _CSI 0x00010101) @ 0x3ffffbc0

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] ACPI: DSDT (v001 COMPAL   DCL561 0x00000006 MSFT 0x0100000e) @ 0x00000000

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] ACPI: FADT (v001 COMPAL DCL56    0x00000200 _CSI 0x00010101) @ 0x3ffffb00

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] ACPI: PM-Timer IO Port: 0x1008

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] ACPI: RSDP (v000 OID_00                                ) @ 0x000e6010

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] ACPI: RSDT (v001 INSYDE RSDT_000 0x00000001 _CSI 0x00010101) @ 0x3fffa7f0

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] ACPI: SSDT (v001 INSYDE   GV3Ref 0x00002000 INTL 0x20021002) @ 0x3fffa830

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bfb80000)

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fffffc0 (ACPI data)

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000]  BIOS-e820: 000000003fffffc0 - 0000000040000000 (ACPI NVS)

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] BIOS-provided physical RAM map:

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fef0000 end: 000000003fff0000 type: 1

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] copy_e820_map() start: 000000003fff0000 size: 000000000000ffc0 end: 000000003fffffc0 type: 3

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] copy_e820_map() start: 000000003fffffc0 size: 0000000000000040 end: 0000000040000000 type: 4

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] copy_e820_map() start: 00000000ffb80000 size: 0000000000080000 end: 00000000ffc00000 type: 2

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] copy_e820_map() start: 00000000fff80000 size: 0000000000080000 end: 0000000100000000 type: 2

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] copy_e820_map() type is E820_RAM

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] copy_e820_map() type is E820_RAM

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] Detected 1993.693 MHz processor.

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000]   DMA             0 ->     4096

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000]   DMA zone: 0 pages reserved

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000]   DMA zone: 32 pages used for memmap

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000]   DMA zone: 4064 pages, LIFO batch:0

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] DMI 2.3 present.

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] early_node_map[1] active PFN ranges

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] Entering add_active_range(0, 0, 262128) 0 entries of 256 used

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000]   HighMem    229376 ->   262128

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000]   HighMem zone: 255 pages used for memmap

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000]   HighMem zone: 32497 pages, LIFO batch:7

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000]   Normal       4096 ->   229376

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000]   Normal zone: 1760 pages used for memmap

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000]   Normal zone: 223520 pages, LIFO batch:31

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] On node 0 totalpages: 262128

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] sanitize end

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] sanitize start

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] Zone PFN ranges:

08/13/2007 10:18:59 PM	laptop	kernel	[   10.523980] Capability LSM initialized

08/13/2007 10:18:59 PM	laptop	kernel	[   10.552875] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])

08/13/2007 10:18:59 PM	laptop	kernel	[   10.552881] ACPI: Processor [CPU0] (supports 8 throttling states)

08/13/2007 10:18:59 PM	laptop	kernel	[   10.835607] usbcore: registered new interface driver usbfs

08/13/2007 10:18:59 PM	laptop	kernel	[   10.835629] usbcore: registered new interface driver hub

08/13/2007 10:18:59 PM	laptop	kernel	[   10.835650] usbcore: registered new device driver usb

08/13/2007 10:18:59 PM	laptop	kernel	[   10.836407] USB Universal Host Controller Interface driver v3.0

08/13/2007 10:18:59 PM	laptop	kernel	[   10.836654] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10

08/13/2007 10:18:59 PM	laptop	kernel	[   10.836657] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:18:59 PM	laptop	kernel	[   10.836667] PCI: Setting latency timer of device 0000:00:1d.0 to 64

08/13/2007 10:18:59 PM	laptop	kernel	[   10.836671] uhci_hcd 0000:00:1d.0: UHCI Host Controller

08/13/2007 10:18:59 PM	laptop	kernel	[   10.836830] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1

08/13/2007 10:18:59 PM	laptop	kernel	[   10.836853] uhci_hcd 0000:00:1d.0: irq 10, io base 0x00001200

08/13/2007 10:18:59 PM	laptop	kernel	[   10.836950] usb usb1: configuration #1 chosen from 1 choice

08/13/2007 10:18:59 PM	laptop	kernel	[   10.836971] hub 1-0:1.0: USB hub found

08/13/2007 10:18:59 PM	laptop	kernel	[   10.836976] hub 1-0:1.0: 2 ports detected

08/13/2007 10:18:59 PM	laptop	kernel	[   10.896881] ieee1394: Initialized config rom entry `ip1394'

08/13/2007 10:18:59 PM	laptop	kernel	[   10.906273] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)

08/13/2007 10:18:59 PM	laptop	kernel	[   10.938020] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10

08/13/2007 10:18:59 PM	laptop	kernel	[   10.938024] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:18:59 PM	laptop	kernel	[   10.938036] PCI: Setting latency timer of device 0000:00:1d.1 to 64

08/13/2007 10:18:59 PM	laptop	kernel	[   10.938039] uhci_hcd 0000:00:1d.1: UHCI Host Controller

08/13/2007 10:18:59 PM	laptop	kernel	[   10.938061] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2

08/13/2007 10:18:59 PM	laptop	kernel	[   10.938085] uhci_hcd 0000:00:1d.1: irq 10, io base 0x00001600

08/13/2007 10:18:59 PM	laptop	kernel	[   10.938172] usb usb2: configuration #1 chosen from 1 choice

08/13/2007 10:18:59 PM	laptop	kernel	[   10.938192] hub 2-0:1.0: USB hub found

08/13/2007 10:18:59 PM	laptop	kernel	[   10.938197] hub 2-0:1.0: 2 ports detected

08/13/2007 10:18:59 PM	laptop	kernel	[   11.041684] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:18:59 PM	laptop	kernel	[   11.041698] PCI: Setting latency timer of device 0000:00:1d.2 to 64

08/13/2007 10:18:59 PM	laptop	kernel	[   11.041702] uhci_hcd 0000:00:1d.2: UHCI Host Controller

08/13/2007 10:18:59 PM	laptop	kernel	[   11.041720] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3

08/13/2007 10:18:59 PM	laptop	kernel	[   11.041743] uhci_hcd 0000:00:1d.2: irq 10, io base 0x00001700

08/13/2007 10:18:59 PM	laptop	kernel	[   11.041825] usb usb3: configuration #1 chosen from 1 choice

08/13/2007 10:18:59 PM	laptop	kernel	[   11.041849] hub 3-0:1.0: USB hub found

08/13/2007 10:18:59 PM	laptop	kernel	[   11.041857] hub 3-0:1.0: 2 ports detected

08/13/2007 10:18:59 PM	laptop	kernel	[   14.468000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5

08/13/2007 10:18:59 PM	laptop	kernel	[   14.500000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4

08/13/2007 10:18:59 PM	laptop	kernel	[   14.556000] iTCO_vendor_support: vendor-support=0

08/13/2007 10:18:59 PM	laptop	kernel	[   14.556000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)

08/13/2007 10:18:59 PM	laptop	kernel	[   14.556000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)

08/13/2007 10:18:59 PM	laptop	kernel	[   14.556000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)

08/13/2007 10:18:59 PM	laptop	kernel	[   14.572000] intel_rng: don't want to disable this in firmware setup, and if

08/13/2007 10:18:59 PM	laptop	kernel	[   14.572000] intel_rng: Firmware space is locked read-only. If you can't or

08/13/2007 10:18:59 PM	laptop	kernel	[   14.572000] intel_rng: RNG, try using the 'no_fwh_detect' option.

08/13/2007 10:18:59 PM	laptop	kernel	[   14.572000] intel_rng: you are certain that your system has a functional

08/13/2007 10:18:59 PM	laptop	kernel	[   14.856000] Linux agpgart interface v0.102 (c) Dave Jones

08/13/2007 10:18:59 PM	laptop	kernel	[   15.024000] agpgart: Detected an Intel 855PM Chipset.

08/13/2007 10:18:59 PM	laptop	kernel	[   15.028000] agpgart: AGP aperture is 64M @ 0xb0000000

08/13/2007 10:18:59 PM	laptop	kernel	[   15.040000] Yenta: CardBus bridge found at 0000:02:03.0 [14c0:0012]

08/13/2007 10:18:59 PM	laptop	kernel	[   15.040000] Yenta: Routing CardBus interrupts to PCI

08/13/2007 10:18:59 PM	laptop	kernel	[   15.040000] Yenta TI: socket 0000:02:03.0, mfunc 0x001c1112, devctl 0x44

08/13/2007 10:18:59 PM	laptop	kernel	[   15.040000] Yenta: Using CSCINT to route CSC interrupts to PCI

08/13/2007 10:18:59 PM	laptop	kernel	[   15.068000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)

08/13/2007 10:18:59 PM	laptop	kernel	[   15.068000] ath_hal: module license 'Proprietary' taints kernel.

08/13/2007 10:18:59 PM	laptop	kernel	[   15.272000] cs: IO port probe 0xa000-0xbfff: clean.

08/13/2007 10:18:59 PM	laptop	kernel	[   15.272000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xbfff

08/13/2007 10:18:59 PM	laptop	kernel	[   15.272000] pcmcia: parent PCI bridge Memory window: 0x90000000 - 0x9fffffff

08/13/2007 10:18:59 PM	laptop	kernel	[   15.272000] pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xdfffffff

08/13/2007 10:18:59 PM	laptop	kernel	[   15.272000] Socket status: 30000006

08/13/2007 10:18:59 PM	laptop	kernel	[   15.272000] Yenta: ISA IRQ mask 0x0830, PCI irq 10

08/13/2007 10:18:59 PM	laptop	kernel	[   15.272000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06

08/13/2007 10:18:59 PM	laptop	kernel	[   15.444000] input: PC Speaker as /class/input/input2

08/13/2007 10:18:59 PM	laptop	kernel	[   15.532000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]

08/13/2007 10:18:59 PM	laptop	kernel	[   15.532000] parport: PnPBIOS parport detected.

08/13/2007 10:18:59 PM	laptop	kernel	[   15.612000] wlan: 0.8.4.2 (0.9.3.1)

08/13/2007 10:18:59 PM	laptop	kernel	[   15.672000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:18:59 PM	laptop	kernel	[   15.672000] ath_pci: 0.9.4.5 (0.9.3.1)

08/13/2007 10:18:59 PM	laptop	kernel	[   15.908000] ath_rate_sample: 1.2 (0.9.3.1)

08/13/2007 10:18:59 PM	laptop	kernel	[   15.912000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps

08/13/2007 10:18:59 PM	laptop	kernel	[   15.912000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps

08/13/2007 10:18:59 PM	laptop	kernel	[   15.912000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP

08/13/2007 10:18:59 PM	laptop	kernel	[   15.912000] wifi0: mac 5.6 phy 4.1 radio 4.6

08/13/2007 10:18:59 PM	laptop	kernel	[   15.912000] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps

08/13/2007 10:18:59 PM	laptop	kernel	[   15.912000] wifi0: Use hw queue 0 for WME_AC_BK traffic

08/13/2007 10:18:59 PM	laptop	kernel	[   15.912000] wifi0: Use hw queue 1 for WME_AC_BE traffic

08/13/2007 10:18:59 PM	laptop	kernel	[   15.912000] wifi0: Use hw queue 2 for WME_AC_VI traffic

08/13/2007 10:18:59 PM	laptop	kernel	[   15.912000] wifi0: Use hw queue 3 for WME_AC_VO traffic

08/13/2007 10:18:59 PM	laptop	kernel	[   15.912000] wifi0: Use hw queue 8 for CAB traffic

08/13/2007 10:18:59 PM	laptop	kernel	[   15.912000] wifi0: Use hw queue 9 for beacons

08/13/2007 10:18:59 PM	laptop	kernel	[   15.984000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x254ab1, caps: 0x804713/0x0

08/13/2007 10:18:59 PM	laptop	kernel	[   16.016000] input: SynPS/2 Synaptics TouchPad as /class/input/input3

08/13/2007 10:18:59 PM	laptop	kernel	[   16.020000] pnp: Device 00:0a activated.

08/13/2007 10:18:59 PM	laptop	kernel	[   16.020000] wbsd: Copyright(c) Pierre Ossman

08/13/2007 10:18:59 PM	laptop	kernel	[   16.020000] wbsd: Winbond W83L51xD SD/MMC card interface driver

08/13/2007 10:18:59 PM	laptop	kernel	[   16.024000] mmc0: W83L51xD id 7112 at 0x248 irq 6 FIFO PnP

08/13/2007 10:18:59 PM	laptop	kernel	[   16.036000] wifi0: Atheros 5212: mem=0xd0000000, irq=10

08/13/2007 10:18:59 PM	laptop	kernel	[   16.060000] irda_init()

08/13/2007 10:18:59 PM	laptop	kernel	[   16.060000] NET: Registered protocol family 23

08/13/2007 10:18:59 PM	laptop	kernel	[   16.320000] cs: IO port probe 0x100-0x3af: excluding 0x230-0x237

08/13/2007 10:18:59 PM	laptop	kernel	[   16.324000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7

08/13/2007 10:18:59 PM	laptop	kernel	[   16.324000] cs: IO port probe 0x820-0x8ff: clean.

08/13/2007 10:18:59 PM	laptop	kernel	[   16.324000] cs: IO port probe 0xa00-0xaff: clean.

08/13/2007 10:18:59 PM	laptop	kernel	[   16.324000] cs: IO port probe 0xc00-0xcf7: clean.

08/13/2007 10:18:59 PM	laptop	kernel	[   16.384000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:18:59 PM	laptop	kernel	[   16.384000] PCI: Setting latency timer of device 0000:00:1f.5 to 64

08/13/2007 10:18:59 PM	laptop	kernel	[   17.204000] intel8x0: clocking to 48000

08/13/2007 10:18:59 PM	laptop	kernel	[   17.204000] intel8x0_measure_ac97_clock: measured 55257 usecs

08/13/2007 10:18:59 PM	laptop	kernel	[   17.240000] NET: Registered protocol family 17

08/13/2007 10:18:59 PM	laptop	kernel	[   17.308000] fuse init (API version 7.8)

08/13/2007 10:18:59 PM	laptop	kernel	[   17.336000] lp0: using parport0 (interrupt-driven).

08/13/2007 10:18:59 PM	laptop	kernel	[   17.404000] ACPI: PCI Interrupt 0000:00:1f.3[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:18:59 PM	laptop	kernel	[   17.512000] Adding 2441840k swap on /dev/disk/by-uuid/f4d24f1c-a9d1-4889-88e5-bcbee8f6f6fb.  Priority:-1 extents:1 across:2441840k

08/13/2007 10:18:59 PM	laptop	kernel	[   17.688000] EXT3 FS on sda1, internal journal

08/13/2007 10:18:59 PM	laptop	kernel	[   17.888000] kjournald starting.  Commit interval 5 seconds

08/13/2007 10:18:59 PM	laptop	kernel	[   17.896000] EXT3-fs: mounted filesystem with ordered data mode.

08/13/2007 10:18:59 PM	laptop	kernel	[   17.896000] EXT3 FS on sda3, internal journal

08/13/2007 10:18:59 PM	laptop	kernel	[   18.528000] ACPI: Battery Slot [BAT1] (battery present)

08/13/2007 10:18:59 PM	laptop	kernel	[   18.568000] ACPI Error (evxfevnt-0189): Could not enable SleepButton event [20060707]

08/13/2007 10:18:59 PM	laptop	kernel	[   18.568000] ACPI: Power Button (FF) [PWRF]

08/13/2007 10:18:59 PM	laptop	kernel	[   18.568000] ACPI Warning (evxface-0146): Could not enable fixed event 3 [20060707]

08/13/2007 10:18:59 PM	laptop	kernel	[   18.568000] input: Power Button (FF) as /class/input/input4

08/13/2007 10:18:59 PM	laptop	kernel	[   18.604000] input: Lid Switch as /class/input/input5

08/13/2007 10:18:59 PM	laptop	kernel	[   18.608000] ACPI: Lid Switch [LID]

08/13/2007 10:18:59 PM	laptop	kernel	[   18.636000] input: Power Button (CM) as /class/input/input6

08/13/2007 10:18:59 PM	laptop	kernel	[   18.640000] ACPI: Power Button (CM) [PWRB]

08/13/2007 10:18:59 PM	laptop	kernel	[   18.720000] No dock devices found.

08/13/2007 10:18:59 PM	laptop	kernel	[   18.752000] Using specific hotkey driver

08/13/2007 10:18:59 PM	laptop	kernel	[   18.776000] ACPI: AC Adapter [ACAD] (off-line)

08/13/2007 10:18:59 PM	laptop	kernel	[   18.784000] ibm_acpi: ec object not found

08/13/2007 10:18:59 PM	laptop	kernel	[   18.816000] pcc_acpi: loading...

08/13/2007 10:18:59 PM	laptop	kernel	[    3.264000] Time: acpi_pm clocksource has been installed.

08/13/2007 10:18:59 PM	laptop	kernel	[    3.312000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:18:59 PM	laptop	kernel	[    3.312000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10

08/13/2007 10:18:59 PM	laptop	kernel	[    3.312000] ehci_hcd 0000:00:1d.7: debug port 1

08/13/2007 10:18:59 PM	laptop	kernel	[    3.312000] ehci_hcd 0000:00:1d.7: EHCI Host Controller

08/13/2007 10:18:59 PM	laptop	kernel	[    3.312000] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xf4000000

08/13/2007 10:18:59 PM	laptop	kernel	[    3.312000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4

08/13/2007 10:18:59 PM	laptop	kernel	[    3.312000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7

08/13/2007 10:18:59 PM	laptop	kernel	[    3.312000] PCI: Setting latency timer of device 0000:00:1d.7 to 64

08/13/2007 10:18:59 PM	laptop	kernel	[    3.316000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004

08/13/2007 10:18:59 PM	laptop	kernel	[    3.316000] hub 4-0:1.0: 6 ports detected

08/13/2007 10:18:59 PM	laptop	kernel	[    3.316000] hub 4-0:1.0: USB hub found

08/13/2007 10:18:59 PM	laptop	kernel	[    3.316000] usb usb4: configuration #1 chosen from 1 choice

08/13/2007 10:18:59 PM	laptop	kernel	[    3.424000] SCSI subsystem initialized

08/13/2007 10:18:59 PM	laptop	kernel	[    3.428000] libata version 2.20 loaded.

08/13/2007 10:18:59 PM	laptop	kernel	[    3.432000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:18:59 PM	laptop	kernel	[    3.432000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011100 irq 14

08/13/2007 10:18:59 PM	laptop	kernel	[    3.432000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011108 irq 15

08/13/2007 10:18:59 PM	laptop	kernel	[    3.432000] ata_piix 0000:00:1f.1: version 2.10ac1

08/13/2007 10:18:59 PM	laptop	kernel	[    3.432000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)

08/13/2007 10:18:59 PM	laptop	kernel	[    3.432000] PCI: Setting latency timer of device 0000:00:1f.1 to 64

08/13/2007 10:18:59 PM	laptop	kernel	[    3.432000] scsi0 : ata_piix

08/13/2007 10:18:59 PM	laptop	kernel	[    3.596000] ata1.00: 117210240 sectors, multi 16: LBA48 

08/13/2007 10:18:59 PM	laptop	kernel	[    3.596000] ata1.00: ATA-6: HTE726060M9AT00, MH4OA6AA, max UDMA/100

08/13/2007 10:18:59 PM	laptop	kernel	[    3.596000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240

08/13/2007 10:18:59 PM	laptop	kernel	[    3.604000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240

08/13/2007 10:18:59 PM	laptop	kernel	[    3.604000] ata1.00: configured for UDMA/100

08/13/2007 10:18:59 PM	laptop	kernel	[    3.604000] scsi1 : ata_piix

08/13/2007 10:18:59 PM	laptop	kernel	[    3.948000] ata2.00: ATAPI, max UDMA/33

08/13/2007 10:18:59 PM	laptop	kernel	[    4.136000] ata2.00: configured for UDMA/33

08/13/2007 10:18:59 PM	laptop	kernel	[    4.136000] scsi 0:0:0:0: Direct-Access     ATA      HTE726060M9AT00  MH4O PQ: 0 ANSI: 5

08/13/2007 10:18:59 PM	laptop	kernel	[    4.140000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:18:59 PM	laptop	kernel	[    4.140000] scsi 1:0:0:0: CD-ROM            TOSHIBA  ODD-DVD SD-R6372 1030 PQ: 0 ANSI: 5

08/13/2007 10:18:59 PM	laptop	kernel	[    4.192000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[d0010800-d0010fff]  Max Packet=[2048]  IR/IT contexts=[4/4]

08/13/2007 10:18:59 PM	laptop	kernel	[    4.200000] 8139cp 0000:02:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip

08/13/2007 10:18:59 PM	laptop	kernel	[    4.200000] 8139cp 0000:02:01.0: Try the "8139too" driver instead.

08/13/2007 10:18:59 PM	laptop	kernel	[    4.200000] 8139too Fast Ethernet driver 0.9.28

08/13/2007 10:18:59 PM	laptop	kernel	[    4.200000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:18:59 PM	laptop	kernel	[    4.200000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'

08/13/2007 10:18:59 PM	laptop	kernel	[    4.200000] eth0: RealTek RTL8139 at 0xf88a2000, 00:02:3f:09:99:a3, IRQ 10

08/13/2007 10:18:59 PM	laptop	kernel	[    4.212000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)

08/13/2007 10:18:59 PM	laptop	kernel	[    4.212000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)

08/13/2007 10:18:59 PM	laptop	kernel	[    4.212000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

08/13/2007 10:18:59 PM	laptop	kernel	[    4.212000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

08/13/2007 10:18:59 PM	laptop	kernel	[    4.212000] sda: Mode Sense: 00 3a 00 00

08/13/2007 10:18:59 PM	laptop	kernel	[    4.212000] sda: Mode Sense: 00 3a 00 00

08/13/2007 10:18:59 PM	laptop	kernel	[    4.212000]  sda: sda1 sda2 < sda5 > sda3 sda4

08/13/2007 10:18:59 PM	laptop	kernel	[    4.212000] sda: Write Protect is off

08/13/2007 10:18:59 PM	laptop	kernel	[    4.212000] sda: Write Protect is off

08/13/2007 10:18:59 PM	laptop	kernel	[    4.244000] sd 0:0:0:0: Attached scsi disk sda

08/13/2007 10:18:59 PM	laptop	kernel	[    4.248000] scsi 1:0:0:0: Attached scsi generic sg1 type 5

08/13/2007 10:18:59 PM	laptop	kernel	[    4.248000] sd 0:0:0:0: Attached scsi generic sg0 type 0

08/13/2007 10:18:59 PM	laptop	kernel	[    4.260000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray

08/13/2007 10:18:59 PM	laptop	kernel	[    4.260000] sr 1:0:0:0: Attached scsi CD-ROM sr0

08/13/2007 10:18:59 PM	laptop	kernel	[    4.260000] Uniform CD-ROM driver Revision: 3.20

08/13/2007 10:18:59 PM	laptop	kernel	[    4.476000] Attempting manual resume

08/13/2007 10:18:59 PM	laptop	kernel	[    4.476000] PM: Checking swsusp image.

08/13/2007 10:18:59 PM	laptop	kernel	[    4.476000] PM: Resume from disk failed.

08/13/2007 10:18:59 PM	laptop	kernel	[    4.476000] swsusp: Resume From Partition 8:5

08/13/2007 10:18:59 PM	laptop	kernel	[    4.512000] EXT3-fs: mounted filesystem with ordered data mode.

08/13/2007 10:18:59 PM	laptop	kernel	[    4.512000] kjournald starting.  Commit interval 5 seconds

08/13/2007 10:18:59 PM	laptop	kernel	[    5.472000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f495240117e]

08/13/2007 10:18:59 PM	laptop	kernel	[    7.837249] Built 1 zonelists.  Total pages: 260081

08/13/2007 10:18:59 PM	laptop	kernel	[    7.837254] Kernel command line: root=UUID=f2db0809-08f4-4d50-bf89-177269e9374a ro quiet splash

08/13/2007 10:18:59 PM	laptop	kernel	[    7.837397] Local APIC disabled by BIOS -- you can enable it with "lapic"

08/13/2007 10:18:59 PM	laptop	kernel	[    7.837406] mapped APIC to ffffd000 (0180c000)

08/13/2007 10:18:59 PM	laptop	kernel	[    7.837409] Enabling fast FPU save and restore... done.

08/13/2007 10:18:59 PM	laptop	kernel	[    7.837412] Enabling unmasked SIMD FPU exception support... done.

08/13/2007 10:18:59 PM	laptop	kernel	[    7.837423] Initializing CPU#0

08/13/2007 10:18:59 PM	laptop	kernel	[    7.837497] PID hash table entries: 4096 (order: 12, 16384 bytes)

08/13/2007 10:18:59 PM	laptop	kernel	[    7.838690] Console: colour VGA+ 80x25

08/13/2007 10:18:59 PM	laptop	kernel	[    7.839234] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)

08/13/2007 10:18:59 PM	laptop	kernel	[    7.839774] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)

08/13/2007 10:18:59 PM	laptop	kernel	[    7.871423] Memory: 1028308k/1048512k available (1992k kernel code, 19468k reserved, 900k data, 328k init, 131008k highmem)

08/13/2007 10:18:59 PM	laptop	kernel	[    7.871432] virtual kernel memory layout:

08/13/2007 10:18:59 PM	laptop	kernel	[    7.871433]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)

08/13/2007 10:18:59 PM	laptop	kernel	[    7.871434]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)

08/13/2007 10:18:59 PM	laptop	kernel	[    7.871435]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)

08/13/2007 10:18:59 PM	laptop	kernel	[    7.871436]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)

08/13/2007 10:18:59 PM	laptop	kernel	[    7.871437]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)

08/13/2007 10:18:59 PM	laptop	kernel	[    7.871438]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)

08/13/2007 10:18:59 PM	laptop	kernel	[    7.871440]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)

08/13/2007 10:18:59 PM	laptop	kernel	[    7.871443] Checking if this processor honours the WP bit even in supervisor mode... Ok.

08/13/2007 10:18:59 PM	laptop	kernel	[    7.949364] Calibrating delay using timer specific routine.. 3989.75 BogoMIPS (lpj=7979504)

08/13/2007 10:18:59 PM	laptop	kernel	[    7.949400] Security Framework v1.0.0 initialized

08/13/2007 10:18:59 PM	laptop	kernel	[    7.949407] SELinux:  Disabled at boot.

08/13/2007 10:18:59 PM	laptop	kernel	[    7.949421] Mount-cache hash table entries: 512

08/13/2007 10:18:59 PM	laptop	kernel	[    7.949542] CPU: After generic identify, caps: afe9f9bf 00000000 00000000 00000000 00000180 00000000 00000000

08/13/2007 10:18:59 PM	laptop	kernel	[    7.949552] CPU: L1 I cache: 32K, L1 D cache: 32K

08/13/2007 10:18:59 PM	laptop	kernel	[    7.949554] CPU: L2 cache: 2048K

08/13/2007 10:18:59 PM	laptop	kernel	[    7.949557] CPU: After all inits, caps: afe9f9bf 00000000 00000000 00002040 00000180 00000000 00000000

08/13/2007 10:18:59 PM	laptop	kernel	[    7.949565] Compat vDSO mapped to ffffe000.

08/13/2007 10:18:59 PM	laptop	kernel	[    7.949569] Remapping vsyscall page to ffffe000

08/13/2007 10:18:59 PM	laptop	kernel	[    7.949578] Checking 'hlt' instruction... OK.

08/13/2007 10:18:59 PM	laptop	kernel	[    7.965429] SMP alternatives: switching to UP code

08/13/2007 10:18:59 PM	laptop	kernel	[    7.965621] Freeing SMP alternatives: 11k freed

08/13/2007 10:18:59 PM	laptop	kernel	[    7.965781] Early unpacking initramfs... done

08/13/2007 10:18:59 PM	laptop	kernel	[    8.248744] ACPI: Core revision 20060707

08/13/2007 10:18:59 PM	laptop	kernel	[    8.248848] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.

08/13/2007 10:18:59 PM	laptop	kernel	[    8.250414] ACPI: setting ELCR to 0200 (from 0c00)

08/13/2007 10:18:59 PM	laptop	kernel	[    8.256719] CPU0: Intel(R) Pentium(R) M processor 2.00GHz stepping 06

08/13/2007 10:18:59 PM	laptop	kernel	[    8.256724] SMP motherboard not detected.

08/13/2007 10:18:59 PM	laptop	kernel	[    8.256726] Local APIC not detected. Using dummy APIC emulation.

08/13/2007 10:18:59 PM	laptop	kernel	[    8.256757] Brought up 1 CPUs

08/13/2007 10:18:59 PM	laptop	kernel	[    8.256963] Booting paravirtualized kernel on bare hardware

08/13/2007 10:18:59 PM	laptop	kernel	[    8.257038] Time:  3:18:40  Date: 07/14/107

08/13/2007 10:18:59 PM	laptop	kernel	[    8.257063] NET: Registered protocol family 16

08/13/2007 10:18:59 PM	laptop	kernel	[    8.257136] EISA bus registered

08/13/2007 10:18:59 PM	laptop	kernel	[    8.257140] ACPI: bus type pci registered

08/13/2007 10:18:59 PM	laptop	kernel	[    8.257172] PCI: PCI BIOS revision 2.10 entry at 0xe97a4, last bus=2

08/13/2007 10:18:59 PM	laptop	kernel	[    8.257174] PCI: Using configuration type 1

08/13/2007 10:18:59 PM	laptop	kernel	[    8.257175] Setting up standard PCI resources

08/13/2007 10:18:59 PM	laptop	kernel	[    8.259298] ACPI: Interpreter enabled

08/13/2007 10:18:59 PM	laptop	kernel	[    8.259300] ACPI: Using PIC for interrupt routing

08/13/2007 10:18:59 PM	laptop	kernel	[    8.259632] ACPI: PCI Root Bridge [PCI0] (0000:00)

08/13/2007 10:18:59 PM	laptop	kernel	[    8.259635] PCI: Probing PCI hardware (bus 00)

08/13/2007 10:18:59 PM	laptop	kernel	[    8.260421] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO

08/13/2007 10:18:59 PM	laptop	kernel	[    8.260425] PCI quirk: region 1300-133f claimed by ICH4 GPIO

08/13/2007 10:18:59 PM	laptop	kernel	[    8.260651] Boot video device is 0000:01:00.0

08/13/2007 10:18:59 PM	laptop	kernel	[    8.260883] PCI: Transparent bridge - 0000:00:1e.0

08/13/2007 10:18:59 PM	laptop	kernel	[    8.260929] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')

08/13/2007 10:18:59 PM	laptop	kernel	[    8.260932] Please report the result to linux-kernel to fix this permanently

08/13/2007 10:18:59 PM	laptop	kernel	[    8.260947] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]

08/13/2007 10:18:59 PM	laptop	kernel	[    8.266191] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]

08/13/2007 10:18:59 PM	laptop	kernel	[    8.266322] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB_._PRT]

08/13/2007 10:18:59 PM	laptop	kernel	[    8.267300] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 *10)

08/13/2007 10:18:59 PM	laptop	kernel	[    8.267469] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 10) *11

08/13/2007 10:18:59 PM	laptop	kernel	[    8.267636] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 10) *11

08/13/2007 10:18:59 PM	laptop	kernel	[    8.267805] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 10) *11

08/13/2007 10:18:59 PM	laptop	kernel	[    8.267981] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.

08/13/2007 10:18:59 PM	laptop	kernel	[    8.268154] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.

08/13/2007 10:18:59 PM	laptop	kernel	[    8.268328] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.

08/13/2007 10:18:59 PM	laptop	kernel	[    8.268503] ACPI: PCI Interrupt Link [LNKH] (IRQs 5 10) *11

08/13/2007 10:18:59 PM	laptop	kernel	[    8.310012] Linux Plug and Play Support v0.97 (c) Adam Belay

08/13/2007 10:18:59 PM	laptop	kernel	[    8.310018] pnp: PnP ACPI init

08/13/2007 10:18:59 PM	laptop	kernel	[    8.333130] pnp: PnP ACPI: found 11 devices

08/13/2007 10:18:59 PM	laptop	kernel	[    8.333133] PnPBIOS: Disabled by ACPI PNP

08/13/2007 10:18:59 PM	laptop	kernel	[    8.333168] PCI: Using ACPI for IRQ routing

08/13/2007 10:18:59 PM	laptop	kernel	[    8.333171] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report

08/13/2007 10:18:59 PM	laptop	kernel	[    8.333196] PCI: Cannot allocate resource region 0 of device 0000:02:03.0

08/13/2007 10:18:59 PM	laptop	kernel	[    8.335847] NET: Registered protocol family 8

08/13/2007 10:18:59 PM	laptop	kernel	[    8.335849] NET: Registered protocol family 20

08/13/2007 10:18:59 PM	laptop	kernel	[    8.336185] PCI: Bridge: 0000:00:01.0

08/13/2007 10:18:59 PM	laptop	kernel	[    8.336187]   IO window: c000-dfff

08/13/2007 10:18:59 PM	laptop	kernel	[    8.336191]   MEM window: e0000000-efffffff

08/13/2007 10:18:59 PM	laptop	kernel	[    8.336194]   PREFETCH window: a0000000-afffffff

08/13/2007 10:18:59 PM	laptop	kernel	[    8.336201] PCI: Bus 3, cardbus bridge: 0000:02:03.0

08/13/2007 10:18:59 PM	laptop	kernel	[    8.336203]   IO window: 0000a400-0000a4ff

08/13/2007 10:18:59 PM	laptop	kernel	[    8.336207]   IO window: 0000a800-0000a8ff

08/13/2007 10:18:59 PM	laptop	kernel	[    8.336210]   PREFETCH window: 90000000-93ffffff

08/13/2007 10:18:59 PM	laptop	kernel	[    8.336214]   MEM window: d4000000-d7ffffff

08/13/2007 10:18:59 PM	laptop	kernel	[    8.336217] PCI: Bridge: 0000:00:1e.0

08/13/2007 10:18:59 PM	laptop	kernel	[    8.336220]   IO window: a000-bfff

08/13/2007 10:18:59 PM	laptop	kernel	[    8.336224]   MEM window: d0000000-dfffffff

08/13/2007 10:18:59 PM	laptop	kernel	[    8.336228]   PREFETCH window: 90000000-9fffffff

08/13/2007 10:18:59 PM	laptop	kernel	[    8.336241] PCI: Setting latency timer of device 0000:00:1e.0 to 64

08/13/2007 10:18:59 PM	laptop	kernel	[    8.336380] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10

08/13/2007 10:18:59 PM	laptop	kernel	[    8.336382] PCI: setting IRQ 10 as level-triggered

08/13/2007 10:18:59 PM	laptop	kernel	[    8.336386] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:18:59 PM	laptop	kernel	[    8.336406] NET: Registered protocol family 2

08/13/2007 10:18:59 PM	laptop	kernel	[    8.368896] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)

08/13/2007 10:18:59 PM	laptop	kernel	[    8.369013] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)

08/13/2007 10:18:59 PM	laptop	kernel	[    8.369961] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)

08/13/2007 10:18:59 PM	laptop	kernel	[    8.370625] TCP: Hash tables configured (established 131072 bind 65536)

08/13/2007 10:18:59 PM	laptop	kernel	[    8.370629] TCP reno registered

08/13/2007 10:18:59 PM	laptop	kernel	[    8.380985] checking if image is initramfs... it is

08/13/2007 10:18:59 PM	laptop	kernel	[    8.933803] Freeing initrd memory: 6772k freed

08/13/2007 10:18:59 PM	laptop	kernel	[    8.934059] Simple Boot Flag at 0x37 set to 0x1

08/13/2007 10:18:59 PM	laptop	kernel	[    8.934244] audit: initializing netlink socket (disabled)

08/13/2007 10:18:59 PM	laptop	kernel	[    8.934260] audit(1187061521.280:1): initialized

08/13/2007 10:18:59 PM	laptop	kernel	[    8.934333] highmem bounce pool size: 64 pages

08/13/2007 10:18:59 PM	laptop	kernel	[    8.934394] VFS: Disk quotas dquot_6.5.1

08/13/2007 10:18:59 PM	laptop	kernel	[    8.934414] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)

08/13/2007 10:18:59 PM	laptop	kernel	[    8.934467] io scheduler noop registered

08/13/2007 10:18:59 PM	laptop	kernel	[    8.934470] io scheduler anticipatory registered

08/13/2007 10:18:59 PM	laptop	kernel	[    8.934472] io scheduler deadline registered

08/13/2007 10:18:59 PM	laptop	kernel	[    8.934482] io scheduler cfq registered (default)

08/13/2007 10:18:59 PM	laptop	kernel	[    8.934774] isapnp: Scanning for PnP cards...

08/13/2007 10:18:59 PM	laptop	kernel	[    9.288154] isapnp: No Plug & Play device found

08/13/2007 10:18:59 PM	laptop	kernel	[    9.309845] Real Time Clock Driver v1.12ac

08/13/2007 10:18:59 PM	laptop	kernel	[    9.309903] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled

08/13/2007 10:18:59 PM	laptop	kernel	[    9.310102] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A

08/13/2007 10:18:59 PM	laptop	kernel	[    9.310814] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10

08/13/2007 10:18:59 PM	laptop	kernel	[    9.310817] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:18:59 PM	laptop	kernel	[    9.310826] ACPI: PCI interrupt for device 0000:00:1f.6 disabled

08/13/2007 10:18:59 PM	laptop	kernel	[    9.310899] mice: PS/2 mouse device common for all mice

08/13/2007 10:18:59 PM	laptop	kernel	[    9.311389] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize

08/13/2007 10:18:59 PM	laptop	kernel	[    9.311590] input: Macintosh mouse button emulation as /class/input/input0

08/13/2007 10:18:59 PM	laptop	kernel	[    9.311620] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2

08/13/2007 10:18:59 PM	laptop	kernel	[    9.311623] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

08/13/2007 10:18:59 PM	laptop	kernel	[    9.311882] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12

08/13/2007 10:18:59 PM	laptop	kernel	[    9.312146] i8042.c: Detected active multiplexing controller, rev 1.1.

08/13/2007 10:18:59 PM	laptop	kernel	[    9.312186] serio: i8042 KBD port at 0x60,0x64 irq 1

08/13/2007 10:18:59 PM	laptop	kernel	[    9.312190] serio: i8042 AUX0 port at 0x60,0x64 irq 12

08/13/2007 10:18:59 PM	laptop	kernel	[    9.312192] serio: i8042 AUX1 port at 0x60,0x64 irq 12

08/13/2007 10:18:59 PM	laptop	kernel	[    9.312194] serio: i8042 AUX2 port at 0x60,0x64 irq 12

08/13/2007 10:18:59 PM	laptop	kernel	[    9.312196] serio: i8042 AUX3 port at 0x60,0x64 irq 12

08/13/2007 10:18:59 PM	laptop	kernel	[    9.312293] EISA: Probing bus 0 at eisa.0

08/13/2007 10:18:59 PM	laptop	kernel	[    9.312300] Cannot allocate resource for EISA slot 1

08/13/2007 10:18:59 PM	laptop	kernel	[    9.312327] EISA: Detected 0 cards.

08/13/2007 10:18:59 PM	laptop	kernel	[    9.342458] TCP cubic registered

08/13/2007 10:18:59 PM	laptop	kernel	[    9.342471] NET: Registered protocol family 1

08/13/2007 10:18:59 PM	laptop	kernel	[    9.342491] Using IPI No-Shortcut mode

08/13/2007 10:18:59 PM	laptop	kernel	[    9.342545] ACPI: (supports S0 S1 S3 S4 S5)

08/13/2007 10:18:59 PM	laptop	kernel	[    9.342583]   Magic number: 3:649:310

08/13/2007 10:18:59 PM	laptop	kernel	[    9.342598]   hash matches device ttyxd

08/13/2007 10:18:59 PM	laptop	kernel	[    9.342697]   hash matches device tty39

08/13/2007 10:18:59 PM	laptop	kernel	[    9.343004] Freeing unused kernel memory: 328k freed

08/13/2007 10:18:59 PM	laptop	kernel	[    9.343650] Time: tsc clocksource has been installed.

08/13/2007 10:18:59 PM	laptop	kernel	[    9.344597] input: AT Translated Set 2 keyboard as /class/input/input1

08/13/2007 10:18:59 PM	laptop	kernel	Inspecting /boot/System.map-2.6.20-16-generic

08/13/2007 10:18:59 PM	laptop	kernel	Loaded 24977 symbols from /boot/System.map-2.6.20-16-generic.

08/13/2007 10:18:59 PM	laptop	kernel	No module symbols loaded - kernel modules not enabled. 

08/13/2007 10:18:59 PM	laptop	kernel	Symbols match kernel version 2.6.20.

08/13/2007 10:18:59 PM	laptop	syslogd 1.4.1#20ubuntu4	restart.

08/13/2007 10:19:00 PM	laptop	dhclient	DHCPREQUEST on ath0 to 255.255.255.255 port 67

08/13/2007 10:19:01 PM	laptop	dhcdbd	Started up.

08/13/2007 10:19:02 PM	laptop	avahi-daemon[4548]	avahi-daemon 0.6.17 starting up.

08/13/2007 10:19:02 PM	laptop	avahi-daemon[4548]	Found user 'avahi' (UID 105) and group 'avahi' (GID 111).

08/13/2007 10:19:02 PM	laptop	avahi-daemon[4548]	Network interface enumeration completed.

08/13/2007 10:19:02 PM	laptop	avahi-daemon[4548]	No service found in /etc/avahi/services.

08/13/2007 10:19:02 PM	laptop	avahi-daemon[4548]	Registering HINFO record with values 'I686'/'LINUX'.

08/13/2007 10:19:02 PM	laptop	avahi-daemon[4548]	Server startup complete. Host name is laptop.local. Local service cookie is 168113587.

08/13/2007 10:19:02 PM	laptop	avahi-daemon[4548]	Successfully called chroot().

08/13/2007 10:19:02 PM	laptop	avahi-daemon[4548]	Successfully dropped remaining capabilities.

08/13/2007 10:19:02 PM	laptop	avahi-daemon[4548]	Successfully dropped root privileges.

08/13/2007 10:19:02 PM	laptop	hpiod	1.7.3 accepting connections at 2208... 

08/13/2007 10:19:02 PM	laptop	kernel	[   21.648000] eth0: link down

08/13/2007 10:19:02 PM	laptop	kernel	[   21.700000] ppdev: user-space parallel port driver

08/13/2007 10:19:02 PM	laptop	NetworkManager	<debug info>^I[1187061542.437835] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_ODD_DVD_SD_R6372'). 

08/13/2007 10:19:02 PM	laptop	NetworkManager	<information>^Iath0: Device is fully-supported using driver 'ath_pci'. 

08/13/2007 10:19:02 PM	laptop	NetworkManager	<information>^IDeactivating device ath0. 

08/13/2007 10:19:02 PM	laptop	NetworkManager	<information>^IDeactivating device eth0. 

08/13/2007 10:19:02 PM	laptop	NetworkManager	<information>^Ieth0: Device is fully-supported using driver '8139too'. 

08/13/2007 10:19:02 PM	laptop	NetworkManager	<information>^Inm_device_init(): device's worker thread started, continuing. 

08/13/2007 10:19:02 PM	laptop	NetworkManager	<information>^Inm_device_init(): device's worker thread started, continuing. 

08/13/2007 10:19:02 PM	laptop	NetworkManager	<information>^Inm_device_init(): waiting for device's worker thread to start 

08/13/2007 10:19:02 PM	laptop	NetworkManager	<information>^Inm_device_init(): waiting for device's worker thread to start 

08/13/2007 10:19:02 PM	laptop	NetworkManager	<information>^INow managing wired Ethernet (802.3) device 'eth0'. 

08/13/2007 10:19:02 PM	laptop	NetworkManager	<information>^INow managing wireless (802.11) device 'ath0'. 

08/13/2007 10:19:02 PM	laptop	NetworkManager	<information>^Istarting... 

08/13/2007 10:19:03 PM	laptop	kernel	[   22.664000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)

08/13/2007 10:19:03 PM	laptop	kernel	[   22.664000] apm: overridden by ACPI.

08/13/2007 10:19:04 PM	laptop	anacron[4883]	Anacron 2.3 started on 2007-08-13

08/13/2007 10:19:04 PM	laptop	anacron[4883]	Normal exit (0 jobs run)

08/13/2007 10:19:04 PM	laptop	hcid[4844]	Bluetooth HCI daemon

08/13/2007 10:19:04 PM	laptop	hcid[4844]	Starting SDP server

08/13/2007 10:19:04 PM	laptop	kernel	[   23.664000] Bluetooth: Core ver 2.11

08/13/2007 10:19:04 PM	laptop	kernel	[   23.664000] Bluetooth: HCI device and connection manager initialized

08/13/2007 10:19:04 PM	laptop	kernel	[   23.664000] Bluetooth: HCI socket layer initialized

08/13/2007 10:19:04 PM	laptop	kernel	[   23.664000] NET: Registered protocol family 31

08/13/2007 10:19:04 PM	laptop	kernel	[   23.724000] Bluetooth: L2CAP socket layer initialized

08/13/2007 10:19:04 PM	laptop	kernel	[   23.724000] Bluetooth: L2CAP ver 2.8

08/13/2007 10:19:04 PM	laptop	kernel	[   23.864000] Bluetooth: RFCOMM socket layer initialized

08/13/2007 10:19:04 PM	laptop	kernel	[   23.864000] Bluetooth: RFCOMM TTY layer initialized

08/13/2007 10:19:04 PM	laptop	kernel	[   23.864000] Bluetooth: RFCOMM ver 1.8

08/13/2007 10:19:04 PM	laptop	NetworkManager	<debug info>^I[1187061544.209617] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 

08/13/2007 10:19:04 PM	laptop	/usr/sbin/cron[4910]	(CRON) INFO (pidfile fd = 3)

08/13/2007 10:19:04 PM	laptop	/usr/sbin/cron[4911]	(CRON) INFO (Running @reboot jobs)

08/13/2007 10:19:04 PM	laptop	/usr/sbin/cron[4911]	(CRON) STARTUP (fork ok)

08/13/2007 10:19:05 PM	laptop	kernel	[   25.168000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.

08/13/2007 10:19:05 PM	laptop	kernel	[   25.168000] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0

08/13/2007 10:19:05 PM	laptop	kernel	[   25.196000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:19:07 PM	laptop	dhclient	DHCPREQUEST on ath0 to 255.255.255.255 port 67

08/13/2007 10:19:08 PM	laptop	kernel	[   27.532000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.

08/13/2007 10:19:08 PM	laptop	kernel	[   27.532000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode

08/13/2007 10:19:08 PM	laptop	kernel	[   27.532000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode

08/13/2007 10:19:08 PM	laptop	kernel	[   27.532000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)

08/13/2007 10:19:08 PM	laptop	kernel	[   27.532000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)

08/13/2007 10:19:08 PM	laptop	kernel	[   27.532000] [fglrx] Have to use kernel AGP support to avoid conflicts.

08/13/2007 10:19:08 PM	laptop	kernel	[   27.532000] [fglrx] Internal AGP support requested, but kernel AGP support active.

08/13/2007 10:19:08 PM	laptop	kernel	[   27.540000] [fglrx] free       GART = 51113984

08/13/2007 10:19:08 PM	laptop	kernel	[   27.540000] [fglrx] free       Inv  = 0

08/13/2007 10:19:08 PM	laptop	kernel	[   27.540000] [fglrx] free       LFB  = 96432128

08/13/2007 10:19:08 PM	laptop	kernel	[   27.540000] [fglrx] max single GART = 51113984

08/13/2007 10:19:08 PM	laptop	kernel	[   27.540000] [fglrx] max single Inv  = 0

08/13/2007 10:19:08 PM	laptop	kernel	[   27.540000] [fglrx] max single LFB  = 96432128

08/13/2007 10:19:08 PM	laptop	kernel	[   27.540000] [fglrx] total      GART = 67108864

08/13/2007 10:19:08 PM	laptop	kernel	[   27.540000] [fglrx] total      Inv  = 0

08/13/2007 10:19:08 PM	laptop	kernel	[   27.540000] [fglrx] total      LFB  = 134217728

08/13/2007 10:19:08 PM	laptop	kernel	[   27.540000] [fglrx] total      TIM  = 0

08/13/2007 10:19:12 PM	laptop	kdm_greet[5030]	Can't open default user face

08/13/2007 10:19:17 PM	laptop	dhclient	DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4

08/13/2007 10:19:21 PM	laptop	dhclient	DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4

08/13/2007 10:19:23 PM	laptop	kdm_greet[5030]	Internal error: memory corruption detected

08/13/2007 10:19:25 PM	laptop	dhclient	DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8

08/13/2007 10:19:33 PM	laptop	dhclient	DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 13

08/13/2007 10:19:43 PM	laptop	hcid[4844]	Default passkey agent (:1.7, /org/bluez/passkey_agent_5199) registered

08/13/2007 10:19:43 PM	laptop	kernel	[   63.376000] ADDRCONF(NETDEV_UP): eth0: link is not ready

08/13/2007 10:19:43 PM	laptop	kernel	[   63.376000] lo: Disabled Privacy Extensions

08/13/2007 10:19:43 PM	laptop	kernel	[   63.376000] NET: Registered protocol family 10

08/13/2007 10:19:44 PM	laptop	avahi-daemon[4548]	Registering new address record for fe80::20f:eaff:fe91:3517 on ath0.*.

08/13/2007 10:19:46 PM	laptop	dhclient	DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 2

08/13/2007 10:19:48 PM	laptop	avahi-daemon[4548]	Joining mDNS multicast group on interface ath0.IPv4 with address 192.168.2.6.

08/13/2007 10:19:48 PM	laptop	avahi-daemon[4548]	New relevant interface ath0.IPv4 for mDNS.

08/13/2007 10:19:48 PM	laptop	avahi-daemon[4548]	Registering new address record for 192.168.2.6 on ath0.IPv4.

08/13/2007 10:19:48 PM	laptop	dhclient	No DHCPOFFERS received.

08/13/2007 10:19:48 PM	laptop	dhclient	Trying recorded lease 192.168.2.6

08/13/2007 10:19:53 PM	laptop	kernel	[   73.436000] ath0: no IPv6 routers present

08/13/2007 10:19:53 PM	laptop	NetworkManager	<information>^IUpdating allowed wireless network lists. 

08/13/2007 10:19:58 PM	laptop	avahi-autoipd(ath0)[5256]	fopen() failed: Permission denied

08/13/2007 10:19:58 PM	laptop	avahi-autoipd(ath0)[5256]	Found user 'avahi-autoipd' (UID 103) and group 'avahi-autoipd' (GID 109).

08/13/2007 10:19:58 PM	laptop	avahi-autoipd(ath0)[5256]	Starting with address 169.254.4.222

08/13/2007 10:19:58 PM	laptop	avahi-autoipd(ath0)[5256]	Successfully called chroot().

08/13/2007 10:19:58 PM	laptop	avahi-autoipd(ath0)[5256]	Successfully dropped root privileges.

08/13/2007 10:19:58 PM	laptop	avahi-daemon[4548]	Interface ath0.IPv4 no longer relevant for mDNS.

08/13/2007 10:19:58 PM	laptop	avahi-daemon[4548]	Leaving mDNS multicast group on interface ath0.IPv4 with address 192.168.2.6.

08/13/2007 10:19:58 PM	laptop	avahi-daemon[4548]	Withdrawing address record for 192.168.2.6 on ath0.

08/13/2007 10:20:02 PM	laptop	avahi-autoipd(ath0)[5256]	Callout BIND, address 169.254.4.222 on interface ath0

08/13/2007 10:20:03 PM	laptop	avahi-daemon[4548]	Joining mDNS multicast group on interface ath0.IPv4 with address 169.254.4.222.

08/13/2007 10:20:03 PM	laptop	avahi-daemon[4548]	New relevant interface ath0.IPv4 for mDNS.

08/13/2007 10:20:03 PM	laptop	avahi-daemon[4548]	Registering new address record for 169.254.4.222 on ath0.IPv4.

08/13/2007 10:20:06 PM	laptop	avahi-autoipd(ath0)[5256]	fopen() failed: Permission denied

08/13/2007 10:20:06 PM	laptop	avahi-autoipd(ath0)[5256]	Successfully claimed IP address 169.254.4.222

08/13/2007 10:20:06 PM	laptop	dhclient	No working leases in persistent database - sleeping.

08/13/2007 10:20:37 PM	laptop	ntpdate[5310]	can't find host ntp.ubuntu.com 

08/13/2007 10:20:37 PM	laptop	ntpdate[5310]	no servers can be used, exiting

08/13/2007 10:27:23 PM	laptop	dhclient	DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 6

08/13/2007 10:27:29 PM	laptop	dhclient	DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 14

08/13/2007 10:27:43 PM	laptop	dhclient	DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11

08/13/2007 10:27:54 PM	laptop	avahi-autoipd(ath0)[5256]	A routable address has been configured.

08/13/2007 10:27:54 PM	laptop	avahi-autoipd(ath0)[5256]	Callout UNBIND, address 169.254.4.222 on interface ath0

08/13/2007 10:27:54 PM	laptop	avahi-daemon[4548]	Joining mDNS multicast group on interface ath0.IPv4 with address 192.168.2.6.

08/13/2007 10:27:54 PM	laptop	avahi-daemon[4548]	Leaving mDNS multicast group on interface ath0.IPv4 with address 169.254.4.222.

08/13/2007 10:27:54 PM	laptop	avahi-daemon[4548]	Registering new address record for 192.168.2.6 on ath0.IPv4.

08/13/2007 10:27:54 PM	laptop	avahi-daemon[4548]	Withdrawing address record for 169.254.4.222 on ath0.

08/13/2007 10:27:54 PM	laptop	dhclient	No DHCPOFFERS received.

08/13/2007 10:27:54 PM	laptop	dhclient	Trying recorded lease 192.168.2.6

08/13/2007 10:28:04 PM	laptop	avahi-autoipd(ath0)[5256]	No longer a routable address configured, restarting probe process.

08/13/2007 10:28:04 PM	laptop	avahi-daemon[4548]	Interface ath0.IPv4 no longer relevant for mDNS.

08/13/2007 10:28:04 PM	laptop	avahi-daemon[4548]	Leaving mDNS multicast group on interface ath0.IPv4 with address 192.168.2.6.

08/13/2007 10:28:04 PM	laptop	avahi-daemon[4548]	Withdrawing address record for 192.168.2.6 on ath0.

08/13/2007 10:28:04 PM	laptop	dhclient	No working leases in persistent database - sleeping.

08/13/2007 10:28:08 PM	laptop	avahi-autoipd(ath0)[5256]	Callout BIND, address 169.254.4.222 on interface ath0

08/13/2007 10:28:08 PM	laptop	avahi-daemon[4548]	Joining mDNS multicast group on interface ath0.IPv4 with address 169.254.4.222.

08/13/2007 10:28:08 PM	laptop	avahi-daemon[4548]	New relevant interface ath0.IPv4 for mDNS.

08/13/2007 10:28:08 PM	laptop	avahi-daemon[4548]	Registering new address record for 169.254.4.222 on ath0.IPv4.

08/13/2007 10:28:12 PM	laptop	avahi-autoipd(ath0)[5256]	fopen() failed: Permission denied

08/13/2007 10:28:12 PM	laptop	avahi-autoipd(ath0)[5256]	Successfully claimed IP address 169.254.4.222

08/13/2007 10:28:37 PM	laptop	anacron[5443]	Anacron 2.3 started on 2007-08-13

08/13/2007 10:28:37 PM	laptop	anacron[5443]	Normal exit (0 jobs run)

08/13/2007 10:34:36 PM	laptop	dhclient	DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7

08/13/2007 10:34:43 PM	laptop	dhclient	DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9

08/13/2007 10:34:52 PM	laptop	dhclient	DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12

08/13/2007 10:35:04 PM	laptop	dhclient	DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3

08/13/2007 10:35:07 PM	laptop	avahi-autoipd(ath0)[5256]	A routable address has been configured.

08/13/2007 10:35:07 PM	laptop	avahi-autoipd(ath0)[5256]	Callout UNBIND, address 169.254.4.222 on interface ath0

08/13/2007 10:35:07 PM	laptop	avahi-daemon[4548]	Joining mDNS multicast group on interface ath0.IPv4 with address 192.168.2.6.

08/13/2007 10:35:07 PM	laptop	avahi-daemon[4548]	Leaving mDNS multicast group on interface ath0.IPv4 with address 169.254.4.222.

08/13/2007 10:35:07 PM	laptop	avahi-daemon[4548]	Registering new address record for 192.168.2.6 on ath0.IPv4.

08/13/2007 10:35:07 PM	laptop	avahi-daemon[4548]	Withdrawing address record for 169.254.4.222 on ath0.

08/13/2007 10:35:07 PM	laptop	dhclient	No DHCPOFFERS received.

08/13/2007 10:35:07 PM	laptop	dhclient	Trying recorded lease 192.168.2.6

08/13/2007 10:35:10 PM	laptop	avahi-autoipd(ath0)[5256]	No longer a routable address configured, restarting probe process.

08/13/2007 10:35:10 PM	laptop	avahi-daemon[4548]	Interface ath0.IPv4 no longer relevant for mDNS.

08/13/2007 10:35:10 PM	laptop	avahi-daemon[4548]	Leaving mDNS multicast group on interface ath0.IPv4 with address 192.168.2.6.

08/13/2007 10:35:10 PM	laptop	avahi-daemon[4548]	Withdrawing address record for 192.168.2.6 on ath0.

08/13/2007 10:35:10 PM	laptop	dhclient	No working leases in persistent database - sleeping.

08/13/2007 10:35:14 PM	laptop	avahi-autoipd(ath0)[5256]	Callout BIND, address 169.254.4.222 on interface ath0

08/13/2007 10:35:14 PM	laptop	avahi-daemon[4548]	Joining mDNS multicast group on interface ath0.IPv4 with address 169.254.4.222.

08/13/2007 10:35:14 PM	laptop	avahi-daemon[4548]	New relevant interface ath0.IPv4 for mDNS.

08/13/2007 10:35:14 PM	laptop	avahi-daemon[4548]	Registering new address record for 169.254.4.222 on ath0.IPv4.

08/13/2007 10:35:18 PM	laptop	avahi-autoipd(ath0)[5256]	fopen() failed: Permission denied

08/13/2007 10:35:18 PM	laptop	avahi-autoipd(ath0)[5256]	Successfully claimed IP address 169.254.4.222


```

/var/log/messages
```
08/13/2007 09:31:08 PM	laptop	none	-- MARK --

08/13/2007 09:51:08 PM	laptop	none	-- MARK --

08/13/2007 09:59:54 PM	laptop	none	exiting on signal 15

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000]     0:        0 ->   262128

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] 127MB HIGHMEM available.

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] 896MB LOWMEM available.

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] ACPI: PM-Timer IO Port: 0x1008

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bfb80000)

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fffffc0 (ACPI data)

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000]  BIOS-e820: 000000003fffffc0 - 0000000040000000 (ACPI NVS)

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] BIOS-provided physical RAM map:

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fef0000 end: 000000003fff0000 type: 1

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] copy_e820_map() start: 000000003fff0000 size: 000000000000ffc0 end: 000000003fffffc0 type: 3

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] copy_e820_map() start: 000000003fffffc0 size: 0000000000000040 end: 0000000040000000 type: 4

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] copy_e820_map() start: 00000000ffb80000 size: 0000000000080000 end: 00000000ffc00000 type: 2

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] copy_e820_map() start: 00000000fff80000 size: 0000000000080000 end: 0000000100000000 type: 2

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] copy_e820_map() type is E820_RAM

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] copy_e820_map() type is E820_RAM

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] Detected 1993.689 MHz processor.

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000]   DMA             0 ->     4096

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] DMI 2.3 present.

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] early_node_map[1] active PFN ranges

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000]   HighMem    229376 ->   262128

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000]   Normal       4096 ->   229376

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] sanitize end

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] sanitize start

08/13/2007 10:00:47 PM	laptop	kernel	[    0.000000] Zone PFN ranges:

08/13/2007 10:00:47 PM	laptop	kernel	[   10.028836] isapnp: No Plug & Play device found

08/13/2007 10:00:47 PM	laptop	kernel	[   10.050354] Real Time Clock Driver v1.12ac

08/13/2007 10:00:47 PM	laptop	kernel	[   10.050413] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled

08/13/2007 10:00:47 PM	laptop	kernel	[   10.050612] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A

08/13/2007 10:00:47 PM	laptop	kernel	[   10.051321] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10

08/13/2007 10:00:47 PM	laptop	kernel	[   10.051325] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:00:47 PM	laptop	kernel	[   10.051333] ACPI: PCI interrupt for device 0000:00:1f.6 disabled

08/13/2007 10:00:47 PM	laptop	kernel	[   10.051404] mice: PS/2 mouse device common for all mice

08/13/2007 10:00:47 PM	laptop	kernel	[   10.051894] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize

08/13/2007 10:00:47 PM	laptop	kernel	[   10.052096] input: Macintosh mouse button emulation as /class/input/input0

08/13/2007 10:00:47 PM	laptop	kernel	[   10.052127] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2

08/13/2007 10:00:47 PM	laptop	kernel	[   10.052130] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

08/13/2007 10:00:47 PM	laptop	kernel	[   10.052358] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12

08/13/2007 10:00:47 PM	laptop	kernel	[   10.052630] i8042.c: Detected active multiplexing controller, rev 1.1.

08/13/2007 10:00:47 PM	laptop	kernel	[   10.052671] serio: i8042 KBD port at 0x60,0x64 irq 1

08/13/2007 10:00:47 PM	laptop	kernel	[   10.052674] serio: i8042 AUX0 port at 0x60,0x64 irq 12

08/13/2007 10:00:47 PM	laptop	kernel	[   10.052676] serio: i8042 AUX1 port at 0x60,0x64 irq 12

08/13/2007 10:00:47 PM	laptop	kernel	[   10.052678] serio: i8042 AUX2 port at 0x60,0x64 irq 12

08/13/2007 10:00:47 PM	laptop	kernel	[   10.052680] serio: i8042 AUX3 port at 0x60,0x64 irq 12

08/13/2007 10:00:47 PM	laptop	kernel	[   10.052778] EISA: Probing bus 0 at eisa.0

08/13/2007 10:00:47 PM	laptop	kernel	[   10.052785] Cannot allocate resource for EISA slot 1

08/13/2007 10:00:47 PM	laptop	kernel	[   10.052812] EISA: Detected 0 cards.

08/13/2007 10:00:47 PM	laptop	kernel	[   10.082942] TCP cubic registered

08/13/2007 10:00:47 PM	laptop	kernel	[   10.082954] NET: Registered protocol family 1

08/13/2007 10:00:47 PM	laptop	kernel	[   10.082975] Using IPI No-Shortcut mode

08/13/2007 10:00:47 PM	laptop	kernel	[   10.083031] ACPI: (supports S0 S1 S3 S4 S5)

08/13/2007 10:00:47 PM	laptop	kernel	[   10.083068]   Magic number: 3:340:7

08/13/2007 10:00:47 PM	laptop	kernel	[   10.083485] Freeing unused kernel memory: 328k freed

08/13/2007 10:00:47 PM	laptop	kernel	[   10.084418] Time: tsc clocksource has been installed.

08/13/2007 10:00:47 PM	laptop	kernel	[   10.085076] input: AT Translated Set 2 keyboard as /class/input/input1

08/13/2007 10:00:47 PM	laptop	kernel	[   11.264784] Capability LSM initialized

08/13/2007 10:00:47 PM	laptop	kernel	[   11.293697] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])

08/13/2007 10:00:47 PM	laptop	kernel	[   11.293703] ACPI: Processor [CPU0] (supports 8 throttling states)

08/13/2007 10:00:47 PM	laptop	kernel	[   11.576455] usbcore: registered new interface driver usbfs

08/13/2007 10:00:47 PM	laptop	kernel	[   11.576477] usbcore: registered new interface driver hub

08/13/2007 10:00:47 PM	laptop	kernel	[   11.576498] usbcore: registered new device driver usb

08/13/2007 10:00:47 PM	laptop	kernel	[   11.577220] USB Universal Host Controller Interface driver v3.0

08/13/2007 10:00:47 PM	laptop	kernel	[   11.577466] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10

08/13/2007 10:00:47 PM	laptop	kernel	[   11.577469] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:00:47 PM	laptop	kernel	[   11.577482] uhci_hcd 0000:00:1d.0: UHCI Host Controller

08/13/2007 10:00:47 PM	laptop	kernel	[   11.577644] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1

08/13/2007 10:00:47 PM	laptop	kernel	[   11.577667] uhci_hcd 0000:00:1d.0: irq 10, io base 0x00001200

08/13/2007 10:00:47 PM	laptop	kernel	[   11.577759] usb usb1: configuration #1 chosen from 1 choice

08/13/2007 10:00:47 PM	laptop	kernel	[   11.577777] hub 1-0:1.0: USB hub found

08/13/2007 10:00:47 PM	laptop	kernel	[   11.577783] hub 1-0:1.0: 2 ports detected

08/13/2007 10:00:47 PM	laptop	kernel	[   11.644369] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)

08/13/2007 10:00:47 PM	laptop	kernel	[   11.678778] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10

08/13/2007 10:00:47 PM	laptop	kernel	[   11.678783] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:00:47 PM	laptop	kernel	[   11.678799] uhci_hcd 0000:00:1d.1: UHCI Host Controller

08/13/2007 10:00:47 PM	laptop	kernel	[   11.678822] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2

08/13/2007 10:00:47 PM	laptop	kernel	[   11.678844] uhci_hcd 0000:00:1d.1: irq 10, io base 0x00001600

08/13/2007 10:00:47 PM	laptop	kernel	[   11.678933] usb usb2: configuration #1 chosen from 1 choice

08/13/2007 10:00:47 PM	laptop	kernel	[   11.678953] hub 2-0:1.0: USB hub found

08/13/2007 10:00:47 PM	laptop	kernel	[   11.678959] hub 2-0:1.0: 2 ports detected

08/13/2007 10:00:47 PM	laptop	kernel	[   11.782458] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:00:47 PM	laptop	kernel	[   11.782476] uhci_hcd 0000:00:1d.2: UHCI Host Controller

08/13/2007 10:00:47 PM	laptop	kernel	[   11.782494] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3

08/13/2007 10:00:47 PM	laptop	kernel	[   11.782517] uhci_hcd 0000:00:1d.2: irq 10, io base 0x00001700

08/13/2007 10:00:47 PM	laptop	kernel	[   11.782597] usb usb3: configuration #1 chosen from 1 choice

08/13/2007 10:00:47 PM	laptop	kernel	[   11.782621] hub 3-0:1.0: USB hub found

08/13/2007 10:00:47 PM	laptop	kernel	[   11.782627] hub 3-0:1.0: 2 ports detected

08/13/2007 10:00:47 PM	laptop	kernel	[   14.676000] Linux agpgart interface v0.102 (c) Dave Jones

08/13/2007 10:00:47 PM	laptop	kernel	[   14.680000] iTCO_vendor_support: vendor-support=0

08/13/2007 10:00:47 PM	laptop	kernel	[   14.680000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)

08/13/2007 10:00:47 PM	laptop	kernel	[   14.680000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)

08/13/2007 10:00:47 PM	laptop	kernel	[   14.680000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)

08/13/2007 10:00:47 PM	laptop	kernel	[   14.692000] intel_rng: don't want to disable this in firmware setup, and if

08/13/2007 10:00:47 PM	laptop	kernel	[   14.692000] intel_rng: Firmware space is locked read-only. If you can't or

08/13/2007 10:00:47 PM	laptop	kernel	[   14.692000] intel_rng: RNG, try using the 'no_fwh_detect' option.

08/13/2007 10:00:47 PM	laptop	kernel	[   14.692000] intel_rng: you are certain that your system has a functional

08/13/2007 10:00:47 PM	laptop	kernel	[   15.160000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5

08/13/2007 10:00:47 PM	laptop	kernel	[   15.164000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4

08/13/2007 10:00:47 PM	laptop	kernel	[   15.328000] agpgart: Detected an Intel 855PM Chipset.

08/13/2007 10:00:47 PM	laptop	kernel	[   15.332000] agpgart: AGP aperture is 64M @ 0xb0000000

08/13/2007 10:00:47 PM	laptop	kernel	[   15.340000] input: PC Speaker as /class/input/input2

08/13/2007 10:00:47 PM	laptop	kernel	[   15.528000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]

08/13/2007 10:00:47 PM	laptop	kernel	[   15.528000] parport: PnPBIOS parport detected.

08/13/2007 10:00:47 PM	laptop	kernel	[   15.564000] NET: Registered protocol family 23

08/13/2007 10:00:47 PM	laptop	kernel	[   15.600000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)

08/13/2007 10:00:47 PM	laptop	kernel	[   15.600000] ath_hal: module license 'Proprietary' taints kernel.

08/13/2007 10:00:47 PM	laptop	kernel	[   15.636000] Yenta: CardBus bridge found at 0000:02:03.0 [14c0:0012]

08/13/2007 10:00:47 PM	laptop	kernel	[   15.636000] Yenta: Routing CardBus interrupts to PCI

08/13/2007 10:00:47 PM	laptop	kernel	[   15.636000] Yenta TI: socket 0000:02:03.0, mfunc 0x001c1112, devctl 0x44

08/13/2007 10:00:47 PM	laptop	kernel	[   15.636000] Yenta: Using CSCINT to route CSC interrupts to PCI

08/13/2007 10:00:47 PM	laptop	kernel	[   15.740000] wlan: 0.8.4.2 (0.9.3.1)

08/13/2007 10:00:47 PM	laptop	kernel	[   15.744000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x254ab1, caps: 0x804713/0x0

08/13/2007 10:00:47 PM	laptop	kernel	[   15.776000] input: SynPS/2 Synaptics TouchPad as /class/input/input3

08/13/2007 10:00:47 PM	laptop	kernel	[   15.800000] ath_pci: 0.9.4.5 (0.9.3.1)

08/13/2007 10:00:47 PM	laptop	kernel	[   15.860000] pnp: Device 00:0a activated.

08/13/2007 10:00:47 PM	laptop	kernel	[   15.860000] wbsd: Copyright(c) Pierre Ossman

08/13/2007 10:00:47 PM	laptop	kernel	[   15.860000] wbsd: Winbond W83L51xD SD/MMC card interface driver

08/13/2007 10:00:47 PM	laptop	kernel	[   15.864000] mmc0: W83L51xD id 7112 at 0x248 irq 6 FIFO PnP

08/13/2007 10:00:47 PM	laptop	kernel	[   15.876000] cs: IO port probe 0xa000-0xbfff: clean.

08/13/2007 10:00:47 PM	laptop	kernel	[   15.876000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xbfff

08/13/2007 10:00:47 PM	laptop	kernel	[   15.876000] pcmcia: parent PCI bridge Memory window: 0x90000000 - 0x9fffffff

08/13/2007 10:00:47 PM	laptop	kernel	[   15.876000] pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xdfffffff

08/13/2007 10:00:47 PM	laptop	kernel	[   15.876000] Socket status: 30000006

08/13/2007 10:00:47 PM	laptop	kernel	[   15.876000] Yenta: ISA IRQ mask 0x0808, PCI irq 10

08/13/2007 10:00:47 PM	laptop	kernel	[   15.876000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06

08/13/2007 10:00:47 PM	laptop	kernel	[   15.888000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:00:47 PM	laptop	kernel	[   16.196000] ath_rate_sample: 1.2 (0.9.3.1)

08/13/2007 10:00:47 PM	laptop	kernel	[   16.196000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps

08/13/2007 10:00:47 PM	laptop	kernel	[   16.196000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps

08/13/2007 10:00:47 PM	laptop	kernel	[   16.196000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP

08/13/2007 10:00:47 PM	laptop	kernel	[   16.196000] wifi0: mac 5.6 phy 4.1 radio 4.6

08/13/2007 10:00:47 PM	laptop	kernel	[   16.196000] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps

08/13/2007 10:00:47 PM	laptop	kernel	[   16.196000] wifi0: Use hw queue 0 for WME_AC_BK traffic

08/13/2007 10:00:47 PM	laptop	kernel	[   16.196000] wifi0: Use hw queue 1 for WME_AC_BE traffic

08/13/2007 10:00:47 PM	laptop	kernel	[   16.196000] wifi0: Use hw queue 2 for WME_AC_VI traffic

08/13/2007 10:00:47 PM	laptop	kernel	[   16.196000] wifi0: Use hw queue 3 for WME_AC_VO traffic

08/13/2007 10:00:47 PM	laptop	kernel	[   16.196000] wifi0: Use hw queue 8 for CAB traffic

08/13/2007 10:00:47 PM	laptop	kernel	[   16.196000] wifi0: Use hw queue 9 for beacons

08/13/2007 10:00:47 PM	laptop	kernel	[   16.264000] wifi0: Atheros 5212: mem=0xd0000000, irq=10

08/13/2007 10:00:47 PM	laptop	kernel	[   16.396000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:00:47 PM	laptop	kernel	[   16.532000] cs: IO port probe 0x100-0x3af: excluding 0x230-0x237

08/13/2007 10:00:47 PM	laptop	kernel	[   16.532000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7

08/13/2007 10:00:47 PM	laptop	kernel	[   16.536000] cs: IO port probe 0x820-0x8ff: clean.

08/13/2007 10:00:47 PM	laptop	kernel	[   16.536000] cs: IO port probe 0xa00-0xaff: clean.

08/13/2007 10:00:47 PM	laptop	kernel	[   16.536000] cs: IO port probe 0xc00-0xcf7: clean.

08/13/2007 10:00:47 PM	laptop	kernel	[   17.216000] intel8x0: clocking to 48000

08/13/2007 10:00:47 PM	laptop	kernel	[   17.216000] intel8x0_measure_ac97_clock: measured 55446 usecs

08/13/2007 10:00:47 PM	laptop	kernel	[   17.336000] fuse init (API version 7.8)

08/13/2007 10:00:47 PM	laptop	kernel	[   17.356000] lp0: using parport0 (interrupt-driven).

08/13/2007 10:00:47 PM	laptop	kernel	[   17.428000] NET: Registered protocol family 17

08/13/2007 10:00:47 PM	laptop	kernel	[   17.440000] ACPI: PCI Interrupt 0000:00:1f.3[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:00:47 PM	laptop	kernel	[   17.552000] Adding 2441840k swap on /dev/disk/by-uuid/f4d24f1c-a9d1-4889-88e5-bcbee8f6f6fb.  Priority:-1 extents:1 across:2441840k

08/13/2007 10:00:47 PM	laptop	kernel	[   17.724000] EXT3 FS on sda1, internal journal

08/13/2007 10:00:47 PM	laptop	kernel	[   17.916000] kjournald starting.  Commit interval 5 seconds

08/13/2007 10:00:47 PM	laptop	kernel	[   17.924000] EXT3-fs: mounted filesystem with ordered data mode.

08/13/2007 10:00:47 PM	laptop	kernel	[   17.924000] EXT3 FS on sda3, internal journal

08/13/2007 10:00:47 PM	laptop	kernel	[   18.600000] ACPI: Battery Slot [BAT1] (battery present)

08/13/2007 10:00:47 PM	laptop	kernel	[   18.640000] ACPI: Power Button (FF) [PWRF]

08/13/2007 10:00:47 PM	laptop	kernel	[   18.640000] input: Power Button (FF) as /class/input/input4

08/13/2007 10:00:47 PM	laptop	kernel	[   18.672000] input: Lid Switch as /class/input/input5

08/13/2007 10:00:47 PM	laptop	kernel	[   18.676000] ACPI: Lid Switch [LID]

08/13/2007 10:00:47 PM	laptop	kernel	[   18.704000] input: Power Button (CM) as /class/input/input6

08/13/2007 10:00:47 PM	laptop	kernel	[   18.708000] ACPI: Power Button (CM) [PWRB]

08/13/2007 10:00:47 PM	laptop	kernel	[   18.804000] No dock devices found.

08/13/2007 10:00:47 PM	laptop	kernel	[   18.832000] Using specific hotkey driver

08/13/2007 10:00:47 PM	laptop	kernel	[   18.852000] ACPI: AC Adapter [ACAD] (off-line)

08/13/2007 10:00:47 PM	laptop	kernel	[   18.888000] pcc_acpi: loading...

08/13/2007 10:00:47 PM	laptop	kernel	[    3.264000] Time: acpi_pm clocksource has been installed.

08/13/2007 10:00:47 PM	laptop	kernel	[    3.316000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:00:47 PM	laptop	kernel	[    3.316000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10

08/13/2007 10:00:47 PM	laptop	kernel	[    3.316000] ehci_hcd 0000:00:1d.7: debug port 1

08/13/2007 10:00:47 PM	laptop	kernel	[    3.316000] ehci_hcd 0000:00:1d.7: EHCI Host Controller

08/13/2007 10:00:47 PM	laptop	kernel	[    3.316000] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xf4000000

08/13/2007 10:00:47 PM	laptop	kernel	[    3.316000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4

08/13/2007 10:00:47 PM	laptop	kernel	[    3.320000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004

08/13/2007 10:00:47 PM	laptop	kernel	[    3.320000] hub 4-0:1.0: 6 ports detected

08/13/2007 10:00:47 PM	laptop	kernel	[    3.320000] hub 4-0:1.0: USB hub found

08/13/2007 10:00:47 PM	laptop	kernel	[    3.320000] usb usb4: configuration #1 chosen from 1 choice

08/13/2007 10:00:47 PM	laptop	kernel	[    3.428000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:00:47 PM	laptop	kernel	[    3.480000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[d0010800-d0010fff]  Max Packet=[2048]  IR/IT contexts=[4/4]

08/13/2007 10:00:47 PM	laptop	kernel	[    3.484000] 8139cp 0000:02:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip

08/13/2007 10:00:47 PM	laptop	kernel	[    3.484000] 8139cp 0000:02:01.0: Try the "8139too" driver instead.

08/13/2007 10:00:47 PM	laptop	kernel	[    3.492000] SCSI subsystem initialized

08/13/2007 10:00:47 PM	laptop	kernel	[    3.504000] 8139too Fast Ethernet driver 0.9.28

08/13/2007 10:00:47 PM	laptop	kernel	[    3.504000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:00:47 PM	laptop	kernel	[    3.504000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011100 irq 14

08/13/2007 10:00:47 PM	laptop	kernel	[    3.504000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011108 irq 15

08/13/2007 10:00:47 PM	laptop	kernel	[    3.504000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)

08/13/2007 10:00:47 PM	laptop	kernel	[    3.504000] scsi0 : ata_piix

08/13/2007 10:00:47 PM	laptop	kernel	[    3.668000] ata1.00: 117210240 sectors, multi 16: LBA48 

08/13/2007 10:00:47 PM	laptop	kernel	[    3.668000] ata1.00: ATA-6: HTE726060M9AT00, MH4OA6AA, max UDMA/100

08/13/2007 10:00:47 PM	laptop	kernel	[    3.668000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240

08/13/2007 10:00:47 PM	laptop	kernel	[    3.676000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240

08/13/2007 10:00:47 PM	laptop	kernel	[    3.676000] ata1.00: configured for UDMA/100

08/13/2007 10:00:47 PM	laptop	kernel	[    3.676000] scsi1 : ata_piix

08/13/2007 10:00:47 PM	laptop	kernel	[    4.020000] ata2.00: ATAPI, max UDMA/33

08/13/2007 10:00:47 PM	laptop	kernel	[    4.208000] ata2.00: configured for UDMA/33

08/13/2007 10:00:47 PM	laptop	kernel	[    4.208000] scsi 0:0:0:0: Direct-Access     ATA      HTE726060M9AT00  MH4O PQ: 0 ANSI: 5

08/13/2007 10:00:47 PM	laptop	kernel	[    4.212000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:00:47 PM	laptop	kernel	[    4.212000] eth0: RealTek RTL8139 at 0xf88a2000, 00:02:3f:09:99:a3, IRQ 10

08/13/2007 10:00:47 PM	laptop	kernel	[    4.212000] scsi 1:0:0:0: CD-ROM            TOSHIBA  ODD-DVD SD-R6372 1030 PQ: 0 ANSI: 5

08/13/2007 10:00:47 PM	laptop	kernel	[    4.224000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)

08/13/2007 10:00:47 PM	laptop	kernel	[    4.224000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)

08/13/2007 10:00:47 PM	laptop	kernel	[    4.224000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

08/13/2007 10:00:47 PM	laptop	kernel	[    4.224000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

08/13/2007 10:00:47 PM	laptop	kernel	[    4.224000]  sda: sda1 sda2 < sda5 > sda3 sda4

08/13/2007 10:00:47 PM	laptop	kernel	[    4.224000] sda: Write Protect is off

08/13/2007 10:00:47 PM	laptop	kernel	[    4.224000] sda: Write Protect is off

08/13/2007 10:00:47 PM	laptop	kernel	[    4.264000] sd 0:0:0:0: Attached scsi disk sda

08/13/2007 10:00:47 PM	laptop	kernel	[    4.268000] scsi 1:0:0:0: Attached scsi generic sg1 type 5

08/13/2007 10:00:47 PM	laptop	kernel	[    4.268000] sd 0:0:0:0: Attached scsi generic sg0 type 0

08/13/2007 10:00:47 PM	laptop	kernel	[    4.280000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray

08/13/2007 10:00:47 PM	laptop	kernel	[    4.280000] Uniform CD-ROM driver Revision: 3.20

08/13/2007 10:00:47 PM	laptop	kernel	[    4.492000] Attempting manual resume

08/13/2007 10:00:47 PM	laptop	kernel	[    4.524000] EXT3-fs: mounted filesystem with ordered data mode.

08/13/2007 10:00:47 PM	laptop	kernel	[    4.524000] kjournald starting.  Commit interval 5 seconds

08/13/2007 10:00:47 PM	laptop	kernel	[    8.578019] Built 1 zonelists.  Total pages: 260081

08/13/2007 10:00:47 PM	laptop	kernel	[    8.578023] Kernel command line: root=UUID=f2db0809-08f4-4d50-bf89-177269e9374a ro quiet splash

08/13/2007 10:00:47 PM	laptop	kernel	[    8.578167] Local APIC disabled by BIOS -- you can enable it with "lapic"

08/13/2007 10:00:47 PM	laptop	kernel	[    8.578179] Enabling fast FPU save and restore... done.

08/13/2007 10:00:47 PM	laptop	kernel	[    8.578181] Enabling unmasked SIMD FPU exception support... done.

08/13/2007 10:00:47 PM	laptop	kernel	[    8.578192] Initializing CPU#0

08/13/2007 10:00:47 PM	laptop	kernel	[    8.578266] PID hash table entries: 4096 (order: 12, 16384 bytes)

08/13/2007 10:00:47 PM	laptop	kernel	[    8.579476] Console: colour VGA+ 80x25

08/13/2007 10:00:47 PM	laptop	kernel	[    8.580017] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)

08/13/2007 10:00:47 PM	laptop	kernel	[    8.580565] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)

08/13/2007 10:00:47 PM	laptop	kernel	[    8.613420] Memory: 1028308k/1048512k available (1992k kernel code, 19468k reserved, 900k data, 328k init, 131008k highmem)

08/13/2007 10:00:47 PM	laptop	kernel	[    8.613429] virtual kernel memory layout:

08/13/2007 10:00:47 PM	laptop	kernel	[    8.613430]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)

08/13/2007 10:00:47 PM	laptop	kernel	[    8.613431]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)

08/13/2007 10:00:47 PM	laptop	kernel	[    8.613432]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)

08/13/2007 10:00:47 PM	laptop	kernel	[    8.613433]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)

08/13/2007 10:00:47 PM	laptop	kernel	[    8.613434]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)

08/13/2007 10:00:47 PM	laptop	kernel	[    8.613435]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)

08/13/2007 10:00:47 PM	laptop	kernel	[    8.613436]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)

08/13/2007 10:00:47 PM	laptop	kernel	[    8.613439] Checking if this processor honours the WP bit even in supervisor mode... Ok.

08/13/2007 10:00:47 PM	laptop	kernel	[    8.690132] Calibrating delay using timer specific routine.. 3989.72 BogoMIPS (lpj=7979452)

08/13/2007 10:00:47 PM	laptop	kernel	[    8.690168] Security Framework v1.0.0 initialized

08/13/2007 10:00:47 PM	laptop	kernel	[    8.690175] SELinux:  Disabled at boot.

08/13/2007 10:00:47 PM	laptop	kernel	[    8.690189] Mount-cache hash table entries: 512

08/13/2007 10:00:47 PM	laptop	kernel	[    8.690323] CPU: L1 I cache: 32K, L1 D cache: 32K

08/13/2007 10:00:47 PM	laptop	kernel	[    8.690325] CPU: L2 cache: 2048K

08/13/2007 10:00:47 PM	laptop	kernel	[    8.690336] Compat vDSO mapped to ffffe000.

08/13/2007 10:00:47 PM	laptop	kernel	[    8.690340] Remapping vsyscall page to ffffe000

08/13/2007 10:00:47 PM	laptop	kernel	[    8.690349] Checking 'hlt' instruction... OK.

08/13/2007 10:00:47 PM	laptop	kernel	[    8.706199] SMP alternatives: switching to UP code

08/13/2007 10:00:47 PM	laptop	kernel	[    8.706389] Freeing SMP alternatives: 11k freed

08/13/2007 10:00:47 PM	laptop	kernel	[    8.706548] Early unpacking initramfs... done

08/13/2007 10:00:47 PM	laptop	kernel	[    8.989522] ACPI: Core revision 20060707

08/13/2007 10:00:47 PM	laptop	kernel	[    8.989626] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.

08/13/2007 10:00:47 PM	laptop	kernel	[    8.991191] ACPI: setting ELCR to 0200 (from 0c00)

08/13/2007 10:00:47 PM	laptop	kernel	[    8.997478] CPU0: Intel(R) Pentium(R) M processor 2.00GHz stepping 06

08/13/2007 10:00:47 PM	laptop	kernel	[    8.997484] SMP motherboard not detected.

08/13/2007 10:00:47 PM	laptop	kernel	[    8.997486] Local APIC not detected. Using dummy APIC emulation.

08/13/2007 10:00:47 PM	laptop	kernel	[    8.997517] Brought up 1 CPUs

08/13/2007 10:00:47 PM	laptop	kernel	[    8.997726] Booting paravirtualized kernel on bare hardware

08/13/2007 10:00:47 PM	laptop	kernel	[    8.997800] Time:  3:00:28  Date: 07/14/107

08/13/2007 10:00:47 PM	laptop	kernel	[    8.997825] NET: Registered protocol family 16

08/13/2007 10:00:47 PM	laptop	kernel	[    8.997898] EISA bus registered

08/13/2007 10:00:47 PM	laptop	kernel	[    8.997901] ACPI: bus type pci registered

08/13/2007 10:00:47 PM	laptop	kernel	[    8.997932] PCI: PCI BIOS revision 2.10 entry at 0xe97a4, last bus=2

08/13/2007 10:00:47 PM	laptop	kernel	[    8.997934] PCI: Using configuration type 1

08/13/2007 10:00:47 PM	laptop	kernel	[    8.997936] Setting up standard PCI resources

08/13/2007 10:00:47 PM	laptop	kernel	[    9.000059] ACPI: Interpreter enabled

08/13/2007 10:00:47 PM	laptop	kernel	[    9.000061] ACPI: Using PIC for interrupt routing

08/13/2007 10:00:47 PM	laptop	kernel	[    9.000392] ACPI: PCI Root Bridge [PCI0] (0000:00)

08/13/2007 10:00:47 PM	laptop	kernel	[    9.001183] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO

08/13/2007 10:00:47 PM	laptop	kernel	[    9.001186] PCI quirk: region 1300-133f claimed by ICH4 GPIO

08/13/2007 10:00:47 PM	laptop	kernel	[    9.001645] PCI: Transparent bridge - 0000:00:1e.0

08/13/2007 10:00:47 PM	laptop	kernel	[    9.001691] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')

08/13/2007 10:00:47 PM	laptop	kernel	[    9.001693] Please report the result to linux-kernel to fix this permanently

08/13/2007 10:00:47 PM	laptop	kernel	[    9.008060] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 *10)

08/13/2007 10:00:47 PM	laptop	kernel	[    9.008228] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 10) *11

08/13/2007 10:00:47 PM	laptop	kernel	[    9.008395] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 10) *11

08/13/2007 10:00:47 PM	laptop	kernel	[    9.008564] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 10) *11

08/13/2007 10:00:47 PM	laptop	kernel	[    9.008740] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.

08/13/2007 10:00:47 PM	laptop	kernel	[    9.008914] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.

08/13/2007 10:00:47 PM	laptop	kernel	[    9.009088] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.

08/13/2007 10:00:47 PM	laptop	kernel	[    9.009263] ACPI: PCI Interrupt Link [LNKH] (IRQs 5 10) *11

08/13/2007 10:00:47 PM	laptop	kernel	[    9.050779] Linux Plug and Play Support v0.97 (c) Adam Belay

08/13/2007 10:00:47 PM	laptop	kernel	[    9.050786] pnp: PnP ACPI init

08/13/2007 10:00:47 PM	laptop	kernel	[    9.073898] pnp: PnP ACPI: found 11 devices

08/13/2007 10:00:47 PM	laptop	kernel	[    9.073901] PnPBIOS: Disabled by ACPI PNP

08/13/2007 10:00:47 PM	laptop	kernel	[    9.073936] PCI: Using ACPI for IRQ routing

08/13/2007 10:00:47 PM	laptop	kernel	[    9.073938] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report

08/13/2007 10:00:47 PM	laptop	kernel	[    9.073964] PCI: Cannot allocate resource region 0 of device 0000:02:03.0

08/13/2007 10:00:47 PM	laptop	kernel	[    9.076614] NET: Registered protocol family 8

08/13/2007 10:00:47 PM	laptop	kernel	[    9.076616] NET: Registered protocol family 20

08/13/2007 10:00:47 PM	laptop	kernel	[    9.076954] PCI: Bridge: 0000:00:01.0

08/13/2007 10:00:47 PM	laptop	kernel	[    9.076956]   IO window: c000-dfff

08/13/2007 10:00:47 PM	laptop	kernel	[    9.076959]   MEM window: e0000000-efffffff

08/13/2007 10:00:47 PM	laptop	kernel	[    9.076962]   PREFETCH window: a0000000-afffffff

08/13/2007 10:00:47 PM	laptop	kernel	[    9.076970] PCI: Bus 3, cardbus bridge: 0000:02:03.0

08/13/2007 10:00:47 PM	laptop	kernel	[    9.076971]   IO window: 0000a400-0000a4ff

08/13/2007 10:00:47 PM	laptop	kernel	[    9.076975]   IO window: 0000a800-0000a8ff

08/13/2007 10:00:47 PM	laptop	kernel	[    9.076979]   PREFETCH window: 90000000-93ffffff

08/13/2007 10:00:47 PM	laptop	kernel	[    9.076983]   MEM window: d4000000-d7ffffff

08/13/2007 10:00:47 PM	laptop	kernel	[    9.076986] PCI: Bridge: 0000:00:1e.0

08/13/2007 10:00:47 PM	laptop	kernel	[    9.076988]   IO window: a000-bfff

08/13/2007 10:00:47 PM	laptop	kernel	[    9.076993]   MEM window: d0000000-dfffffff

08/13/2007 10:00:47 PM	laptop	kernel	[    9.076997]   PREFETCH window: 90000000-9fffffff

08/13/2007 10:00:47 PM	laptop	kernel	[    9.077149] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10

08/13/2007 10:00:47 PM	laptop	kernel	[    9.077154] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:00:47 PM	laptop	kernel	[    9.077175] NET: Registered protocol family 2

08/13/2007 10:00:47 PM	laptop	kernel	[    9.109664] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)

08/13/2007 10:00:47 PM	laptop	kernel	[    9.109779] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)

08/13/2007 10:00:47 PM	laptop	kernel	[    9.110727] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)

08/13/2007 10:00:47 PM	laptop	kernel	[    9.111391] TCP: Hash tables configured (established 131072 bind 65536)

08/13/2007 10:00:47 PM	laptop	kernel	[    9.111394] TCP reno registered

08/13/2007 10:00:47 PM	laptop	kernel	[    9.121754] checking if image is initramfs... it is

08/13/2007 10:00:47 PM	laptop	kernel	[    9.674496] Freeing initrd memory: 6772k freed

08/13/2007 10:00:47 PM	laptop	kernel	[    9.674751] Simple Boot Flag at 0x37 set to 0x1

08/13/2007 10:00:47 PM	laptop	kernel	[    9.674938] audit: initializing netlink socket (disabled)

08/13/2007 10:00:47 PM	laptop	kernel	[    9.674954] audit(1187060429.284:1): initialized

08/13/2007 10:00:47 PM	laptop	kernel	[    9.675028] highmem bounce pool size: 64 pages

08/13/2007 10:00:47 PM	laptop	kernel	[    9.675090] VFS: Disk quotas dquot_6.5.1

08/13/2007 10:00:47 PM	laptop	kernel	[    9.675109] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)

08/13/2007 10:00:47 PM	laptop	kernel	[    9.675163] io scheduler noop registered

08/13/2007 10:00:47 PM	laptop	kernel	[    9.675166] io scheduler anticipatory registered

08/13/2007 10:00:47 PM	laptop	kernel	[    9.675168] io scheduler deadline registered

08/13/2007 10:00:47 PM	laptop	kernel	[    9.675178] io scheduler cfq registered (default)

08/13/2007 10:00:47 PM	laptop	kernel	[    9.675470] isapnp: Scanning for PnP cards...

08/13/2007 10:00:47 PM	laptop	kernel	Inspecting /boot/System.map-2.6.20-16-generic

08/13/2007 10:00:47 PM	laptop	kernel	Loaded 24977 symbols from /boot/System.map-2.6.20-16-generic.

08/13/2007 10:00:47 PM	laptop	kernel	No module symbols loaded - kernel modules not enabled. 

08/13/2007 10:00:47 PM	laptop	kernel	Symbols match kernel version 2.6.20.

08/13/2007 10:00:47 PM	laptop	syslogd 1.4.1#20ubuntu4	restart.

08/13/2007 10:00:50 PM	laptop	dhcdbd	Started up.

08/13/2007 10:00:50 PM	laptop	hpiod	1.7.3 accepting connections at 2208... 

08/13/2007 10:00:50 PM	laptop	kernel	[   21.708000] eth0: link down

08/13/2007 10:00:50 PM	laptop	kernel	[   21.892000] ppdev: user-space parallel port driver

08/13/2007 10:00:51 PM	laptop	kernel	[   22.756000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)

08/13/2007 10:00:51 PM	laptop	kernel	[   22.756000] apm: overridden by ACPI.

08/13/2007 10:00:52 PM	laptop	kernel	[   23.624000] Bluetooth: Core ver 2.11

08/13/2007 10:00:52 PM	laptop	kernel	[   23.624000] Bluetooth: HCI device and connection manager initialized

08/13/2007 10:00:52 PM	laptop	kernel	[   23.624000] Bluetooth: HCI socket layer initialized

08/13/2007 10:00:52 PM	laptop	kernel	[   23.624000] NET: Registered protocol family 31

08/13/2007 10:00:52 PM	laptop	kernel	[   23.668000] Bluetooth: L2CAP socket layer initialized

08/13/2007 10:00:52 PM	laptop	kernel	[   23.668000] Bluetooth: L2CAP ver 2.8

08/13/2007 10:00:52 PM	laptop	kernel	[   23.804000] Bluetooth: RFCOMM socket layer initialized

08/13/2007 10:00:52 PM	laptop	kernel	[   23.804000] Bluetooth: RFCOMM TTY layer initialized

08/13/2007 10:00:52 PM	laptop	kernel	[   23.804000] Bluetooth: RFCOMM ver 1.8

08/13/2007 10:00:53 PM	laptop	kernel	[   25.104000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.

08/13/2007 10:00:53 PM	laptop	kernel	[   25.104000] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0

08/13/2007 10:00:53 PM	laptop	kernel	[   25.132000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:00:55 PM	laptop	kernel	[   27.468000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.

08/13/2007 10:00:55 PM	laptop	kernel	[   27.468000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode

08/13/2007 10:00:55 PM	laptop	kernel	[   27.468000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode

08/13/2007 10:00:55 PM	laptop	kernel	[   27.468000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)

08/13/2007 10:00:55 PM	laptop	kernel	[   27.468000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)

08/13/2007 10:00:55 PM	laptop	kernel	[   27.468000] [fglrx] Have to use kernel AGP support to avoid conflicts.

08/13/2007 10:00:55 PM	laptop	kernel	[   27.468000] [fglrx] Internal AGP support requested, but kernel AGP support active.

08/13/2007 10:00:55 PM	laptop	kernel	[   27.476000] [fglrx] free       GART = 51113984

08/13/2007 10:00:55 PM	laptop	kernel	[   27.476000] [fglrx] free       Inv  = 0

08/13/2007 10:00:55 PM	laptop	kernel	[   27.476000] [fglrx] free       LFB  = 96432128

08/13/2007 10:00:55 PM	laptop	kernel	[   27.476000] [fglrx] max single GART = 51113984

08/13/2007 10:00:55 PM	laptop	kernel	[   27.476000] [fglrx] max single Inv  = 0

08/13/2007 10:00:55 PM	laptop	kernel	[   27.476000] [fglrx] max single LFB  = 96432128

08/13/2007 10:00:55 PM	laptop	kernel	[   27.476000] [fglrx] total      GART = 67108864

08/13/2007 10:00:55 PM	laptop	kernel	[   27.476000] [fglrx] total      Inv  = 0

08/13/2007 10:00:55 PM	laptop	kernel	[   27.476000] [fglrx] total      LFB  = 134217728

08/13/2007 10:00:55 PM	laptop	kernel	[   27.476000] [fglrx] total      TIM  = 0

08/13/2007 10:01:18 PM	laptop	kernel	[   49.692000] ip_tables: (C) 2000-2006 Netfilter Core Team

08/13/2007 10:01:18 PM	laptop	kernel	[   49.856000] Netfilter messages via NETLINK v0.30.

08/13/2007 10:01:18 PM	laptop	kernel	[   49.880000] nf_conntrack version 0.5.0 (8191 buckets, 65528 max)

08/13/2007 10:01:20 PM	laptop	none	exiting on signal 15

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000]     0:        0 ->   262128

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] 127MB HIGHMEM available.

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] 896MB LOWMEM available.

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] ACPI: PM-Timer IO Port: 0x1008

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bfb80000)

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000]  BIOS-e820: 000000003fff0000 - 000000003fffffc0 (ACPI data)

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000]  BIOS-e820: 000000003fffffc0 - 0000000040000000 (ACPI NVS)

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] BIOS-provided physical RAM map:

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009fc00 end: 000000000009fc00 type: 1

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] copy_e820_map() start: 000000000009fc00 size: 0000000000000400 end: 00000000000a0000 type: 2

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] copy_e820_map() start: 00000000000e0000 size: 0000000000020000 end: 0000000000100000 type: 2

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fef0000 end: 000000003fff0000 type: 1

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] copy_e820_map() start: 000000003fff0000 size: 000000000000ffc0 end: 000000003fffffc0 type: 3

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] copy_e820_map() start: 000000003fffffc0 size: 0000000000000040 end: 0000000040000000 type: 4

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] copy_e820_map() start: 00000000ffb80000 size: 0000000000080000 end: 00000000ffc00000 type: 2

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] copy_e820_map() start: 00000000fff80000 size: 0000000000080000 end: 0000000100000000 type: 2

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] copy_e820_map() type is E820_RAM

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] copy_e820_map() type is E820_RAM

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] Detected 1993.693 MHz processor.

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000]   DMA             0 ->     4096

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] DMI 2.3 present.

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] early_node_map[1] active PFN ranges

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000]   HighMem    229376 ->   262128

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000]   Normal       4096 ->   229376

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] sanitize end

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] sanitize start

08/13/2007 10:18:59 PM	laptop	kernel	[    0.000000] Zone PFN ranges:

08/13/2007 10:18:59 PM	laptop	kernel	[   10.523980] Capability LSM initialized

08/13/2007 10:18:59 PM	laptop	kernel	[   10.552875] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])

08/13/2007 10:18:59 PM	laptop	kernel	[   10.552881] ACPI: Processor [CPU0] (supports 8 throttling states)

08/13/2007 10:18:59 PM	laptop	kernel	[   10.835607] usbcore: registered new interface driver usbfs

08/13/2007 10:18:59 PM	laptop	kernel	[   10.835629] usbcore: registered new interface driver hub

08/13/2007 10:18:59 PM	laptop	kernel	[   10.835650] usbcore: registered new device driver usb

08/13/2007 10:18:59 PM	laptop	kernel	[   10.836407] USB Universal Host Controller Interface driver v3.0

08/13/2007 10:18:59 PM	laptop	kernel	[   10.836654] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10

08/13/2007 10:18:59 PM	laptop	kernel	[   10.836657] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:18:59 PM	laptop	kernel	[   10.836671] uhci_hcd 0000:00:1d.0: UHCI Host Controller

08/13/2007 10:18:59 PM	laptop	kernel	[   10.836830] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1

08/13/2007 10:18:59 PM	laptop	kernel	[   10.836853] uhci_hcd 0000:00:1d.0: irq 10, io base 0x00001200

08/13/2007 10:18:59 PM	laptop	kernel	[   10.836950] usb usb1: configuration #1 chosen from 1 choice

08/13/2007 10:18:59 PM	laptop	kernel	[   10.836971] hub 1-0:1.0: USB hub found

08/13/2007 10:18:59 PM	laptop	kernel	[   10.836976] hub 1-0:1.0: 2 ports detected

08/13/2007 10:18:59 PM	laptop	kernel	[   10.906273] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)

08/13/2007 10:18:59 PM	laptop	kernel	[   10.938020] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10

08/13/2007 10:18:59 PM	laptop	kernel	[   10.938024] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:18:59 PM	laptop	kernel	[   10.938039] uhci_hcd 0000:00:1d.1: UHCI Host Controller

08/13/2007 10:18:59 PM	laptop	kernel	[   10.938061] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2

08/13/2007 10:18:59 PM	laptop	kernel	[   10.938085] uhci_hcd 0000:00:1d.1: irq 10, io base 0x00001600

08/13/2007 10:18:59 PM	laptop	kernel	[   10.938172] usb usb2: configuration #1 chosen from 1 choice

08/13/2007 10:18:59 PM	laptop	kernel	[   10.938192] hub 2-0:1.0: USB hub found

08/13/2007 10:18:59 PM	laptop	kernel	[   10.938197] hub 2-0:1.0: 2 ports detected

08/13/2007 10:18:59 PM	laptop	kernel	[   11.041684] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:18:59 PM	laptop	kernel	[   11.041702] uhci_hcd 0000:00:1d.2: UHCI Host Controller

08/13/2007 10:18:59 PM	laptop	kernel	[   11.041720] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3

08/13/2007 10:18:59 PM	laptop	kernel	[   11.041743] uhci_hcd 0000:00:1d.2: irq 10, io base 0x00001700

08/13/2007 10:18:59 PM	laptop	kernel	[   11.041825] usb usb3: configuration #1 chosen from 1 choice

08/13/2007 10:18:59 PM	laptop	kernel	[   11.041849] hub 3-0:1.0: USB hub found

08/13/2007 10:18:59 PM	laptop	kernel	[   11.041857] hub 3-0:1.0: 2 ports detected

08/13/2007 10:18:59 PM	laptop	kernel	[   14.468000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5

08/13/2007 10:18:59 PM	laptop	kernel	[   14.500000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4

08/13/2007 10:18:59 PM	laptop	kernel	[   14.556000] iTCO_vendor_support: vendor-support=0

08/13/2007 10:18:59 PM	laptop	kernel	[   14.556000] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0x1060)

08/13/2007 10:18:59 PM	laptop	kernel	[   14.556000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)

08/13/2007 10:18:59 PM	laptop	kernel	[   14.556000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)

08/13/2007 10:18:59 PM	laptop	kernel	[   14.572000] intel_rng: don't want to disable this in firmware setup, and if

08/13/2007 10:18:59 PM	laptop	kernel	[   14.572000] intel_rng: Firmware space is locked read-only. If you can't or

08/13/2007 10:18:59 PM	laptop	kernel	[   14.572000] intel_rng: RNG, try using the 'no_fwh_detect' option.

08/13/2007 10:18:59 PM	laptop	kernel	[   14.572000] intel_rng: you are certain that your system has a functional

08/13/2007 10:18:59 PM	laptop	kernel	[   14.856000] Linux agpgart interface v0.102 (c) Dave Jones

08/13/2007 10:18:59 PM	laptop	kernel	[   15.024000] agpgart: Detected an Intel 855PM Chipset.

08/13/2007 10:18:59 PM	laptop	kernel	[   15.028000] agpgart: AGP aperture is 64M @ 0xb0000000

08/13/2007 10:18:59 PM	laptop	kernel	[   15.040000] Yenta: CardBus bridge found at 0000:02:03.0 [14c0:0012]

08/13/2007 10:18:59 PM	laptop	kernel	[   15.040000] Yenta: Routing CardBus interrupts to PCI

08/13/2007 10:18:59 PM	laptop	kernel	[   15.040000] Yenta TI: socket 0000:02:03.0, mfunc 0x001c1112, devctl 0x44

08/13/2007 10:18:59 PM	laptop	kernel	[   15.040000] Yenta: Using CSCINT to route CSC interrupts to PCI

08/13/2007 10:18:59 PM	laptop	kernel	[   15.068000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)

08/13/2007 10:18:59 PM	laptop	kernel	[   15.068000] ath_hal: module license 'Proprietary' taints kernel.

08/13/2007 10:18:59 PM	laptop	kernel	[   15.272000] cs: IO port probe 0xa000-0xbfff: clean.

08/13/2007 10:18:59 PM	laptop	kernel	[   15.272000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xbfff

08/13/2007 10:18:59 PM	laptop	kernel	[   15.272000] pcmcia: parent PCI bridge Memory window: 0x90000000 - 0x9fffffff

08/13/2007 10:18:59 PM	laptop	kernel	[   15.272000] pcmcia: parent PCI bridge Memory window: 0xd0000000 - 0xdfffffff

08/13/2007 10:18:59 PM	laptop	kernel	[   15.272000] Socket status: 30000006

08/13/2007 10:18:59 PM	laptop	kernel	[   15.272000] Yenta: ISA IRQ mask 0x0830, PCI irq 10

08/13/2007 10:18:59 PM	laptop	kernel	[   15.272000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06

08/13/2007 10:18:59 PM	laptop	kernel	[   15.444000] input: PC Speaker as /class/input/input2

08/13/2007 10:18:59 PM	laptop	kernel	[   15.532000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]

08/13/2007 10:18:59 PM	laptop	kernel	[   15.532000] parport: PnPBIOS parport detected.

08/13/2007 10:18:59 PM	laptop	kernel	[   15.612000] wlan: 0.8.4.2 (0.9.3.1)

08/13/2007 10:18:59 PM	laptop	kernel	[   15.672000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:18:59 PM	laptop	kernel	[   15.672000] ath_pci: 0.9.4.5 (0.9.3.1)

08/13/2007 10:18:59 PM	laptop	kernel	[   15.908000] ath_rate_sample: 1.2 (0.9.3.1)

08/13/2007 10:18:59 PM	laptop	kernel	[   15.912000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps

08/13/2007 10:18:59 PM	laptop	kernel	[   15.912000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps

08/13/2007 10:18:59 PM	laptop	kernel	[   15.912000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP

08/13/2007 10:18:59 PM	laptop	kernel	[   15.912000] wifi0: mac 5.6 phy 4.1 radio 4.6

08/13/2007 10:18:59 PM	laptop	kernel	[   15.912000] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps

08/13/2007 10:18:59 PM	laptop	kernel	[   15.912000] wifi0: Use hw queue 0 for WME_AC_BK traffic

08/13/2007 10:18:59 PM	laptop	kernel	[   15.912000] wifi0: Use hw queue 1 for WME_AC_BE traffic

08/13/2007 10:18:59 PM	laptop	kernel	[   15.912000] wifi0: Use hw queue 2 for WME_AC_VI traffic

08/13/2007 10:18:59 PM	laptop	kernel	[   15.912000] wifi0: Use hw queue 3 for WME_AC_VO traffic

08/13/2007 10:18:59 PM	laptop	kernel	[   15.912000] wifi0: Use hw queue 8 for CAB traffic

08/13/2007 10:18:59 PM	laptop	kernel	[   15.912000] wifi0: Use hw queue 9 for beacons

08/13/2007 10:18:59 PM	laptop	kernel	[   15.984000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x254ab1, caps: 0x804713/0x0

08/13/2007 10:18:59 PM	laptop	kernel	[   16.016000] input: SynPS/2 Synaptics TouchPad as /class/input/input3

08/13/2007 10:18:59 PM	laptop	kernel	[   16.020000] pnp: Device 00:0a activated.

08/13/2007 10:18:59 PM	laptop	kernel	[   16.020000] wbsd: Copyright(c) Pierre Ossman

08/13/2007 10:18:59 PM	laptop	kernel	[   16.020000] wbsd: Winbond W83L51xD SD/MMC card interface driver

08/13/2007 10:18:59 PM	laptop	kernel	[   16.024000] mmc0: W83L51xD id 7112 at 0x248 irq 6 FIFO PnP

08/13/2007 10:18:59 PM	laptop	kernel	[   16.036000] wifi0: Atheros 5212: mem=0xd0000000, irq=10

08/13/2007 10:18:59 PM	laptop	kernel	[   16.060000] NET: Registered protocol family 23

08/13/2007 10:18:59 PM	laptop	kernel	[   16.320000] cs: IO port probe 0x100-0x3af: excluding 0x230-0x237

08/13/2007 10:18:59 PM	laptop	kernel	[   16.324000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7

08/13/2007 10:18:59 PM	laptop	kernel	[   16.324000] cs: IO port probe 0x820-0x8ff: clean.

08/13/2007 10:18:59 PM	laptop	kernel	[   16.324000] cs: IO port probe 0xa00-0xaff: clean.

08/13/2007 10:18:59 PM	laptop	kernel	[   16.324000] cs: IO port probe 0xc00-0xcf7: clean.

08/13/2007 10:18:59 PM	laptop	kernel	[   16.384000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:18:59 PM	laptop	kernel	[   17.204000] intel8x0: clocking to 48000

08/13/2007 10:18:59 PM	laptop	kernel	[   17.204000] intel8x0_measure_ac97_clock: measured 55257 usecs

08/13/2007 10:18:59 PM	laptop	kernel	[   17.240000] NET: Registered protocol family 17

08/13/2007 10:18:59 PM	laptop	kernel	[   17.308000] fuse init (API version 7.8)

08/13/2007 10:18:59 PM	laptop	kernel	[   17.336000] lp0: using parport0 (interrupt-driven).

08/13/2007 10:18:59 PM	laptop	kernel	[   17.404000] ACPI: PCI Interrupt 0000:00:1f.3[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:18:59 PM	laptop	kernel	[   17.512000] Adding 2441840k swap on /dev/disk/by-uuid/f4d24f1c-a9d1-4889-88e5-bcbee8f6f6fb.  Priority:-1 extents:1 across:2441840k

08/13/2007 10:18:59 PM	laptop	kernel	[   17.688000] EXT3 FS on sda1, internal journal

08/13/2007 10:18:59 PM	laptop	kernel	[   17.888000] kjournald starting.  Commit interval 5 seconds

08/13/2007 10:18:59 PM	laptop	kernel	[   17.896000] EXT3-fs: mounted filesystem with ordered data mode.

08/13/2007 10:18:59 PM	laptop	kernel	[   17.896000] EXT3 FS on sda3, internal journal

08/13/2007 10:18:59 PM	laptop	kernel	[   18.528000] ACPI: Battery Slot [BAT1] (battery present)

08/13/2007 10:18:59 PM	laptop	kernel	[   18.568000] ACPI: Power Button (FF) [PWRF]

08/13/2007 10:18:59 PM	laptop	kernel	[   18.568000] input: Power Button (FF) as /class/input/input4

08/13/2007 10:18:59 PM	laptop	kernel	[   18.604000] input: Lid Switch as /class/input/input5

08/13/2007 10:18:59 PM	laptop	kernel	[   18.608000] ACPI: Lid Switch [LID]

08/13/2007 10:18:59 PM	laptop	kernel	[   18.636000] input: Power Button (CM) as /class/input/input6

08/13/2007 10:18:59 PM	laptop	kernel	[   18.640000] ACPI: Power Button (CM) [PWRB]

08/13/2007 10:18:59 PM	laptop	kernel	[   18.720000] No dock devices found.

08/13/2007 10:18:59 PM	laptop	kernel	[   18.752000] Using specific hotkey driver

08/13/2007 10:18:59 PM	laptop	kernel	[   18.776000] ACPI: AC Adapter [ACAD] (off-line)

08/13/2007 10:18:59 PM	laptop	kernel	[   18.816000] pcc_acpi: loading...

08/13/2007 10:18:59 PM	laptop	kernel	[    3.264000] Time: acpi_pm clocksource has been installed.

08/13/2007 10:18:59 PM	laptop	kernel	[    3.312000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:18:59 PM	laptop	kernel	[    3.312000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10

08/13/2007 10:18:59 PM	laptop	kernel	[    3.312000] ehci_hcd 0000:00:1d.7: debug port 1

08/13/2007 10:18:59 PM	laptop	kernel	[    3.312000] ehci_hcd 0000:00:1d.7: EHCI Host Controller

08/13/2007 10:18:59 PM	laptop	kernel	[    3.312000] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xf4000000

08/13/2007 10:18:59 PM	laptop	kernel	[    3.312000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4

08/13/2007 10:18:59 PM	laptop	kernel	[    3.316000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004

08/13/2007 10:18:59 PM	laptop	kernel	[    3.316000] hub 4-0:1.0: 6 ports detected

08/13/2007 10:18:59 PM	laptop	kernel	[    3.316000] hub 4-0:1.0: USB hub found

08/13/2007 10:18:59 PM	laptop	kernel	[    3.316000] usb usb4: configuration #1 chosen from 1 choice

08/13/2007 10:18:59 PM	laptop	kernel	[    3.424000] SCSI subsystem initialized

08/13/2007 10:18:59 PM	laptop	kernel	[    3.432000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:18:59 PM	laptop	kernel	[    3.432000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011100 irq 14

08/13/2007 10:18:59 PM	laptop	kernel	[    3.432000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011108 irq 15

08/13/2007 10:18:59 PM	laptop	kernel	[    3.432000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)

08/13/2007 10:18:59 PM	laptop	kernel	[    3.432000] scsi0 : ata_piix

08/13/2007 10:18:59 PM	laptop	kernel	[    3.596000] ata1.00: 117210240 sectors, multi 16: LBA48 

08/13/2007 10:18:59 PM	laptop	kernel	[    3.596000] ata1.00: ATA-6: HTE726060M9AT00, MH4OA6AA, max UDMA/100

08/13/2007 10:18:59 PM	laptop	kernel	[    3.596000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240

08/13/2007 10:18:59 PM	laptop	kernel	[    3.604000] ata1.00: ata_hpa_resize 1: sectors = 117210240, hpa_sectors = 117210240

08/13/2007 10:18:59 PM	laptop	kernel	[    3.604000] ata1.00: configured for UDMA/100

08/13/2007 10:18:59 PM	laptop	kernel	[    3.604000] scsi1 : ata_piix

08/13/2007 10:18:59 PM	laptop	kernel	[    3.948000] ata2.00: ATAPI, max UDMA/33

08/13/2007 10:18:59 PM	laptop	kernel	[    4.136000] ata2.00: configured for UDMA/33

08/13/2007 10:18:59 PM	laptop	kernel	[    4.136000] scsi 0:0:0:0: Direct-Access     ATA      HTE726060M9AT00  MH4O PQ: 0 ANSI: 5

08/13/2007 10:18:59 PM	laptop	kernel	[    4.140000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:18:59 PM	laptop	kernel	[    4.140000] scsi 1:0:0:0: CD-ROM            TOSHIBA  ODD-DVD SD-R6372 1030 PQ: 0 ANSI: 5

08/13/2007 10:18:59 PM	laptop	kernel	[    4.192000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[d0010800-d0010fff]  Max Packet=[2048]  IR/IT contexts=[4/4]

08/13/2007 10:18:59 PM	laptop	kernel	[    4.200000] 8139cp 0000:02:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip

08/13/2007 10:18:59 PM	laptop	kernel	[    4.200000] 8139cp 0000:02:01.0: Try the "8139too" driver instead.

08/13/2007 10:18:59 PM	laptop	kernel	[    4.200000] 8139too Fast Ethernet driver 0.9.28

08/13/2007 10:18:59 PM	laptop	kernel	[    4.200000] ACPI: PCI Interrupt 0000:02:01.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:18:59 PM	laptop	kernel	[    4.200000] eth0: RealTek RTL8139 at 0xf88a2000, 00:02:3f:09:99:a3, IRQ 10

08/13/2007 10:18:59 PM	laptop	kernel	[    4.212000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)

08/13/2007 10:18:59 PM	laptop	kernel	[    4.212000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)

08/13/2007 10:18:59 PM	laptop	kernel	[    4.212000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

08/13/2007 10:18:59 PM	laptop	kernel	[    4.212000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA

08/13/2007 10:18:59 PM	laptop	kernel	[    4.212000]  sda: sda1 sda2 < sda5 > sda3 sda4

08/13/2007 10:18:59 PM	laptop	kernel	[    4.212000] sda: Write Protect is off

08/13/2007 10:18:59 PM	laptop	kernel	[    4.212000] sda: Write Protect is off

08/13/2007 10:18:59 PM	laptop	kernel	[    4.244000] sd 0:0:0:0: Attached scsi disk sda

08/13/2007 10:18:59 PM	laptop	kernel	[    4.248000] scsi 1:0:0:0: Attached scsi generic sg1 type 5

08/13/2007 10:18:59 PM	laptop	kernel	[    4.248000] sd 0:0:0:0: Attached scsi generic sg0 type 0

08/13/2007 10:18:59 PM	laptop	kernel	[    4.260000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray

08/13/2007 10:18:59 PM	laptop	kernel	[    4.260000] Uniform CD-ROM driver Revision: 3.20

08/13/2007 10:18:59 PM	laptop	kernel	[    4.476000] Attempting manual resume

08/13/2007 10:18:59 PM	laptop	kernel	[    4.512000] EXT3-fs: mounted filesystem with ordered data mode.

08/13/2007 10:18:59 PM	laptop	kernel	[    4.512000] kjournald starting.  Commit interval 5 seconds

08/13/2007 10:18:59 PM	laptop	kernel	[    7.837249] Built 1 zonelists.  Total pages: 260081

08/13/2007 10:18:59 PM	laptop	kernel	[    7.837254] Kernel command line: root=UUID=f2db0809-08f4-4d50-bf89-177269e9374a ro quiet splash

08/13/2007 10:18:59 PM	laptop	kernel	[    7.837397] Local APIC disabled by BIOS -- you can enable it with "lapic"

08/13/2007 10:18:59 PM	laptop	kernel	[    7.837409] Enabling fast FPU save and restore... done.

08/13/2007 10:18:59 PM	laptop	kernel	[    7.837412] Enabling unmasked SIMD FPU exception support... done.

08/13/2007 10:18:59 PM	laptop	kernel	[    7.837423] Initializing CPU#0

08/13/2007 10:18:59 PM	laptop	kernel	[    7.837497] PID hash table entries: 4096 (order: 12, 16384 bytes)

08/13/2007 10:18:59 PM	laptop	kernel	[    7.838690] Console: colour VGA+ 80x25

08/13/2007 10:18:59 PM	laptop	kernel	[    7.839234] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)

08/13/2007 10:18:59 PM	laptop	kernel	[    7.839774] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)

08/13/2007 10:18:59 PM	laptop	kernel	[    7.871423] Memory: 1028308k/1048512k available (1992k kernel code, 19468k reserved, 900k data, 328k init, 131008k highmem)

08/13/2007 10:18:59 PM	laptop	kernel	[    7.871432] virtual kernel memory layout:

08/13/2007 10:18:59 PM	laptop	kernel	[    7.871433]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)

08/13/2007 10:18:59 PM	laptop	kernel	[    7.871434]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)

08/13/2007 10:18:59 PM	laptop	kernel	[    7.871435]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)

08/13/2007 10:18:59 PM	laptop	kernel	[    7.871436]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)

08/13/2007 10:18:59 PM	laptop	kernel	[    7.871437]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)

08/13/2007 10:18:59 PM	laptop	kernel	[    7.871438]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)

08/13/2007 10:18:59 PM	laptop	kernel	[    7.871440]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)

08/13/2007 10:18:59 PM	laptop	kernel	[    7.871443] Checking if this processor honours the WP bit even in supervisor mode... Ok.

08/13/2007 10:18:59 PM	laptop	kernel	[    7.949364] Calibrating delay using timer specific routine.. 3989.75 BogoMIPS (lpj=7979504)

08/13/2007 10:18:59 PM	laptop	kernel	[    7.949400] Security Framework v1.0.0 initialized

08/13/2007 10:18:59 PM	laptop	kernel	[    7.949407] SELinux:  Disabled at boot.

08/13/2007 10:18:59 PM	laptop	kernel	[    7.949421] Mount-cache hash table entries: 512

08/13/2007 10:18:59 PM	laptop	kernel	[    7.949552] CPU: L1 I cache: 32K, L1 D cache: 32K

08/13/2007 10:18:59 PM	laptop	kernel	[    7.949554] CPU: L2 cache: 2048K

08/13/2007 10:18:59 PM	laptop	kernel	[    7.949565] Compat vDSO mapped to ffffe000.

08/13/2007 10:18:59 PM	laptop	kernel	[    7.949569] Remapping vsyscall page to ffffe000

08/13/2007 10:18:59 PM	laptop	kernel	[    7.949578] Checking 'hlt' instruction... OK.

08/13/2007 10:18:59 PM	laptop	kernel	[    7.965429] SMP alternatives: switching to UP code

08/13/2007 10:18:59 PM	laptop	kernel	[    7.965621] Freeing SMP alternatives: 11k freed

08/13/2007 10:18:59 PM	laptop	kernel	[    7.965781] Early unpacking initramfs... done

08/13/2007 10:18:59 PM	laptop	kernel	[    8.248744] ACPI: Core revision 20060707

08/13/2007 10:18:59 PM	laptop	kernel	[    8.248848] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.

08/13/2007 10:18:59 PM	laptop	kernel	[    8.250414] ACPI: setting ELCR to 0200 (from 0c00)

08/13/2007 10:18:59 PM	laptop	kernel	[    8.256719] CPU0: Intel(R) Pentium(R) M processor 2.00GHz stepping 06

08/13/2007 10:18:59 PM	laptop	kernel	[    8.256724] SMP motherboard not detected.

08/13/2007 10:18:59 PM	laptop	kernel	[    8.256726] Local APIC not detected. Using dummy APIC emulation.

08/13/2007 10:18:59 PM	laptop	kernel	[    8.256757] Brought up 1 CPUs

08/13/2007 10:18:59 PM	laptop	kernel	[    8.256963] Booting paravirtualized kernel on bare hardware

08/13/2007 10:18:59 PM	laptop	kernel	[    8.257038] Time:  3:18:40  Date: 07/14/107

08/13/2007 10:18:59 PM	laptop	kernel	[    8.257063] NET: Registered protocol family 16

08/13/2007 10:18:59 PM	laptop	kernel	[    8.257136] EISA bus registered

08/13/2007 10:18:59 PM	laptop	kernel	[    8.257140] ACPI: bus type pci registered

08/13/2007 10:18:59 PM	laptop	kernel	[    8.257172] PCI: PCI BIOS revision 2.10 entry at 0xe97a4, last bus=2

08/13/2007 10:18:59 PM	laptop	kernel	[    8.257174] PCI: Using configuration type 1

08/13/2007 10:18:59 PM	laptop	kernel	[    8.257175] Setting up standard PCI resources

08/13/2007 10:18:59 PM	laptop	kernel	[    8.259298] ACPI: Interpreter enabled

08/13/2007 10:18:59 PM	laptop	kernel	[    8.259300] ACPI: Using PIC for interrupt routing

08/13/2007 10:18:59 PM	laptop	kernel	[    8.259632] ACPI: PCI Root Bridge [PCI0] (0000:00)

08/13/2007 10:18:59 PM	laptop	kernel	[    8.260421] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO

08/13/2007 10:18:59 PM	laptop	kernel	[    8.260425] PCI quirk: region 1300-133f claimed by ICH4 GPIO

08/13/2007 10:18:59 PM	laptop	kernel	[    8.260883] PCI: Transparent bridge - 0000:00:1e.0

08/13/2007 10:18:59 PM	laptop	kernel	[    8.260929] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')

08/13/2007 10:18:59 PM	laptop	kernel	[    8.260932] Please report the result to linux-kernel to fix this permanently

08/13/2007 10:18:59 PM	laptop	kernel	[    8.267300] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 *10)

08/13/2007 10:18:59 PM	laptop	kernel	[    8.267469] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 10) *11

08/13/2007 10:18:59 PM	laptop	kernel	[    8.267636] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 10) *11

08/13/2007 10:18:59 PM	laptop	kernel	[    8.267805] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 10) *11

08/13/2007 10:18:59 PM	laptop	kernel	[    8.267981] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.

08/13/2007 10:18:59 PM	laptop	kernel	[    8.268154] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.

08/13/2007 10:18:59 PM	laptop	kernel	[    8.268328] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.

08/13/2007 10:18:59 PM	laptop	kernel	[    8.268503] ACPI: PCI Interrupt Link [LNKH] (IRQs 5 10) *11

08/13/2007 10:18:59 PM	laptop	kernel	[    8.310012] Linux Plug and Play Support v0.97 (c) Adam Belay

08/13/2007 10:18:59 PM	laptop	kernel	[    8.310018] pnp: PnP ACPI init

08/13/2007 10:18:59 PM	laptop	kernel	[    8.333130] pnp: PnP ACPI: found 11 devices

08/13/2007 10:18:59 PM	laptop	kernel	[    8.333133] PnPBIOS: Disabled by ACPI PNP

08/13/2007 10:18:59 PM	laptop	kernel	[    8.333168] PCI: Using ACPI for IRQ routing

08/13/2007 10:18:59 PM	laptop	kernel	[    8.333171] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report

08/13/2007 10:18:59 PM	laptop	kernel	[    8.333196] PCI: Cannot allocate resource region 0 of device 0000:02:03.0

08/13/2007 10:18:59 PM	laptop	kernel	[    8.335847] NET: Registered protocol family 8

08/13/2007 10:18:59 PM	laptop	kernel	[    8.335849] NET: Registered protocol family 20

08/13/2007 10:18:59 PM	laptop	kernel	[    8.336185] PCI: Bridge: 0000:00:01.0

08/13/2007 10:18:59 PM	laptop	kernel	[    8.336187]   IO window: c000-dfff

08/13/2007 10:18:59 PM	laptop	kernel	[    8.336191]   MEM window: e0000000-efffffff

08/13/2007 10:18:59 PM	laptop	kernel	[    8.336194]   PREFETCH window: a0000000-afffffff

08/13/2007 10:18:59 PM	laptop	kernel	[    8.336201] PCI: Bus 3, cardbus bridge: 0000:02:03.0

08/13/2007 10:18:59 PM	laptop	kernel	[    8.336203]   IO window: 0000a400-0000a4ff

08/13/2007 10:18:59 PM	laptop	kernel	[    8.336207]   IO window: 0000a800-0000a8ff

08/13/2007 10:18:59 PM	laptop	kernel	[    8.336210]   PREFETCH window: 90000000-93ffffff

08/13/2007 10:18:59 PM	laptop	kernel	[    8.336214]   MEM window: d4000000-d7ffffff

08/13/2007 10:18:59 PM	laptop	kernel	[    8.336217] PCI: Bridge: 0000:00:1e.0

08/13/2007 10:18:59 PM	laptop	kernel	[    8.336220]   IO window: a000-bfff

08/13/2007 10:18:59 PM	laptop	kernel	[    8.336224]   MEM window: d0000000-dfffffff

08/13/2007 10:18:59 PM	laptop	kernel	[    8.336228]   PREFETCH window: 90000000-9fffffff

08/13/2007 10:18:59 PM	laptop	kernel	[    8.336380] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10

08/13/2007 10:18:59 PM	laptop	kernel	[    8.336386] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:18:59 PM	laptop	kernel	[    8.336406] NET: Registered protocol family 2

08/13/2007 10:18:59 PM	laptop	kernel	[    8.368896] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)

08/13/2007 10:18:59 PM	laptop	kernel	[    8.369013] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)

08/13/2007 10:18:59 PM	laptop	kernel	[    8.369961] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)

08/13/2007 10:18:59 PM	laptop	kernel	[    8.370625] TCP: Hash tables configured (established 131072 bind 65536)

08/13/2007 10:18:59 PM	laptop	kernel	[    8.370629] TCP reno registered

08/13/2007 10:18:59 PM	laptop	kernel	[    8.380985] checking if image is initramfs... it is

08/13/2007 10:18:59 PM	laptop	kernel	[    8.933803] Freeing initrd memory: 6772k freed

08/13/2007 10:18:59 PM	laptop	kernel	[    8.934059] Simple Boot Flag at 0x37 set to 0x1

08/13/2007 10:18:59 PM	laptop	kernel	[    8.934244] audit: initializing netlink socket (disabled)

08/13/2007 10:18:59 PM	laptop	kernel	[    8.934260] audit(1187061521.280:1): initialized

08/13/2007 10:18:59 PM	laptop	kernel	[    8.934333] highmem bounce pool size: 64 pages

08/13/2007 10:18:59 PM	laptop	kernel	[    8.934394] VFS: Disk quotas dquot_6.5.1

08/13/2007 10:18:59 PM	laptop	kernel	[    8.934414] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)

08/13/2007 10:18:59 PM	laptop	kernel	[    8.934467] io scheduler noop registered

08/13/2007 10:18:59 PM	laptop	kernel	[    8.934470] io scheduler anticipatory registered

08/13/2007 10:18:59 PM	laptop	kernel	[    8.934472] io scheduler deadline registered

08/13/2007 10:18:59 PM	laptop	kernel	[    8.934482] io scheduler cfq registered (default)

08/13/2007 10:18:59 PM	laptop	kernel	[    8.934774] isapnp: Scanning for PnP cards...

08/13/2007 10:18:59 PM	laptop	kernel	[    9.288154] isapnp: No Plug & Play device found

08/13/2007 10:18:59 PM	laptop	kernel	[    9.309845] Real Time Clock Driver v1.12ac

08/13/2007 10:18:59 PM	laptop	kernel	[    9.309903] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled

08/13/2007 10:18:59 PM	laptop	kernel	[    9.310102] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A

08/13/2007 10:18:59 PM	laptop	kernel	[    9.310814] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10

08/13/2007 10:18:59 PM	laptop	kernel	[    9.310817] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:18:59 PM	laptop	kernel	[    9.310826] ACPI: PCI interrupt for device 0000:00:1f.6 disabled

08/13/2007 10:18:59 PM	laptop	kernel	[    9.310899] mice: PS/2 mouse device common for all mice

08/13/2007 10:18:59 PM	laptop	kernel	[    9.311389] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize

08/13/2007 10:18:59 PM	laptop	kernel	[    9.311590] input: Macintosh mouse button emulation as /class/input/input0

08/13/2007 10:18:59 PM	laptop	kernel	[    9.311620] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2

08/13/2007 10:18:59 PM	laptop	kernel	[    9.311623] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx

08/13/2007 10:18:59 PM	laptop	kernel	[    9.311882] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12

08/13/2007 10:18:59 PM	laptop	kernel	[    9.312146] i8042.c: Detected active multiplexing controller, rev 1.1.

08/13/2007 10:18:59 PM	laptop	kernel	[    9.312186] serio: i8042 KBD port at 0x60,0x64 irq 1

08/13/2007 10:18:59 PM	laptop	kernel	[    9.312190] serio: i8042 AUX0 port at 0x60,0x64 irq 12

08/13/2007 10:18:59 PM	laptop	kernel	[    9.312192] serio: i8042 AUX1 port at 0x60,0x64 irq 12

08/13/2007 10:18:59 PM	laptop	kernel	[    9.312194] serio: i8042 AUX2 port at 0x60,0x64 irq 12

08/13/2007 10:18:59 PM	laptop	kernel	[    9.312196] serio: i8042 AUX3 port at 0x60,0x64 irq 12

08/13/2007 10:18:59 PM	laptop	kernel	[    9.312293] EISA: Probing bus 0 at eisa.0

08/13/2007 10:18:59 PM	laptop	kernel	[    9.312300] Cannot allocate resource for EISA slot 1

08/13/2007 10:18:59 PM	laptop	kernel	[    9.312327] EISA: Detected 0 cards.

08/13/2007 10:18:59 PM	laptop	kernel	[    9.342458] TCP cubic registered

08/13/2007 10:18:59 PM	laptop	kernel	[    9.342471] NET: Registered protocol family 1

08/13/2007 10:18:59 PM	laptop	kernel	[    9.342491] Using IPI No-Shortcut mode

08/13/2007 10:18:59 PM	laptop	kernel	[    9.342545] ACPI: (supports S0 S1 S3 S4 S5)

08/13/2007 10:18:59 PM	laptop	kernel	[    9.342583]   Magic number: 3:649:310

08/13/2007 10:18:59 PM	laptop	kernel	[    9.342598]   hash matches device ttyxd

08/13/2007 10:18:59 PM	laptop	kernel	[    9.342697]   hash matches device tty39

08/13/2007 10:18:59 PM	laptop	kernel	[    9.343004] Freeing unused kernel memory: 328k freed

08/13/2007 10:18:59 PM	laptop	kernel	[    9.343650] Time: tsc clocksource has been installed.

08/13/2007 10:18:59 PM	laptop	kernel	[    9.344597] input: AT Translated Set 2 keyboard as /class/input/input1

08/13/2007 10:18:59 PM	laptop	kernel	Inspecting /boot/System.map-2.6.20-16-generic

08/13/2007 10:18:59 PM	laptop	kernel	Loaded 24977 symbols from /boot/System.map-2.6.20-16-generic.

08/13/2007 10:18:59 PM	laptop	kernel	No module symbols loaded - kernel modules not enabled. 

08/13/2007 10:18:59 PM	laptop	kernel	Symbols match kernel version 2.6.20.

08/13/2007 10:18:59 PM	laptop	syslogd 1.4.1#20ubuntu4	restart.

08/13/2007 10:19:01 PM	laptop	dhcdbd	Started up.

08/13/2007 10:19:02 PM	laptop	hpiod	1.7.3 accepting connections at 2208... 

08/13/2007 10:19:02 PM	laptop	kernel	[   21.648000] eth0: link down

08/13/2007 10:19:02 PM	laptop	kernel	[   21.700000] ppdev: user-space parallel port driver

08/13/2007 10:19:03 PM	laptop	kernel	[   22.664000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)

08/13/2007 10:19:03 PM	laptop	kernel	[   22.664000] apm: overridden by ACPI.

08/13/2007 10:19:04 PM	laptop	kernel	[   23.664000] Bluetooth: Core ver 2.11

08/13/2007 10:19:04 PM	laptop	kernel	[   23.664000] Bluetooth: HCI device and connection manager initialized

08/13/2007 10:19:04 PM	laptop	kernel	[   23.664000] Bluetooth: HCI socket layer initialized

08/13/2007 10:19:04 PM	laptop	kernel	[   23.664000] NET: Registered protocol family 31

08/13/2007 10:19:04 PM	laptop	kernel	[   23.724000] Bluetooth: L2CAP socket layer initialized

08/13/2007 10:19:04 PM	laptop	kernel	[   23.724000] Bluetooth: L2CAP ver 2.8

08/13/2007 10:19:04 PM	laptop	kernel	[   23.864000] Bluetooth: RFCOMM socket layer initialized

08/13/2007 10:19:04 PM	laptop	kernel	[   23.864000] Bluetooth: RFCOMM TTY layer initialized

08/13/2007 10:19:04 PM	laptop	kernel	[   23.864000] Bluetooth: RFCOMM ver 1.8

08/13/2007 10:19:05 PM	laptop	kernel	[   25.168000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.

08/13/2007 10:19:05 PM	laptop	kernel	[   25.168000] [fglrx] module loaded - fglrx 8.34.8 [Feb 20 2007] on minor 0

08/13/2007 10:19:05 PM	laptop	kernel	[   25.196000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10

08/13/2007 10:19:08 PM	laptop	kernel	[   27.532000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.

08/13/2007 10:19:08 PM	laptop	kernel	[   27.532000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode

08/13/2007 10:19:08 PM	laptop	kernel	[   27.532000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode

08/13/2007 10:19:08 PM	laptop	kernel	[   27.532000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)

08/13/2007 10:19:08 PM	laptop	kernel	[   27.532000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)

08/13/2007 10:19:08 PM	laptop	kernel	[   27.532000] [fglrx] Have to use kernel AGP support to avoid conflicts.

08/13/2007 10:19:08 PM	laptop	kernel	[   27.532000] [fglrx] Internal AGP support requested, but kernel AGP support active.

08/13/2007 10:19:08 PM	laptop	kernel	[   27.540000] [fglrx] free       GART = 51113984

08/13/2007 10:19:08 PM	laptop	kernel	[   27.540000] [fglrx] free       Inv  = 0

08/13/2007 10:19:08 PM	laptop	kernel	[   27.540000] [fglrx] free       LFB  = 96432128

08/13/2007 10:19:08 PM	laptop	kernel	[   27.540000] [fglrx] max single GART = 51113984

08/13/2007 10:19:08 PM	laptop	kernel	[   27.540000] [fglrx] max single Inv  = 0

08/13/2007 10:19:08 PM	laptop	kernel	[   27.540000] [fglrx] max single LFB  = 96432128

08/13/2007 10:19:08 PM	laptop	kernel	[   27.540000] [fglrx] total      GART = 67108864

08/13/2007 10:19:08 PM	laptop	kernel	[   27.540000] [fglrx] total      Inv  = 0

08/13/2007 10:19:08 PM	laptop	kernel	[   27.540000] [fglrx] total      LFB  = 134217728

08/13/2007 10:19:08 PM	laptop	kernel	[   27.540000] [fglrx] total      TIM  = 0

08/13/2007 10:19:43 PM	laptop	kernel	[   63.376000] ADDRCONF(NETDEV_UP): eth0: link is not ready

08/13/2007 10:19:43 PM	laptop	kernel	[   63.376000] lo: Disabled Privacy Extensions

08/13/2007 10:19:43 PM	laptop	kernel	[   63.376000] NET: Registered protocol family 10

08/13/2007 10:39:01 PM	laptop	none	-- MARK --

08/13/2007 10:41:16 PM	laptop	kernel	[ 1355.876000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.

08/13/2007 10:41:16 PM	laptop	kernel	[ 1355.876000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode

08/13/2007 10:41:16 PM	laptop	kernel	[ 1355.876000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode

08/13/2007 10:41:16 PM	laptop	kernel	[ 1355.876000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)

08/13/2007 10:41:16 PM	laptop	kernel	[ 1355.876000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)

08/13/2007 10:41:16 PM	laptop	kernel	[ 1355.876000] [fglrx] Have to use kernel AGP support to avoid conflicts.

08/13/2007 10:41:16 PM	laptop	kernel	[ 1355.876000] [fglrx] Internal AGP support requested, but kernel AGP support active.

08/13/2007 10:41:16 PM	laptop	kernel	[ 1355.884000] [fglrx] free       GART = 51113984

08/13/2007 10:41:16 PM	laptop	kernel	[ 1355.884000] [fglrx] free       Inv  = 0

08/13/2007 10:41:16 PM	laptop	kernel	[ 1355.884000] [fglrx] free       LFB  = 96432128

08/13/2007 10:41:16 PM	laptop	kernel	[ 1355.884000] [fglrx] max single GART = 51113984

08/13/2007 10:41:16 PM	laptop	kernel	[ 1355.884000] [fglrx] max single Inv  = 0

08/13/2007 10:41:16 PM	laptop	kernel	[ 1355.884000] [fglrx] max single LFB  = 96432128

08/13/2007 10:41:16 PM	laptop	kernel	[ 1355.884000] [fglrx] total      GART = 67108864

08/13/2007 10:41:16 PM	laptop	kernel	[ 1355.884000] [fglrx] total      Inv  = 0

08/13/2007 10:41:16 PM	laptop	kernel	[ 1355.884000] [fglrx] total      LFB  = 134217728

08/13/2007 10:41:16 PM	laptop	kernel	[ 1355.884000] [fglrx] total      TIM  = 0

08/13/2007 10:41:25 PM	laptop	kernel	[ 1364.716000] ip_tables: (C) 2000-2006 Netfilter Core Team

08/13/2007 10:41:25 PM	laptop	kernel	[ 1364.848000] Netfilter messages via NETLINK v0.30.

08/13/2007 10:41:25 PM	laptop	kernel	[ 1364.864000] nf_conntrack version 0.5.0 (8191 buckets, 65528 max)

08/13/2007 10:41:27 PM	laptop	none	exiting on signal 15

08/13/2007 10:56:38 PM	laptop	kernel	[  254.796000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready

08/13/2007 10:56:38 PM	laptop	kernel	[  254.872000] ADDRCONF(NETDEV_UP): ath0: link is not ready

08/13/2007 10:56:39 PM	laptop	kernel	[  255.796000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready

08/13/2007 10:56:40 PM	laptop	dhcdbd	dhco_input_option: Value -1 cannot be converted to type L 

08/13/2007 10:56:40 PM	laptop	dhcdbd	dhco_parse_option_settings: bad option setting: new_dhcp_lease_time = -1 

08/13/2007 10:56:40 PM	laptop	dhcdbd	message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.host_name

08/13/2007 10:56:40 PM	laptop	dhcdbd	message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.nis_domain

08/13/2007 10:56:40 PM	laptop	dhcdbd	message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.nis_servers


```

---

### Post by lookformeb on 2007-08-16
I did some reading relating to my Laptop Model (CL56-15) and found I needed the Acer HotKey Driver to allow (k)ubuntu to use the switch.

To do this, I did the following:
---------------------------------------------------------------------
```
$ wget http://www.cakey.de/acerhk/archives/acerhk-0.5.34.tar.bz2
$ tar xvjf acerhk-0.5.34.tar.bz2
$ cd acerhk-0.5.34
$ nano acerhk.c
``` and change the following line from: ```
#include <linux/config.h>
``` to: ```
#include <linux/autoconf.h>
```
---------------------------------------------------------------------
Then:
```
$ make
$ sudo make install
$ sudo modprobe acerhk
```

(If you have problems with the make command, read INSTALL (step 3) in the acerhk-0.5.34 directory.)
---------------------------------------------------------------------
Then add acerhk to */etc/modules* :
```
$ sudo -s
$ echo "acerhk" >> /etc/modules
$ exit
```
---------------------------------------------------------------------
Edit */etc/network/if-pre-up.d/wireless-tools* to enable the wireless card on boot:
```
$ sudo nano -w /etc/network/if-pre-up.d/wireless-tools
``` and add the following directly after the *#!/bin/sh* line```
echo 1 > /proc/driver/acerhk/wirelessled
```
---------------------------------------------------------------------

I have been able to confirm that this allows me to actually use the switch to turn on/off the Wireless device and the LED.
**I will update this thread in a few weeks to confirm that this indefinitely solved my issue.**

If you have any problems, check these sources:
[http://folk.uio.no/krisvh/linux/cl56.html#wireless]("http://folk.uio.no/krisvh/linux/cl56.html#wireless")
[http://ubuntuforums.org/showthread.php?t=517228&page=3]("http://ubuntuforums.org/showthread.php?t=517228&page=3")
[Acer HotKey Drivers]("http://www.cakey.de/acerhk/")

---

