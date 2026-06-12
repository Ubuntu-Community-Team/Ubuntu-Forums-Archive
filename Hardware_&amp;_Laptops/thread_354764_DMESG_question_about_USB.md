---
title: "DMESG question about USB"
date: 2007-02-06
forum: Hardware &amp; Laptops
---

### Post by klittzzer on 2007-02-06
I have been trying to get my USB removable devices to hotplug in Ubuntu Edgy. As it stands, they are only detected and enabled by Edgy if I plug them before I boot the notebook.
I am getting somewhere. After reinstalling windows on a partition I plugged in my mp3 player (2gib SigmaTel) and reformatted it to FAT32 (it was FAT16 and Ubuntu really didn't like it-it took about 5mins for Edgy to access the files) and Edgy seems to be able to access the device faster. Also, when I try to hotplug the device, it still doesn't show up anywhere on my notebook but I do now get something which refers to the device when I run dmesg.

The following is the output of dmesg after I plug the device which doesn't show up unless I plug it before boot.

littzzer@notebook:~$ dmesg
[17179569.184000] Linux version 2.6.17-10-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Tue Dec 5 22:28:26 UTC 2006 (Ubuntu 2.6.17-10.34-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001bfef000 (usable)
[17179569.184000]  BIOS-e820: 000000001bff0000 - 000000001bffffc0 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001bffffc0 - 000000001c000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 447MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 114671
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 110575 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 OID_00                                ) @ 0x000e6010
[17179569.184000] ACPI: RSDT (v001 INSYDE FACP_000 0x00000100 0000 0x00010200) @ 0x1bffc3c0
[17179569.184000] ACPI: FADT (v001 INSYDE FACP_000 0x00000100 0000 0x00010200) @ 0x1bfffb10
[17179569.184000] ACPI: MADT (v001 INSYDE APIC_000 0x30303030 0000 0x00010200) @ 0x1bfffba0
[17179569.184000] ACPI: DSDT (v001 MTC___ 8650____ 0x00001000 INTL 0x02002036) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:13 APIC version 20
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 1c000000:e3f80000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 1592.609 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179570.228000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179570.228000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.244000] Memory: 444776k/458684k available (1910k kernel code, 13388k reserved, 1069k data, 308k init, 0k highmem)
[17179570.244000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179570.324000] Calibrating delay using timer specific routine.. 3188.82 BogoMIPS (lpj=6377650)
[17179570.324000] Security Framework v1.0.0 initialized
[17179570.324000] SELinux:  Disabled at boot.
[17179570.324000] Mount-cache hash table entries: 512
[17179570.324000] CPU: After generic identify, caps: afe9fbff 00000000 00000000 00000000 00000000 00000000 00000000
[17179570.324000] CPU: After vendor identify, caps: afe9fbff 00000000 00000000 00000000 00000000 00000000 00000000
[17179570.324000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179570.324000] CPU: L2 cache: 1024K
[17179570.324000] CPU: After all inits, caps: afe9fbff 00000000 00000000 00000040 00000000 00000000 00000000
[17179570.324000] Checking 'hlt' instruction... OK.
[17179570.340000] SMP alternatives: switching to UP code
[17179570.340000] Freeing SMP alternatives: 16k freed
[17179570.340000] checking if image is initramfs... it is
[17179570.932000] Freeing initrd memory: 5623k freed
[17179570.932000] ACPI: Core revision 20060707
[17179570.932000] ACPI: Looking for DSDT ... not found!
[17179570.944000] CPU0: Intel(R) Celeron(R) M processor         1.60GHz stepping 08
[17179570.944000] Total of 1 processors activated (3188.82 BogoMIPS).
[17179570.944000] ENABLING IO-APIC IRQs
[17179570.944000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179571.088000] Brought up 1 CPUs
[17179571.088000] migration_cost=0
[17179571.088000] NET: Registered protocol family 16
[17179571.088000] EISA bus registered
[17179571.088000] ACPI: bus type pci registered
[17179571.088000] PCI: PCI BIOS revision 2.10 entry at 0xe9c04, last bus=1
[17179571.088000] PCI: Using configuration type 1
[17179571.088000] Setting up standard PCI resources
[17179571.088000] ACPI: Interpreter enabled
[17179571.092000] ACPI: Using IOAPIC for interrupt routing
[17179571.092000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179571.092000] PCI: Probing PCI hardware (bus 00)
[17179571.092000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179571.092000] PCI quirk: region 1000-107f claimed by vt8235 PM
[17179571.092000] PCI quirk: region 1400-140f claimed by vt8235 SMB
[17179571.092000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:11.1
[17179571.092000] Boot video device is 0000:01:00.0
[17179571.092000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.108000] ACPI: Embedded Controller [EC0] (gpe 1) interrupt mode.
[17179571.108000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 14 15)
[17179571.108000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 *7 10 11 14 15)
[17179571.108000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 10 11 14 15)
[17179571.108000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *10 11 14 15)
[17179571.112000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[17179571.112000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[17179571.112000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[17179571.112000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 14 15) *0, disabled.
[17179571.112000] ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0, disabled.
[17179571.112000] ACPI: PCI Interrupt Link [ALKB] (IRQs 23) *11
[17179571.112000] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *5, disabled.
[17179571.112000] ACPI Error (uteval-0269): Return object type is incorrect [\_SB_.PCI0.ALKD._CRS] (Node dbfd2b1c), AE_TYPE
[17179571.112000] ACPI Error (uteval-0275): Type returned from _CRS was incorrect: Integer, expected Btypes: 4 [20060707]
[17179571.112000] ACPI Exception (pci_link-0281): AE_TYPE, Evaluating _CRS [20060707]
[17179571.112000] ACPI: PCI Interrupt Link [ALKD] (IRQs 21) *0
[17179571.112000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.112000] pnp: PnP ACPI init
[17179571.116000] pnp: PnP ACPI: found 9 devices
[17179571.116000] PnPBIOS: Disabled by ACPI PNP
[17179571.116000] PCI: Using ACPI for IRQ routing
[17179571.116000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.120000] pnp: 00:07: ioport range 0x330-0x331 has been reserved
[17179571.120000] pnp: 00:07: ioport range 0x4d0-0x4d1 has been reserved
[17179571.120000] pnp: 00:07: ioport range 0x1000-0x107f could not be reserved
[17179571.120000] pnp: 00:07: ioport range 0x1400-0x140f has been reserved
[17179571.120000] PCI: Bridge: 0000:00:01.0
[17179571.120000]   IO window: c000-dfff
[17179571.120000]   MEM window: c0000000-cfffffff
[17179571.120000]   PREFETCH window: 90000000-9fffffff
[17179571.120000] PCI: Bus 2, cardbus bridge: 0000:00:09.0
[17179571.120000]   IO window: 00001800-000018ff
[17179571.120000]   IO window: 00001c00-00001cff
[17179571.120000]   PREFETCH window: 20000000-21ffffff
[17179571.120000]   MEM window: 22000000-23ffffff
[17179571.120000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[17179571.120000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 169
[17179571.120000] NET: Registered protocol family 2
[17179571.160000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179571.160000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179571.160000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179571.160000] TCP: Hash tables configured (established 16384 bind 8192)
[17179571.160000] TCP reno registered
[17179571.160000] audit: initializing netlink socket (disabled)
[17179571.160000] audit(1170778426.160:1): initialized
[17179571.160000] VFS: Disk quotas dquot_6.5.1
[17179571.160000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.160000] Initializing Cryptographic API
[17179571.160000] io scheduler noop registered
[17179571.160000] io scheduler anticipatory registered
[17179571.160000] io scheduler deadline registered
[17179571.160000] io scheduler cfq registered (default)
[17179571.160000] isapnp: Scanning for PnP cards...
[17179571.516000] isapnp: No Plug & Play device found
[17179571.548000] Real Time Clock Driver v1.12ac
[17179571.548000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179571.548000] mice: PS/2 mouse device common for all mice
[17179571.548000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.548000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.548000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.548000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179571.564000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179571.568000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179571.568000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179571.572000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179571.572000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179571.572000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.576000] EISA: Probing bus 0 at eisa.0
[17179571.576000] Cannot allocate resource for EISA slot 1
[17179571.576000] EISA: Detected 0 cards.
[17179571.576000] TCP bic registered
[17179571.576000] NET: Registered protocol family 1
[17179571.576000] NET: Registered protocol family 8
[17179571.576000] NET: Registered protocol family 20
[17179571.576000] Using IPI No-Shortcut mode
[17179571.576000] ACPI: (supports S0 S1 S3 S4 S5)
[17179571.576000] Freeing unused kernel memory: 308k freed
[17179571.604000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.712000] Capability LSM initialized
[17179572.744000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179572.744000] ACPI: Processor [CPU0] (supports 16 throttling states)
[17179573.040000] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[17179573.040000] ACPI: PCI Interrupt Link [ALKA] disabled and referenced, BIOS bug
[17179573.040000] ACPI: PCI Interrupt Link [ALKA] BIOS reported IRQ 0, using IRQ 20
[17179573.040000] ACPI: PCI Interrupt Link [ALKA] enabled at IRQ 20
[17179573.040000] ACPI: PCI Interrupt 0000:00:11.1[A] -> Link [ALKA] -> GSI 20 (level, low) -> IRQ 177
[17179573.040000] PCI: Via IRQ fixup for 0000:00:11.1, from 0 to 1
[17179573.040000] VP_IDE: chipset revision 6
[17179573.040000] VP_IDE: not 100% native mode: will probe irqs later
[17179573.040000] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[17179573.040000]     ide0: BM-DMA at 0x1100-0x1107, BIOS settings: hda:DMA, hdb:pio
[17179573.040000]     ide1: BM-DMA at 0x1108-0x110f, BIOS settings: hdc:DMA, hdd:pio
[17179573.040000] Probing IDE interface ide0...
[17179573.460000] hda: WDC WD800VE-07HDT0, ATA DISK drive
[17179574.132000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.180000] Probing IDE interface ide1...
[17179575.044000] hdc: PHILIPS DVD+/-RW SDVD8431, ATAPI CD/DVD-ROM drive
[17179575.716000] ide1 at 0x170-0x177,0x376 on irq 15
[17179575.720000] hda: max request size: 128KiB
[17179575.728000] hda: 156301488 sectors (80026 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(100)
[17179575.728000] hda: cache flushes supported
[17179575.728000]  hda: hda1 hda2 hda3 hda4
[17179575.836000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179575.836000] Uniform CD-ROM driver Revision: 3.20
[17179576.288000] usbcore: registered new driver usbfs
[17179576.288000] usbcore: registered new driver hub
[17179576.292000] USB Universal Host Controller Interface driver v3.0
[17179576.292000] ACPI Error (uteval-0269): Return object type is incorrect [\_SB_.PCI0.ALKD._CRS] (Node dbfd2b1c), AE_TYPE
[17179576.292000] ACPI Error (uteval-0275): Type returned from _CRS was incorrect: Integer, expected Btypes: 4 [20060707]
[17179576.292000] ACPI Exception (pci_link-0281): AE_TYPE, Evaluating _CRS [20060707]
[17179576.292000] ACPI: Unable to set IRQ for PCI Interrupt Link [ALKD]. Try pci=noacpi or acpi=off
[17179576.292000] ACPI: Invalid IRQ link routing entry
[17179576.292000] ACPI: Unable to derive IRQ for device 0000:00:10.0
[17179576.292000] ACPI: PCI Interrupt 0000:00:10.0[A]: no GSI - using IRQ 11
[17179576.292000] uhci_hcd 0000:00:10.0: UHCI Host Controller
[17179576.292000] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[17179576.292000] uhci_hcd 0000:00:10.0: irq 11, io base 0x00001200
[17179576.296000] usb usb1: configuration #1 chosen from 1 choice
[17179576.296000] hub 1-0:1.0: USB hub found
[17179576.296000] hub 1-0:1.0: 2 ports detected
[17179576.400000] ACPI Error (uteval-0269): Return object type is incorrect [\_SB_.PCI0.ALKD._CRS] (Node dbfd2b1c), AE_TYPE
[17179576.400000] ACPI Error (uteval-0275): Type returned from _CRS was incorrect: Integer, expected Btypes: 4 [20060707]
[17179576.400000] ACPI Exception (pci_link-0281): AE_TYPE, Evaluating _CRS [20060707]
[17179576.400000] ACPI: Unable to set IRQ for PCI Interrupt Link [ALKD]. Try pci=noacpi or acpi=off
[17179576.400000] ACPI: Invalid IRQ link routing entry
[17179576.400000] ACPI: Unable to derive IRQ for device 0000:00:10.1
[17179576.400000] ACPI: PCI Interrupt 0000:00:10.1[B]: no GSI - using IRQ 7
[17179576.400000] uhci_hcd 0000:00:10.1: UHCI Host Controller
[17179576.400000] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[17179576.400000] uhci_hcd 0000:00:10.1: irq 7, io base 0x00001220
[17179576.400000] usb usb2: configuration #1 chosen from 1 choice
[17179576.400000] hub 2-0:1.0: USB hub found
[17179576.400000] hub 2-0:1.0: 2 ports detected
[17179576.504000] ACPI Error (uteval-0269): Return object type is incorrect [\_SB_.PCI0.ALKD._CRS] (Node dbfd2b1c), AE_TYPE
[17179576.504000] ACPI Error (uteval-0275): Type returned from _CRS was incorrect: Integer, expected Btypes: 4 [20060707]
[17179576.504000] ACPI Exception (pci_link-0281): AE_TYPE, Evaluating _CRS [20060707]
[17179576.504000] ACPI: Unable to set IRQ for PCI Interrupt Link [ALKD]. Try pci=noacpi or acpi=off
[17179576.504000] ACPI: Invalid IRQ link routing entry
[17179576.504000] ACPI: Unable to derive IRQ for device 0000:00:10.2
[17179576.504000] ACPI: PCI Interrupt 0000:00:10.2[C]: no GSI - using IRQ 5
[17179576.504000] uhci_hcd 0000:00:10.2: UHCI Host Controller
[17179576.504000] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[17179576.504000] uhci_hcd 0000:00:10.2: irq 5, io base 0x00001240
[17179576.504000] usb usb3: configuration #1 chosen from 1 choice
[17179576.504000] hub 3-0:1.0: USB hub found
[17179576.504000] hub 3-0:1.0: 2 ports detected
[17179576.608000] PCI: Enabling device 0000:00:10.3 (0000 -> 0002)
[17179576.608000] ACPI Error (uteval-0269): Return object type is incorrect [\_SB_.PCI0.ALKD._CRS] (Node dbfd2b1c), AE_TYPE
[17179576.608000] ACPI Error (uteval-0275): Type returned from _CRS was incorrect: Integer, expected Btypes: 4 [20060707]
[17179576.608000] ACPI Exception (pci_link-0281): AE_TYPE, Evaluating _CRS [20060707]
[17179576.608000] ACPI: Unable to set IRQ for PCI Interrupt Link [ALKD]. Try pci=noacpi or acpi=off
[17179576.608000] ACPI: Invalid IRQ link routing entry
[17179576.608000] ACPI: Unable to derive IRQ for device 0000:00:10.3
[17179576.608000] ACPI: PCI Interrupt 0000:00:10.3[D]: no GSI - using IRQ 10
[17179576.608000] ehci_hcd 0000:00:10.3: EHCI Host Controller
[17179576.608000] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[17179576.608000] ehci_hcd 0000:00:10.3: irq 10, io mem 0x24011000
[17179576.608000] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179576.608000] usb usb4: configuration #1 chosen from 1 choice
[17179576.608000] hub 4-0:1.0: USB hub found
[17179576.608000] hub 4-0:1.0: 6 ports detected
[17179576.744000] Attempting manual resume
[17179576.800000] kjournald starting.  Commit interval 5 seconds
[17179576.800000] EXT3-fs: mounted filesystem with ordered data mode.
[17179577.752000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[17179581.292000] usb 2-1: configuration #1 chosen from 1 choice
[17179585.632000] ath_hal: module license 'Proprietary' taints kernel.
[17179585.636000] ath_hal: 0.9.17.2 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[17179585.808000] wlan: 0.8.4.2 (0.9.2.1)
[17179585.820000] ath_rate_sample: 1.2 (0.9.2.1)
[17179585.824000] ath_pci: 0.9.4.5 (0.9.2.1)
[17179585.824000] PCI: Enabling device 0000:00:06.0 (0000 -> 0002)
[17179585.824000] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 19 (level, low) -> IRQ 185
[17179586.696000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[17179586.696000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179586.696000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[17179586.696000] wifi0: mac 7.8 phy 4.5 radio 5.6
[17179586.696000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[17179586.696000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[17179586.696000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[17179586.696000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[17179586.696000] wifi0: Use hw queue 8 for CAB traffic
[17179586.696000] wifi0: Use hw queue 9 for beacons
[17179587.148000] wifi0: Atheros 5212: mem=0x24000000, irq=185
[17179587.224000] Linux agpgart interface v0.101 (c) Dave Jones
[17179587.244000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179587.244000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179587.280000] irda_init()
[17179587.280000] NET: Registered protocol family 23
[17179587.412000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[17179587.412000] ACPI: PCI Interrupt Link [ALKB] BIOS reported IRQ 11, using IRQ 23
[17179587.412000] ACPI: PCI Interrupt Link [ALKB] enabled at IRQ 23
[17179587.412000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [ALKB] -> GSI 23 (level, low) -> IRQ 193
[17179587.412000] PCI: Via IRQ fixup for 0000:00:12.0, from 11 to 1
[17179587.416000] eth0: VIA Rhine II at 0x1e200, 00:40:d0:8d:27:ed, IRQ 193.
[17179587.420000] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 41e1.
[17179587.432000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 17 (level, low) -> IRQ 169
[17179587.432000] Yenta: CardBus bridge found at 0000:00:09.0 [1734:10ab]
[17179587.432000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179587.432000] Yenta: Routing CardBus interrupts to PCI
[17179587.432000] Yenta TI: socket 0000:00:09.0, mfunc 0x01001002, devctl 0x44
[17179587.468000] input: PC Speaker as /class/input/input1
[17179587.664000] Yenta: ISA IRQ mask 0x0058, PCI irq 169
[17179587.664000] Socket status: 30000006
[17179587.664000] ACPI: PCI Interrupt Link [ALKC] disabled and referenced, BIOS bug
[17179587.664000] ACPI: PCI Interrupt Link [ALKC] BIOS reported IRQ 5, using IRQ 22
[17179587.664000] ACPI: PCI Interrupt Link [ALKC] enabled at IRQ 22
[17179587.664000] ACPI: PCI Interrupt 0000:00:11.6[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 201
[17179587.664000] PCI: Via IRQ fixup for 0000:00:11.6, from 5 to 9
[17179587.668000] PCI: Setting latency timer of device 0000:00:11.6 to 64
[17179587.876000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[17179587.884000] usbcore: registered new driver libusual
[17179587.944000] SCSI subsystem initialized
[17179587.948000] Initializing USB Mass Storage driver...
[17179587.948000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179587.948000] usbcore: registered new driver usb-storage
[17179587.948000] USB Mass Storage support registered.
[17179587.948000] usb-storage: device found at 2
[17179587.948000] usb-storage: waiting for device to settle before scanning
[17179588.184000] agpgart: Detected VIA PM800/PN800/PM880/PN880 chipset
[17179588.192000] agpgart: AGP aperture is 128M @ 0xa0000000
[17179588.192000] ACPI: PCI Interrupt 0000:00:11.5[C] -> Link [ALKC] -> GSI 22 (level, low) -> IRQ 201
[17179588.192000] PCI: Via IRQ fixup for 0000:00:11.5, from 5 to 9
[17179588.192000] PCI: Setting latency timer of device 0000:00:11.5 to 64
[17179588.252000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0xa5a0b1, caps: 0xa04713/0x0
[17179588.308000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[17179588.340000] ts: Compaq touchscreen protocol output
[17179588.568000] cs: IO port probe 0x100-0x3af: clean.
[17179588.568000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179588.572000] cs: IO port probe 0x820-0x8ff: clean.
[17179588.572000] cs: IO port probe 0xc00-0xcf7: clean.
[17179588.572000] cs: IO port probe 0xa00-0xaff: clean.
[17179588.868000] NET: Registered protocol family 17
[17179589.000000] lp: driver loaded but no devices found
[17179589.024000] Adding 1044216k swap on /dev/disk/by-uuid/44af5fbf-d0cd-47f6-9bc3-fd20c655051a.  Priority:-1 extents:1 across:1044216k
[17179589.160000] EXT3 FS on hda1, internal journal
[17179589.412000] kjournald starting.  Commit interval 5 seconds
[17179589.420000] EXT3 FS on hda2, internal journal
[17179589.420000] EXT3-fs: mounted filesystem with ordered data mode.
[17179589.480000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179589.560000] NTFS volume version 3.1.
[17179589.860000] NET: Registered protocol family 10
[17179589.860000] lo: Disabled Privacy Extensions
[17179589.860000] IPv6 over IPv4 tunneling driver
[17179593.136000] usb-storage: device scan complete
[17179593.892000]   Vendor: Generic   Model: MP3 Player        Rev: 0100
[17179593.892000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[17179594.004000] ACPI: AC Adapter [AC] (on-line)
[17179594.068000] ACPI: Battery Slot [BAT0] (battery present)
[17179594.084000] ACPI: Power Button (FF) [PWRF]
[17179594.084000] ACPI: Lid Switch [LID]
[17179594.084000] ACPI: Sleep Button (CM) [SBTN]
[17179594.084000] ACPI: Power Button (CM) [PBTN]
[17179594.228000] ibm_acpi: ec object not found
[17179594.284000] pcc_acpi: loading...
[17179594.400000] ACPI: Video Device [VGA0] (multi-head: yes  rom: no  post: no)
[17179595.152000] SCSI device sda: 1021184 2048-byte hdwr sectors (2091 MB)
[17179595.908000] sda: Write Protect is off
[17179595.908000] sda: Mode Sense: 3e 00 00 00
[17179595.908000] sda: assuming drive cache: write through
[17179597.108000] [drm] Initialized drm 1.0.1 20051102
[17179597.532000] apm: BIOS not found.
[17179597.620000] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 209
[17179597.620000] PCI: Via IRQ fixup for 0000:01:00.0, from 11 to 1
[17179597.620000] [drm] Initialized via 2.7.4 20051116 on minor 0
[17179597.652000] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[17179597.652000] agpgart: Device is in legacy mode, falling back to 2.x
[17179597.652000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 0x mode
[17179597.652000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 0x mode
[17179598.180000] SCSI device sda: 1021184 2048-byte hdwr sectors (2091 MB)
[17179598.932000] sda: Write Protect is off
[17179598.932000] sda: Mode Sense: 3e 00 00 00
[17179598.932000] sda: assuming drive cache: write through
[17179598.932000]  sda: sda1
[17179600.016000] ath0: no IPv6 routers present
[17179600.184000] eth0: no IPv6 routers present
[17179600.196000] sd 0:0:0:0: Attached scsi removable disk sda
[17179600.220000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179600.904000] Bluetooth: Core ver 2.8
[17179600.904000] NET: Registered protocol family 31
[17179600.904000] Bluetooth: HCI device and connection manager initialized
[17179600.904000] Bluetooth: HCI socket layer initialized
[17179600.952000] Bluetooth: L2CAP ver 2.8
[17179600.952000] Bluetooth: L2CAP socket layer initialized
[17179600.976000] Bluetooth: RFCOMM socket layer initialized
[17179600.976000] Bluetooth: RFCOMM TTY layer initialized
[17179600.976000] Bluetooth: RFCOMM ver 1.7
[17179633.204000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17179927.036000] usb 2-1: USB disconnect, address 2
[17180710.516000] ehci_hcd 0000:00:10.3: remove, state 1
[17180710.516000] usb usb4: USB disconnect, address 1
[17180710.516000] ehci_hcd 0000:00:10.3: USB bus 4 deregistered
[17180710.516000] ACPI: Link isn't initialized
[17180710.516000] ACPI: Unable to derive IRQ for device 0000:00:10.3


Does anyone know what this means? I can see there is a problem with the USB device but am not yet able to decipher the message.
I have been trying for a while now to get Ubuntu fully operational with the removable media I have for a while now and have spent hours on the web trying to find answers.
If anyone can tell me what I have to do to resolve this issue I will be well grateful.

Thanks

klittzzer

---

