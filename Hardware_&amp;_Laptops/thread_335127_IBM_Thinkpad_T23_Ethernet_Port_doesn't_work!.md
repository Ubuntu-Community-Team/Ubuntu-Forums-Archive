---
title: "IBM Thinkpad T23 Ethernet Port doesn't work!"
date: 2007-01-09
forum: Hardware &amp; Laptops
---

### Post by fastluck on 2007-01-09
I bought an IBM T23 Thinkpad off of EBay.  I can't get the network to work.  When I restart the network, this happens:

```
# /etc/init.d/networking restart  * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:d0:59:84:43:d4
Sending on   LPF/eth0/00:d0:59:84:43:d4
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFFLAGS: Resource temporarily unavailable
SIOCSIFFLAGS: Resource temporarily unavailable
Listening on LPF/eth0/00:d0:59:84:43:d4
Sending on   LPF/eth0/00:d0:59:84:43:d4
Sending on   Socket/fallback
receive_packet failed on eth0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
send_packet: Network is down

```

Here's my dmesg output:
```
[4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[4294667.296000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000001ff60000 (usable)
[4294667.296000]  BIOS-e820: 000000001ff60000 - 000000001ff7a000 (ACPI data)
[4294667.296000]  BIOS-e820: 000000001ff7a000 - 000000001ff7c000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 000000001ff7c000 - 0000000020000000 (reserved)
[4294667.296000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 511MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 130912
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 126816 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI present.
[4294667.296000] ACPI: RSDP (v002 IBM                                   ) @ 0x000f73b0
[4294667.296000] ACPI: XSDT (v001 IBM    TP-1A    0x00001081  LTP 0x00000000) @ 0x1ff6fd95
[4294667.296000] ACPI: FADT (v001 IBM    TP-1A    0x00001081 IBM  0x00000001) @ 0x1ff6fdd9
[4294667.296000] ACPI: SSDT (v001 IBM    TP-1A    0x00001081 MSFT 0x0100000d) @ 0x1ff6fe8d
[4294667.296000] ACPI: ECDT (v001 IBM    TP-1A    0x00001081 IBM  0x00000001) @ 0x1ff79f87
[4294667.296000] ACPI: BOOT (v001 IBM    TP-1A    0x00001081  LTP 0x00000001) @ 0x1ff79fd8
[4294667.296000] ACPI: DSDT (v001 IBM    TP-1A    0x00001081 MSFT 0x0100000d) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x1008
[4294667.296000] Allocating PCI resources starting at 30000000 (gap: 20000000:df800000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash
[4294667.296000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[4294667.296000] mapped APIC to ffffd000 (01401000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[4294667.296000] Detected 1132.472 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294667.453000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[4294667.455000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294667.485000] Memory: 508084k/523648k available (1976k kernel code, 15024k reserved, 606k data, 288k init, 0k highmem)
[4294667.485000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[4294667.545000] Calibrating delay using timer specific routine.. 2265.90 BogoMIPS (lpj=1132951)
[4294667.545000] Security Framework v1.0.0 initialized
[4294667.545000] SELinux:  Disabled at boot.
[4294667.545000] Mount-cache hash table entries: 512
[4294667.545000] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[4294667.545000] CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[4294667.545000] CPU: L1 I cache: 16K, L1 D cache: 16K
[4294667.545000] CPU: L2 cache: 512K
[4294667.545000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[4294667.545000] mtrr: v2.0 (20020519)
[4294667.545000] CPU: Intel(R) Pentium(R) III Mobile CPU      1133MHz stepping 01
[4294667.545000] Enabling fast FPU save and restore... done.
[4294667.545000] Enabling unmasked SIMD FPU exception support... done.
[4294667.545000] Checking 'hlt' instruction... OK.
[4294667.549000] checking if image is initramfs... it is
[4294668.895000] Freeing initrd memory: 6837k freed
[4294668.915000] ACPI: Looking for DSDT ... not found!
[4294668.922000] ACPI: setting ELCR to 0200 (from 0800)
[4294668.943000] NET: Registered protocol family 16
[4294668.944000] EISA bus registered
[4294668.944000] ACPI: bus type pci registered
[4294668.944000] PCI: PCI BIOS revision 2.10 entry at 0xfd8fe, last bus=8
[4294668.944000] PCI: Using configuration type 1
[4294668.944000] ACPI: Subsystem revision 20051216
[4294668.947000] ACPI: Found ECDT
[4294668.947000] ACPI: Could not use ECDT
[4294668.954000]     ACPI-0284: *** Error: Region EmbeddedControl(3) has no handler
[4294668.954000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.PCI0.LPC_.FDC_._INI] (Node dff41ac0), AE_NOT_EXIST
[4294668.954000]     ACPI-0284: *** Error: Region EmbeddedControl(3) has no handler
[4294668.954000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.PCI0.LPC_.EC__._INI] (Node dff464a0), AE_NOT_EXIST
[4294668.956000] ACPI: Interpreter enabled
[4294668.956000] ACPI: Using PIC for interrupt routing
[4294668.957000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11)
[4294668.958000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11)
[4294668.959000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11)
[4294668.960000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 *11)
[4294668.961000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11)
[4294668.962000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[4294668.962000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[4294668.963000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11) *0, disabled.
[4294668.964000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294668.964000] PCI: Probing PCI hardware (bus 00)
[4294668.966000]     ACPI-0284: *** Error: Region EmbeddedControl(3) has no handler
[4294668.966000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.PCI0.LPC_.EC__.BAT0._STA] (Node dff46ae0), AE_NOT_EXIST
[4294668.966000]     ACPI-0158: *** Error: Method execution failed [\_SB_.PCI0.LPC_.EC__.BAT0._STA] (Node dff46ae0), AE_NOT_EXIST
[4294668.966000]     ACPI-0284: *** Error: Region EmbeddedControl(3) has no handler
[4294668.966000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.PCI0.LPC_.EC__.BAT1._STA] (Node dff46960), AE_NOT_EXIST
[4294668.967000]     ACPI-0158: *** Error: Method execution failed [\_SB_.PCI0.LPC_.EC__.BAT1._STA] (Node dff46960), AE_NOT_EXIST
[4294668.967000]     ACPI-0284: *** Error: Region EmbeddedControl(3) has no handler
[4294668.968000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.PCI0.LPC_.EC__.BGID] (Node dff41c00), AE_NOT_EXIST
[4294668.968000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.PCI0.LPC_.EC__.BINI] (Node dff41c20), AE_NOT_EXIST
[4294668.968000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.PCI0.LPC_.EC__.BSTA] (Node dff41c60), AE_NOT_EXIST
[4294668.968000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.PCI0.IDE0.SCND.MSTR._STA] (Node dff41b20), AE_NOT_EXIST
[4294668.968000]     ACPI-0158: *** Error: Method execution failed [\_SB_.PCI0.IDE0.SCND.MSTR._STA] (Node dff41b20), AE_NOT_EXIST
[4294668.968000]     ACPI-0284: *** Error: Region EmbeddedControl(3) has no handler
[4294668.968000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.PCI0.LPC_.EC__.BGID] (Node dff41c00), AE_NOT_EXIST
[4294668.968000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.PCI0.LPC_.EC__.BINI] (Node dff41c20), AE_NOT_EXIST
[4294668.968000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.PCI0.LPC_.EC__.BSTA] (Node dff41c60), AE_NOT_EXIST
[4294668.968000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.PCI0.USB0.URTH.UNST._STA] (Node dff41320), AE_NOT_EXIST
[4294668.968000]     ACPI-0158: *** Error: Method execution failed [\_SB_.PCI0.USB0.URTH.UNST._STA] (Node dff41320), AE_NOT_EXIST
[4294668.969000]     ACPI-0284: *** Error: Region EmbeddedControl(3) has no handler
[4294668.969000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.PCI0.LPC_.EC__.BGID] (Node dff41c00), AE_NOT_EXIST
[4294668.969000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.PCI0.LPC_.EC__.BINI] (Node dff41c20), AE_NOT_EXIST
[4294668.969000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.PCI0.LPC_.EC__.BSTA] (Node dff41c60), AE_NOT_EXIST
[4294668.969000]     ACPI-0517: *** Error: Method parse/execution failed [\_SB_.NEST._STA] (Node dff41960), AE_NOT_EXIST
[4294668.969000]     ACPI-0158: *** Error: Method execution failed [\_SB_.NEST._STA] (Node dff41960), AE_NOT_EXIST
[4294668.969000] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[4294668.969000] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[4294668.969000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[4294668.969000] Boot video device is 0000:01:00.0
[4294668.970000] PCI: Transparent bridge - 0000:00:1e.0
[4294668.970000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294668.977000] ACPI: Embedded Controller [EC] (gpe 28) interrupt mode.
[4294668.977000] ACPI: Power Resource [PUBS] (on)
[4294668.979000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[4294668.979000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[4294668.982000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294668.982000] pnp: PnP ACPI init
[4294668.989000] pnp: PnP ACPI: found 13 devices
[4294668.989000] PnPBIOS: Disabled by ACPI PNP
[4294668.989000] PCI: Using ACPI for IRQ routing
[4294668.989000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[4294668.998000] PCI: Bridge: 0000:00:01.0
[4294668.998000]   IO window: disabled.
[4294668.998000]   MEM window: c0100000-c01fffff
[4294668.998000]   PREFETCH window: e0000000-ebffffff
[4294668.998000] PCI: Bus 3, cardbus bridge: 0000:02:00.0
[4294668.998000]   IO window: 00002000-000020ff
[4294668.998000]   IO window: 00002400-000024ff
[4294668.998000]   PREFETCH window: f0000000-f1ffffff
[4294668.998000]   MEM window: c2000000-c3ffffff
[4294668.998000] PCI: Bus 7, cardbus bridge: 0000:02:00.1
[4294668.998000]   IO window: 00002800-000028ff
[4294668.998000]   IO window: 00002c00-00002cff
[4294668.998000]   PREFETCH window: f2000000-f3ffffff
[4294668.998000]   MEM window: c4000000-c5ffffff
[4294668.998000] PCI: Bridge: 0000:00:1e.0
[4294668.998000]   IO window: 2000-6fff
[4294668.998000]   MEM window: c0200000-cfffffff
[4294668.998000]   PREFETCH window: f0000000-f7ffffff
[4294668.998000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[4294668.998000] **** SET: Misaligned resource pointer: de9aff02 Type 07 Len 0
[4294668.999000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[4294668.999000] PCI: setting IRQ 11 as level-triggered
[4294668.999000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294668.999000] **** SET: Misaligned resource pointer: de9aff02 Type 07 Len 0
[4294668.999000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[4294668.999000] ACPI: PCI Interrupt 0000:02:00.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[4294669.000000] Simple Boot Flag at 0x35 set to 0x1
[4294669.000000] audit: initializing netlink socket (disabled)
[4294669.000000] audit(1168304365.999:1): initialized
[4294669.000000] VFS: Disk quotas dquot_6.5.1
[4294669.000000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294669.000000] Initializing Cryptographic API
[4294669.000000] io scheduler noop registered
[4294669.001000] io scheduler anticipatory registered
[4294669.001000] io scheduler deadline registered
[4294669.001000] io scheduler cfq registered
[4294669.001000] isapnp: Scanning for PnP cards...
[4294669.357000] isapnp: No Plug & Play device found
[4294669.381000] PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[4294669.386000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294669.387000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294669.387000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[4294669.391000] **** SET: Misaligned resource pointer: df97caa2 Type 00 Len 42
[4294669.391000] pnp: Device 00:09 activated.
[4294669.392000] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a NS16550A
[4294669.393000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[4294669.393000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294669.393000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294669.393000] mice: PS/2 mouse device common for all mice
[4294669.394000] EISA: Probing bus 0 at eisa.0
[4294669.394000] Cannot allocate resource for EISA slot 1
[4294669.394000] Cannot allocate resource for EISA slot 2
[4294669.394000] Cannot allocate resource for EISA slot 3
[4294669.394000] Cannot allocate resource for EISA slot 4
[4294669.394000] Cannot allocate resource for EISA slot 5
[4294669.394000] Cannot allocate resource for EISA slot 6
[4294669.394000] EISA: Detected 0 cards.
[4294669.394000] NET: Registered protocol family 2
[4294669.404000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294669.404000] IP route cache hash table entries: 8192 (order: 3, 32768 bytes)
[4294669.404000] TCP established hash table entries: 32768 (order: 5, 131072 bytes)
[4294669.404000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[4294669.405000] TCP: Hash tables configured (established 32768 bind 32768)
[4294669.405000] TCP reno registered
[4294669.405000] TCP bic registered
[4294669.405000] NET: Registered protocol family 1
[4294669.405000] NET: Registered protocol family 8
[4294669.405000] NET: Registered protocol family 20
[4294669.405000] Using IPI Shortcut mode
[4294669.405000] ACPI wakeup devices: 
[4294669.405000]  LID SLPB PCI0 UART PCI1 USB0 USB1 USB2 AC97 
[4294669.405000] ACPI: (supports S0 S3 S4 S5)
[4294669.405000] Freeing unused kernel memory: 288k freed
[4294669.482000] vga16fb: initializing
[4294669.482000] vga16fb: mapped to 0xc00a0000
[4294669.599000] Console: switching to colour frame buffer device 80x25
[4294669.599000] fb0: VGA16 VGA frame buffer device
[4294670.616000] Capability LSM initialized
[4294670.746000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[4294670.749000] ACPI: Thermal Zone [THM0] (57 C)
[4294671.311000] ICH3M: IDE controller at PCI slot 0000:00:1f.1
[4294671.311000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[4294671.311000] **** SET: Misaligned resource pointer: df99fae2 Type 07 Len 0
[4294671.312000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[4294671.312000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[4294671.312000] ICH3M: chipset revision 1
[4294671.312000] ICH3M: not 100% native mode: will probe irqs later
[4294671.312000]     ide0: BM-DMA at 0x1860-0x1867, BIOS settings: hda:DMA, hdb:pio
[4294671.312000]     ide1: BM-DMA at 0x1868-0x186f, BIOS settings: hdc:DMA, hdd:pio
[4294671.312000] Probing IDE interface ide0...
[4294671.576000] hda: IC25N030ATCS04-0, ATA DISK drive
[4294672.188000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294672.210000] Probing IDE interface ide1...
[4294672.882000] hdc: MATSHITADVD-ROM SR-8177, ATAPI CD/DVD-ROM drive
[4294673.188000] ide1 at 0x170-0x177,0x376 on irq 15
[4294673.201000] hda: max request size: 128KiB
[4294673.211000] hda: 58605120 sectors (30005 MB) w/1768KiB Cache, CHS=62016/15/63, UDMA(100)
[4294673.212000] hda: cache flushes not supported
[4294673.212000]  hda: hda1 hda2 < hda5 >
[4294673.258000] hdc: ATAPI 24X DVD-ROM drive, 256kB Cache, UDMA(33)
[4294673.258000] Uniform CD-ROM driver Revision: 3.20
[4294673.504000] usbcore: registered new driver usbfs
[4294673.504000] usbcore: registered new driver hub
[4294673.507000] USB Universal Host Controller Interface driver v2.3
[4294673.508000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294673.508000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294673.508000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[4294673.508000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294673.508000] uhci_hcd 0000:00:1d.0: irq 11, io base 0x00001800
[4294673.509000] hub 1-0:1.0: USB hub found
[4294673.509000] hub 1-0:1.0: 2 ports detected
[4294673.610000] **** SET: Misaligned resource pointer: dfb68b02 Type 07 Len 0
[4294673.611000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[4294673.611000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[4294673.611000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294673.611000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[4294673.611000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294673.611000] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001820
[4294673.611000] hub 2-0:1.0: USB hub found
[4294673.611000] hub 2-0:1.0: 2 ports detected
[4294673.712000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[4294673.712000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294673.712000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[4294673.712000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294673.712000] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001840
[4294673.712000] hub 3-0:1.0: USB hub found
[4294673.712000] hub 3-0:1.0: 2 ports detected
[4294673.922000] Attempting manual resume
[4294673.965000] EXT3-fs: mounted filesystem with ordered data mode.
[4294673.983000] kjournald starting.  Commit interval 5 seconds
[4294691.583000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294691.618000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294691.654000] hw_random hardware driver 1.0.0 loaded
[4294691.664000] Linux agpgart interface v0.101 (c) Dave Jones
[4294691.671000] agpgart: Detected an Intel 830M Chipset.
[4294691.687000] agpgart: AGP aperture is 256M @ 0xd0000000
[4294692.598000] PCI: Enabling device 0000:00:1f.5 (0000 -> 0001)
[4294692.598000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[4294692.598000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[4294692.769000] ltmodem: module license 'Proprietary' taints kernel.
[4294692.771000] Loading Lucent Modem Controller driver version 8.26-alk-8
[4294692.772000] ACPI: PCI Interrupt 0000:02:02.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[4294692.772000] Detected Parameters Irq=11 BaseAddress=0x6000 ComAddress=0x6440
[4294692.772000] ttyLTM0 at I/O 0x6000 (irq = 11) is a Lucent/Agere Modem
[4294692.952000] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[4294692.969000] input: TPPS/2 IBM TrackPoint as /class/input/input1
[4294693.072000] input: PC Speaker as /class/input/input2
[4294693.095000] e100: Intel(R) PRO/100 Network Driver, 3.4.14-k4-NAPI
[4294693.095000] e100: Copyright(c) 1999-2005 Intel Corporation
[4294693.178000] Real Time Clock Driver v1.12
[4294693.295000] intel8x0_measure_ac97_clock: measured 50707 usecs
[4294693.295000] intel8x0: clocking to 48000
[4294693.464000] ts: Compaq touchscreen protocol output
[4294693.481000] parport: PnPBIOS parport detected.
[4294693.481000] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[4294693.521000] **** SET: Misaligned resource pointer: db7e09c2 Type 07 Len 0
[4294693.522000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[4294693.522000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[4294693.546000] e100: eth0: e100_probe: addr 0xc0200000, irq 11, MAC addr 00:D0:59:84:43:D4
[4294693.548000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294693.548000] Yenta: CardBus bridge found at 0000:02:00.0 [1014:023b]
[4294693.548000] Yenta: Using INTVAL to route CSC interrupts to PCI
[4294693.548000] Yenta: Routing CardBus interrupts to PCI
[4294693.548000] Yenta TI: socket 0000:02:00.0, mfunc 0x01d21022, devctl 0x64
[4294693.711000] Floppy drive(s): fd0 is 1.44M
[4294693.732000] FDC 0 is a National Semiconductor PC87306
[4294693.761000] irda_init()
[4294693.761000] NET: Registered protocol family 23
[4294693.771000] Yenta: ISA IRQ mask 0x0438, PCI irq 11
[4294693.771000] Socket status: 30000006
[4294693.771000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x6fff
[4294693.771000] cs: IO port probe 0x2000-0x6fff: clean.
[4294693.773000] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[4294693.773000] pcmcia: parent PCI bridge Memory window: 0xf0000000 - 0xf7ffffff
[4294693.797000] ACPI: PCI Interrupt 0000:02:00.1[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[4294693.797000] Yenta: CardBus bridge found at 0000:02:00.1 [1014:023b]
[4294693.797000] Yenta: Using INTVAL to route CSC interrupts to PCI
[4294693.797000] Yenta: Routing CardBus interrupts to PCI
[4294693.797000] Yenta TI: socket 0000:02:00.1, mfunc 0x01d21022, devctl 0x64
[4294693.806000] **** SET: Misaligned resource pointer: db599042 Type 00 Len 42
[4294693.806000] **** SET: Misaligned resource pointer: db5990c6 Type 07 Len 0
[4294693.807000] pnp: Device 00:0b activated.
[4294693.807000] nsc_ircc_pnp_probe() : Found cfg_base 0x000 ; firbase 0x2F8 ; irq 3 ; dma 1.
[4294693.807000] nsc-ircc, Found chip at base=0x000
[4294693.807000] nsc-ircc, driver loaded (Dag Brattli)
[4294693.807000] IrDA: Registered device irda0
[4294693.807000] nsc-ircc, Found dongle: HP HSDL-1100/HSDL-2100
[4294693.807000] nsc-ircc, Found chip at base=0x02e
[4294693.807000] nsc-ircc, driver loaded (Dag Brattli)
[4294693.807000] nsc_ircc_open(), can't get iobase of 0x2f8
[4294693.947000] Unable to handle kernel NULL pointer dereference at virtual address 00000004
[4294693.947000]  printing eip:
[4294693.947000] c013112f
[4294693.947000] *pde = 00000000
[4294693.947000] Oops: 0002 [#1]
[4294693.947000] PREEMPT 
[4294693.947000] Modules linked in: irtty_sir sir_dev nsc_ircc irda floppy crc_ccitt parport_pc tsdev parport rtc e100 mii pcspkr ltserial ltmodem yenta_socket rsrc_nonstatic pcmcia_core snd_intel8x0 snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss psmouse serio_raw snd_pcm snd_timer snd soundcore snd_page_alloc intel_agp agpgart hw_random shpchp pci_hotplug evdev ext3 jbd ide_generic uhci_hcd usbcore ide_cd cdrom ide_disk piix generic thermal processor fan capability commoncap vga16fb vgastate fbcon tileblit font bitblit softcursor
[4294693.947000] CPU:    0
[4294693.947000] EIP:    0060:[<c013112f>]    Tainted: P      VLI
[4294693.947000] EFLAGS: 00010002   (2.6.15-23-386) 
[4294693.947000] EIP is at finish_wait+0x2f/0x70
[4294693.947000] eax: dafaa000   ebx: 00000286   ecx: 00000000   edx: 00000000
[4294693.947000] esi: dafabfd8   edi: dafabfcc   ebp: 00000000   esp: dafabfbc
[4294693.947000] ds: 007b   es: 007b   ss: 0068
[4294693.947000] Process kIrDAd (pid: 3051, threadinfo=dafaa000 task=daf91a70)
[4294693.947000] Stack: dafaa000 00000000 00000000 e0a5f840 00000000 daf91a70 c0118940 00000000 
[4294693.947000]        00000000 e0a5f790 00000000 c0101385 db7a1f98 00000000 00000000 00000000 
[4294693.947000]        00000000 
[4294693.947000] Call Trace:
[4294693.947000]  [<e0a5f840>] irda_thread+0xb0/0xf0 [sir_dev]
[4294693.947000]  [<c0118940>] default_wake_function+0x0/0x20
[4294693.947000]  [<e0a5f790>] irda_thread+0x0/0xf0 [sir_dev]
[4294693.947000]  [<c0101385>] kernel_thread_helper+0x5/0x10
[4294693.947000] Code: d7 b8 00 e0 ff ff 21 e0 8b 00 c7 00 00 00 00 00 8d 72 0c 3b 72 0c 74 34 9c 5b fa b8 00 e0 ff ff 21 e0 ff 40 14 8b 4f 0c 8b 56 04 <89> 51 04 89 0a 89 77 0c 89 76 04 53 9d ff 48 14 8b 40 08 a8 08 
[4294693.947000]  <6>note: kIrDAd[3051] exited with preempt_count 1
[4294694.020000] Yenta: ISA IRQ mask 0x0438, PCI irq 11
[4294694.020000] Socket status: 30000006
[4294694.020000] Yenta: Raising subordinate bus# of parent bus (#02) from #08 to #0a
[4294694.020000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x6fff
[4294694.020000] cs: IO port probe 0x2000-0x6fff: clean.
[4294694.022000] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xcfffffff
[4294694.022000] pcmcia: parent PCI bridge Memory window: 0xf0000000 - 0xf7ffffff
[4294694.781000] cs: IO port probe 0x100-0x3af: clean.
[4294694.782000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[4294694.782000] cs: IO port probe 0x820-0x8ff: clean.
[4294694.783000] cs: IO port probe 0xc00-0xcf7: clean.
[4294694.783000] cs: IO port probe 0xa00-0xaff: clean.
[4294694.784000] cs: IO port probe 0x100-0x3af: clean.
[4294694.785000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[4294694.785000] cs: IO port probe 0x820-0x8ff: clean.
[4294694.786000] cs: IO port probe 0xc00-0xcf7: clean.
[4294694.786000] cs: IO port probe 0xa00-0xaff: clean.
[4294695.321000] lp0: using parport0 (interrupt-driven).
[4294695.407000] Adding 1228932k swap on /dev/hda5.  Priority:-1 extents:1 across:1228932k
[4294695.548000] EXT3 FS on hda1, internal journal
[4294695.816000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294695.816000] md: bitmap version 4.39
[4294696.074000] NET: Registered protocol family 17
[4294696.888000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[4294697.725000] cdrom: open failed.
[4294705.057000] ACPI: AC Adapter [AC] (on-line)
[4294705.138000] ACPI: Battery Slot [BAT0] (battery present)
[4294705.233000] ACPI: Power Button (FF) [PWRF]
[4294705.233000] ACPI: Lid Switch [LID]
[4294705.233000] ACPI: Sleep Button (CM) [SLPB]
[4294705.397000] ibm_acpi: IBM ThinkPad ACPI Extras v0.12a
[4294705.397000] ibm_acpi: http://ibm-acpi.sf.net/
[4294705.398000] ibm_acpi: dock device not present
[4294705.429000] pcc_acpi: loading...
[4294705.569000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[4294711.896000] [drm] Initialized drm 1.0.1 20051102
[4294711.928000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[4294711.929000] [drm] Initialized savage 2.4.1 20050313 on minor 0
[4294711.930000] mtrr: base(0xe4000000) is not aligned on a size(0x5000000) boundary
[4294711.931000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[4294711.931000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[4294711.931000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[4294713.782000] ppdev: user-space parallel port driver
[4294714.168000] IBM machine detected. Enabling interrupts during APM calls.
[4294714.168000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294714.168000] apm: overridden by ACPI.
[4294719.365000] Non-volatile memory driver v1.2
[4294719.382000] input: /usr/sbin/thinkpad-keys as /class/input/input3
[4294720.530000] Bluetooth: Core ver 2.8
[4294720.530000] NET: Registered protocol family 31
[4294720.530000] Bluetooth: HCI device and connection manager initialized
[4294720.530000] Bluetooth: HCI socket layer initialized
[4294720.599000] Bluetooth: L2CAP ver 2.8
[4294720.599000] Bluetooth: L2CAP socket layer initialized
[4294720.640000] Bluetooth: RFCOMM socket layer initialized
[4294720.640000] Bluetooth: RFCOMM TTY layer initialized
[4294720.640000] Bluetooth: RFCOMM ver 1.7
[4294735.915000] NET: Registered protocol family 10
[4294735.916000] lo: Disabled Privacy Extensions
[4294735.916000] IPv6 over IPv4 tunneling driver
[4295085.720000] eepro100.c:v1.09j-t 9/29/99 Donald Becker http://www.scyld.com/network/eepro100.html
[4295085.720000] eepro100.c: $Revision: 1.36 $ 2000/11/17 Modified by Andrey V. Savochkin <saw@saw.sw.com.sg> and others
[4301677.722000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[4301679.423000] SCSI subsystem initialized
[4301679.448000] Initializing USB Mass Storage driver...
[4301679.449000] scsi0 : SCSI emulation for USB Mass Storage devices
[4301679.449000] usb-storage: device found at 2
[4301679.449000] usb-storage: waiting for device to settle before scanning
[4301679.449000] usbcore: registered new driver usb-storage
[4301679.449000] USB Mass Storage support registered.
[4301684.454000]   Vendor: Memorex   Model: TD Classic 003B   Rev: PMAP
[4301684.454000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4301684.462000] usb-storage: device scan complete
[4301685.099000] Driver 'sd' needs updating - please use bus_type methods
[4301686.065000] SCSI device sda: 4030464 512-byte hdwr sectors (2064 MB)
[4301686.068000] sda: Write Protect is off
[4301686.068000] sda: Mode Sense: 23 00 00 00
[4301686.068000] sda: assuming drive cache: write through
[4301686.118000] SCSI device sda: 4030464 512-byte hdwr sectors (2064 MB)
[4301686.121000] sda: Write Protect is off
[4301686.121000] sda: Mode Sense: 23 00 00 00
[4301686.121000] sda: assuming drive cache: write through
[4301686.121000]  sda: sda1
[4301686.127000] sd 0:0:0:0: Attached scsi removable disk sda
[4301686.443000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[4301689.130000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

```

