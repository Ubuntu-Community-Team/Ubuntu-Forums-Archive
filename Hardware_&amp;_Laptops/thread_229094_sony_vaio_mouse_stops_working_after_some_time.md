---
title: "sony vaio mouse stops working after some time"
date: 2006-08-04
forum: Hardware &amp; Laptops
---

### Post by sandlion on 2006-08-04
After some time (1min, 5 hours), I get this in dmesg and my mouse stops working (touchpad still works):
```
[17183374.984000] drivers/usb/input/hid-core.c: input irq status -75 received

```

If I unplug it and plug it back in, it works again.
Sometimes the whole computer hangs (no caps lock, no sysreq, total hang).

sony vaio pcg-k17

I can't figure this one out... any ideas are welcome.  Thx.
dmesg
```

[17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000d4000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003bf70000 (usable)
[17179569.184000]  BIOS-e820: 000000003bf70000 - 000000003bf7f000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000003bf7f000 - 000000003bf80000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003bf80000 - 000000003c000000 (reserved)
[17179569.184000]  BIOS-e820: 000000004bf80000 - 000000004c000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[17179569.184000] 63MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 245616
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 16240 pages, LIFO batch:3
[17179569.184000] DMI present.
[17179569.184000] ATI board detected. Disabling timer routing over 8254.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6fc0
[17179569.184000] ACPI: RSDT (v001 SONY   K7       0x06040000  LTP 0x00000000) @ 0x3bf7a3e2
[17179569.184000] ACPI: FADT (v001 SONY   K7       0x06040000 PTL  0x000f4240) @ 0x3bf7ef64
[17179569.184000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x3bf7efd8
[17179569.184000] ACPI: SSDT (v001  INTEL  EISTRef 0x00002000 INTL 0x20030224) @ 0x3bf7a412
[17179569.184000] ACPI: DSDT (v001  SONY  K7       0x06040000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x8008
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 4c000000:b3f80000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda2 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (01782000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 65536 bytes)
[17179569.184000] Detected 3057.199 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.500000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179572.500000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.528000] Memory: 963380k/982464k available (1976k kernel code, 18420k reserved, 606k data, 288k init, 64960k highmem)
[17179572.528000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.608000] Calibrating delay using timer specific routine.. 6118.71 BogoMIPS (lpj=12237432)
[17179572.608000] Security Framework v1.0.0 initialized
[17179572.608000] SELinux:  Disabled at boot.
[17179572.608000] Mount-cache hash table entries: 512
[17179572.608000] CPU: After generic identify, caps: bfebf9ff 00000000 00000000 00000000 00004400 00000000 00000000
[17179572.608000] CPU: After vendor identify, caps: bfebf9ff 00000000 00000000 00000000 00004400 00000000 00000000
[17179572.608000] CPU: Trace cache: 12K uops, L1 D cache: 8K
[17179572.608000] CPU: L2 cache: 512K
[17179572.608000] CPU: After all inits, caps: bfebf9ff 00000000 00000000 00000080 00004400 00000000 00000000
[17179572.608000] mtrr: v2.0 (20020519)
[17179572.608000] CPU: Intel Mobile Intel(R) Pentium(R) 4     CPU 3.06GHz stepping 09
[17179572.608000] Enabling fast FPU save and restore... done.
[17179572.608000] Enabling unmasked SIMD FPU exception support... done.
[17179572.608000] Checking 'hlt' instruction... OK.
[17179572.624000] checking if image is initramfs... it is
[17179573.088000] Freeing initrd memory: 6614k freed
[17179573.104000] ACPI: Looking for DSDT ... not found!
[17179573.108000] ACPI: setting ELCR to 0200 (from 0c00)
[17179573.132000] NET: Registered protocol family 16
[17179573.132000] EISA bus registered
[17179573.132000] ACPI: bus type pci registered
[17179573.132000] PCI: PCI BIOS revision 2.10 entry at 0xfd890, last bus=1
[17179573.132000] PCI: Using configuration type 1
[17179573.136000] ACPI: Subsystem revision 20051216
[17179573.136000] ACPI: Interpreter enabled
[17179573.136000] ACPI: Using PIC for interrupt routing
[17179573.136000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.136000] PCI: Probing PCI hardware (bus 00)
[17179573.140000] PCI quirk: region 8000-803f claimed by ali7101 ACPI
[17179573.140000] PCI quirk: region 8040-805f claimed by ali7101 SMB
[17179573.140000] Boot video device is 0000:01:05.0
[17179573.140000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.140000] ACPI: PCI Interrupt Link [LNK0] (IRQs 4) *0, disabled.
[17179573.140000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3) *11
[17179573.140000] ACPI: PCI Interrupt Link [LNK2] (IRQs 10) *11
[17179573.140000] ACPI: PCI Interrupt Link [LNK3] (IRQs 11) *0, disabled.
[17179573.140000] ACPI: PCI Interrupt Link [LNK4] (IRQs 6) *10
[17179573.140000] ACPI: PCI Interrupt Link [LNK5] (IRQs *11)
[17179573.140000] ACPI: PCI Interrupt Link [LNK6] (IRQs 9) *0, disabled.
[17179573.140000] ACPI: PCI Interrupt Link [LNK7] (IRQs 9) *11
[17179573.140000] ACPI: PCI Interrupt Link [LNK8] (IRQs 3 4 5 7 10 *11)
[17179573.144000] ACPI: Embedded Controller [EC0] (gpe 24) interrupt mode.
[17179573.144000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PPB_._PRT]
[17179573.152000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.152000] pnp: PnP ACPI init
[17179573.156000] pnp: PnP ACPI: found 11 devices
[17179573.156000] PnPBIOS: Disabled by ACPI PNP
[17179573.156000] PCI: Using ACPI for IRQ routing
[17179573.156000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.160000] pnp: 00:04: ioport range 0x40b-0x40b has been reserved
[17179573.160000] pnp: 00:04: ioport range 0x480-0x48f has been reserved
[17179573.160000] pnp: 00:04: ioport range 0x4d0-0x4d1 has been reserved
[17179573.160000] pnp: 00:04: ioport range 0x4d6-0x4d6 has been reserved
[17179573.160000] pnp: 00:04: ioport range 0x8000-0x807f could not be reserved
[17179573.160000] PCI: Bridge: 0000:00:01.0
[17179573.160000]   IO window: a000-afff
[17179573.160000]   MEM window: e0300000-e03fffff
[17179573.160000]   PREFETCH window: f0000000-f7ffffff
[17179573.160000] PCI: Bus 2, cardbus bridge: 0000:00:0a.0
[17179573.160000]   IO window: 00001400-000014ff
[17179573.160000]   IO window: 00001800-000018ff
[17179573.160000]   PREFETCH window: 50000000-51ffffff
[17179573.160000]   MEM window: 52000000-53ffffff
[17179573.160000] **** SET: Misaligned resource pointer: c186f6c2 Type 07 Len 0
[17179573.160000] ACPI: PCI Interrupt Link [LNK0] enabled at IRQ 4
[17179573.160000] PCI: setting IRQ 4 as level-triggered
[17179573.160000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNK0] -> GSI 4 (level, low) -> IRQ 4
[17179573.160000] Simple Boot Flag at 0x35 set to 0x1
[17179573.160000] audit: initializing netlink socket (disabled)
[17179573.160000] audit(1154642377.160:1): initialized
[17179573.160000] highmem bounce pool size: 64 pages
[17179573.160000] VFS: Disk quotas dquot_6.5.1
[17179573.160000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.160000] Initializing Cryptographic API
[17179573.160000] io scheduler noop registered
[17179573.160000] io scheduler anticipatory registered
[17179573.160000] io scheduler deadline registered
[17179573.160000] io scheduler cfq registered
[17179573.160000] Activating ISA DMA hang workarounds.
[17179573.160000] isapnp: Scanning for PnP cards...
[17179573.512000] isapnp: No Plug & Play device found
[17179573.528000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179573.532000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179573.532000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.532000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179573.532000] PCI: Enabling device 0000:00:03.0 (0000 -> 0003)
[17179573.532000] **** SET: Misaligned resource pointer: dfece1c2 Type 07 Len 0
[17179573.532000] ACPI: PCI Interrupt Link [LNK6] enabled at IRQ 9
[17179573.532000] PCI: setting IRQ 9 as level-triggered
[17179573.532000] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNK6] -> GSI 9 (level, low) -> IRQ 9
[17179573.532000] 0000:00:03.0: ttyS9 at I/O 0x1028 (irq = 9) is a 8250
[17179573.532000] 0000:00:03.0: ttyS12 at I/O 0x1040 (irq = 9) is a 8250
[17179573.536000] 0000:00:03.0: ttyS14 at I/O 0x1050 (irq = 9) is a 8250
[17179573.536000] 0000:00:03.0: ttyS16 at I/O 0x1060 (irq = 9) is a 8250
[17179573.536000] 0000:00:03.0: ttyS18 at I/O 0x1070 (irq = 9) is a 8250
[17179573.536000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179573.536000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.536000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.536000] mice: PS/2 mouse device common for all mice
[17179573.536000] EISA: Probing bus 0 at eisa.0
[17179573.536000] Cannot allocate resource for EISA slot 1
[17179573.536000] Cannot allocate resource for EISA slot 8
[17179573.536000] EISA: Detected 0 cards.
[17179573.536000] NET: Registered protocol family 2
[17179573.572000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179573.572000] TCP established hash table entries: 131072 (order: 7, 524288 bytes)
[17179573.572000] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[17179573.572000] TCP: Hash tables configured (established 131072 bind 65536)
[17179573.572000] TCP reno registered
[17179573.572000] TCP bic registered
[17179573.572000] NET: Registered protocol family 1
[17179573.572000] NET: Registered protocol family 8
[17179573.572000] NET: Registered protocol family 20
[17179573.572000] Using IPI Shortcut mode
[17179573.572000] ACPI wakeup devices: 
[17179573.572000] PCI0 SLT1 ENET MODM USB1 USB2 USB3 
[17179573.572000] ACPI: (supports S0 S3 S4 S5)
[17179573.572000] Freeing unused kernel memory: 288k freed
[17179573.576000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.620000] vga16fb: initializing
[17179573.620000] vga16fb: mapped to 0xc00a0000
[17179573.740000] Console: switching to colour frame buffer device 80x30
[17179573.740000] fb0: VGA16 VGA frame buffer device
[17179574.848000] Capability LSM initialized
[17179574.880000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179574.880000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179574.884000] ACPI: Thermal Zone [TZ01] (36 C)
[17179575.444000] ALI15X3: IDE controller at PCI slot 0000:00:0f.0
[17179575.444000] ACPI: PCI Interrupt 0000:00:0f.0[A]: no GSI
[17179575.444000] ALI15X3: chipset revision 196
[17179575.444000] ALI15X3: not 100% native mode: will probe irqs later
[17179575.444000]     ide0: BM-DMA at 0x8080-0x8087, BIOS settings: hda:DMA, hdb:pio
[17179575.444000]     ide1: BM-DMA at 0x8088-0x808f, BIOS settings: hdc:DMA, hdd:pio
[17179575.444000] Probing IDE interface ide0...
[17179575.732000] hda: SAMSUNG MP0603H, ATA DISK drive
[17179576.404000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179576.496000] Probing IDE interface ide1...
[17179577.236000] hdc: PIONEER DVD-RW DVR-K12D, ATAPI CD/DVD-ROM drive
[17179577.908000] ide1 at 0x170-0x177,0x376 on irq 15
[17179577.920000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache, UDMA(33)
[17179577.920000] Uniform CD-ROM driver Revision: 3.20
[17179577.924000] hda: max request size: 128KiB
[17179577.924000] hda: 117304992 sectors (60060 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[17179577.924000] hda: cache flushes supported
[17179577.924000]  hda: hda1 hda2 hda3 < hda5 >
[17179578.564000] ieee1394: Initialized config rom entry `ip1394'
[17179578.568000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[17179578.568000] **** SET: Misaligned resource pointer: df854602 Type 07 Len 0
[17179578.568000] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 10
[17179578.568000] PCI: setting IRQ 10 as level-triggered
[17179578.568000] ACPI: PCI Interrupt 0000:00:0a.2[C] -> Link [LNK2] -> GSI 10 (level, low) -> IRQ 10
[17179578.616000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[10]  MMIO=[e000b000-e000b7ff]  Max Packet=[2048]
[17179578.628000] usbcore: registered new driver usbfs
[17179578.628000] usbcore: registered new driver hub
[17179578.628000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179578.628000] ACPI: PCI Interrupt 0000:00:0c.0[A] -> Link [LNK2] -> GSI 10 (level, low) -> IRQ 10
[17179578.628000] ohci_hcd 0000:00:0c.0: OHCI Host Controller
[17179578.632000] ohci_hcd 0000:00:0c.0: new USB bus registered, assigned bus number 1
[17179578.632000] ohci_hcd 0000:00:0c.0: irq 10, io mem 0xe0009000
[17179578.664000] hub 1-0:1.0: USB hub found
[17179578.664000] hub 1-0:1.0: 3 ports detected
[17179578.768000] **** SET: Misaligned resource pointer: dfd8edc2 Type 07 Len 0
[17179578.768000] ACPI: PCI Interrupt Link [LNK4] enabled at IRQ 6
[17179578.768000] PCI: setting IRQ 6 as level-triggered
[17179578.768000] ACPI: PCI Interrupt 0000:00:0c.1[B] -> Link [LNK4] -> GSI 6 (level, low) -> IRQ 6
[17179578.768000] ohci_hcd 0000:00:0c.1: OHCI Host Controller
[17179578.768000] ohci_hcd 0000:00:0c.1: new USB bus registered, assigned bus number 2
[17179578.768000] ohci_hcd 0000:00:0c.1: irq 6, io mem 0xe000a000
[17179578.800000] hub 2-0:1.0: USB hub found
[17179578.800000] hub 2-0:1.0: 2 ports detected
[17179578.904000] **** SET: Misaligned resource pointer: dfd8eac2 Type 07 Len 0
[17179578.904000] ACPI: PCI Interrupt Link [LNK5] enabled at IRQ 11
[17179578.904000] PCI: setting IRQ 11 as level-triggered
[17179578.904000] ACPI: PCI Interrupt 0000:00:0c.2[C] -> Link [LNK5] -> GSI 11 (level, low) -> IRQ 11
[17179578.904000] ehci_hcd 0000:00:0c.2: EHCI Host Controller
[17179578.928000] ehci_hcd 0000:00:0c.2: new USB bus registered, assigned bus number 3
[17179578.928000] ehci_hcd 0000:00:0c.2: irq 11, io mem 0xe000b800
[17179578.928000] ehci_hcd 0000:00:0c.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179578.928000] hub 3-0:1.0: USB hub found
[17179578.928000] hub 3-0:1.0: 5 ports detected
[17179579.176000] Attempting manual resume
[17179579.232000] EXT3-fs: mounted filesystem with ordered data mode.
[17179579.248000] kjournald starting.  Commit interval 5 seconds
[17179579.520000] usb 2-1: new low speed USB device using ohci_hcd and address 3
[17179579.888000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[08004603019a9505]
[17179592.160000] ath_hal: module license 'Proprietary' taints kernel.
[17179592.160000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
[17179592.204000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179592.220000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179592.352000] wlan: 0.8.6.0 (EXPERIMENTAL)
[17179592.372000] ath_rate_sample: 1.2
[17179592.380000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
[17179592.380000] PCI: Enabling device 0000:00:09.0 (0000 -> 0002)
[17179592.384000] **** SET: Misaligned resource pointer: dfaefc02 Type 07 Len 0
[17179592.384000] ACPI: PCI Interrupt Link [LNK3] enabled at IRQ 11
[17179592.384000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNK3] -> GSI 11 (level, low) -> IRQ 11
[17179592.804000] Build date: Jul 10 2006
[17179592.804000] Debugging version (IEEE80211)
[17179592.804000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[17179592.804000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179592.804000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
[17179592.804000] ath0: mac 5.9 phy 4.3 radio 4.6
[17179592.804000] ath0: Use hw queue 1 for WME_AC_BE traffic
[17179592.804000] ath0: Use hw queue 0 for WME_AC_BK traffic
[17179592.804000] ath0: Use hw queue 2 for WME_AC_VI traffic
[17179592.804000] ath0: Use hw queue 3 for WME_AC_VO traffic
[17179592.804000] ath0: Use hw queue 8 for CAB traffic
[17179592.804000] ath0: Use hw queue 9 for beacons
[17179592.804000] Debugging version (ATH)
[17179592.804000] ath0: Atheros 5212: mem=0x54000000, irq=11
[17179592.968000] ali15x3_smbus 0000:00:06.0: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[17179592.968000] ali15x3_smbus 0000:00:06.0: ALI15X3 not detected, module not inserted.
[17179593.028000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNK0] -> GSI 4 (level, low) -> IRQ 4
[17179593.028000] Yenta: CardBus bridge found at 0000:00:0a.0 [104d:8175]
[17179593.028000] Yenta: Enabling burst memory read transactions
[17179593.028000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179593.028000] Yenta: Routing CardBus interrupts to PCI
[17179593.028000] Yenta TI: socket 0000:00:0a.0, mfunc 0x000a1b22, devctl 0x64
[17179593.040000] Real Time Clock Driver v1.12
[17179593.100000] 8139too Fast Ethernet driver 0.9.27
[17179593.112000] Linux agpgart interface v0.101 (c) Dave Jones
[17179593.112000] agpgart: Detected Ati IGP345M chipset
[17179593.128000] agpgart: AGP aperture is 128M @ 0xe8000000
[17179593.132000] parport: PnPBIOS parport detected.
[17179593.132000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179593.140000] input: PC Speaker as /class/input/input1
[17179593.260000] Yenta: ISA IRQ mask 0x0028, PCI irq 4
[17179593.260000] Socket status: 30000006
[17179593.288000] **** SET: Misaligned resource pointer: f7642cc2 Type 07 Len 0
[17179593.288000] ACPI: PCI Interrupt Link [LNK7] enabled at IRQ 9
[17179593.288000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LNK7] -> GSI 9 (level, low) -> IRQ 9
[17179593.400000] **** SET: Misaligned resource pointer: f7642cc2 Type 07 Len 0
[17179593.400000] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 3
[17179593.400000] PCI: setting IRQ 3 as level-triggered
[17179593.400000] ACPI: PCI Interrupt 0000:00:12.0[A] -> Link [LNK1] -> GSI 3 (level, low) -> IRQ 3
[17179593.404000] eth0: RealTek RTL8139 at 0xf89cec00, 08:00:46:d0:4b:fa, IRQ 3
[17179593.404000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[17179593.412000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179593.524000] usbcore: registered new driver hiddev
[17179593.536000] input: HP Mouse as /class/input/input2
[17179593.536000] input: USB HID v1.00 Mouse [HP Mouse] on usb-0000:00:0c.1-1
[17179593.536000] usbcore: registered new driver usbhid
[17179593.536000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179593.564000] ts: Compaq touchscreen protocol output
[17179593.868000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x256eb1, caps: 0xa04753/0x0
[17179593.912000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[17179594.028000] cs: IO port probe 0x100-0x3af: excluding 0x200-0x207 0x220-0x22f 0x330-0x337 0x388-0x38f
[17179594.032000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179594.032000] cs: IO port probe 0x820-0x8ff: clean.
[17179594.032000] cs: IO port probe 0xc00-0xcf7: clean.
[17179594.032000] cs: IO port probe 0xa00-0xaff: clean.
[17179594.328000] AC'97 1 does not respond - RESET
[17179594.328000] AC'97 1 access is not valid [0xffffffff], removing mixer.
[17179594.328000] ali mixer 1 creating error.
[17179594.668000] lp0: using parport0 (interrupt-driven).
[17179594.716000] SCSI subsystem initialized
[17179594.728000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[17179594.728000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179594.728000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179594.796000] Adding 2000052k swap on /dev/hda5.  Priority:-1 extents:1 across:2000052k
[17179594.920000] EXT3 FS on hda2, internal journal
[17179595.120000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179595.120000] md: bitmap version 4.39
[17179595.564000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179596.248000] cdrom: open failed.
[17179598.228000] ACPI: AC Adapter [ACAD] (on-line)
[17179598.372000] ACPI: Battery Slot [BAT1] (battery absent)
[17179598.456000] ACPI: Power Button (FF) [PWRF]
[17179598.456000] ACPI: Sleep Button (CM) [SBTN]
[17179598.456000] ACPI: Power Button (CM) [PBTN]
[17179598.456000] ACPI: Lid Switch [LID]
[17179598.552000] ibm_acpi: ec object not found
[17179598.580000] pcc_acpi: loading...
[17179598.604000] ACPI Sony Notebook Control Driver v0.2 successfully installed
[17179598.672000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[17179599.192000] acpi-cpufreq: CPU0 - ACPI performance management activated.
[17179603.948000] ppdev: user-space parallel port driver
[17179604.756000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179604.756000] apm: overridden by ACPI.
[17179609.896000] eth0: link down
[17179611.632000] input: Sony Vaio Jogdial as /class/input/input4
[17179611.664000] input: Sony Vaio Keys as /class/input/input5
[17179611.724000] sonypi: Sony Programmable I/O Controller Driverv1.26.
[17179611.724000] sonypi: detected type2 model, verbose = 0, fnkeyinit = off, camera = off, compat = off, mask = 0xffffffff, useinput = on, acpi = on
[17179611.724000] sonypi: enabled at irq=11, port1=0x1080, port2=0x1084
[17179611.724000] sonypi: device allocated minor is 61
[17179614.016000] NET: Registered protocol family 10
[17179614.016000] lo: Disabled Privacy Extensions
[17179614.016000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179614.016000] IPv6 over IPv4 tunneling driver
[17179614.944000] Bluetooth: Core ver 2.8
[17179614.944000] NET: Registered protocol family 31
[17179614.944000] Bluetooth: HCI device and connection manager initialized
[17179614.944000] Bluetooth: HCI socket layer initialized
[17179614.992000] Bluetooth: L2CAP ver 2.8
[17179614.992000] Bluetooth: L2CAP socket layer initialized
[17179615.028000] Bluetooth: RFCOMM socket layer initialized
[17179615.028000] Bluetooth: RFCOMM TTY layer initialized
[17179615.028000] Bluetooth: RFCOMM ver 1.7
[17179624.896000] ath0: no IPv6 routers present
[17179640.660000] NET: Registered protocol family 17
[17179659.068000] ath0: no IPv6 routers present
[17179835.556000] usb 3-1: new high speed USB device using ehci_hcd and address 3
[17179835.688000] usb 3-1: config 1 descriptor has 1 excess byte, ignoring
[17179835.884000] Initializing USB Mass Storage driver...
[17179835.884000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179835.884000] usb-storage: device found at 3
[17179835.884000] usb-storage: waiting for device to settle before scanning
[17179835.884000] usbcore: registered new driver usb-storage
[17179835.884000] USB Mass Storage support registered.
[17179846.320000] usb 3-1: USB disconnect, address 3
[17179846.320000] usb-storage: device scan complete
[17179849.416000] usb 3-1: new high speed USB device using ehci_hcd and address 4
[17179849.548000] usb 3-1: config 1 descriptor has 1 excess byte, ignoring
[17179849.548000] scsi1 : SCSI emulation for USB Mass Storage devices
[17179849.548000] usb-storage: device found at 4
[17179849.548000] usb-storage: waiting for device to settle before scanning
[17179860.272000]  1:0:0:0: scsi: Device offlined - not ready after error recovery
[17179860.272000] usb-storage: device scan complete
[17179860.380000] usb 3-1: USB disconnect, address 4
[17179870.584000] usb 3-1: new high speed USB device using ehci_hcd and address 5
[17179870.716000] usb 3-1: config 1 descriptor has 1 excess byte, ignoring
[17179870.716000] scsi2 : SCSI emulation for USB Mass Storage devices
[17179870.716000] usb-storage: device found at 5
[17179870.716000] usb-storage: waiting for device to settle before scanning
[17179875.716000]   Vendor: TOSHIBA   Model: MK6022GAX         Rev: 0811
[17179875.716000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179875.736000] usb-storage: device scan complete
[17179875.772000] Driver 'sd' needs updating - please use bus_type methods
[17179875.776000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[17179875.776000] sda: assuming drive cache: write through
[17179875.780000] SCSI device sda: 117210240 512-byte hdwr sectors (60012 MB)
[17179875.780000] sda: assuming drive cache: write through
[17179875.780000]  sda: sda1 sda2 < sda5 >
[17179875.864000] sd 2:0:0:0: Attached scsi disk sda
[17179875.876000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[17179876.852000] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[17179876.852000] kjournald starting.  Commit interval 5 seconds
[17179876.852000] EXT3 FS on sda1, internal journal
[17179876.852000] EXT3-fs: recovery complete.
[17179876.856000] EXT3-fs: mounted filesystem with ordered data mode.
[17180548.476000] usb 3-1: USB disconnect, address 5
[17183374.984000] drivers/usb/input/hid-core.c: input irq status -75 received
[17183381.584000] usb 2-1: USB disconnect, address 3
[17183385.584000] ohci_hcd 0000:00:0c.1: IRQ INTR_SF lossage
[17183386.288000] usb 1-1: new low speed USB device using ohci_hcd and address 2
[17183386.528000] input: HP Mouse as /class/input/input6
[17183386.528000] input: USB HID v1.00 Mouse [HP Mouse] on usb-0000:00:0c.0-1


```


lspci
```
0000:00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
0000:00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
0000:00:03.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
0000:00:04.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
0000:00:06.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
0000:00:07.0 ISA bridge: ALi Corporation M1533 PCI to ISA Bridge [Aladdin IV]
0000:00:09.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
0000:00:0a.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
0000:00:0a.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
0000:00:0a.3 Mass storage controller: Texas Instruments PCI7420/PCI7620 Dual Socket CardBus and Smart Card Cont. w/ 1394a-2000 OHCI Two-Port  PHY/Link-Layer Cont. an
0000:00:0c.0 USB Controller: NEC Corporation USB (rev 43)
0000:00:0c.1 USB Controller: NEC Corporation USB (rev 43)
0000:00:0c.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
0000:00:0f.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
0000:00:12.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M


```

---

### Post by madchicken on 2006-08-04
Same problem here with a Vaio PCGK195HP.
I've read somewhere is a problem with the cpu scaling and the kernel.
I'm searching among bugs in Launchpad...

---

### Post by madchicken on 2006-08-04
I found this:

[http://bugzilla.kernel.org/show_bug.cgi?id=4724](http://bugzilla.kernel.org/show_bug.cgi?id=4724)

It seems that someone must reboot the system to solve the problem...

---

### Post by sandlion on 2006-08-04
thx madchicken

yeah man, what you are finding is consistent w/ what i'm seeing here

i bought a new mouse and keyboard, still happens (that was a few weeks ago).

i'm wondering if my usb port itself is hosed on the laptop?

---

