---
title: "Some bootlog questions"
date: 2006-06-29
forum: Hardware &amp; Laptops
---

### Post by LPent on 2006-06-29
dmesg gives me the following output:

```

[17179569.184000] Linux version 2.6.15-25-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003ffc0000 (usable)
[17179569.184000]  BIOS-e820: 000000003ffc0000 - 000000003ffcf000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000003ffcf000 - 0000000040000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb80000 - 0000000100000000 (reserved)
[17179569.184000] 127MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000ff780
[17179569.184000] On node 0 totalpages: 262080
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32704 pages, LIFO batch:7
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f6990
[17179569.184000] ACPI: RSDT (v001 A M I  OEMRSDT  0x11000507 MSFT 0x00000097) @ 0x3ffc0000
[17179569.184000] ACPI: FADT (v002 A M I  OEMFACP  0x11000507 MSFT 0x00000097) @ 0x3ffc0200
[17179569.184000] ACPI: MADT (v001 A M I  OEMAPIC  0x11000507 MSFT 0x00000097) @ 0x3ffc0390
[17179569.184000] ACPI: MCFG (v001 A M I  OEMMCFG  0x11000507 MSFT 0x00000097) @ 0x3ffc03f0
[17179569.184000] ACPI: OEMB (v001 A M I  AMI_OEM  0x11000507 MSFT 0x00000097) @ 0x3ffcf040
[17179569.184000] ACPI: SSDT (v001    AMI   CPU1PM 0x00000001 INTL 0x02002026) @ 0x3ffc8e20
[17179569.184000] ACPI: DSDT (v001  0AAAA 0AAAA000 0x00000000 INTL 0x02002026) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:13 APIC version 20
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:bed14000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda4 ro quiet
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 1729.182 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179573.216000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179573.216000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179573.240000] Memory: 1028648k/1048320k available (1976k kernel code, 18932k reserved, 606k data, 288k init, 130816k highmem)
[17179573.240000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179573.320000] Calibrating delay using timer specific routine.. 3462.19 BogoMIPS (lpj=6924393)
[17179573.320000] Security Framework v1.0.0 initialized
[17179573.320000] SELinux:  Disabled at boot.
[17179573.320000] Mount-cache hash table entries: 512
[17179573.320000] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000 00000000
[17179573.320000] CPU: After vendor identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000 00000000
[17179573.320000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179573.320000] CPU: L2 cache: 2048K
[17179573.320000] CPU: After all inits, caps: afe9fbff 00100000 00000000 00000040 00000180 00000000 00000000
[17179573.320000] mtrr: v2.0 (20020519)
[17179573.320000] CPU: Intel(R) Pentium(R) M processor 1.73GHz stepping 08
[17179573.320000] Enabling fast FPU save and restore... done.
[17179573.320000] Enabling unmasked SIMD FPU exception support... done.
[17179573.320000] Checking 'hlt' instruction... OK.
[17179573.336000] checking if image is initramfs... it is
[17179573.932000] Freeing initrd memory: 6613k freed
[17179573.940000] ACPI: Looking for DSDT ... not found!
[17179573.956000] ENABLING IO-APIC IRQs
[17179573.956000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179574.100000] NET: Registered protocol family 16
[17179574.100000] EISA bus registered
[17179574.100000] ACPI: bus type pci registered
[17179574.100000] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=3
[17179574.100000] PCI: Using MMCONFIG
[17179574.100000] ACPI: Subsystem revision 20051216
[17179574.220000] ACPI: Interpreter enabled
[17179574.220000] ACPI: Using IOAPIC for interrupt routing
[17179574.224000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179574.224000] PCI: Probing PCI hardware (bus 00)
[17179574.224000] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[17179574.224000] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[17179574.224000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179574.224000] Boot video device is 0000:03:00.0
[17179574.224000] PCI: Transparent bridge - 0000:00:1e.0
[17179574.224000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179574.228000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[17179574.232000] ACPI: Embedded Controller [EC0] (gpe 28) interrupt mode.
[17179574.236000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P3._PRT]
[17179574.236000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *11 12)
[17179574.236000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 12) *11
[17179574.236000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 6 7 12)
[17179574.236000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 *6 7 12)
[17179574.236000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 6 7 12)
[17179574.236000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 12) *0, disabled.
[17179574.236000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 12)
[17179574.240000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 12)
[17179574.240000] ACPI: Power Resource [GFAN] (off)
[17179574.240000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179574.240000] pnp: PnP ACPI init
[17179574.244000] pnp: PnP ACPI: found 14 devices
[17179574.244000] PnPBIOS: Disabled by ACPI PNP
[17179574.244000] PCI: Using ACPI for IRQ routing
[17179574.244000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179574.252000] pnp: 00:0b: ioport range 0xa00-0xa0f has been reserved
[17179574.252000] PCI: Bridge: 0000:00:01.0
[17179574.252000]   IO window: disabled.
[17179574.252000]   MEM window: faa00000-feafffff
[17179574.252000]   PREFETCH window: bfe00000-dfefffff
[17179574.252000] PCI: Bus 2, cardbus bridge: 0000:01:01.0
[17179574.252000]   IO window: 0000d000-0000d0ff
[17179574.252000]   IO window: 0000d400-0000d4ff
[17179574.252000]   PREFETCH window: 50000000-51ffffff
[17179574.252000]   MEM window: 54000000-55ffffff
[17179574.252000] PCI: Bridge: 0000:00:1e.0
[17179574.252000]   IO window: d000-dfff
[17179574.252000]   MEM window: fa900000-fa9fffff
[17179574.252000]   PREFETCH window: 50000000-52ffffff
[17179574.252000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179574.252000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179574.252000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179574.252000] ACPI: PCI Interrupt 0000:01:01.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179574.252000] audit: initializing netlink socket (disabled)
[17179574.252000] audit(1151582430.252:1): initialized
[17179574.252000] highmem bounce pool size: 64 pages
[17179574.252000] VFS: Disk quotas dquot_6.5.1
[17179574.252000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179574.252000] Initializing Cryptographic API
[17179574.252000] io scheduler noop registered
[17179574.252000] io scheduler anticipatory registered
[17179574.252000] io scheduler deadline registered
[17179574.252000] io scheduler cfq registered
[17179574.252000] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179574.252000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179574.252000] assign_interrupt_mode Found MSI capability
[17179574.252000] Allocate Port Service[pcie00]
[17179574.252000] Allocate Port Service[pcie03]
[17179574.252000] isapnp: Scanning for PnP cards...
[17179574.608000] isapnp: No Plug & Play device found
[17179574.620000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[17179574.620000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179574.624000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179574.624000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179574.624000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179574.624000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179574.624000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.624000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179574.624000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179574.624000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179574.624000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.624000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179574.624000] mice: PS/2 mouse device common for all mice
[17179574.624000] EISA: Probing bus 0 at eisa.0
[17179574.624000] EISA: Detected 0 cards.
[17179574.628000] NET: Registered protocol family 2
[17179574.668000] IP route cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179574.668000] TCP established hash table entries: 262144 (order: 8, 1048576 bytes)
[17179574.668000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179574.668000] TCP: Hash tables configured (established 262144 bind 65536)
[17179574.668000] TCP reno registered
[17179574.668000] TCP bic registered
[17179574.668000] NET: Registered protocol family 1
[17179574.668000] NET: Registered protocol family 8
[17179574.668000] NET: Registered protocol family 20
[17179574.668000] Using IPI Shortcut mode
[17179574.668000] ACPI wakeup devices: 
[17179574.668000] P0P1 CBS0 P394 CRD0 CRD1 MPCI LAN0 USB1 USB2 USB3 USB4 EUSB MC97 AZAL SLPB 
[17179574.668000] ACPI: (supports S0 S3 S4 S5)
[17179574.668000] Freeing unused kernel memory: 288k freed
[17179574.708000] Capability LSM initialized
[17179574.736000] ACPI: Fan [FN00] (off)
[17179574.740000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[17179574.740000] ACPI: Processor [CPU1] (supports 8 throttling states)
[17179574.776000] ACPI: Thermal Zone [THRM] (28 C)
[17179574.784000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179575.056000] ICH6: IDE controller at PCI slot 0000:00:1f.1
[17179575.056000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 201
[17179575.056000] ICH6: chipset revision 4
[17179575.056000] ICH6: not 100% native mode: will probe irqs later
[17179575.056000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
[17179575.056000]     ide1: BM-DMA at 0xffa8-0xffaf, BIOS settings: hdc:pio, hdd:pio
[17179575.056000] Probing IDE interface ide0...
[17179575.344000] hda: HTS721060G9AT00, ATA DISK drive
[17179575.792000] hdb: TSSTcorpCD/DVDW TS-L532A, ATAPI CD/DVD-ROM drive
[17179575.848000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179575.872000] Probing IDE interface ide1...
[17179576.444000] hda: max request size: 1024KiB
[17179576.448000] hda: 117210240 sectors (60011 MB) w/7539KiB Cache, CHS=16383/255/63, UDMA(100)
[17179576.448000] hda: cache flushes supported
[17179576.448000]  hda: hda1 hda2 hda3 hda4
[17179576.568000] hdb: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179576.568000] Uniform CD-ROM driver Revision: 3.20
[17179576.920000] usbcore: registered new driver usbfs
[17179576.920000] usbcore: registered new driver hub
[17179576.920000] USB Universal Host Controller Interface driver v2.3
[17179576.920000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 209
[17179576.920000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179576.920000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179576.920000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179576.920000] uhci_hcd 0000:00:1d.0: irq 209, io base 0x0000e480
[17179576.920000] hub 1-0:1.0: USB hub found
[17179576.920000] hub 1-0:1.0: 2 ports detected
[17179576.976000] ieee1394: Initialized config rom entry `ip1394'
[17179577.024000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 217
[17179577.024000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179577.024000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179577.024000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179577.024000] uhci_hcd 0000:00:1d.1: irq 217, io base 0x0000e800
[17179577.024000] hub 2-0:1.0: USB hub found
[17179577.024000] hub 2-0:1.0: 2 ports detected
[17179577.128000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 201
[17179577.128000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179577.128000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179577.128000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179577.128000] uhci_hcd 0000:00:1d.2: irq 201, io base 0x0000e880
[17179577.128000] hub 3-0:1.0: USB hub found
[17179577.128000] hub 3-0:1.0: 2 ports detected
[17179577.232000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 169
[17179577.232000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[17179577.232000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[17179577.232000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[17179577.232000] uhci_hcd 0000:00:1d.3: irq 169, io base 0x0000ec00
[17179577.232000] hub 4-0:1.0: USB hub found
[17179577.232000] hub 4-0:1.0: 2 ports detected
[17179577.264000] usb 1-1: new low speed USB device using uhci_hcd and address 2
[17179577.336000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[17179577.336000] ACPI: PCI Interrupt 0000:01:01.1[B] -> GSI 18 (level, low) -> IRQ 201
[17179577.344000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 209
[17179577.344000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179577.344000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179577.344000] ehci_hcd 0000:00:1d.7: debug port 1
[17179577.344000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179577.344000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[17179577.344000] ehci_hcd 0000:00:1d.7: irq 209, io mem 0xfebffc00
[17179577.348000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179577.348000] hub 5-0:1.0: USB hub found
[17179577.348000] hub 5-0:1.0: 8 ports detected
[17179577.392000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[201]  MMIO=[fa9fe000-fa9fe7ff]  Max Packet=[2048]
[17179577.472000] Probing IDE interface ide1...
[17179577.788000] usb 1-1: device not accepting address 2, error -71
[17179578.172000] Attempting manual resume
[17179578.212000] EXT3-fs: mounted filesystem with ordered data mode.
[17179578.224000] kjournald starting.  Commit interval 5 seconds
[17179578.396000] usb 5-5: new high speed USB device using ehci_hcd and address 3
[17179578.672000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e01800034b60d2]
[17179578.824000] usb 1-1: new low speed USB device using uhci_hcd and address 4
[17179586.676000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179586.680000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179586.872000] hw_random: RNG not detected
[17179586.912000] Linux agpgart interface v0.101 (c) Dave Jones
[17179586.932000] agpgart: Detected an Intel 915GM Chipset.
[17179586.952000] agpgart: AGP aperture is 256M @ 0x0
[17179586.968000] nvidia: module license 'NVIDIA' taints kernel.
[17179586.972000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179586.972000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[17179586.972000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006
[17179587.544000] ACPI: PCI Interrupt 0000:01:01.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179587.544000] Yenta: CardBus bridge found at 0000:01:01.0 [1043:1177]
[17179587.596000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179587.596000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[17179587.620000] Real Time Clock Driver v1.12
[17179587.652000] ieee80211_1_1_13_crypt: registered algorithm 'NULL'
[17179587.652000] ieee80211_1_1_13: 802.11 data/management/control stack, 1.1.13
[17179587.652000] ieee80211_1_1_13: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179587.664000] ieee80211_crypt: registered algorithm 'NULL'
[17179587.664000] ieee80211: 802.11 data/management/control stack, git-1.1.7
[17179587.664000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179587.672000] Yenta: ISA IRQ mask 0x04b8, PCI irq 177
[17179587.672000] Socket status: 30000006
[17179587.672000] pcmcia: parent PCI bridge I/O window: 0xd000 - 0xdfff
[17179587.672000] cs: IO port probe 0xd000-0xdfff: clean.
[17179587.672000] pcmcia: parent PCI bridge Memory window: 0xfa900000 - 0xfa9fffff
[17179587.672000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x52ffffff
[17179587.672000] sdhci: Secure Digital Host Controller Interface driver, 0.10
[17179587.672000] sdhci: Copyright(c) Pierre Ossman
[17179587.888000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1
[17179587.888000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179587.888000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!
[17179587.908000] input: PC Speaker as /class/input/input1
[17179587.924000] irda_init()
[17179587.924000] NET: Registered protocol family 23
[17179588.172000] ACPI: PCI Interrupt 0000:01:01.2[C] -> GSI 19 (level, low) -> IRQ 217
[17179588.172000] Synaptics Touchpad, model: 1, fw: 6.1, id: 0xa3a0b3, caps: 0xa04713/0x10008
[17179588.184000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 20 (level, low) -> IRQ 225
[17179588.184000] skge 1.3 addr 0xfa9f8000 irq 225 chip Yukon-Lite rev 9
[17179588.184000] skge eth0: addr 00:15:f2:ab:45:17
[17179588.212000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[17179588.224000] sdhci: ============== REGISTER DUMP ==============
[17179588.224000] sdhci: Sys addr: 0x00000000 | Version:  0x00000200
[17179588.224000] sdhci: Blk size: 0x00000000 | Blk cnt:  0x00000000
[17179588.224000] sdhci: Argument: 0x00000000 | Trn mode: 0x00000000
[17179588.224000] sdhci: Present:  0x01fa0000 | Host ctl: 0x00000000
[17179588.224000] sdhci: Power:    0x00000000 | Blk gap:  0x00000000
[17179588.224000] sdhci: Walk up:  0x00000000 | Clock:    0x00000000
[17179588.224000] sdhci: Timeout:  0x0000000e | Int stat: 0x00000000
[17179588.224000] sdhci: Int enab: 0xe1ff00cf | Sig enab: 0xe1ff00cf
[17179588.224000] sdhci: AC12 err: 0x00000000 | Slot int: 0x00000000
[17179588.224000] sdhci: Caps:     0x018021a1 | Max curr: 0x00000040
[17179588.224000] sdhci: ===========================================
[17179588.272000] mmc0: SDHCI at 0xfa9fe800 irq 217 DMA
[17179588.272000] ACPI: PCI Interrupt 0000:01:03.0[A] -> GSI 22 (level, low) -> IRQ 233
[17179588.272000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17179588.548000] parport: PnPBIOS parport detected.
[17179588.548000] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[17179589.100000] ts: Compaq touchscreen protocol output
[17179589.112000] usbcore: registered new driver hiddev
[17179589.132000] input: Logitech Optical USB Mouse as /class/input/input3
[17179589.132000] input: USB HID v1.10 Mouse [Logitech Optical USB Mouse] on usb-0000:00:1d.0-1
[17179589.132000] usbcore: registered new driver usbhid
[17179589.132000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179589.332000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[17179589.352000] usbcore: registered new driver snd-usb-audio
[17179589.524000] cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x370-0x37f
[17179589.528000] cs: IO port probe 0x3e0-0x4ff: excluding 0x400-0x41f 0x4d0-0x4d7
[17179589.528000] cs: IO port probe 0x820-0x8ff: clean.
[17179589.528000] cs: IO port probe 0xc00-0xcf7: clean.
[17179589.528000] cs: IO port probe 0xa00-0xaff: clean.
[17179589.748000] lp0: using parport0 (interrupt-driven).
[17179589.756000] ieee80211_crypt: registered algorithm 'WEP'
[17179589.848000] skge eth0: enabling interface
[17179589.888000] SCSI subsystem initialized
[17179589.900000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[17179589.900000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179589.900000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179589.940000] Adding 2048276k swap on /dev/hda3.  Priority:-1 extents:1 across:2048276k
[17179589.968000] EXT3 FS on hda4, internal journal
[17179590.080000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179590.080000] md: bitmap version 4.39
[17179590.364000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[17179590.732000] cdrom: open failed.
[17179590.992000] NET: Registered protocol family 17
[17179591.100000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[17179591.180000] NTFS volume version 3.1.
[17179591.212000] kjournald starting.  Commit interval 5 seconds
[17179591.220000] EXT3 FS on hda2, internal journal
[17179591.220000] EXT3-fs: mounted filesystem with ordered data mode.
[17179592.600000] NET: Registered protocol family 10
[17179592.600000] lo: Disabled Privacy Extensions
[17179592.600000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179592.600000] IPv6 over IPv4 tunneling driver
[17179595.860000] ACPI: AC Adapter [AC0] (on-line)
[17179595.900000] ACPI: Battery Slot [BAT0] (battery present)
[17179595.928000] Asus Laptop ACPI Extras version 0.29
[17179595.928000]   no string returned by INIT
[17179595.928000]   trying default values, supply the developers with your DSDT
[17179595.964000] ACPI: Power Button (FF) [PWRF]
[17179595.964000] ACPI: Lid Switch [LID]
[17179595.964000] ACPI: Sleep Button (CM) [SLPB]
[17179596.044000] ibm_acpi: ec object not found
[17179596.068000] pcc_acpi: loading...
[17179596.144000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179596.144000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179597.684000] ppdev: user-space parallel port driver
[17179598.916000] apm: BIOS not found.
[17179603.224000] eth1: no IPv6 routers present

```

I am wondering what the following items mean and what I can/must do about them:

1) [17179573.940000] ACPI: Looking for DSDT ... not found!
2) [17179577.788000] usb 1-1: device not accepting address 2, error -71
3) [17179587.888000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!
4) [17179595.928000] Asus Laptop ACPI Extras version 0.29
[17179595.928000]   no string returned by INIT
[17179595.928000]   trying default values, supply the developers with your DSDT

---