Thanks in advance for any help you can provide.

John

---

### Post by teaker1s on 2007-01-09
terminal 
[COLOR="Red"]sudo lspci[/COLOR]

if no ethernet listed:-

you may find that the port is there but not functional as I had a T28 and it had combined modem/ethernet port card  for ethernet-some were shipped without the modem/ethernet card.

if you remove panel underneath you will find modem-if you see a loose plug it's ethernet and card will need changing.

---

### Post by fastluck on 2007-01-09
Teaker,

Thanks for the quick reply.  I have green light confirmation--the card is there. But I'll open it up as you suggest just to be sure.

Thanks,

John

---

### Post by teaker1s on 2007-01-09
you should be fine, the t28 I had the port was dead no lights/nothing.
as you have lights it must be another issue

---

### Post by fastluck on 2007-01-09
I opened the laptop, and it does contain an ethernet card.  It has these numbers on it:

EC NO: H32706
FRU P/N: 26P8181

Any ideas?

Cheers,

John

---

### Post by teaker1s on 2007-01-10
try these and post output's
[COLOR="Red"]
sudo lspci[/COLOR]

[COLOR="Red"]sudo lsusb[/COLOR]

 [COLOR="Red"]iwconfig[/COLOR]

see if we can see it in the list, maybe it will just need a driver

