---
title: "Toshiba Wifi problem"
date: 2006-07-25
forum: Hardware &amp; Laptops
---

### Post by dwaldie on 2006-07-25
Hello,
     I need your help.  I bought a laptop two nights ago and installed ubuntu on it as soon as I could.  Everything worked right 'out of the box' but the wifi.  I have been searching the forums and google and trying the advise on everything that I thought would help, but to no success.
     My laptop is a Toshiba A110 and the built in Wifi card is an Atheros card.  I do not know which model, and I am not sure how to tell.  If there is a way to get this working I could really use some help.

Thank you,
David Waldie

---

### Post by rbalfour on 2006-07-25
Post the output of the following command.

$ sudo dmesg

---

### Post by dwaldie on 2006-07-25
here you go...

[17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Mon Jul 17 19:52:53 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000dc000 - 00000000000e0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001be80000 (usable)
[17179569.184000]  BIOS-e820: 000000001be80000 - 000000001be93000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001be93000 - 000000001bf00000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001bf00000 - 000000001c000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 446MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f6a90
[17179569.184000] On node 0 totalpages: 114304
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 110208 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI present.
[17179569.184000] ATI board detected. Disabling timer routing over 8254.
[17179569.184000] ACPI: RSDP (v000 TOSCPL                                ) @ 0x000f6a00
[17179569.184000] ACPI: RSDT (v001 TOSCPL   RSDT   0x06040000  LTP 0x00000000) @ 0x1be8d997
[17179569.184000] ACPI: FADT (v001 TOSCPL SB450    0x06040000 ATI  0x000f4240) @ 0x1be92f00
[17179569.184000] ACPI: MADT (v001 PTLTD         APIC   0x06040000  LTP 0x00000000) @ 0x1be92f74
[17179569.184000] ACPI: MCFG (v001 PTLTD    MCFG   0x06040000  LTP 0x00000000) @ 0x1be92fc4
[17179569.184000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20050228) @ 0x1be8df04
[17179569.184000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20050228) @ 0x1be8d9cf
[17179569.184000] ACPI: DSDT (v001 TOSCPL    SB450 0x06040000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x8008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:14 APIC version 20
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
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
[17179569.184000] Detected 1467.021 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.088000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.088000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179572.100000] Memory: 442668k/457216k available (1976k kernel code, 13896k reserved, 606k data, 288k init, 0k highmem)
[17179572.100000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.180000] Calibrating delay using timer specific routine.. 2939.69 BogoMIPS (lpj=5879394)
[17179572.180000] Security Framework v1.0.0 initialized
[17179572.180000] SELinux:  Disabled at boot.
[17179572.180000] Mount-cache hash table entries: 512
[17179572.180000] CPU: After generic identify, caps: afe9fbff 00000000 00000000 00000000 0000c109 00000000 00000000
[17179572.180000] CPU: After vendor identify, caps: afe9fbff 00000000 00000000 00000000 0000c109 00000000 00000000
[17179572.180000] monitor/mwait feature present.
[17179572.180000] using mwait in idle threads.
[17179572.180000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179572.180000] CPU: L2 cache: 1024K
[17179572.180000] CPU: After all inits, caps: afe9fbff 00000000 00000000 00000040 0000c109 00000000 00000000
[17179572.180000] mtrr: v2.0 (20020519)
[17179572.180000] CPU: Intel(R) Celeron(R) M CPU        410  @ 1.46GHz stepping 08
[17179572.180000] Enabling fast FPU save and restore... done.
[17179572.180000] Enabling unmasked SIMD FPU exception support... done.
[17179572.180000] Checking 'hlt' instruction... OK.
[17179572.196000] checking if image is initramfs... it is
[17179572.924000] Freeing initrd memory: 6617k freed
[17179572.956000] ACPI: Looking for DSDT ... not found!
[17179573.608000] ENABLING IO-APIC IRQs
[17179573.608000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179573.752000] NET: Registered protocol family 16
[17179573.752000] EISA bus registered
[17179573.752000] ACPI: bus type pci registered
[17179573.752000] PCI: PCI BIOS revision 2.10 entry at 0xfd5b4, last bus=14
[17179573.752000] PCI: Using MMCONFIG
[17179573.756000] ACPI: Subsystem revision 20051216
[17179573.768000] ACPI: Interpreter enabled
[17179573.768000] ACPI: Using IOAPIC for interrupt routing
[17179573.768000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.768000] PCI: Probing PCI hardware (bus 00)
[17179573.792000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
[17179573.792000] Boot video device is 0000:01:05.0
[17179573.792000] PCI: Transparent bridge - 0000:00:14.4
[17179573.792000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.796000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[17179573.796000] ACPI: Embedded Controller [EC0] (gpe 19) interrupt mode.
[17179573.796000] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[17179573.796000] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[17179573.796000] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[17179573.796000] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[17179573.800000] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[17179573.800000] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[17179573.800000] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[17179573.800000] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[17179573.800000] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7) *0, disabled.
[17179573.844000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[17179573.844000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[17179573.844000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.844000] pnp: PnP ACPI init
[17179573.868000] pnp: PnP ACPI: found 10 devices
[17179573.868000] PnPBIOS: Disabled by ACPI PNP
[17179573.868000] PCI: Using ACPI for IRQ routing
[17179573.868000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.904000] pnp: 00:07: ioport range 0x1080-0x1080 has been reserved
[17179573.904000] pnp: 00:07: ioport range 0x220-0x22f has been reserved
[17179573.904000] pnp: 00:07: ioport range 0x40b-0x40b has been reserved
[17179573.904000] pnp: 00:07: ioport range 0x4d0-0x4d1 has been reserved
[17179573.904000] PCI: Bridge: 0000:00:01.0
[17179573.904000]   IO window: 9000-9fff
[17179573.904000]   MEM window: d0000000-d00fffff
[17179573.904000]   PREFETCH window: d8000000-dfffffff
[17179573.904000] PCI: Bridge: 0000:00:06.0
[17179573.904000]   IO window: disabled.
[17179573.904000]   MEM window: d0100000-d01fffff
[17179573.904000]   PREFETCH window: disabled.
[17179573.904000] PCI: Bus 10, cardbus bridge: 0000:09:04.0
[17179573.904000]   IO window: 0000a800-0000a8ff
[17179573.904000]   IO window: 0000ac00-0000acff
[17179573.904000]   PREFETCH window: 20000000-21ffffff
[17179573.904000]   MEM window: 24000000-25ffffff
[17179573.904000] PCI: Bridge: 0000:00:14.4
[17179573.904000]   IO window: a000-afff
[17179573.904000]   MEM window: d0200000-d02fffff
[17179573.904000]   PREFETCH window: 20000000-21ffffff
[17179573.904000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[17179573.904000] ACPI: PCI Interrupt 0000:09:04.0[A] -> GSI 17 (level, low) -> IRQ 185
[17179573.904000] audit: initializing netlink socket (disabled)
[17179573.904000] audit(1153812214.904:1): initialized
[17179573.904000] VFS: Disk quotas dquot_6.5.1
[17179573.904000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.904000] Initializing Cryptographic API
[17179573.904000] io scheduler noop registered
[17179573.904000] io scheduler anticipatory registered
[17179573.904000] io scheduler deadline registered
[17179573.904000] io scheduler cfq registered
[17179573.904000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[17179573.904000] pcie_portdrv_probe->Dev[5a38:1002] has invalid IRQ. Check vendor BIOS
[17179573.904000] assign_interrupt_mode Found MSI capability
[17179573.904000] Allocate Port Service[pcie00]
[17179573.904000] Allocate Port Service[pcie01]
[17179573.904000] Allocate Port Service[pcie03]
[17179573.904000] isapnp: Scanning for PnP cards...
[17179574.260000] isapnp: No Plug & Play device found
[17179574.280000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[17179574.280000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179574.280000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179574.280000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179574.280000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179574.280000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179574.280000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.280000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179574.280000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179574.280000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.280000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179574.280000] mice: PS/2 mouse device common for all mice
[17179574.280000] EISA: Probing bus 0 at eisa.0
[17179574.280000] Cannot allocate resource for EISA slot 1
[17179574.280000] Cannot allocate resource for EISA slot 8
[17179574.280000] EISA: Detected 0 cards.
[17179574.280000] NET: Registered protocol family 2
[17179574.320000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179574.320000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[17179574.320000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[17179574.320000] TCP: Hash tables configured (established 16384 bind 16384)
[17179574.320000] TCP reno registered
[17179574.320000] TCP bic registered
[17179574.320000] NET: Registered protocol family 1
[17179574.320000] NET: Registered protocol family 8
[17179574.320000] NET: Registered protocol family 20
[17179574.320000] Using IPI Shortcut mode
[17179574.320000] ACPI wakeup devices:
[17179574.320000]  PB2  PB3  PB4  PB6  PB7 OHC1 OHC2 EHCI  P2P ELAN MODM AZLA
[17179574.320000] ACPI: (supports S0 S3 S4 S5)
[17179574.320000] Freeing unused kernel memory: 288k freed
[17179574.368000] vga16fb: initializing
[17179574.368000] vga16fb: mapped to 0xc00a0000
[17179574.464000] Console: switching to colour frame buffer device 80x25
[17179574.464000] fb0: VGA16 VGA frame buffer device
[17179574.884000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179575.480000] Capability LSM initialized
[17179575.616000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179576.072000] SCSI subsystem initialized
[17179576.076000] ACPI: bus type scsi registered
[17179576.076000] libata version 1.20 loaded.
[17179576.076000] sata_sil 0000:00:12.0: version 0.9
[17179576.076000] PCI: Enabling device 0000:00:12.0 (0005 -> 0007)
[17179576.076000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 209
[17179576.076000] ata1: SATA max UDMA/100 cmd 0xDC874080 ctl 0xDC87408A bmdma 0xDC874000 irq 209
[17179576.076000] ata2: SATA max UDMA/100 cmd 0xDC8740C0 ctl 0xDC8740CA bmdma 0xDC874008 irq 209
[17179576.444000] ata1: dev 0 cfg 00:045a 49:0f00 82:746b 83:7f69 84:6063 85:f469 86:3d49 87:6063 88:203f 93:0000
[17179576.444000] ata1: dev 0 ATA-7, max UDMA/100, 117210240 sectors: LBA48
[17179576.444000] sata_get_dev_handle: SATA dev addr=0x120000, handle=0xdbe69b60
[17179576.488000] ata1: dev 0 configured for UDMA/100
[17179576.488000] sata_get_dev_handle: SATA dev addr=0x120000, handle=0xdbe69b60
[17179576.532000] scsi0 : sata_sil
[17179576.736000] ata2: no device found (phy stat 00000000)
[17179576.736000] scsi1 : sata_sil
[17179576.736000]   Vendor: ATA       Model: HTS541060G9SA00   Rev: MB3O
[17179576.736000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179576.744000] Driver 'sd' needs updating - please use bus_type methods
[17179576.744000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[17179576.744000] SCSI device sda: drive cache: write back
[17179576.744000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[17179576.744000] SCSI device sda: drive cache: write back
[17179576.744000]  sda: sda1 sda2 < sda5 sda6 >
[17179576.804000] sd 0:0:0:0: Attached scsi disk sda
[17179576.988000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[17179576.988000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 217
[17179576.988000] ATIIXP: chipset revision 128
[17179576.988000] ATIIXP: not 100% native mode: will probe irqs later
[17179576.988000]     ide1: BM-DMA at 0x8468-0x846f, BIOS settings: hdc:DMA, hdd:pio
[17179576.988000] Probing IDE interface ide1...
[17179577.724000] hdc: HL-DT-ST DVDRAM GMA-4082N, ATAPI CD/DVD-ROM drive
[17179578.060000] ide1 at 0x170-0x177,0x376 on irq 15
[17179578.072000] hdc: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179578.072000] Uniform CD-ROM driver Revision: 3.20
[17179578.160000] usbcore: registered new driver usbfs
[17179578.160000] usbcore: registered new driver hub
[17179578.160000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179578.160000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 225
[17179578.160000] ohci_hcd 0000:00:13.0: OHCI Host Controller
[17179578.160000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[17179578.160000] ohci_hcd 0000:00:13.0: irq 225, io mem 0xd0504000
[17179578.200000] ieee1394: Initialized config rom entry `ip1394'
[17179578.224000] hub 1-0:1.0: USB hub found
[17179578.224000] hub 1-0:1.0: 4 ports detected
[17179578.328000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 225
[17179578.328000] ohci_hcd 0000:00:13.1: OHCI Host Controller
[17179578.328000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[17179578.328000] ohci_hcd 0000:00:13.1: irq 225, io mem 0xd0505000
[17179578.332000] hub 2-0:1.0: USB hub found
[17179578.332000] hub 2-0:1.0: 4 ports detected
[17179578.436000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[17179578.436000] ACPI: PCI Interrupt 0000:09:00.0[A] -> GSI 16 (level, low) -> IRQ 217
[17179578.468000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 225
[17179578.468000] ehci_hcd 0000:00:13.2: EHCI Host Controller
[17179578.468000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[17179578.468000] ehci_hcd 0000:00:13.2: irq 225, io mem 0xd0506000
[17179578.468000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179578.468000] hub 3-0:1.0: USB hub found
[17179578.468000] hub 3-0:1.0: 8 ports detected
[17179578.488000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[217]  MMIO=[d0200000-d02007ff]  Max Packet=[2048]
[17179578.584000] Probing IDE interface ide0...
[17179579.164000] Attempting manual resume
[17179579.764000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f679a400494]
[17179589.916000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179590.872000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179590.876000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179591.076000] Linux agpgart interface v0.101 (c) Dave Jones
[17179591.296000] wlan: 0.8.4.2 (svn r1692)
[17179591.368000] ath_hal: module license 'Proprietary' taints kernel.
[17179591.368000] ath_hal: 0.9.17.2 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[17179591.432000] ath_rate_sample: 1.2 (svn r1692)
[17179591.456000] ath_pci: 0.9.4.5 (svn r1692)
[17179591.456000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 233
[17179591.456000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[17179591.456000] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[17179591.456000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[17179591.484000] wlan: 0.8.4.2 (svn 2006-07-10)
[17179591.488000] new_ath_rate_sample: Unknown symbol new_ath_hal_computetxtime
[17179591.492000] new_ath_pci: Unknown symbol new_ath_rate_node_cleanup
[17179591.492000] new_ath_pci: Unknown symbol new_ath_hal_computetxtime
[17179591.492000] new_ath_pci: Unknown symbol new_ath_hal_probe
[17179591.492000] new_ath_pci: Unknown symbol _new_ath_hal_attach
[17179591.492000] new_ath_pci: Unknown symbol new_ath_rate_setupxtxdesc
[17179591.492000] new_ath_pci: Unknown symbol new_ath_hal_detach
[17179591.492000] new_ath_pci: Unknown symbol new_ath_rate_newassoc
[17179591.492000] new_ath_pci: Unknown symbol new_ath_rate_tx_complete
[17179591.492000] new_ath_pci: Unknown symbol new_ath_hal_init_channels
[17179591.492000] new_ath_pci: Unknown symbol new_ath_hal_getwirelessmodes
[17179591.492000] new_ath_pci: Unknown symbol new_ath_rate_node_init
[17179591.492000] new_ath_pci: Unknown symbol new_ath_rate_attach
[17179591.492000] new_ath_pci: Unknown symbol new_ath_rate_detach
[17179591.492000] new_ath_pci: Unknown symbol new_ath_rate_findrate
[17179591.492000] new_ath_pci: Unknown symbol new_ath_rate_newstate
[17179591.492000] new_ath_pci: Unknown symbol new_ath_hal_mhz2ieee
[17179591.580000] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 217
[17179591.936000] input: PS/2 Mouse as /class/input/input1
[17179591.956000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input2
[17179592.188000] ts: Compaq touchscreen protocol output
[17179592.280000] Real Time Clock Driver v1.12
[17179592.280000] input: PC Speaker as /class/input/input3
[17179592.380000] 8139too Fast Ethernet driver 0.9.27
[17179593.040000] hda_codec: Unknown model for ALC861, trying auto-probe from BIOS...
[17179593.232000] ACPI: PCI Interrupt 0000:09:04.0[A] -> GSI 17 (level, low) -> IRQ 185
[17179593.232000] Yenta: CardBus bridge found at 0000:09:04.0 [1179:ff00]
[17179593.232000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179593.232000] Yenta: Routing CardBus interrupts to PCI
[17179593.232000] Yenta TI: socket 0000:09:04.0, mfunc 0x00111c12, devctl 0x44
[17179593.464000] Yenta: ISA IRQ mask 0x0ef8, PCI irq 185
[17179593.464000] Socket status: 30000006
[17179593.464000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[17179593.464000] cs: IO port probe 0xa000-0xafff: clean.
[17179593.464000] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xd02fffff
[17179593.464000] pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x21ffffff
[17179593.472000] ACPI: PCI Interrupt 0000:09:06.0[A] -> GSI 22 (level, low) -> IRQ 209
[17179593.472000] eth0: RealTek RTL8139 at 0xdcb50800, 00:16:d4:25:6e:6a, IRQ 209
[17179593.472000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179593.480000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179593.608000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179593.816000] cs: IO port probe 0x100-0x3af: clean.
[17179593.820000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179593.820000] cs: IO port probe 0x820-0x8ff: excluding 0x878-0x87f
[17179593.820000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[17179593.824000] cs: IO port probe 0xa00-0xaff: clean.
[17179594.192000] lp: driver loaded but no devices found
[17179594.236000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[17179594.236000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179594.236000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179594.308000] Adding 2040212k swap on /dev/sda6.  Priority:-1 extents:1 across:2040212k
[17179594.656000] NET: Registered protocol family 17
[17179594.720000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179594.720000] md: bitmap version 4.39
[17179595.080000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179595.512000] cdrom: open failed.
[17179595.796000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[17179595.852000] NTFS volume version 3.1.
[17179598.604000] NET: Registered protocol family 10
[17179598.604000] lo: Disabled Privacy Extensions
[17179598.604000] IPv6 over IPv4 tunneling driver
[17179601.668000] ACPI: AC Adapter [ACAD] (on-line)
[17179601.732000] ACPI: Battery Slot [BAT1] (battery present)
[17179601.816000] ACPI: Power Button (FF) [PWRF]
[17179601.816000] ACPI: Lid Switch [LID]
[17179601.816000] ACPI: Power Button (CM) [PWRB]
[17179601.936000] ibm_acpi: ec object not found
[17179601.968000] pcc_acpi: loading...
[17179602.068000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179606.684000] [fglrx] Maximum main memory to use for locked dma buffers: 372 MBytes.
[17179606.688000] [fglrx] module loaded - fglrx 8.26.18 [Jun 22 2006] on minor 0
[17179606.700000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 185
[17179606.768000] ppdev: user-space parallel port driver
[17179608.504000] [fglrx] total      GART = 134217728
[17179608.508000] [fglrx] free       GART = 118226944
[17179608.508000] [fglrx] max single GART = 118226944
[17179608.508000] [fglrx] total      LFB  = 60780544
[17179608.508000] [fglrx] free       LFB  = 52588544
[17179608.508000] [fglrx] max single LFB  = 52588544
[17179608.508000] [fglrx] total      Inv  = 0
[17179608.508000] [fglrx] free       Inv  = 0
[17179608.508000] [fglrx] max single Inv  = 0
[17179608.508000] [fglrx] total      TIM  = 0
[17179609.076000] apm: BIOS not found.
[17179609.548000] eth0: no IPv6 routers present
[17179613.412000] Bluetooth: Core ver 2.8
[17179613.412000] NET: Registered protocol family 31
[17179613.412000] Bluetooth: HCI device and connection manager initialized
[17179613.412000] Bluetooth: HCI socket layer initialized
[17179613.440000] Bluetooth: L2CAP ver 2.8
[17179613.440000] Bluetooth: L2CAP socket layer initialized
[17179613.460000] Bluetooth: RFCOMM socket layer initialized
[17179613.460000] Bluetooth: RFCOMM TTY layer initialized
[17179613.460000] Bluetooth: RFCOMM ver 1.7
[17179615.252000] hda-intel: Invalid position buffer, using LPIB read method instead.
[17179630.164000] eth0: no IPv6 routers present
[17179636.616000] psmouse.c: GlidePoint at isa0060/serio4/input0 lost synchronization, throwing 1 bytes away.
[17182115.924000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17182116.464000] ndiswrapper (wrapper_init:173): loadndiswrapper failed (1792); check system log for messages from 'loadndisdriver'
[17182116.464000] ndiswrapper (wrapper_init:180): ndiswrapper: initialization failed
[17182171.664000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17182171.668000] ndiswrapper (wrapper_init:173): loadndiswrapper failed (1792); check system log for messages from 'loadndisdriver'
[17182171.668000] ndiswrapper (wrapper_init:180): ndiswrapper: initialization failed
[17182240.908000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17182240.908000] ndiswrapper (wrapper_init:173): loadndiswrapper failed (1792); check system log for messages from 'loadndisdriver'
[17182240.908000] ndiswrapper (wrapper_init:180): ndiswrapper: initialization failed
[17182325.584000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17182325.588000] ndiswrapper (wrapper_init:173): loadndiswrapper failed (1792); check system log for messages from 'loadndisdriver'
[17182325.588000] ndiswrapper (wrapper_init:180): ndiswrapper: initialization failed

---

### Post by rbalfour on 2006-07-25
Okay, I see you tried with NDISWrapper. Did you tried to install the latest MadWiFi drivers?

First, let's remove the NDISwrapper and repost the dmesg.

---

### Post by dwaldie on 2006-07-25
Thank you for taking the time to help.  I did try MadWifi but to no success.

here is what you asked for

[17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Mon Jul 17 19:52:53 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009dc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009dc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000dc000 - 00000000000e0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001be80000 (usable)
[17179569.184000]  BIOS-e820: 000000001be80000 - 000000001be93000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001be93000 - 000000001bf00000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001bf00000 - 000000001c000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 446MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f6a90
[17179569.184000] On node 0 totalpages: 114304
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 110208 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI present.
[17179569.184000] ATI board detected. Disabling timer routing over 8254.
[17179569.184000] ACPI: RSDP (v000 TOSCPL                                ) @ 0x000f6a00
[17179569.184000] ACPI: RSDT (v001 TOSCPL   RSDT   0x06040000  LTP 0x00000000) @ 0x1be8d997
[17179569.184000] ACPI: FADT (v001 TOSCPL SB450    0x06040000 ATI  0x000f4240) @ 0x1be92f00
[17179569.184000] ACPI: MADT (v001 PTLTD         APIC   0x06040000  LTP 0x00000000) @ 0x1be92f74
[17179569.184000] ACPI: MCFG (v001 PTLTD    MCFG   0x06040000  LTP 0x00000000) @ 0x1be92fc4
[17179569.184000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20050228) @ 0x1be8df04
[17179569.184000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20050228) @ 0x1be8d9cf
[17179569.184000] ACPI: DSDT (v001 TOSCPL    SB450 0x06040000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x8008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:14 APIC version 20
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
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
[17179569.184000] Detected 1466.900 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179570.724000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179570.724000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.740000] Memory: 442668k/457216k available (1976k kernel code, 13896k reserved, 606k data, 288k init, 0k highmem)
[17179570.740000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179570.820000] Calibrating delay using timer specific routine.. 2939.68 BogoMIPS (lpj=5879376)
[17179570.820000] Security Framework v1.0.0 initialized
[17179570.820000] SELinux:  Disabled at boot.
[17179570.820000] Mount-cache hash table entries: 512
[17179570.820000] CPU: After generic identify, caps: afe9fbff 00000000 00000000 00000000 0000c109 00000000 00000000
[17179570.820000] CPU: After vendor identify, caps: afe9fbff 00000000 00000000 00000000 0000c109 00000000 00000000
[17179570.820000] monitor/mwait feature present.
[17179570.820000] using mwait in idle threads.
[17179570.820000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179570.820000] CPU: L2 cache: 1024K
[17179570.820000] CPU: After all inits, caps: afe9fbff 00000000 00000000 00000040 0000c109 00000000 00000000
[17179570.820000] mtrr: v2.0 (20020519)
[17179570.820000] CPU: Intel(R) Celeron(R) M CPU        410  @ 1.46GHz stepping 08
[17179570.820000] Enabling fast FPU save and restore... done.
[17179570.820000] Enabling unmasked SIMD FPU exception support... done.
[17179570.820000] Checking 'hlt' instruction... OK.
[17179570.836000] checking if image is initramfs... it is
[17179571.564000] Freeing initrd memory: 6617k freed
[17179571.596000] ACPI: Looking for DSDT ... not found!
[17179572.248000] ENABLING IO-APIC IRQs
[17179572.248000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179572.396000] NET: Registered protocol family 16
[17179572.396000] EISA bus registered
[17179572.396000] ACPI: bus type pci registered
[17179572.396000] PCI: PCI BIOS revision 2.10 entry at 0xfd5b4, last bus=14
[17179572.396000] PCI: Using MMCONFIG
[17179572.400000] ACPI: Subsystem revision 20051216
[17179572.416000] ACPI: Interpreter enabled
[17179572.416000] ACPI: Using IOAPIC for interrupt routing
[17179572.416000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179572.416000] PCI: Probing PCI hardware (bus 00)
[17179572.436000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:14.1
[17179572.436000] Boot video device is 0000:01:05.0
[17179572.436000] PCI: Transparent bridge - 0000:00:14.4
[17179572.436000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179572.440000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB6_._PRT]
[17179572.440000] ACPI: Embedded Controller [EC0] (gpe 19) interrupt mode.
[17179572.440000] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[17179572.440000] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[17179572.440000] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[17179572.440000] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[17179572.444000] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[17179572.444000] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[17179572.444000] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[17179572.444000] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[17179572.444000] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7) *0, disabled.
[17179572.484000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[17179572.484000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[17179572.484000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179572.484000] pnp: PnP ACPI init
[17179572.508000] pnp: PnP ACPI: found 10 devices
[17179572.508000] PnPBIOS: Disabled by ACPI PNP
[17179572.508000] PCI: Using ACPI for IRQ routing
[17179572.508000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.544000] pnp: 00:07: ioport range 0x1080-0x1080 has been reserved
[17179572.544000] pnp: 00:07: ioport range 0x220-0x22f has been reserved
[17179572.544000] pnp: 00:07: ioport range 0x40b-0x40b has been reserved
[17179572.544000] pnp: 00:07: ioport range 0x4d0-0x4d1 has been reserved
[17179572.544000] PCI: Bridge: 0000:00:01.0
[17179572.544000]   IO window: 9000-9fff
[17179572.544000]   MEM window: d0000000-d00fffff
[17179572.544000]   PREFETCH window: d8000000-dfffffff
[17179572.544000] PCI: Bridge: 0000:00:06.0
[17179572.544000]   IO window: disabled.
[17179572.544000]   MEM window: d0100000-d01fffff
[17179572.544000]   PREFETCH window: disabled.
[17179572.544000] PCI: Bus 10, cardbus bridge: 0000:09:04.0
[17179572.544000]   IO window: 0000a800-0000a8ff
[17179572.544000]   IO window: 0000ac00-0000acff
[17179572.544000]   PREFETCH window: 20000000-21ffffff
[17179572.544000]   MEM window: 24000000-25ffffff
[17179572.544000] PCI: Bridge: 0000:00:14.4
[17179572.544000]   IO window: a000-afff
[17179572.544000]   MEM window: d0200000-d02fffff
[17179572.544000]   PREFETCH window: 20000000-21ffffff
[17179572.544000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[17179572.544000] ACPI: PCI Interrupt 0000:09:04.0[A] -> GSI 17 (level, low) -> IRQ 185
[17179572.544000] audit: initializing netlink socket (disabled)
[17179572.544000] audit(1153825952.544:1): initialized
[17179572.544000] VFS: Disk quotas dquot_6.5.1
[17179572.544000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.544000] Initializing Cryptographic API
[17179572.544000] io scheduler noop registered
[17179572.544000] io scheduler anticipatory registered
[17179572.544000] io scheduler deadline registered
[17179572.544000] io scheduler cfq registered
[17179572.544000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[17179572.544000] pcie_portdrv_probe->Dev[5a38:1002] has invalid IRQ. Check vendor BIOS
[17179572.544000] assign_interrupt_mode Found MSI capability
[17179572.544000] Allocate Port Service[pcie00]
[17179572.544000] Allocate Port Service[pcie01]
[17179572.544000] Allocate Port Service[pcie03]
[17179572.544000] isapnp: Scanning for PnP cards...
[17179572.912000] isapnp: No Plug & Play device found
[17179572.928000] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[17179572.928000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179572.928000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179572.928000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179572.928000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179572.928000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179572.928000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179572.928000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179572.932000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179572.932000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.932000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179572.932000] mice: PS/2 mouse device common for all mice
[17179572.932000] EISA: Probing bus 0 at eisa.0
[17179572.932000] Cannot allocate resource for EISA slot 1
[17179572.932000] Cannot allocate resource for EISA slot 8
[17179572.932000] EISA: Detected 0 cards.
[17179572.932000] NET: Registered protocol family 2
[17179572.972000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179572.972000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[17179572.972000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[17179572.972000] TCP: Hash tables configured (established 16384 bind 16384)
[17179572.972000] TCP reno registered
[17179572.972000] TCP bic registered
[17179572.972000] NET: Registered protocol family 1
[17179572.972000] NET: Registered protocol family 8
[17179572.972000] NET: Registered protocol family 20
[17179572.972000] Using IPI Shortcut mode
[17179572.972000] ACPI wakeup devices:
[17179572.972000]  PB2  PB3  PB4  PB6  PB7 OHC1 OHC2 EHCI  P2P ELAN MODM AZLA
[17179572.972000] ACPI: (supports S0 S3 S4 S5)
[17179572.972000] Freeing unused kernel memory: 288k freed
[17179573.020000] vga16fb: initializing
[17179573.020000] vga16fb: mapped to 0xc00a0000
[17179573.116000] Console: switching to colour frame buffer device 80x25
[17179573.116000] fb0: VGA16 VGA frame buffer device
[17179573.536000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179574.236000] Capability LSM initialized
[17179574.268000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179574.712000] SCSI subsystem initialized
[17179574.716000] ACPI: bus type scsi registered
[17179574.716000] libata version 1.20 loaded.
[17179574.716000] sata_sil 0000:00:12.0: version 0.9
[17179574.716000] PCI: Enabling device 0000:00:12.0 (0005 -> 0007)
[17179574.716000] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 209
[17179574.716000] ata1: SATA max UDMA/100 cmd 0xDC874080 ctl 0xDC87408A bmdma 0xDC874000 irq 209
[17179574.716000] ata2: SATA max UDMA/100 cmd 0xDC8740C0 ctl 0xDC8740CA bmdma 0xDC874008 irq 209
[17179575.084000] ata1: dev 0 cfg 00:045a 49:0f00 82:746b 83:7f69 84:6063 85:f469 86:3d49 87:6063 88:203f 93:0000
[17179575.084000] ata1: dev 0 ATA-7, max UDMA/100, 117210240 sectors: LBA48
[17179575.084000] sata_get_dev_handle: SATA dev addr=0x120000, handle=0xdbe69b60
[17179575.128000] ata1: dev 0 configured for UDMA/100
[17179575.128000] sata_get_dev_handle: SATA dev addr=0x120000, handle=0xdbe69b60
[17179575.172000] scsi0 : sata_sil
[17179575.376000] ata2: no device found (phy stat 00000000)
[17179575.376000] scsi1 : sata_sil
[17179575.376000]   Vendor: ATA       Model: HTS541060G9SA00   Rev: MB3O
[17179575.376000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179575.384000] Driver 'sd' needs updating - please use bus_type methods
[17179575.384000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[17179575.384000] SCSI device sda: drive cache: write back
[17179575.384000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[17179575.384000] SCSI device sda: drive cache: write back
[17179575.384000]  sda: sda1 sda2 < sda5 sda6 >
[17179575.448000] sd 0:0:0:0: Attached scsi disk sda
[17179575.656000] ATIIXP: IDE controller at PCI slot 0000:00:14.1
[17179575.656000] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 217
[17179575.656000] ATIIXP: chipset revision 128
[17179575.656000] ATIIXP: not 100% native mode: will probe irqs later
[17179575.656000]     ide1: BM-DMA at 0x8468-0x846f, BIOS settings: hdc:DMA, hdd:pio
[17179575.656000] Probing IDE interface ide1...
[17179576.392000] hdc: HL-DT-ST DVDRAM GMA-4082N, ATAPI CD/DVD-ROM drive
[17179576.728000] ide1 at 0x170-0x177,0x376 on irq 15
[17179576.740000] hdc: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179576.740000] Uniform CD-ROM driver Revision: 3.20
[17179576.828000] usbcore: registered new driver usbfs
[17179576.828000] usbcore: registered new driver hub
[17179576.832000] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 225
[17179576.832000] ehci_hcd 0000:00:13.2: EHCI Host Controller
[17179576.832000] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1
[17179576.832000] ehci_hcd 0000:00:13.2: irq 225, io mem 0xd0506000
[17179576.832000] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179576.832000] hub 1-0:1.0: USB hub found
[17179576.832000] hub 1-0:1.0: 8 ports detected
[17179576.872000] ieee1394: Initialized config rom entry `ip1394'
[17179576.904000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179576.904000] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 225
[17179576.904000] ohci_hcd 0000:00:13.0: OHCI Host Controller
[17179576.936000] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[17179576.936000] ohci_hcd 0000:00:13.0: irq 225, io mem 0xd0504000
[17179576.936000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[17179576.936000] ACPI: PCI Interrupt 0000:09:00.0[A] -> GSI 16 (level, low) -> IRQ 217
[17179576.968000] hub 2-0:1.0: USB hub found
[17179576.968000] hub 2-0:1.0: 4 ports detected
[17179577.000000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[217]  MMIO=[d0200000-d02007ff]  Max Packet=[2048]
[17179577.072000] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 225
[17179577.072000] ohci_hcd 0000:00:13.1: OHCI Host Controller
[17179577.072000] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[17179577.072000] ohci_hcd 0000:00:13.1: irq 225, io mem 0xd0505000
[17179577.076000] hub 3-0:1.0: USB hub found
[17179577.076000] hub 3-0:1.0: 4 ports detected
[17179577.204000] Probing IDE interface ide0...
[17179577.784000] Attempting manual resume
[17179578.276000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f679a400494]
[17179588.468000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179589.568000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179589.572000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179589.708000] Linux agpgart interface v0.101 (c) Dave Jones
[17179590.128000] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 217
[17179590.424000] Real Time Clock Driver v1.12
[17179590.480000] wlan: 0.8.4.2 (0.9.1)
[17179590.488000] ath_hal: module license 'Proprietary' taints kernel.
[17179590.488000] ath_hal: 0.9.17.2 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[17179590.516000] input: PC Speaker as /class/input/input1
[17179590.520000] input: PS/2 Mouse as /class/input/input2
[17179590.528000] ath_rate_sample: 1.2 (0.9.1)
[17179590.540000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input3
[17179590.540000] ath_pci: 0.9.4.5 (0.9.1)
[17179590.848000] ts: Compaq touchscreen protocol output
[17179590.864000] 8139too Fast Ethernet driver 0.9.27
[17179591.536000] hda_codec: Unknown model for ALC861, trying auto-probe from BIOS...
[17179591.728000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 233
[17179591.728000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[17179591.728000] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)
[17179591.728000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[17179591.728000] ACPI: PCI Interrupt 0000:09:04.0[A] -> GSI 17 (level, low) -> IRQ 185
[17179591.728000] Yenta: CardBus bridge found at 0000:09:04.0 [1179:ff00]
[17179591.728000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179591.728000] Yenta: Routing CardBus interrupts to PCI
[17179591.728000] Yenta TI: socket 0000:09:04.0, mfunc 0x00111c12, devctl 0x44
[17179591.796000] wlan: 0.8.4.2 (svn 2006-07-10)
[17179591.808000] new_ath_rate_sample: Unknown symbol new_ath_hal_computetxtime
[17179591.816000] new_ath_pci: Unknown symbol new_ath_rate_node_cleanup
[17179591.816000] new_ath_pci: Unknown symbol new_ath_hal_computetxtime
[17179591.816000] new_ath_pci: Unknown symbol new_ath_hal_probe
[17179591.816000] new_ath_pci: Unknown symbol _new_ath_hal_attach
[17179591.816000] new_ath_pci: Unknown symbol new_ath_rate_setupxtxdesc
[17179591.816000] new_ath_pci: Unknown symbol new_ath_hal_detach
[17179591.816000] new_ath_pci: Unknown symbol new_ath_rate_newassoc
[17179591.816000] new_ath_pci: Unknown symbol new_ath_rate_tx_complete
[17179591.816000] new_ath_pci: Unknown symbol new_ath_hal_init_channels
[17179591.816000] new_ath_pci: Unknown symbol new_ath_hal_getwirelessmodes
[17179591.816000] new_ath_pci: Unknown symbol new_ath_rate_node_init
[17179591.816000] new_ath_pci: Unknown symbol new_ath_rate_attach
[17179591.816000] new_ath_pci: Unknown symbol new_ath_rate_detach
[17179591.816000] new_ath_pci: Unknown symbol new_ath_rate_findrate
[17179591.816000] new_ath_pci: Unknown symbol new_ath_rate_newstate
[17179591.816000] new_ath_pci: Unknown symbol new_ath_hal_mhz2ieee
[17179591.960000] Yenta: ISA IRQ mask 0x0ef8, PCI irq 185
[17179591.960000] Socket status: 30000006
[17179591.960000] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[17179591.960000] cs: IO port probe 0xa000-0xafff: clean.
[17179591.960000] pcmcia: parent PCI bridge Memory window: 0xd0200000 - 0xd02fffff
[17179591.960000] pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x21ffffff
[17179591.968000] ACPI: PCI Interrupt 0000:09:06.0[A] -> GSI 22 (level, low) -> IRQ 209
[17179591.968000] eth0: RealTek RTL8139 at 0xdc990800, 00:16:d4:25:6e:6a, IRQ 209
[17179591.968000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179591.976000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179592.112000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[17179592.328000] cs: IO port probe 0x100-0x3af: clean.
[17179592.328000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179592.332000] cs: IO port probe 0x820-0x8ff: excluding 0x878-0x87f
[17179592.332000] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[17179592.332000] cs: IO port probe 0xa00-0xaff: clean.
[17179592.692000] lp: driver loaded but no devices found
[17179592.736000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[17179592.736000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179592.736000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179592.804000] Adding 2040212k swap on /dev/sda6.  Priority:-1 extents:1 across:2040212k
[17179593.172000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179593.172000] md: bitmap version 4.39
[17179593.188000] NET: Registered protocol family 17
[17179593.632000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179593.896000] NET: Registered protocol family 10
[17179593.896000] lo: Disabled Privacy Extensions
[17179593.896000] IPv6 over IPv4 tunneling driver
[17179594.096000] cdrom: open failed.
[17179594.392000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[17179594.448000] NTFS volume version 3.1.
[17179598.244000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179598.288000] ndiswrapper (wrapper_init:173): loadndiswrapper failed (1792); check system log for messages from 'loadndisdriver'
[17179598.292000] ndiswrapper (wrapper_init:180): ndiswrapper: initialization failed
[17179598.328000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179598.332000] ndiswrapper (wrapper_init:173): loadndiswrapper failed (1792); check system log for messages from 'loadndisdriver'
[17179598.332000] ndiswrapper (wrapper_init:180): ndiswrapper: initialization failed
[17179598.356000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179598.356000] ndiswrapper (wrapper_init:173): loadndiswrapper failed (1792); check system log for messages from 'loadndisdriver'
[17179598.356000] ndiswrapper (wrapper_init:180): ndiswrapper: initialization failed
[17179598.384000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179598.384000] ndiswrapper (wrapper_init:173): loadndiswrapper failed (1792); check system log for messages from 'loadndisdriver'
[17179598.384000] ndiswrapper (wrapper_init:180): ndiswrapper: initialization failed
[17179600.256000] ACPI: AC Adapter [ACAD] (off-line)
[17179600.320000] ACPI: Battery Slot [BAT1] (battery present)
[17179600.404000] ACPI: Power Button (FF) [PWRF]
[17179600.404000] ACPI: Lid Switch [LID]
[17179600.404000] ACPI: Power Button (CM) [PWRB]
[17179600.524000] ibm_acpi: ec object not found
[17179600.556000] pcc_acpi: loading...
[17179600.660000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179604.496000] eth0: no IPv6 routers present
[17179604.804000] ppdev: user-space parallel port driver
[17179605.516000] [fglrx] Maximum main memory to use for locked dma buffers: 372 MBytes.
[17179605.516000] [fglrx] module loaded - fglrx 8.26.18 [Jun 22 2006] on minor 0
[17179605.528000] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 185
[17179607.116000] apm: BIOS not found.
[17179607.352000] [fglrx] total      GART = 134217728
[17179607.352000] [fglrx] free       GART = 118226944
[17179607.352000] [fglrx] max single GART = 118226944
[17179607.352000] [fglrx] total      LFB  = 60780544
[17179607.352000] [fglrx] free       LFB  = 52588544
[17179607.352000] [fglrx] max single LFB  = 52588544
[17179607.356000] [fglrx] total      Inv  = 0
[17179607.356000] [fglrx] free       Inv  = 0
[17179607.356000] [fglrx] max single Inv  = 0
[17179607.356000] [fglrx] total      TIM  = 0
[17179611.204000] Bluetooth: Core ver 2.8
[17179611.204000] NET: Registered protocol family 31
[17179611.204000] Bluetooth: HCI device and connection manager initialized
[17179611.204000] Bluetooth: HCI socket layer initialized
[17179611.232000] Bluetooth: L2CAP ver 2.8
[17179611.232000] Bluetooth: L2CAP socket layer initialized
[17179611.260000] Bluetooth: RFCOMM socket layer initialized
[17179611.260000] Bluetooth: RFCOMM TTY layer initialized
[17179611.260000] Bluetooth: RFCOMM ver 1.7
[17179613.628000] hda-intel: Invalid position buffer, using LPIB read method instead.
[17179624.292000] eth0: no IPv6 routers present
[17179630.356000] psmouse.c: GlidePoint at isa0060/serio4/input0 lost synchronization, throwing 1 bytes away.
[17179630.428000] psmouse.c: GlidePoint at isa0060/serio4/input0 lost sync at byte 6
[17179630.432000] psmouse.c: GlidePoint at isa0060/serio4/input0 - driver resynched.
[17179630.432000] psmouse.c: GlidePoint at isa0060/serio4/input0 lost sync at byte 1
[17179630.440000] psmouse.c: GlidePoint at isa0060/serio4/input0 - driver resynched.
[17179630.452000] psmouse.c: GlidePoint at isa0060/serio4/input0 lost sync at byte 1
[17179630.464000] psmouse.c: GlidePoint at isa0060/serio4/input0 - driver resynched.
[17179630.624000] atkbd.c: Spurious ACK on isa0060/serio0. Some program, like XFree86, might be trying access hardware directly.
[17179630.824000] atkbd.c: Spurious ACK on isa0060/serio0. Some program, like XFree86, might be trying access hardware directly.
[17179632.096000] psmouse.c: GlidePoint at isa0060/serio4/input0 lost sync at byte 6
[17179632.100000] psmouse.c: GlidePoint at isa0060/serio4/input0 - driver resynched.
[17179632.104000] psmouse.c: GlidePoint at isa0060/serio4/input0 lost sync at byte 1
[17179632.112000] psmouse.c: GlidePoint at isa0060/serio4/input0 - driver resynched.
[17179632.116000] psmouse.c: GlidePoint at isa0060/serio4/input0 lost sync at byte 1
[17179632.116000] psmouse.c: GlidePoint at isa0060/serio4/input0 - driver resynched.
[17179632.528000] psmouse.c: GlidePoint at isa0060/serio4/input0 lost sync at byte 2
[17179632.528000] psmouse.c: GlidePoint at isa0060/serio4/input0 lost sync at byte 1
[17179632.532000] psmouse.c: GlidePoint at isa0060/serio4/input0 - driver resynched.
[17179632.596000] psmouse.c: GlidePoint at isa0060/serio4/input0 lost sync at byte 1
[17179632.604000] psmouse.c: GlidePoint at isa0060/serio4/input0 - driver resynched.
[17179644.104000] atkbd.c: Spurious ACK on isa0060/serio0. Some program, like XFree86, might be trying access hardware directly.
[17179644.304000] atkbd.c: Spurious ACK on isa0060/serio0. Some program, like XFree86, might be trying access hardware directly.


thanks again,
Dave

---

### Post by rbalfour on 2006-07-26
here is the deal. Basically your card is support, but Ubuntu drivers don't support your version.

2 choices.
1) Setup NDISWRAPPER and not the source and compile, but via the Ubuntu package manager, just do a seach for NDISWRAPPER
2) Get the lastest MadWifi from [http://sourceforge.net/projects/madwifi/](http://sourceforge.net/projects/madwifi/)
make and make install then reboot, try out your wireless card.

Now with option 1, it should work, but it will be using Windows drivers to run the network card, so not all the features will work and may or may not be stable.
I would try 2nd option first, then fallback on option 2. Some will disagree with me on this process, but everyone has a solution, but always misses the point. To get it working! gl and I will be watching this post for an update. Also , keep notes on what and how you did it, in case you have an issue, you can post the notes...

---

### Post by dwaldie on 2006-07-26
Hello,
     I did step two last night I think.  Here is what I did and in what order.

1) I did a full update of all packages using apt.

2) I then downloaded the madwifi drivers from their sourceforge sight and built them and installed them using make and make install.  During the make install it asked me if I wanted to ignore or remove the old drivers and I chose remove.  

3)  I then rebooted and still nothing.

When I use the command iwconfig it gives me the following message.

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.


I do not know what to do from here.

Thanks,
Dave

---

### Post by rbalfour on 2006-07-26
Plese post the output from this command.
$ lspci -v

---

### Post by dwaldie on 2006-07-26
dwaldie@dwaldie-laptop:~$ lspci -v
0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5a31 (rev 01)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, 66MHz, medium devsel, latency 64

0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f (prog-if 00 [ Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: d0000000-d00fffff
        Prefetchable memory behind bridge: d8000000-dfffffff
        Capabilities: <available only to root>

0000:00:06.0 PCI bridge: ATI Technologies Inc: Unknown device 5a38 (prog-if 00 [ Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=07, sec-latency=0
        Memory behind bridge: d0100000-d01fffff
        Capabilities: <available only to root>

0000:00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 209
        I/O ports at 8440 [size=8]
        I/O ports at 8430 [size=4]
        I/O ports at 8420 [size=8]
        I/O ports at 8410 [size=4]
        I/O ports at 8400 [size=16]
        Memory at d0507000 (32-bit, non-prefetchable) [size=512]
        Expansion ROM at 22000000 [disabled] [size=512K]
        Capabilities: <available only to root>

0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 225
        Memory at d0504000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 225
        Memory at d0505000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller  (rev 80) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 225
        Memory at d0506000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: 66MHz, medium devsel
        I/O ports at 8450 [size=16]
        Memory at d0507400 (32-bit, non-prefetchable) [size=1K]

0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE C ontroller ATI (rev 80) (prog-if 88 [Master SecP])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 217
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at <ignored>
        I/O ports at 8460 [size=16]
        Capabilities: <available only to root>

0000:00:14.2 0403: ATI Technologies Inc: Unknown device 437b (rev 01)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, slow devsel, latency 64, IRQ 217
        Memory at d0500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, 66MHz, medium devsel, latency 0

0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=09, subordinate=0e, sec-latency=64
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: d0200000-d02fffff
        Prefetchable memory behind bridge: 20000000-21ffffff

0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5a6 2 (prog-if 00 [VGA])
        Subsystem: Toshiba America Info Systems: Unknown device ff03
        Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 11
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 9000 [size=256]
        Memory at d0000000 (32-bit, non-prefetchable) [size=64K]
        Expansion ROM at d0020000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:02:00.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 0 01c (rev 01)
        Subsystem: Askey Computer Corp.: Unknown device 7106
        Flags: fast devsel, IRQ 233
        Memory at d0100000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <available only to root>

0000:09:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Control ler (rev c0) (prog-if 10 [OHCI])
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 64, IRQ 217
        Memory at d0200000 (32-bit, non-prefetchable) [size=2K]
        I/O ports at a400 [size=128]
        Capabilities: <available only to root>

0000:09:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 0 1)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 168, IRQ 185
        Memory at d0201000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=09, secondary=0a, subordinate=0d, sec-latency=176
        Memory window 0: 20000000-21fff000 (prefetchable)
        Memory window 1: 24000000-25fff000
        I/O window 0: 0000a800-0000a8ff
        I/O window 1: 0000ac00-0000acff
        16-bit legacy interface ports at 0001

0000:09:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C /8139C+ (rev 10)
        Subsystem: Toshiba America Info Systems: Unknown device ff00
        Flags: bus master, medium devsel, latency 64, IRQ 209
        I/O ports at a000 [size=256]
        Memory at d0200800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

dwaldie@dwaldie-laptop:~$

---

### Post by ozorba on 2006-07-26
You appear to be using 386 kernel.

Have you tried to run it with 686 kernel?

Once I had a similar problem. But I was using Centrino with Intel wifi chipset. As soon as I installed 686 kernel my wireless worked.

You can find the 686 kernel under linux-image-686, I think.

---

### Post by MrBbDD_OK on 2006-07-26
Try sudo lsmod ath_pci and see if it's loaded. If not sudo insmod ath_pci should load it. I have an older Toshiba with a D-Link Atheros card and it was picked up and set up by the install. You may have to enter wireless commands via iwconfig to set it up:) .

---

### Post by dwaldie on 2006-07-26
Still no luck.  I installed the new kernel, kernel headers and re-compiled and installed the madwifi drivers.  This still did not work.  I am totally stumped here.  

Dave

---

### Post by rbalfour on 2006-07-28
Another solution for you.
Download this disc -> [http://ftp.rz.tu-braunschweig.de/pub/mirror/auditor/auditor-200605-02-no-ipw2100.iso](http://ftp.rz.tu-braunschweig.de/pub/mirror/auditor/auditor-200605-02-no-ipw2100.iso)

Burn it to a CD and boot that laptop up with it and check to see if the wireless card works. This will cover all support MadWiFi cards and more.
If it works, dump a lspci and lsmod and iwconfig to a txt file and post it.

Sorry it is taking so long...

---

### Post by MrBbDD_OK on 2006-07-29
Please ignore my previous post. i hadn't read all the dmesg output from hal_pci, the other component of ath_pci. It's trying to load, but you must need a newer driver. Sorry to confuze you.

Britt Dickson
'

---

### Post by dwaldie on 2006-07-30
Thank you for all the help it is much appreciated, and don't worry about rbalfour, nothing is always easy, and I am learning, which can't be all bad.  I had to wait for my new month of internet usage so I would not go over in download bandwidth.  I am downloading it now and will post the info later on this afternoon.

Dave

---

### Post by krypto_wizard on 2006-07-30
Usually, Atheros drivers work out of the box in any version of Ubuntu.

---

### Post by dwaldie on 2006-07-30
Hello,
    I burnt the iso and booted it up but no success.  I guess that my wifi card is not supported yet under linux.  Hopefuly soon though.

Dave

---

### Post by dwaldie on 2006-08-02
Yeah, I got it working using the Windows driver for my card.  This is awsome.

Thank you both for all the help and time,
David

---

### Post by Galactic Jack on 2007-07-03
> **dwaldie said:**
> Yeah, I got it working using the Windows driver for my card.  This is awsome.

Thank you both for all the help and time,
David

WHat windows driver was it. I've been having a hell of a time with madwifi and ndiswrapper trying to install this damn wireless card. Theo nly one I've found that would actually say that it was both working and receiving the hardware was netopOEM.inf but it doesn't do anything to actually make it work

GJ

---

