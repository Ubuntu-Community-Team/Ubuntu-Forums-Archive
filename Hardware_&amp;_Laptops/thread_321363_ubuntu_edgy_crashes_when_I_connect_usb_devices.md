---
title: "ubuntu edgy crashes when I connect usb devices"
date: 2006-12-18
forum: Hardware &amp; Laptops
---

### Post by slotmakine on 2006-12-18
When I connect usb (printer,camera) edgy stops freezing my mouse pointer and screen..I read about modifying kernel trough grub adding "irqpoll vga=791",but if I hit tab in grub  I'get error unidentify string,and if I reboot and back again in to grub it doesn't mantain my last edit of the kernel...Please help me,I'm new to x and ubuntu,and I wish use my print and camera with edgy..thanks..
here my dmesg:
> [PHP][17179569.184000] Linux version 2.6.17-10-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 22:28:26 UTC 2006 (Ubuntu 2.6.17-10.34-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000001fff0000 - 000000001fff8000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001fff8000 - 0000000020000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffee0000 - 00000000fff00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 511MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000fbc70
[17179569.184000] On node 0 totalpages: 131056
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126960 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 AMI                                   ) @ 0x000fab70
[17179569.184000] ACPI: RSDT (v001 AMIINT SiS740XX 0x00001000 MSFT 0x0100000b) @ 0x1fff0000
[17179569.184000] ACPI: FADT (v001 AMIINT SiS740XX 0x00000011 MSFT 0x0100000b) @ 0x1fff0030
[17179569.184000] ACPI: MADT (v001 AMIINT SiS740XX 0x00001000 MSFT 0x0100000b) @ 0x1fff00c0
[17179569.184000] ACPI: DSDT (v001    SiS      746 0x00000100 MSFT 0x0100000d) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:10 APIC version 16
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 2000.103 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.536000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.536000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179572.552000] Memory: 510056k/524224k available (1910k kernel code, 13596k reserved, 1069k data, 308k init, 0k highmem)
[17179572.552000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.632000] Calibrating delay using timer specific routine.. 4002.77 BogoMIPS (lpj=8005556)
[17179572.632000] Security Framework v1.0.0 initialized
[17179572.632000] SELinux:  Disabled at boot.
[17179572.632000] Mount-cache hash table entries: 512
[17179572.632000] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[17179572.632000] CPU: After vendor identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[17179572.632000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179572.632000] CPU: L2 Cache: 256K (64 bytes/line)
[17179572.632000] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
[17179572.632000] Checking 'hlt' instruction... OK.
[17179572.648000] SMP alternatives: switching to UP code
[17179572.648000] Freeing SMP alternatives: 16k freed
[17179572.648000] checking if image is initramfs... it is
[17179573.112000] Freeing initrd memory: 5321k freed
[17179573.112000] ACPI: Core revision 20060707
[17179573.116000] ACPI: Looking for DSDT ... not found!
[17179573.116000] CPU0: AMD Athlon(tm) XP 2400+ stepping 00
[17179573.116000] Total of 1 processors activated (4002.77 BogoMIPS).
[17179573.116000] ENABLING IO-APIC IRQs
[17179573.116000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179573.260000] Brought up 1 CPUs
[17179573.260000] migration_cost=0
[17179573.260000] NET: Registered protocol family 16
[17179573.260000] EISA bus registered
[17179573.260000] ACPI: bus type pci registered
[17179573.260000] PCI: PCI BIOS revision 2.10 entry at 0xfdb31, last bus=2
[17179573.260000] PCI: Using configuration type 1
[17179573.260000] Setting up standard PCI resources
[17179573.264000] ACPI: Interpreter enabled
[17179573.264000] ACPI: Using IOAPIC for interrupt routing
[17179573.264000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.264000] PCI: Probing PCI hardware (bus 00)
[17179573.268000] Uncovering SIS963 that hid as a SIS503 (compatible=0)
[17179573.268000] Enabling SiS 96x SMBus.
[17179573.268000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:02.5
[17179573.268000] Boot video device is 0000:01:00.0
[17179573.268000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.284000] ACPI: Power Resource [URP1] (off)
[17179573.284000] ACPI: Power Resource [URP2] (off)
[17179573.284000] ACPI: Power Resource [FDDP] (off)
[17179573.284000] ACPI: Power Resource [LPTP] (off)
[17179573.288000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179573.288000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179573.288000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179573.288000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179573.288000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179573.288000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179573.288000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179573.288000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179573.288000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.288000] pnp: PnP ACPI init
[17179573.292000] pnp: PnP ACPI: found 14 devices
[17179573.292000] PnPBIOS: Disabled by ACPI PNP
[17179573.292000] PCI: Using ACPI for IRQ routing
[17179573.292000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.296000] PCI: Bridge: 0000:00:01.0
[17179573.296000]   IO window: disabled.
[17179573.296000]   MEM window: cdd00000-cfefffff
[17179573.296000]   PREFETCH window: bda00000-cdbfffff
[17179573.296000] NET: Registered protocol family 2
[17179573.328000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179573.328000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179573.328000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179573.328000] TCP: Hash tables configured (established 16384 bind 8192)
[17179573.328000] TCP reno registered
[17179573.328000] audit: initializing netlink socket (disabled)
[17179573.328000] audit(1166458121.328:1): initialized
[17179573.328000] VFS: Disk quotas dquot_6.5.1
[17179573.328000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.328000] Initializing Cryptographic API
[17179573.328000] io scheduler noop registered
[17179573.328000] io scheduler anticipatory registered
[17179573.328000] io scheduler deadline registered
[17179573.328000] io scheduler cfq registered (default)
[17179581.328000] 0000:00:03.2 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[17179581.328000] isapnp: Scanning for PnP cards...
[17179581.680000] isapnp: No Plug & Play device found
[17179581.704000] Real Time Clock Driver v1.12ac
[17179581.704000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179581.704000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179581.704000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179581.704000] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179581.704000] mice: PS/2 mouse device common for all mice
[17179581.704000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179581.704000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179581.704000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179581.704000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[17179581.708000] Failed to disable AUX port, but continuing anyway... Is this a SiS?
[17179581.708000] If AUX port is really absent please use the 'i8042.noaux' option.
[17179581.712000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179581.712000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179581.716000] EISA: Probing bus 0 at eisa.0
[17179581.716000] EISA: Detected 0 cards.
[17179581.716000] TCP bic registered
[17179581.716000] NET: Registered protocol family 1
[17179581.716000] NET: Registered protocol family 8
[17179581.716000] NET: Registered protocol family 20
[17179581.716000] Using IPI No-Shortcut mode
[17179581.716000] ACPI: (supports S0 S1 S4 S5)
[17179581.720000] Freeing unused kernel memory: 308k freed
[17179581.804000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179582.872000] Capability LSM initialized
[17179583.464000] SIS5513: IDE controller at PCI slot 0000:00:02.5
[17179583.464000] SIS5513: chipset revision 0
[17179583.464000] SIS5513: not 100% native mode: will probe irqs later
[17179583.464000] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
[17179583.464000]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb:DMA
[17179583.464000]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:DMA
[17179583.464000] Probing IDE interface ide0...
[17179583.752000] hda: Maxtor 6Y060L0, ATA DISK drive
[17179584.424000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179584.432000] Probing IDE interface ide1...
[17179585.168000] hdc: LG DVD-ROM DRD-8120B, ATAPI CD/DVD-ROM drive
[17179585.952000] hdd: PHILIPS SPD2400L1, ATAPI CD/DVD-ROM drive
[17179586.008000] ide1 at 0x170-0x177,0x376 on irq 15
[17179586.028000] hda: max request size: 128KiB
[17179586.040000] hda: 120103200 sectors (61492 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(133)
[17179586.040000] hda: cache flushes supported
[17179586.040000]  hda: hda1 hda2 < hda5 >
[17179586.084000] hdc: ATAPI 40X DVD-ROM drive, 512kB Cache, UDMA(33)
[17179586.084000] Uniform CD-ROM driver Revision: 3.20
[17179586.088000] hdd: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179586.348000] usbcore: registered new driver usbfs
[17179586.348000] usbcore: registered new driver hub
[17179586.352000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179586.352000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 169
[17179586.352000] ohci_hcd 0000:00:03.0: OHCI Host Controller
[17179586.352000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[17179586.368000] ohci_hcd 0000:00:03.0: irq 169, io mem 0xcfffd000
[17179586.424000] usb usb1: configuration #1 chosen from 1 choice
[17179586.424000] hub 1-0:1.0: USB hub found
[17179586.424000] hub 1-0:1.0: 3 ports detected
[17179586.528000] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 177
[17179586.528000] ohci_hcd 0000:00:03.1: OHCI Host Controller
[17179586.528000] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[17179586.544000] ohci_hcd 0000:00:03.1: irq 177, io mem 0xcfffe000
[17179586.600000] usb usb2: configuration #1 chosen from 1 choice
[17179586.600000] hub 2-0:1.0: USB hub found
[17179586.600000] hub 2-0:1.0: 3 ports detected
[17179586.712000] ACPI: PCI Interrupt 0000:00:03.2[D] -> GSI 23 (level, low) -> IRQ 185
[17179586.712000] ehci_hcd 0000:00:03.2: EHCI Host Controller
[17179586.712000] ehci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[17179586.712000] PCI: cache line size of 64 is not supported by device 0000:00:03.2
[17179586.712000] ehci_hcd 0000:00:03.2: irq 185, io mem 0xcffff000
[17179586.712000] ehci_hcd 0000:00:03.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179586.712000] usb usb3: configuration #1 chosen from 1 choice
[17179586.712000] hub 3-0:1.0: USB hub found
[17179586.712000] hub 3-0:1.0: 6 ports detected
[17179586.876000] Attempting manual resume
[17179586.888000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179586.888000] EXT3-fs: write access will be enabled during recovery.
[17179588.868000] kjournald starting.  Commit interval 5 seconds
[17179588.868000] EXT3-fs: recovery complete.
[17179588.888000] EXT3-fs: mounted filesystem with ordered data mode.
[17179598.440000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[17179598.620000] gameport: EMU10K1 is pci0000:00:0a.1/gameport0, io 0xdc00, speed 1217kHz
[17179598.728000] 8139too Fast Ethernet driver 0.9.27
[17179598.728000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> GSI 17 (level, low) -> IRQ 193
[17179598.728000] eth0: RealTek RTL8139 at 0xe089af00, 00:a0:d2:a5:42:c3, IRQ 193
[17179598.728000] eth0:  Identified 8139 chip type 'RTL-8139B'
[17179598.796000] Floppy drive(s): fd0 is 1.44M
[17179598.816000] FDC 0 is a post-1991 82077
[17179599.092000] sis900.c: v1.08.09 Sep. 19 2005
[17179599.092000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 201
[17179599.096000] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[17179599.104000] 0000:00:04.0: Using transceiver found at address 1 as default
[17179599.104000] eth1: SiS 900 PCI Fast Ethernet at 0xd800, IRQ 201, 00:0b:6a:4e:8b:e5.
[17179599.120000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179599.220000] Linux agpgart interface v0.101 (c) Dave Jones
[17179599.356000] agpgart: Detected SiS 746 chipset
[17179599.364000] agpgart: AGP aperture is 64M @ 0xd0000000
[17179599.448000] input: PC Speaker as /class/input/input1
[17179599.824000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179599.828000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179599.840000] parport: PnPBIOS parport detected.
[17179599.840000] parport0: PC-style at 0x378 (0x778), irq 7, dma 0 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[17179599.944000] irda_init()
[17179599.944000] NET: Registered protocol family 23
[17179600.056000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 18 (level, low) -> IRQ 209
[17179600.160000] input: ImPS/2 Generic Wheel Mouse as /class/input/input2
[17179600.224000] ts: Compaq touchscreen protocol output
[17179600.452000] NET: Registered protocol family 17
[17179600.628000] lp0: using parport0 (interrupt-driven).
[17179600.668000] Adding 1510068k swap on /dev/disk/by-uuid/10c416c8-7b76-4e01-a94e-932560db86dd.  Priority:-1 extents:1 across:1510068k
[17179600.736000] EXT3 FS on hda1, internal journal
[17179601.408000] eth0: Media Link On 100mbps full-duplex 
[17179601.756000] ACPI: Power Button (FF) [PWRF]
[17179601.756000] ACPI: Power Button (CM) [PWRB]
[17179601.868000] ibm_acpi: ec object not found
[17179601.904000] pcc_acpi: loading...
[17179605.056000] apm: BIOS not found.
[17179611.560000] Bluetooth: Core ver 2.8
[17179611.560000] NET: Registered protocol family 31
[17179611.560000] Bluetooth: HCI device and connection manager initialized
[17179611.560000] Bluetooth: HCI socket layer initialized
[17179611.576000] Bluetooth: L2CAP ver 2.8
[17179611.576000] Bluetooth: L2CAP socket layer initialized
[17179611.624000] Bluetooth: RFCOMM socket layer initialized
[17179611.624000] Bluetooth: RFCOMM TTY layer initialized
[17179611.624000] Bluetooth: RFCOMM ver 1.7
[17179614.208000] NET: Registered protocol family 10
[17179614.208000] lo: Disabled Privacy Extensions
[17179614.208000] IPv6 over IPv4 tunneling driver
[17179625.160000] eth0: no IPv6 routers present
[/PHP]

---