---

### Post by hal10000 on 2007-01-10
You may install some thinkpad-specific packages which might help you:

1. [COLOR="Red"]sudo apt-get install thinkpad-base[/COLOR] (Configuration files for thinkpad-modules packages)
2. [COLOR="Red"]sudo apt-get install tpctl[/COLOR] (ThinkPad hardware configuration tools).
3. [COLOR="Red"]sudo apt-get install tbp[/COLOR] (program to use the IBM ThinkPad(tm) special keys)

Other packages may be useful too:
hdaps-utils (HDAPS (IBM Hard Drive Active Protection System) utilities)
kmilo-legacy (KDE, KMilo lets you use the special keys on some keyboards and laptops)
mwavem (Mwave/ACP modem support software)
tleds (blinks keyboard LEDs for TX and RX network packets)
thinkpad-source (Source code for thinkpad-modules packages)

---

### Post by fastluck on 2007-01-10
> **teaker1s said:**
> try these and post output's
[COLOR="Red"]
sudo lspci[/COLOR]

[COLOR="Red"]sudo lsusb[/COLOR]

 [COLOR="Red"]iwconfig[/COLOR]

see if we can see it in the list, maybe it will just need a driver

Teaker,

Thanks--here's the output: (The last item is the network card)

**lspci**
```
0000:00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 41)
0000:00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 01)
0000:01:00.0 VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05)
0000:02:00.0 CardBus bridge: Texas Instruments PCI1420
0000:02:00.1 CardBus bridge: Texas Instruments PCI1420
0000:02:02.0 Communication controller: Agere Systems WinModem 56k (rev 01)
0000:02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 41)

```

