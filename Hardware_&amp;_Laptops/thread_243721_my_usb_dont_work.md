---
title: "my usb dont work"
date: 2006-08-25
forum: Hardware &amp; Laptops
---

### Post by shibby on 2006-08-25
hi,

For 2 day, i have had problem with usb, indeed my usb works at the begining and then my mouse (usb) stop working...
i dont know how to do for fix it, someone can help me ?

---

### Post by Woei on 2006-08-25
We'd love to help, but we can't do much without more specific information. What hardware are we talking about (brand and make of your laptop) for example. Please open up a terminal (gnome-terminal for example), and type 'dmesg > usb-troubles'. Then copy and paste the output of that file here, so we may have a clue as to what's going on.

---

### Post by shibby on 2006-08-25
ok sorry, 
my laptop is a toshiba and my dmesg is following :

here is my : dmesg | grep usb results :

> [17179578.924000] usbcore: registered new driver usbfs
[17179578.924000] usbcore: registered new driver hub
[17179580.740000] usb 2-2: new low speed USB device using ohci_hcd and address 2
[17179580.964000] usbcore: registered new driver hiddev
[17179580.972000] input: USB HID v1.10 Mouse [Acrox USB & PS/2 Mouse] on usb-0000:00:13.1-2
[17179580.972000] usbcore: registered new driver usbhid
[17179580.972000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver


my dmesg : 

```
[17179569.184000] Linux version 2.6.15-26-686 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP PREEMPT Thu Aug 3 03:13:28 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001bea0000 (usable)
[17179569.184000]  BIOS-e820: 000000001bea0000 - 000000001beb0000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001beb0000 - 000000001bf00000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001bf00000 - 000000001c000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 446MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f7710
[17179569.184000] On node 0 totalpages: 114336
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 110240 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI present.
[17179569.184000] ATI board detected. Disabling timer routing over 8254.
[17179569.184000] ACPI: RSDP (v000 TOSINV                                ) @ 0x000f76c0
[17179569.184000] ACPI: RSDT (v001 TOSINV   RSDT   0x06040000  LTP 0x00000000) @ 0x1beabf9b
[17179569.184000] ACPI: FADT (v001 TOSINV Goldfish 0x06040000 ATI  0x000f4240) @ 0x1beafef6
[17179569.184000] ACPI: MADT (v001 TOSINV 	 APIC   0x06040000  LTP 0x00000000) @ 0x1beaff6a
[17179569.184000] ACPI: MCFG (v001 TOSINV   MCFG   0x06040000  LTP 0x00000000) @ 0x1beaffc4
[17179569.184000] ACPI: SSDT (v001 TOSINV  Cpu0Cst 0x00003001 INTL 0x20030224) @ 0x1beac1ce
[17179569.184000] ACPI: SSDT (v001 TOSINV    CpuPm 0x00003000 INTL 0x20030224) @ 0x1beabfd3
[17179569.184000] ACPI: DSDT (v001 TOSINV    SB450 0x06040000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x8008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:13 APIC version 20
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[17179569.184000] ACPI: BIOS IRQ0 pin2 override ignored.
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level)
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 1c000000:c4000000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda5 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[17179569.184000] Detected 1493.142 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.588000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.588000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179572.604000] Memory: 441832k/457344k available (2110k kernel code, 15000k reserved, 595k data, 332k init, 0k highmem)
[17179572.604000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.684000] Calibrating delay using timer specific routine.. 2991.12 BogoMIPS (lpj=5982258)
[17179572.684000] Security Framework v1.0.0 initialized
[17179572.684000] SELinux:  Disabled at boot.
[17179572.684000] Mount-cache hash table entries: 512
[17179572.684000] CPU: After generic identify, caps: afe9fbff 00000000 00000000 00000000 00000000 00000000 00000000
[17179572.684000] CPU: After vendor identify, caps: afe9fbff 00000000 00000000 00000000 00000000 00000000 00000000
[17179572.684000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179572.684000] CPU: L2 cache: 1024K
[17179572.684000] CPU: After all inits, caps: afe9fbff 00000000 00000000 00000040 00000000 00000000 00000000
[17179572.684000] mtrr: v2.0 (20020519)
[17179572.684000] Enabling fast FPU save and restore... done.
[17179572.684000] Enabling unmasked SIMD FPU exception support... done.
[17179572.684000] Checking 'hlt' instruction... OK.
[17179572.700000] SMP alternatives: switching to UP code
[17179572.700000] checking if image is initramfs... it is
[17179573.372000] Freeing initrd memory: 6809k freed
[17179573.388000] ACPI: Looking for DSDT ... not found!
[17179573.408000] CPU0: Intel(R) Celeron(R) M processor         1.50GHz stepping 08
[17179573.408000] Total of 1 processors activated (2991.12 BogoMIPS).
[17179573.408000] ENABLING IO-APIC IRQs
[17179573.408000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179573.552000] Brought up 1 CPUs
[17179573.552000] NET: Registered protocol family 16
[17179573.552000] EISA bus registered
[17179573.552000] ACPI: bus type pci registered
[17179573.552000] PCI: PCI BIOS revision 2.10 entry at 0xfd82c, last bus=4
[17179573.552000] PCI: Using MMCONFIG
[17179573.552000] ACPI: Subsystem revision 20051216
[17179573.560000] ACPI: Interpreter enabled
[17179573.560000] ACPI: Using IOAPIC for interrupt routing
[17179573.564000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.564000] PCI: Probing PCI hardware (bus 00)
[17179573.564000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
[17179573.564000] Boot video device is 0000:01:05.0
[17179573.564000] PCI: Transparent bridge - 0000:00:14.4
[17179573.564000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.568000] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[17179573.568000] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[17179573.568000] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[17179573.568000] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[17179573.572000] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[17179573.572000] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[17179573.572000] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[17179573.572000] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[17179573.572000] ACPI: Embedded Controller [EC0] (gpe 7) interrupt mode.
[17179573.572000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[17179573.572000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[17179573.572000] ACPI: Power Resource [PFA1] (off)
[17179573.572000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.572000] pnp: PnP ACPI init
[17179573.588000] pnp: PnP ACPI: found 9 devices
[17179573.588000] PnPBIOS: Disabled by ACPI PNP
[17179573.588000] PCI: Using ACPI for IRQ routing
[17179573.588000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.600000] pnp: 00:07: ioport range 0x1080-0x1080 has been reserved
[17179573.600000] pnp: 00:07: ioport range 0x220-0x22f has been reserved
[17179573.600000] pnp: 00:07: ioport range 0x400-0x401 has been reserved
[17179573.600000] pnp: 00:07: ioport range 0x40b-0x40b has been reserved
[17179573.600000] PCI: Bridge: 0000:00:01.0
[17179573.600000]   IO window: 9000-9fff
[17179573.600000]   MEM window: c0100000-c01fffff
[17179573.600000]   PREFETCH window: d0000000-dfffffff
[17179573.600000] PCI: Bus 3, cardbus bridge: 0000:02:06.0
[17179573.600000]   IO window: 0000a400-0000a4ff
[17179573.600000]   IO window: 0000a800-0000a8ff
[17179573.600000]   PREFETCH window: 20000000-21ffffff
[17179573.600000]   MEM window: 24000000-25ffffff
[17179573.600000] PCI: Bridge: 0000:00:14.4
[17179573.600000]   IO window: a000-afff
[17179573.600000]   MEM window: c0200000-c02fffff
[17179573.600000]   PREFETCH window: 20000000-21ffffff
[17179573.600000] PCI: Enabling device 0000:02:06.0 (0004 -> 0007)
[17179573.600000] ACPI: PCI Interrupt 0000:02:06.0[A] -> GSI 23 (level, low) -> IRQ 185
[17179573.600000] audit: initializing netlink socket (disabled)
[17179573.600000] audit(1156531781.596:1): initialized
[17179573.600000] VFS: Disk quotas dquot_6.5.1
[17179573.600000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.600000] Initializing Cryptographic API
[17179573.600000] io scheduler noop registered
[17179573.600000] io scheduler anticipatory registered
[17179573.600000] io scheduler deadline registered
[17179573.600000] io scheduler cfq registered
[17179573.604000] isapnp: Scanning for PnP cards...
[17179573.956000] isapnp: No Plug & Play device found
[17179573.976000] Real Time Clock Driver v1.12
[17179573.976000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[17179573.984000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179573.984000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.984000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179573.988000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179573.988000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.988000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.988000] mice: PS/2 mouse device common for all mice
[17179573.992000] EISA: Probing bus 0 at eisa.0
[17179573.992000] Cannot allocate resource for EISA slot 1
[17179573.992000] Cannot allocate resource for EISA slot 8
[17179573.992000] EISA: Detected 0 cards.
[17179573.992000] NET: Registered protocol family 2
[17179574.032000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179574.032000] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[17179574.032000] TCP bind hash table entries: 16384 (order: 5, 196608 bytes)
[17179574.032000] TCP: Hash tables configured (established 16384 bind 16384)
[17179574.032000] TCP reno registered
[17179574.032000] TCP bic registered
[17179574.032000] NET: Registered protocol family 1
[17179574.032000] NET: Registered protocol family 8
[17179574.032000] NET: Registered protocol family 20
[17179574.032000] Using IPI No-Shortcut mode
[17179574.032000] ACPI wakeup devices: 
[17179574.032000]  LID OHC1 OHC2 EHCI  P2P LANC AUDO MODM 
[17179574.032000] ACPI: (supports S0 S3 S4 S5)
[17179574.032000] Freeing unused kernel memory: 332k freed
[17179574.036000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179574.084000] vga16fb: initializing
[17179574.084000] vga16fb: mapped to 0xc00a0000
[17179574.184000] Console: switching to colour frame buffer device 80x25
[17179574.184000] fb0: VGA16 VGA frame buffer device
[17179575.256000] Capability LSM initialized
[17179575.396000] ACPI: Fan [FAN1] (off)
[17179575.400000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179575.400000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179575.608000] ACPI: Thermal Zone [TZCR] (50 C)
[17179576.116000] SCSI subsystem initialized
[17179576.116000] ACPI: bus type scsi registered
[17179576.116000] libata version 1.20 loaded.
[17179576.120000] sata_sil 0000:00:12.0: version 0.9
[17179576.120000] PCI: Enabling device 0000:00:12.0 (0005 -> 0007)
[17179576.120000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 193
[17179576.120000] ata1: SATA max UDMA/100 cmd 0xDC870080 ctl 0xDC87008A bmdma 0xDC870000 irq 193
[17179576.120000] ata2: SATA max UDMA/100 cmd 0xDC8700C0 ctl 0xDC8700CA bmdma 0xDC870008 irq 193
[17179576.488000] ata1: dev 0 cfg 00:045a 49:2f00 82:346b 83:7f09 84:6063 85:3469 86:bf09 87:6063 88:203f 93:0000
[17179576.488000] ata1: dev 0 ATA-7, max UDMA/100, 117210240 sectors: LBA48
[17179576.488000] sata_get_dev_handle: SATA dev addr=0x120000, handle=0xdb7d03a0
[17179576.520000] ata1: dev 0 configured for UDMA/100
[17179576.520000] sata_get_dev_handle: SATA dev addr=0x120000, handle=0xdb7d03a0
[17179576.556000] scsi0 : sata_sil
[17179576.760000] ata2: no device found (phy stat 00000000)
[17179576.760000] scsi1 : sata_sil
[17179576.760000]   Vendor: ATA       Model: FUJITSU MHV2060B  Rev: 0000
[17179576.760000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179576.768000] Driver 'sd' needs updating - please use bus_type methods
[17179576.768000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[17179576.768000] SCSI device sda: drive cache: write back
[17179576.772000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[17179576.772000] SCSI device sda: drive cache: write back
[17179576.772000]  sda: sda1 sda2 < sda5 sda6 >
[17179576.896000] sd 0:0:0:0: Attached scsi disk sda
[17179577.200000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[17179577.200000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 201
[17179577.200000] ATIIXP: chipset revision 128
[17179577.200000] ATIIXP: not 100% native mode: will probe irqs later
[17179577.200000]     ide0: BM-DMA at 0x8460-0x8467, BIOS settings: hda:pio, hdb:pio
[17179577.200000]     ide1: BM-DMA at 0x8468-0x846f, BIOS settings: hdc:DMA, hdd:pio
[17179577.200000] Probing IDE interface ide0...
[17179577.768000] Probing IDE interface ide1...
[17179578.504000] hdc: MATSHITADVD-RAM UJ-841S, ATAPI CD/DVD-ROM drive
[17179578.840000] ide1 at 0x170-0x177,0x376 on irq 15
[17179578.852000] hdc: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179578.852000] Uniform CD-ROM driver Revision: 3.20
[17179578.924000] usbcore: registered new driver usbfs
[17179578.924000] usbcore: registered new driver hub
[17179578.924000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179578.924000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 209
[17179578.924000] ohci_hcd 0000:00:13.0: OHCI Host Controller
[17179579.276000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[17179579.276000] ohci_hcd 0000:00:13.0: irq 209, io mem 0xc0005000
[17179579.300000] ieee1394: Initialized config rom entry `ip1394'
[17179579.332000] hub 1-0:1.0: USB hub found
[17179579.332000] hub 1-0:1.0: 4 ports detected
[17179579.436000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 209
[17179579.436000] ohci_hcd 0000:00:13.1: OHCI Host Controller
[17179579.772000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[17179579.772000] ohci_hcd 0000:00:13.1: irq 209, io mem 0xc0006000
[17179579.828000] hub 2-0:1.0: USB hub found
[17179579.828000] hub 2-0:1.0: 4 ports detected
[17179579.932000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[17179579.932000] ACPI: PCI Interrupt 0000:02:0a.0[A] -> GSI 22 (level, low) -> IRQ 193
[17179579.940000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 209
[17179579.940000] ehci_hcd 0000:00:13.2: EHCI Host Controller
[17179579.940000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[17179579.940000] ehci_hcd 0000:00:13.2: irq 209, io mem 0xc0007000
[17179579.940000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179579.940000] hub 3-0:1.0: USB hub found
[17179579.940000] hub 3-0:1.0: 8 ports detected
[17179579.980000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[193]  MMIO=[c0215800-c0215fff]  Max Packet=[2048]
[17179580.060000] Probing IDE interface ide0...
[17179580.648000] Attempting manual resume
[17179580.664000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179580.664000] EXT3-fs: write access will be enabled during recovery.
[17179580.740000] usb 2-2: new low speed USB device using ohci_hcd and address 2
[17179580.964000] usbcore: registered new driver hiddev
[17179580.972000] input: Acrox USB & PS/2 Mouse as /class/input/input1
[17179580.972000] input: USB HID v1.10 Mouse [Acrox USB & PS/2 Mouse] on usb-0000:00:13.1-2
[17179580.972000] usbcore: registered new driver usbhid
[17179580.972000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179581.252000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00080da0d13285b9]
[17179585.036000] EXT3-fs: recovery complete.
[17179585.036000] kjournald starting.  Commit interval 5 seconds
[17179585.036000] EXT3-fs: mounted filesystem with ordered data mode.
[17179596.084000] ts: Compaq touchscreen protocol output
[17179596.180000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179597.744000] ath_hal: module license 'Proprietary' taints kernel.
[17179597.744000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
[17179597.784000] Linux agpgart interface v0.101 (c) Dave Jones
[17179597.948000] wlan: 0.8.6.0 (EXPERIMENTAL)
[17179597.948000] ath_rate_sample: 1.2
[17179597.956000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
[17179597.956000] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 20 (level, low) -> IRQ 217
[17179598.712000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179598.772000] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 201
[17179598.860000] 8139too Fast Ethernet driver 0.9.27
[17179598.876000] Build date: Jul 10 2006
[17179598.876000] Debugging version (IEEE80211)
[17179598.876000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[17179598.876000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179598.876000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
[17179598.876000] ath0: mac 7.8 phy 4.5 radio 5.6
[17179598.876000] ath0: Use hw queue 1 for WME_AC_BE traffic
[17179598.876000] ath0: Use hw queue 0 for WME_AC_BK traffic
[17179598.876000] ath0: Use hw queue 2 for WME_AC_VI traffic
[17179598.876000] ath0: Use hw queue 3 for WME_AC_VO traffic
[17179598.876000] ath0: Use hw queue 8 for CAB traffic
[17179598.876000] ath0: Use hw queue 9 for beacons
[17179598.876000] Debugging version (ATH)
[17179598.876000] ath0: Atheros 5212: mem=0xc0200000, irq=217
[17179599.256000] input: PC Speaker as /class/input/input2
[17179599.460000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0
[17179599.460000] synaptics: Toshiba Satellite Pro A100 detected, limiting rate to 40pps.
[17179599.476000] hda_codec: Unknown model for ALC861, trying auto-probe from BIOS...
[17179599.496000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[17179599.700000] ACPI: PCI Interrupt 0000:02:06.0[A] -> GSI 23 (level, low) -> IRQ 185
[17179599.700000] Yenta: CardBus bridge found at 0000:02:06.0 [1179:ff10]
[17179599.700000] Yenta: Enabling burst memory read transactions
[17179599.700000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179599.700000] Yenta: Routing CardBus interrupts to PCI
[17179599.700000] Yenta TI: socket 0000:02:06.0, mfunc 0x01111122, devctl 0x64
[17179599.932000] Yenta: ISA IRQ mask 0x0ef8, PCI irq 185
[17179599.932000] Socket status: 30000006
[17179599.932000] Yenta: Raising subordinate bus# of parent bus (#02) from #04 to #06
[17179599.932000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[17179599.932000] cs: IO port probe 0xa000-0xafff: clean.
[17179599.932000] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xc02fffff
[17179599.932000] pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x21ffffff
[17179599.940000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179599.940000] ACPI: PCI Interrupt 0000:02:07.0[A] -> GSI 20 (level, low) -> IRQ 217
[17179599.940000] eth0: RealTek RTL8139 at 0xdc99c000, 00:a0:d1:32:85:b9, IRQ 217
[17179599.940000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179599.948000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179600.096000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179600.288000] cs: IO port probe 0x100-0x3af: excluding 0x1f0-0x1f7
[17179600.288000] cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x4d0-0x4d7
[17179600.292000] cs: IO port probe 0x820-0x8ff: excluding 0x878-0x87f
[17179600.292000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[17179600.292000] cs: IO port probe 0xa00-0xaff: clean.
[17179600.700000] lp: driver loaded but no devices found
[17179600.740000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[17179600.740000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179600.740000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179600.812000] Adding 524432k swap on /dev/sda6.  Priority:-1 extents:1 across:524432k
[17179600.968000] EXT3 FS on sda5, internal journal
[17179601.152000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179601.152000] md: bitmap version 4.39
[17179601.188000] NET: Registered protocol family 17
[17179601.620000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179602.348000] cdrom: open failed.
[17179602.864000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[17179602.968000] NTFS volume version 3.1.
[17179605.664000] NET: Registered protocol family 10
[17179605.664000] lo: Disabled Privacy Extensions
[17179605.664000] IPv6 over IPv4 tunneling driver
[17179609.300000] ACPI: AC Adapter [ADP0] (on-line)
[17179609.440000] ACPI: Battery Slot [BAT0] (battery present)
[17179609.524000] ACPI: Power Button (FF) [PWRF]
[17179609.524000] ACPI: Power Button (CM) [PWRB]
[17179609.524000] ACPI: Lid Switch [LID]
[17179609.644000] ibm_acpi: ec object not found
[17179609.676000] pcc_acpi: loading...
[17179615.976000] [fglrx] Maximum main memory to use for locked dma buffers: 371 MBytes.
[17179615.976000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
[17179616.004000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 225
[17179616.344000] ppdev: user-space parallel port driver
[17179616.536000] eth0: no IPv6 routers present
[17179617.928000] [fglrx] total      GART = 67108864
[17179617.928000] [fglrx] free       GART = 51118080
[17179617.928000] [fglrx] max single GART = 51118080
[17179617.928000] [fglrx] total      LFB  = 60846080
[17179617.928000] apm: BIOS not found.
[17179617.928000] [fglrx] free       LFB  = 52654080
[17179617.928000] [fglrx] max single LFB  = 52654080
[17179617.928000] [fglrx] total      Inv  = 0
[17179617.928000] [fglrx] free       Inv  = 0
[17179617.932000] [fglrx] max single Inv  = 0
[17179617.932000] [fglrx] total      TIM  = 0
[17179621.656000] Bluetooth: Core ver 2.8
[17179621.656000] NET: Registered protocol family 31
[17179621.656000] Bluetooth: HCI device and connection manager initialized
[17179621.656000] Bluetooth: HCI socket layer initialized
[17179621.672000] Bluetooth: L2CAP ver 2.8
[17179621.672000] Bluetooth: L2CAP socket layer initialized
[17179621.712000] Bluetooth: RFCOMM socket layer initialized
[17179621.712000] Bluetooth: RFCOMM TTY layer initialized
[17179621.712000] Bluetooth: RFCOMM ver 1.7
[17179626.572000] hda-intel: Invalid position buffer, using LPIB read method instead.
[17179784.768000]     ACPI-0307: *** Error: No installed handler for fixed event [00000000]
[17180384.668000]     ACPI-0307: *** Error: No installed handler for fixed event [00000000]

```

---

### Post by Woei on 2006-08-25
> **shibby said:**
> ok sorry, 
my laptop is a toshiba and my dmesg is following :

Well, the output looks rather fine apart from one thing.

There's an ACPI error message. ACPI is a standard for controlling power consumption of various devices in a computer. It's also responsible for some interrupt handling. Interrupts are triggered by devices such as an USB mouse and keyboard amongst other. I'm not familiar with this specific error message though.

Do you happen to know the exact components of your laptop. i.e., the chipset used ? Also, does this happen after you hibernate or suspend your laptop ? That's requently the cause for USB devices to stop functioning.

---

### Post by shibby on 2006-08-25
my chipset is an ATI (:s), but i cant find exactly what chipset he is. My laptop is an A100 pro. This doesn't happen after hibernate, Sometimes usb stop 3 minutes after the reboot but now I am using my mouse for 30 minutes without problem ( but i know that will happen ).
I will take care about when they stop.

---

