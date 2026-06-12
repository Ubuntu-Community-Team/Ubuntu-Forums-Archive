---
title: "Wireless No Longer Working After Upgrade"
date: 2006-08-09
forum: Hardware &amp; Laptops
---

### Post by charliejamesuk on 2006-08-09
Have just updated to 6.06 and my wireless card is no longer working, its not even detected by the OS.
The card is PCMCIA so I checked the PCMCIA service which wasn't running. When i try to start the service it fails. I've tried a re-install of PCMCIAUTILS but it still won't start.

Does anybody have any suggestions on getting the card working again?
Any help i much appreciated.

Many Thanks

Charlie

---

### Post by David Corrales on 2006-08-11
Please post your card information (brand, model, etc). That should help better diagnosing your problem :)

---

### Post by charliejamesuk on 2006-08-20
The laptop is a Dell Latitude X300 and the wireless card is a Netgear WG511T PCMCIA Card.

Output of dmesg...
```
17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000d8000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000000f67e000 (usable)
[17179569.184000]  BIOS-e820: 000000000f67e000 - 000000000f6e0000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000000f6e0000 - 000000000f6ec000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000000f6ec000 - 000000000f700000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000000f700000 - 0000000010000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec10000 - 00000000fec20000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fffffc00 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 246MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 63102
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 59006 pages, LIFO batch:15
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 DELL                                  ) @ 0x000f60e0
[17179569.184000] ACPI: RSDT (v001 DELL   Montara  0x06040000  LTP 0x00000000) @ 0x0f6e5db2
[17179569.184000] ACPI: FADT (v001 DELL   MONTARA  0x06040000 PTL  0x00000050) @ 0x0f6ebe9e
[17179569.184000] ACPI: BOOT (v001 DELL   $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x0f6ebfa4
[17179569.184000] ACPI: ASF! (v001 DELL   MONTARA  0x06040000 PTL  0x00000001) @ 0x0f6ebfcc
[17179569.184000] ACPI: SSDT (v001 DELL   MONTARA  0x06040000 INTL 0x20020725) @ 0x0f6e5de6
[17179569.184000] ACPI: DSDT (v001 INTEL  MONTARAG 0x06040000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 10000000:eec10000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (011ee000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[17179569.184000] Detected 1199.108 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.496000] Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179569.496000] Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
[17179569.504000] Memory: 239668k/252408k available (1976k kernel code, 12084k reserved, 606k data, 288k init, 0k highmem)
[17179569.504000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.584000] Calibrating delay using timer specific routine.. 2400.02 BogoMIPS (lpj=4800058)
[17179569.584000] Security Framework v1.0.0 initialized
[17179569.584000] SELinux:  Disabled at boot.
[17179569.584000] Mount-cache hash table entries: 512
[17179569.584000] CPU: After generic identify, caps: a7e9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
[17179569.584000] CPU: After vendor identify, caps: a7e9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
[17179569.584000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179569.584000] CPU: L2 cache: 1024K
[17179569.584000] CPU: After all inits, caps: a7e9f9bf 00000000 00000000 00000040 00000180 00000000 00000000
[17179569.584000] mtrr: v2.0 (20020519)
[17179569.584000] CPU: Intel(R) Pentium(R) M processor 1200MHz stepping 05
[17179569.584000] Enabling fast FPU save and restore... done.
[17179569.584000] Enabling unmasked SIMD FPU exception support... done.
[17179569.584000] Checking 'hlt' instruction... OK.
[17179569.600000] checking if image is initramfs... it is
[17179570.820000] Freeing initrd memory: 6615k freed
[17179570.828000] ACPI: Looking for DSDT ... not found!
[17179570.832000] ACPI: setting ELCR to 0200 (from 0c20)
[17179570.856000] NET: Registered protocol family 16
[17179570.856000] EISA bus registered
[17179570.856000] ACPI: bus type pci registered
[17179570.856000] PCI: PCI BIOS revision 2.10 entry at 0xfd9b0, last bus=2
[17179570.856000] PCI: Using configuration type 1
[17179570.856000] ACPI: Subsystem revision 20051216
[17179570.860000] ACPI: Interpreter enabled
[17179570.860000] ACPI: Using PIC for interrupt routing
[17179570.864000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.864000] PCI: Probing PCI hardware (bus 00)
[17179570.868000] Boot video device is 0000:00:02.0
[17179570.868000] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[17179570.868000] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[17179570.868000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179570.872000] PCI: Transparent bridge - 0000:00:1e.0
[17179570.872000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.872000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[17179570.876000] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
[17179570.876000] ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
[17179570.876000] ACPI: PCI Interrupt Link [LNKC] (IRQs *11)
[17179570.876000] ACPI: PCI Interrupt Link [LNKD] (IRQs *11)
[17179570.876000] ACPI: PCI Interrupt Link [LNKE] (IRQs *5)
[17179570.876000] ACPI: PCI Interrupt Link [LNKF] (IRQs 5) *0, disabled.
[17179570.876000] ACPI: PCI Interrupt Link [LNKG] (IRQs 10) *0, disabled.
[17179570.876000] ACPI: PCI Interrupt Link [LNKH] (IRQs *10)
[17179570.876000] ACPI: Embedded Controller [H_EC] (gpe 28) interrupt mode.
[17179570.884000] ACPI: Power Resource [PFAN] (on)
[17179570.884000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.884000] pnp: PnP ACPI init
[17179570.892000] pnp: PnP ACPI: found 9 devices
[17179570.892000] PnPBIOS: Disabled by ACPI PNP
[17179570.892000] PCI: Using ACPI for IRQ routing
[17179570.892000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.896000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179570.896000] PCI: Bus 3, cardbus bridge: 0000:02:03.0
[17179570.896000]   IO window: 00003000-000030ff
[17179570.896000]   IO window: 00003400-000034ff
[17179570.896000]   PREFETCH window: 20000000-21ffffff
[17179570.896000]   MEM window: 26000000-27ffffff
[17179570.896000] PCI: Bus 7, cardbus bridge: 0000:02:03.1
[17179570.896000]   IO window: 00003800-000038ff
[17179570.896000]   IO window: 00003c00-00003cff
[17179570.896000]   PREFETCH window: 22000000-23ffffff
[17179570.896000]   MEM window: 28000000-29ffffff
[17179570.896000] PCI: Bridge: 0000:00:1e.0
[17179570.896000]   IO window: 3000-3fff
[17179570.896000]   MEM window: e0200000-e02fffff
[17179570.896000]   PREFETCH window: 20000000-23ffffff
[17179570.896000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179570.896000] PCI: Enabling device 0000:02:03.0 (0000 -> 0003)
[17179570.896000] **** SET: Misaligned resource pointer: cf4427c2 Type 07 Len 0
[17179570.896000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[17179570.896000] PCI: setting IRQ 10 as level-triggered
[17179570.896000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[17179570.896000] PCI: Setting latency timer of device 0000:02:03.0 to 64
[17179570.896000] PCI: Enabling device 0000:02:03.1 (0000 -> 0003)
[17179570.896000] **** SET: Misaligned resource pointer: cf4427c2 Type 07 Len 0
[17179570.896000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[17179570.896000] ACPI: PCI Interrupt 0000:02:03.1[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[17179570.896000] PCI: Setting latency timer of device 0000:02:03.1 to 64
[17179570.896000] Simple Boot Flag at 0x38 set to 0x1
[17179570.900000] audit: initializing netlink socket (disabled)
[17179570.900000] audit(1156062179.900:1): initialized
[17179570.900000] VFS: Disk quotas dquot_6.5.1
[17179570.900000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.900000] Initializing Cryptographic API
[17179570.900000] io scheduler noop registered
[17179570.900000] io scheduler anticipatory registered
[17179570.900000] io scheduler deadline registered
[17179570.900000] io scheduler cfq registered
[17179570.900000] isapnp: Scanning for PnP cards...
[17179571.252000] isapnp: No Plug & Play device found
[17179571.268000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179571.272000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179571.272000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179571.272000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179571.272000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179571.272000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179571.272000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.272000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179571.272000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179571.276000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[17179571.276000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[17179571.276000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.276000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.276000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.276000] mice: PS/2 mouse device common for all mice
[17179571.276000] EISA: Probing bus 0 at eisa.0
[17179571.276000] Cannot allocate resource for EISA slot 1
[17179571.276000] Cannot allocate resource for EISA slot 2
[17179571.276000] Cannot allocate resource for EISA slot 3
[17179571.276000] EISA: Detected 0 cards.
[17179571.276000] NET: Registered protocol family 2
[17179571.312000] IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
[17179571.312000] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[17179571.312000] TCP bind hash table entries: 8192 (order: 3, 32768 bytes)
[17179571.312000] TCP: Hash tables configured (established 8192 bind 8192)
[17179571.312000] TCP reno registered
[17179571.312000] TCP bic registered
[17179571.312000] NET: Registered protocol family 1
[17179571.312000] NET: Registered protocol family 8
[17179571.312000] NET: Registered protocol family 20
[17179571.312000] Using IPI Shortcut mode
[17179571.312000] ACPI wakeup devices:
[17179571.312000] LID0 PWRB LANC MPC0 MPC1 MODM
[17179571.312000] ACPI: (supports S0 S3 S4 S5)
[17179571.312000] Freeing unused kernel memory: 288k freed
[17179571.368000] vga16fb: initializing
[17179571.368000] vga16fb: mapped to 0xc00a0000
[17179571.428000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179571.484000] Console: switching to colour frame buffer device 80x25
[17179571.484000] fb0: VGA16 VGA frame buffer device
[17179572.508000] Capability LSM initialized
[17179572.612000] ACPI: Fan [FAN0] (on)
[17179572.616000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[17179572.616000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179572.624000] ACPI: Thermal Zone [THRM] (23 C)
[17179573.052000] ICH4: IDE controller at PCI slot 0000:00:1f.1
[17179573.052000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[17179573.052000] **** SET: Misaligned resource pointer: cf5433c2 Type 07 Len 0
[17179573.052000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[17179573.052000] PCI: setting IRQ 11 as level-triggered
[17179573.052000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179573.052000] ICH4: chipset revision 1
[17179573.052000] ICH4: not 100% native mode: will probe irqs later
[17179573.052000]     ide0: BM-DMA at 0x1810-0x1817, BIOS settings: hda:DMA, hdb:pio
[17179573.052000] Probing IDE interface ide0...
[17179573.340000] hda: FUJITSU MHT2030AT, ATA DISK drive
[17179574.012000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.096000] hda: max request size: 128KiB
[17179574.100000] hda: 58605120 sectors (30005 MB) w/2048KiB Cache, CHS=58140/16/63, UDMA(100)
[17179574.100000] hda: cache flushes supported
[17179574.100000]  hda: hda1 hda2 < hda5 >
[17179574.448000] ieee1394: Initialized config rom entry `ip1394'
[17179574.452000] ohci1394: $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[17179574.452000] ACPI: PCI Interrupt 0000:02:03.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179574.504000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[11]  MMIO=[e0211000-e02117ff]  Max Packet=[2048]
[17179574.512000] usbcore: registered new driver usbfs
[17179574.512000] usbcore: registered new driver hub
[17179574.512000] USB Universal Host Controller Interface driver v2.3
[17179574.512000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[17179574.512000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179574.512000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179574.512000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179574.512000] uhci_hcd 0000:00:1d.0: irq 10, io base 0x00001820
[17179574.516000] hub 1-0:1.0: USB hub found
[17179574.516000] hub 1-0:1.0: 2 ports detected
[17179574.620000] **** SET: Misaligned resource pointer: cf076602 Type 07 Len 0
[17179574.620000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 10
[17179574.620000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[17179574.620000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179574.620000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179574.620000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179574.620000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[17179574.620000] ehci_hcd 0000:00:1d.7: irq 10, io mem 0xe0100000
[17179574.624000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179574.624000] hub 2-0:1.0: USB hub found
[17179574.624000] hub 2-0:1.0: 6 ports detected
[17179574.624000] **** SET: Misaligned resource pointer: cf076402 Type 07 Len 0
[17179574.624000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[17179574.624000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179574.624000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179574.624000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179574.728000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[17179574.728000] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001840
[17179574.728000] hub 3-0:1.0: USB hub found
[17179574.728000] hub 3-0:1.0: 2 ports detected
[17179574.832000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179574.832000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179574.832000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179574.832000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[17179574.832000] uhci_hcd 0000:00:1d.2: irq 11, io base 0x00001860
[17179574.832000] hub 4-0:1.0: USB hub found
[17179574.832000] hub 4-0:1.0: 2 ports detected
[17179574.984000] Probing IDE interface ide1...
[17179575.564000] Attempting manual resume
[17179575.604000] EXT3-fs: mounted filesystem with ordered data mode.
[17179575.616000] kjournald starting.  Commit interval 5 seconds
[17179575.784000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00065b8008133868]
[17179585.900000] Linux agpgart interface v0.101 (c) Dave Jones
[17179585.908000] agpgart: Detected an Intel 855 Chipset.
[17179585.908000] agpgart: Detected 8060K stolen memory.
[17179585.916000] agpgart: AGP aperture is 128M @ 0xe8000000
[17179586.416000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179586.424000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179586.460000] hw_random: RNG not detected
[17179586.804000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[17179586.804000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179586.932000] Real Time Clock Driver v1.12
[17179587.328000] ieee80211_crypt: registered algorithm 'NULL'
[17179587.328000] ieee80211: 802.11 data/management/control stack, git-1.1.7
[17179587.328000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179587.360000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, 1.1.4
[17179587.360000] ipw2100: Copyright(c) 2003-2005 Intel Corporation
[17179587.392000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0xa54ab1, caps: 0x804713/0x0
[17179587.428000] input: SynPS/2 Synaptics TouchPad as /class/input/input1
[17179587.624000] intel8x0_measure_ac97_clock: measured 55435 usecs
[17179587.624000] intel8x0: clocking to 48000
[17179587.624000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[17179587.624000] Yenta: CardBus bridge found at 0000:02:03.0 [1028:014f]
[17179587.752000] Yenta: ISA IRQ mask 0x0038, PCI irq 10
[17179587.752000] Socket status: 30000006
[17179587.752000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[17179587.752000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[17179587.752000] cs: IO port probe 0x3000-0x3fff: clean.
[17179587.752000] pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
[17179587.752000] pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x23ffffff
[17179587.752000] ACPI: PCI Interrupt 0000:02:03.1[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[17179587.752000] Yenta: CardBus bridge found at 0000:02:03.1 [1028:014f]
[17179587.764000] irda_init()
[17179587.764000] NET: Registered protocol family 23
[17179587.812000] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 3 ; dma 3.
[17179587.812000] nsc-ircc, chip->init
[17179587.812000] nsc-ircc, Found chip at base=0x02e
[17179587.812000] nsc-ircc, driver loaded (Dag Brattli)
[17179587.812000] nsc_ircc_open(), can't get iobase of 0x2f8
[17179587.812000] nsc-ircc, Found chip at base=0x02e
[17179587.812000] nsc-ircc, driver loaded (Dag Brattli)
[17179587.812000] nsc_ircc_open(), can't get iobase of 0x2f8
[17179587.812000] pnp: Device 00:06 disabled.
[17179587.880000] Yenta: ISA IRQ mask 0x0030, PCI irq 10
[17179587.880000] Socket status: 30000820
[17179587.880000] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[17179587.880000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[17179587.880000] cs: IO port probe 0x3000-0x3fff: clean.
[17179587.880000] pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
[17179587.880000] pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x23ffffff
[17179587.884000] **** SET: Misaligned resource pointer: ccd27f02 Type 07 Len 0
[17179587.884000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 5
[17179587.884000] PCI: setting IRQ 5 as level-triggered
[17179587.884000] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [LNKE] -> GSI 5 (level, low) -> IRQ 5
[17179587.884000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[17179588.360000] ts: Compaq touchscreen protocol output
[17179588.524000] pccard: CardBus card inserted into slot 1
[17179588.812000] eth0: Radio is disabled by RF switch.
[17179588.948000] cs: IO port probe 0x100-0x3af: clean.
[17179588.948000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179588.948000] cs: IO port probe 0x820-0x8ff: clean.
[17179588.948000] cs: IO port probe 0xc00-0xcf7: clean.
[17179588.948000] cs: IO port probe 0xa00-0xaff: clean.
[17179588.952000] cs: IO port probe 0x100-0x3af: clean.
[17179588.952000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179588.952000] cs: IO port probe 0x820-0x8ff: clean.
[17179588.952000] cs: IO port probe 0xc00-0xcf7: clean.
[17179588.952000] cs: IO port probe 0xa00-0xaff: clean.
[17179588.956000] tg3.c:v3.47 (Dec 28, 2005)
[17179588.956000] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179589.008000] eth1: Tigon3 [partno(BCM95705A50) rev 3001 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000BaseT Ethernet 00:0b:db:e4:48:02
[17179589.008000] eth1: RXcsums[1] LinkChgREG[1] MIirq[1] ASF[0] Split[0] WireSpeed[1] TSOcap[1]
[17179589.008000] eth1: dma_rwctrl[763f0000]
[17179590.784000] lp: driver loaded but no devices found
[17179591.476000] SCSI subsystem initialized
[17179591.548000] sbp2: $Rev: 1306 $ Ben Collins <bcollins@debian.org>
[17179591.548000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179591.548000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179591.656000] Adding 722884k swap on /dev/hda5.  Priority:-1 extents:1 across:722884k
[17179591.760000] tg3: eth0: Link is up at 100 Mbps, full duplex.
[17179591.760000] tg3: eth0: Flow control is on for TX and on for RX.
[17179592.148000] NET: Registered protocol family 17
[17179592.404000] EXT3 FS on hda1, internal journal
[17179592.584000] NET: Registered protocol family 10
[17179592.584000] lo: Disabled Privacy Extensions
[17179592.584000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17179592.584000] IPv6 over IPv4 tunneling driver
[17179592.728000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179592.728000] md: bitmap version 4.39
[17179593.164000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179599.696000] ACPI: AC Adapter [ADP1] (off-line)
[17179599.708000] ACPI: Battery Slot [BAT1] (battery present)
[17179599.708000] ACPI: Battery Slot [BAT2] (battery absent)
[17179599.816000] ACPI: Power Button (FF) [PWRF]
[17179599.816000] ACPI: Lid Switch [LID0]
[17179599.816000] ACPI: Sleep Button (CM) [SLPB]
[17179599.816000] ACPI: Power Button (CM) [PWRB]
[17179599.936000] ibm_acpi: ec object not found
[17179599.972000] pcc_acpi: loading...
[17179600.080000] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[17179602.632000] ppdev: user-space parallel port driver
[17179603.216000] apm: BIOS not found.
[17179603.240000] eth0: no IPv6 routers present
[17179605.020000] ttyS1: LSR safety check engaged!
[17179606.104000] Bluetooth: Core ver 2.8
[17179606.104000] NET: Registered protocol family 31
[17179606.104000] Bluetooth: HCI device and connection manager initialized
[17179606.104000] Bluetooth: HCI socket layer initialized
[17179606.128000] Bluetooth: L2CAP ver 2.8
[17179606.128000] Bluetooth: L2CAP socket layer initialized
[17179606.144000] Bluetooth: RFCOMM socket layer initialized
[17179606.144000] Bluetooth: RFCOMM TTY layer initialized
[17179606.144000] Bluetooth: RFCOMM ver 1.7
[17179609.644000] [drm] Initialized drm 1.0.1 20051102
[17179609.648000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[17179609.648000] [drm] Initialized i915 1.4.0 20060119 on minor 0
[17179609.648000] [drm] Initialized i915 1.4.0 20060119 on minor 1
[17180394.676000] pccard: card ejected from slot 1
[17180396.740000] ACPI: PCI interrupt for device 0000:02:05.0 disabled
[17180396.948000] ACPI: PCI interrupt for device 0000:02:04.0 disabled
[17180396.972000] ieee80211_crypt: unregistered algorithm 'NULL'
[17180400.784000] Stopping tasks: ===========================================================================|
[17180401.252000] Shrinking memory... done (35236 pages freed)
[17180407.612000] ACPI: PCI interrupt for device 0000:02:03.1 disabled
[17180407.612000] ACPI: PCI interrupt for device 0000:02:03.0 disabled
[17180407.612000] ACPI: PCI interrupt for device 0000:00:1f.5 disabled
[17180407.612000] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
[17180407.628000] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
[17180407.628000] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
[17180407.628000] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
[17180407.628000] swsusp: Need to copy 24707 pages
[17180407.628000] swsusp: Restoring Highmem
[17180454.628000] **** SET: Misaligned resource pointer: cef584c2 Type 07 Len 0
[17180454.628000] **** SET: Misaligned resource pointer: cef584c2 Type 07 Len 0
[17180454.628000] **** SET: Misaligned resource pointer: cef584c2 Type 07 Len 0
[17180454.628000] **** SET: Misaligned resource pointer: cef584c2 Type 07 Len 0
[17180454.628000] **** SET: Misaligned resource pointer: cef584c2 Type 07 Len 0
[17180454.628000] **** SET: Misaligned resource pointer: cef584c2 Type 07 Len 0
[17180454.660000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[17180454.660000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[17180454.660000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17180454.660000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17180454.660000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17180454.660000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17180454.660000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17180454.676000] PCI: Enabling device 0000:00:1d.7 (0000 -> 0002)
[17180454.676000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 10 (level, low) -> IRQ 10
[17180454.676000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17180454.676000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17180454.680000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17180454.680000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17180454.680000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17180454.684000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[17180454.684000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17180454.936000] ACPI: PCI Interrupt 0000:02:03.0[A] -> Link [LNKA] -> GSI 10 (level, low) -> IRQ 10
[17180454.936000] ACPI: PCI Interrupt 0000:02:03.1[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[17180454.936000] ACPI: PCI Interrupt 0000:02:03.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17180455.656000] Restarting tasks... done
[17180469.816000] tg3.c:v3.47 (Dec 28, 2005)
[17180469.816000] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17180469.868000] eth0: Tigon3 [partno(BCM95705A50) rev 3001 PHY(5705)] (PCI:33MHz:32-bit) 10/100/1000BaseT Ethernet 00:0b:db:e4:48:02
[17180469.872000] eth0: RXcsums[1] LinkChgREG[1] MIirq[1] ASF[0] Split[0] WireSpeed[1] TSOcap[1]
[17180469.872000] eth0: dma_rwctrl[763f0000]
[17180470.108000] ieee80211_crypt: registered algorithm 'NULL'
[17180470.112000] ieee80211: 802.11 data/management/control stack, git-1.1.7
[17180470.112000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17180470.148000] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, 1.1.4
[17180470.148000] ipw2100: Copyright(c) 2003-2005 Intel Corporation
[17180470.148000] ACPI: PCI Interrupt 0000:02:04.0[A] -> Link [LNKE] -> GSI 5 (level, low) -> IRQ 5
[17180470.148000] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection
[17180471.428000] eth1: Radio is disabled by RF switch.
[17180472.412000] pccard: CardBus card inserted into slot 1
[17180473.044000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17180475.044000] tg3: eth0: Link is up at 100 Mbps, full duplex.
[17180475.044000] tg3: eth0: Flow control is on for TX and on for RX.
[17180475.044000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[17180475.312000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17180477.092000] ACPI: Power Button (FF) [PWRF]
[17180477.092000] ACPI: Lid Switch [LID0]
[17180477.092000] ACPI: Sleep Button (CM) [SLPB]
[17180477.092000] ACPI: Power Button (CM) [PWRB]
[17180477.364000] ACPI: Fan [FAN0] (on)
[17180477.524000] ACPI: Thermal Zone [THRM] (38 C)
[17180478.272000] ACPI: AC Adapter [ADP1] (on-line)
[17180478.368000] ACPI: Battery Slot [BAT1] (battery present)
[17180478.368000] ACPI: Battery Slot [BAT2] (battery absent)
[17180485.528000] eth0: no IPv6 routers present
[17181248.120000] pccard: card ejected from slot 1
[17181345.564000] pccard: CardBus card inserted into slot 1

```


Do you require any other info??

---