**lsusb**
```
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  

```
**iwconfig**
```

lo         no wireless extensions
irda0    no wireless extensions
eth0     no wireless extensions
sit0      no wireless extensions

```

---

### Post by fastluck on 2007-01-10
> **hal10000 said:**
> You may install some thinkpad-specific packages which might help you:

1. [COLOR="Red"]sudo apt-get install thinkpad-base[/COLOR] (Configuration files for thinkpad-modules packages)
2. [COLOR="Red"]sudo apt-get install tpctl[/COLOR] (ThinkPad hardware configuration tools).
3. [COLOR="Red"]sudo apt-get install tbp[/COLOR] (program to use the IBM ThinkPad(tm) special keys)

Other packages may be useful too:
hdaps-utils (HDAPS (IBM Hard Drive Active Protection System) utilities)
kmilo-legacy (KDE, KMilo lets you use the special keys on some keyboards and laptops)
mwavem (Mwave/ACP modem support software)
tleds (blinks keyboard LEDs for TX and RX network packets)
thinkpad-source (Source code for thinkpad-modules packages)

No network, so I looked in /etc/apt.sources.list and saw there was no CD entry.  So I used...

apt-cdrom add

...to add the UBUNTU DVD.  Then I entered...

apt-get update

...to update my sources.  Then I tried to install the packages you mentioned and was told no candidate exists.  Then, just for grins, I tried to install kde with the same result.

John

---

### Post by hal10000 on 2007-01-10
you have to enable the universe and multiverse sections to get (most) of these packages.
You don't need the  cdrom entry (it's better to comment it out unless you have slow internet connection).

---

### Post by fastluck on 2007-01-10
Hal,

I don't **have** an internet connection because I can't get my network card to work.

John

---

### Post by fastluck on 2007-01-10
...and Universe and Multiverse are apparently not on the CD-Rom.  I added them to sources.list and apt-get update was unable to read th4e indexes.

John

---

### Post by hal10000 on 2007-01-10
Sorry, i forgotten that this is the reason why you do this all here, shame on me.

---

### Post by fastluck on 2007-01-10
> **hal10000 said:**
> Sorry, i forgotten that this is the reason why you do this all here, shame on me.

Hal,

Don't sweat it!  I don't think that the network hardware on this machine is supported anyway.  I'm going to see if I can't scrounge a PCMCIA card somewhere and just use it.

Cheers,

John

---

### Post by jogege on 2007-01-11
try passing this to the kernel while booting, "Linux acpi=off pnpbios=off".

On my thinkpad X21, unless I use this, I cant get the ethernet port to work. Might be the same issue with you.

---

### Post by fastluck on 2007-01-11
Jogege,

Thanks for the tip.  I'll give that a try later (right now I'm downloading updates using my dog-slow satellite connection. I put a PCMCIA network card in that is working).

John

---

### Post by iMav on 2007-02-04
> **fastluck said:**
> Thanks for the tip.  I'll give that a try later (right now I'm downloading updates using my dog-slow satellite connection. I put a PCMCIA network card in that is working).
I have nothing to add other than the fact that I just purchased a T23 off of ebay and am awaiting its arrival and that I also have satellite internet and can feel your pain!

Of course, my satellite internet dish is sitting on top of a bomb shelter in southern Iraq and my T23 has a long commute before I see it (shipped home and then the wife has to ship it over to me here).  :)

---

### Post by gradedcheese on 2007-02-04
FYI, I have several T23s here and Ethernet works on them just fine.  My NIC is the same as yours (except rev42 rather than 41) with lspci saying:

02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)

So I suspect that you have a dead NIC?  "lsmod | grep e100" should show you that the e100 module is loaded, is that the case?  These cards are supported by e100 according to: [http://thinkwiki.org/wiki/Ethernet_Daughter_Card_%28EDC%29](http://thinkwiki.org/wiki/Ethernet_Daughter_Card_%28EDC%29)

---

### Post by fastluck on 2007-02-04
I ended up just yanking the card and tossing it.  I put a PCMCIA card in that does work.

John

---

### Post by fastluck on 2007-02-04
> **iMav said:**
> Of course, my satellite internet dish is sitting on top of a bomb shelter in southern Iraq and my T23 has a long commute before I see it (shipped home and then the wife has to ship it over to me here).  :)

IMav,  I hope it gets to you soon.  Hopefully they've improved shipping since the first Gulf War.  And kudos to you for the job you're doing over there!

Cheers,

John

---

### Post by rofarmer on 2007-02-04
I too have this type of problem.  My ThinkPad is an A20M, and I just this morning installed Ubuntu - my very first experience with Linux.  I finally got it to boot, but it does not connect to my router.  It USED to, when I had a Windows hard disk in, but now with a new disk with Linux it does not connect.  All these suggestions about SUDO mean nothing to me.  I assume they are command line things, but I have zero clue where to input that sort of thing.

---

### Post by chili555 on 2007-02-04
rofarmer--

Go to Applications -> Accessories -> Terminal and input them right there.

---

### Post by rofarmer on 2007-02-04
Hmm.  "Terminal". NOT intuitive for a newbie.  OK, now I know WHERE to type a command, but WHAT do I type ?  Am I supposed to download either the Universe or Multiverse programs, if that is what they are ?

---

### Post by chili555 on 2007-02-04
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

---

### Post by rofarmer on 2007-02-05
As a Linux newbie, let me express the opinion that many of these posts are of little value, as they describe things with the assumption that we newbies know what you are talking about.  Please remember that we BY DEFINITION have come from a Windows environment, and have little idea/experience about all this stuff.  My problem is a ThinkPad that won't connect to the internet, despite doing that just fine with the old hard drive.  I see suggestions about getting "thinkpad-base", and "tpctl" with no details as to where I should go to get them, and what I am to do when I do.  I am keen to become a Linux supporter, but the problems I am having just getting it installed and connecting to the internet are WAY beyond anything I have experienced in Windows.  These are UGLY problems.

---

### Post by chili555 on 2007-02-05
Hang in there and stay with it, because two rewards await you on the top of the learning curve; first, the pride in learning something new and becoming proficient at it, and second, a world wonderfully free of viruses, worms, mal-ware, spy-ware, the inevitable slowdowns and inevitable reinstalls.

We all came from where you are now and even though some of us are 63 years old and can't remember if our cardiologist appointment is tomorrow or yesterday, we figured it out. You can, too.

I don't necessarily know that > we BY DEFINITION have come from a Windows environment because some of you have come from a Mac environment. Moreover, there are a lot of books and magazines dealing with Linux that include a DVD with Ubuntu or another distribution on it. So, some have come to this forum with a lot of reading under their belts and have a pretty good understanding of the basics. 

I don't think tpctl or thinkpad-base is keeping you from connecting to your router. Let's back up.

Is this an ethernet or wireless card you are trying to use? I think Ubuntu has not quite figured out which module (driver, in Windows-speak) it needs. Let's help it.

Open up that terminal and issue a command: sudo lspci -v and tell us the lines dealing with ethernet controller and network controller. Let's also take a look at sudo ifconfig and sudo iwconfig (if this is a wireless card you are trying to set up.)

We will get it going together!

---

### Post by fastluck on 2007-02-05
> **rofarmer said:**
> [snip]All these suggestions about SUDO mean nothing to me.  I assume they are command line things, but I have zero clue where to input that sort of thing.

Rofarmer,

Personally, I find sudo to be a pain.  You can go to the command-line (select Gnome menu item Application then Terminal) and type this:

[FONT="Courier New"]sudo su -
[/FONT]
Then enter your password.  Then, type this:

[FONT="Courier New"]passwd[/FONT]

...and enter your password again.  From then on, whenever you need to log in as root,  just type

[FONT="Courier New"]su[/FONT]

...at the command-line and enter your password to become root.

John

---

### Post by fastluck on 2007-02-05
Rofarmer,

Linux is over-hyped as "just as easy as Windows" when it a**bsolutely is not**.  I remember five or six years ago when I started using it, and how frustrating it was to modify any setting. There's no common interface to set everything up, and it's hard to find apps to set things up.

But take each task one at a time, do Google searches and leave lots of messages, and it won't take too long before you realize that Linux is easier to customize and far more flexible and powerful than Windows can ever pretend to be.

And don't be afraid of the command-line!  Microsoft took a beating years ago because DOS was underneath Windows 3.1.  And ever since then, they've been ashamed of the command-line.  Linux flaunts it, and by using the command-line you'll realize the full power and flexibility of this great OS.

Cheers,

John

---

### Post by rofarmer on 2007-02-06
Thanks for the offers of help.  I delayed trying Linux until now, because of all the problems I had hear about.  I figured that by now it would be pretty good.  Guess it is not quite at the level for untrained fresh off the boat people.  Anyway, sudo lspci reports that my TP has an Ethernet Pro 100 (rev 09) 82557/8/9.  Sudo iwconfig reports no wireless extensions (as expected).  Sudo ifconfig makes no report at all.  It is blank.  Not even a "command not found".  The ethernet cable port shows a green light, with an occasional  high speed flutter.  It is most of the time solid, not blinking.  I figure this means it is TRYING to connect to my router.  I suppose I could save the reports from these commands, to a text file, copy it to diskette, move the disk to the PC that DOES connect, and paste it here.

---

### Post by chili555 on 2007-02-06
Now we're getting there!

Your ethernet card wants the module eepro100. Let's see if it got inserted automatically by doing lsmod | grep eepro100. That means, approximately, "list all the modules running and tell me if one of them is eepro100." If eepro100 is listed, we're almost home!

If it is not, simply insert it with sudo insmod  eepro100. This means, approximately, "insert the module eepro100."

Then, configure your ethernet connection through System -> Administration -> Networking. Highlight the ethernet interface and click Properties. You probably want DHCP and then check Enable... in the upper left corner and the interface should start right up.

Let us know how you make out. We'll get it!

PS - Try sudo ifconfig -a (My bad, sorry.)

---

### Post by rofarmer on 2007-02-06
lsmod | grep | eepro100 produces no response.

sudo insmod eepro100 produces "no such file or directory".

Do you want the output of sudo ifconfig -a ?

---

### Post by rofarmer on 2007-02-06
Sorry, **lsmod | grep | eepro100** produces **bash: eepro100: command not found**

---

### Post by chili555 on 2007-02-06
It was not lsmod | grep | eepro100. The command is sudo lsmod | grep eepro100. You have an extra "pipe" in there.

Let's try sudo modprobe eepro100.

> Do you want the output of sudo ifconfig -a Yes, please.

---

### Post by rofarmer on 2007-02-06
Oh this just gets better every minute.  

Sudo modprobe eepro100 produces no response.  

Sudo ifconfig -a produces a series of paragraphs which I can copy & paste to a file I create using OOo.  But when I try to save that file to floppy A:, I get an error message.  If I try repeatedly to save to the floppy (so I can paste it here) the diskette becomes unusable, and cannot even be reformated on my main PC.  When I insert a fresh floppy disk, Linux does not even see there is an existing file there.  This would seem to imply that floppies cannot be used to pass files from Linux to Windows, as they are not compatible at all.  Great news.  If you can tell me exactly what you are looking for, I can try retyping it as I read from the ThinkPad.

---

### Post by rofarmer on 2007-02-06
Sudo lsmod | grep eepro100

produces

eepro100         33168 0
mii                    6912 2 eepro`00, e100

---

### Post by chili555 on 2007-02-06
Super! The correct module is there!

Now, what happens when you configure your ethernet connection through System -> Administration -> Networking.  Does the interface start up? Can you ping -c3 [www.google.com?](www.google.com?)

---

### Post by rofarmer on 2007-02-06
This gets even funnier with every passing action.  There are TWO floppy-1 icons, PLUS a picture of a floppy diskette.  One of the floppy-1 items says it is not mounted, and cannot be accessed.  I was finally able to write (I think) the ipconfig file to a freshly formatted floppy.  When I ask to see the details on that disk, sure enough, there is the file I created.  But when I take this floppy to my desktop, it is shown to be blank.  When I put it back into the Linux machine, the file has disappeared.   I then took a different floppy, which has about 10 files on it.  None of them show up on the Linux ThinkPad.  I then re-inserted the original single-file diskette, and when I check to see if the single file is there, I get the list of the ten files that are on the diskette that I had removed !  Now my experience so far with WIndows and OS/2 is that the SECOND you swap out a diskette, the OS understands that a refresh of the drive contents is required.  Ubuntu seems to have some sort of delay.  (Cue background music from the X-files).

---

### Post by rofarmer on 2007-02-06
System-->Administration-->Networking comes up with the Connections tab showing "Wired COnnection" ticked, and Modem Connection not.  The General tab has Host Name filled in with my workstation name.  Domain Name is blank.  The DNS tab has two DNS servers listed, which I added manually (copied from my desktop) and Search Domains has none.  Hosts has a bunch of stuff, none of which I created manually.  Anything else I should do ?

---

### Post by rofarmer on 2007-02-06
When I click on the twin-screen icon at the top (Connection Properties), it shows eth0 as disconnected.  If I click on Configure, it comes up with Static IP Address, and some values for IP address, Subnet Mask, and Gateway address.  Changing this to Automatic DHCP of course removes the Subnet Mask etc. but the internet is still not accessible.

---

### Post by chili555 on 2007-02-06
I feel your floppy pain, but let's solve one problem at a time...all my limited brain has room for.

Please go  through System -> Administration -> Networking, set the ethernet to DHCP, check Enable and then see if it gets a connection. If it does not, open a terminal and do sudo ifup eth0 and let us know what you see.

PS- I recently replaced the case on my wife's desktop (running Fedora Core 6) and I put the floppy drive and the old case in the back of her old 1983 Chevy wagon and sent it all to the crusher, where it belongs. I bought her a shiny new 256Mb USB key and a Cadillac Deville.

---

### Post by rofarmer on 2007-02-06
sudo ifup eth0 gets

/etc/network/interfaces:23: duplicate interface
ifup: couldn't read interfaces file "etc/network/interfaces"

---

### Post by chili555 on 2007-02-06
Well, now, that's a strange one!

Let's do some detective work. First, is eth0 listed as an interface when you do sudo ifconfig -a? Next, just for the curiosity of it, do cat /etc/network/interfaces and let's see what, if anything, we can see. I can't believe it is missing altogether, because I don't think your system would even run without at least an entry for the mysterious loopback device: lo.

Last, open up System -> Administration -> Networking, highlight the Wired Connection, click properties and confirm that the interface is DHCP and *enabled.* 

We're closing in on it...any minute now!

---

### Post by rofarmer on 2007-02-06
eth0 IS listed as an interface when I do sudo ifconfig -a 

sudo cat /etc/network/interfaces brings up a bunch of stuff as follows (manually typing it in)

auto lo
iface lo inet loopback

iface eth0 inet dhcp
address x.x.x.x
netmask y.y.y.y
gateway z.z.z.z

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

iface eth0 inet static
address x.x.x.x
netmask y.y.y.y
gateway z.z.z.z


System -> Administration -> Networking, highlight the Wired Connection, click properties and confirm that the interface is DHCP and enabled.  This is correct

---

### Post by chili555 on 2007-02-06
A-haaa!!!

See eth0 is listed twice? Dunno how it got there, but let's fix it up. Do sudo gedit /etc/network/interfaces. Gedit is a simple text editor, like your old friend Wordpad. Remove the second instance of eth0 altogether. Change the first one from this:> iface eth0 inet dhcp
address x.x.x.x
netmask y.y.y.y
gateway z.z.z.z

To this: > iface eth0 inet dhcp

Now, SAVE and close gedit. Try sudo ifup eth0 and let me know the result.

PS - By now, you would have rebooted your Windows machine 27 times!

---

### Post by rofarmer on 2007-02-06
Hah !!!!! Fantastic.  The sudo command came back with a whole bunch of stuff,  and it certainly looked like it was about to connect.  When I jumped to my Firefox session, sure enough it was working.  Now I can download SETI and get at the rest of the internet.

I really appreciate the help......I will have to check out the diskette drive problem as well.  Part of what throws me off is that the insert/overtype toggle does not seem to work.  It is stuck in insert mode.  BAD programming.

---

### Post by chili555 on 2007-02-06
Woot! Have fun and learn some more linux. We'll look for you on these forums!

Be sure to run System -> Administration -> Update Manager and get the updates.

---

### Post by rofarmer on 2007-02-06
OK, I downloaded the SETI package, and I am used to Windows and the "run" command in the dowload window.  That does not work here, it tries to open GEDIT.  What do I do to unpack something ending in .sh ?

---

### Post by chili555 on 2007-02-06
You don't really "unpack" it; you just run it in the good ole terminal:
   sh File_you_downloaded.sh

Also see [http://boinc.berkeley.edu/release_notes.php](http://boinc.berkeley.edu/release_notes.php)

I run Folding@Home on five computers here and the part you should be especially interested in is running on boot. You can check to see if it is running by doing the command top. I just ran top on one of mine and, among other things, it says FahCore_7a.exe is consuming 99.6% of my CPU cycles. Clearly, it's running.

Since this is no longer a post related to getting an ethernet card running on a Thinkpad, it's best to start a new thread asking a specific question.

---

### Post by mndzmyst on 2008-01-31
I am having the same problem. I fresh install of gutsy on a t23 does not recognize my ethernet port. It was working fine in windows right before i installed ubuntu. nothing in this thread has helped. can someone please help me???? i bought this laptop 'cuz it was supposed to go flawlessly. but a laptop with no internet is pretty much useless.

---

