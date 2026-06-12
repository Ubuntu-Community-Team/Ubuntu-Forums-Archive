---
title: "USB TV Device to work With Lucid lynx"
date: 2010-09-08
forum: Hardware
---

### Post by Nabeel Abbas on 2010-09-08
I hav a [Dany USB Tv Device]("http://www.danytech.com/presentation/viewproduct.aspx?Product_Id=182") which i used to use with Windows,but Since its drivers and a TV player ,that came bundled with it are for windows,So can there be a way to run it on LINUX  :D

---

### Post by DemonBob on 2010-09-08
There may be...

Hook up the device, reboot, then run the following commands and post the output of 

```
sudo lsusb
```

```
dmesg
```

Copy the output of both commands and post them here.

And

---

### Post by Nabeel Abbas on 2010-09-09
output of lsusb
> Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 15d9:0a4c Dexon 
Bus 002 Device 002: ID 05e3:0606 Genesys Logic, Inc. USB 2.0 Hub / D-Link DUB-H4 USB 2.0 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1f71:3301  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

and of dmesg> 
[    0.126224] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.126275] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xe8000000-0xefffffff]
[    0.126394] pci 0000:00:1d.0: reg 20 io port: [0xbf80-0xbf9f]
[    0.126448] pci 0000:00:1d.1: reg 20 io port: [0xbf40-0xbf5f]
[    0.126502] pci 0000:00:1d.2: reg 20 io port: [0xbf20-0xbf3f]
[    0.126565] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf4fffc00-0xf4ffffff]
[    0.126623] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.126629] pci 0000:00:1d.7: PME# disabled
[    0.126722] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[    0.126727] pci 0000:00:1f.0: quirk: region 0880-08bf claimed by ICH4 GPIO
[    0.126752] pci 0000:00:1f.1: reg 10 io port: [0x1f0-0x1f7]
[    0.126760] pci 0000:00:1f.1: reg 14 io port: [0x3f4-0x3f7]
[    0.126768] pci 0000:00:1f.1: reg 18 io port: [0x170-0x177]
[    0.126776] pci 0000:00:1f.1: reg 1c io port: [0x374-0x377]
[    0.126783] pci 0000:00:1f.1: reg 20 io port: [0xbfa0-0xbfaf]
[    0.126791] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    0.126836] pci 0000:00:1f.5: reg 10 io port: [0xb800-0xb8ff]
[    0.126843] pci 0000:00:1f.5: reg 14 io port: [0xbc40-0xbc7f]
[    0.126851] pci 0000:00:1f.5: reg 18 32bit mmio: [0xf4fff800-0xf4fff9ff]
[    0.126858] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xf4fff400-0xf4fff4ff]
[    0.126889] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    0.126894] pci 0000:00:1f.5: PME# disabled
[    0.126925] pci 0000:00:1f.6: reg 10 io port: [0xb400-0xb4ff]
[    0.126932] pci 0000:00:1f.6: reg 14 io port: [0xb080-0xb0ff]
[    0.126970] pci 0000:00:1f.6: PME# supported from D0 D3hot D3cold
[    0.126975] pci 0000:00:1f.6: PME# disabled
[    0.127012] pci 0000:01:00.0: reg 10 32bit mmio: [0xfc000000-0xfcffffff]
[    0.127019] pci 0000:01:00.0: reg 14 32bit mmio pref: [0xf0000000-0xf3ffffff]
[    0.127038] pci 0000:01:00.0: reg 30 32bit mmio pref: [0x80000000-0x8001ffff]
[    0.127090] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
[    0.127094] pci 0000:00:01.0: bridge 32bit mmio: [0xfc000000-0xfdffffff]
[    0.127099] pci 0000:00:01.0: bridge 32bit mmio pref: [0xf0000000-0xf3ffffff]
[    0.127155] pci 0000:02:00.0: reg 10 64bit mmio: [0xfaff0000-0xfaffffff]
[    0.127208] pci 0000:02:00.0: PME# supported from D3hot D3cold
[    0.127213] pci 0000:02:00.0: PME# disabled
[    0.127249] pci 0000:02:01.0: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.127269] pci 0000:02:01.0: supports D1 D2
[    0.127272] pci 0000:02:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.127277] pci 0000:02:01.0: PME# disabled
[    0.127312] pci 0000:02:01.1: reg 10 32bit mmio: [0x000000-0x000fff]
[    0.127332] pci 0000:02:01.1: supports D1 D2
[    0.127335] pci 0000:02:01.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.127340] pci 0000:02:01.1: PME# disabled
[    0.127374] pci 0000:02:01.2: reg 10 32bit mmio: [0xfafef800-0xfafeffff]
[    0.127382] pci 0000:02:01.2: reg 14 32bit mmio: [0xfafe8000-0xfafebfff]
[    0.127422] pci 0000:02:01.2: supports D1 D2
[    0.127425] pci 0000:02:01.2: PME# supported from D0 D1 D2 D3hot
[    0.127430] pci 0000:02:01.2: PME# disabled
[    0.127461] pci 0000:02:01.3: reg 10 io port: [0xecf8-0xecff]
[    0.127539] pci 0000:02:03.0: reg 10 32bit mmio: [0xfafee000-0xfafeefff]
[    0.127584] pci 0000:02:03.0: PME# supported from D0 D3hot D3cold
[    0.127589] pci 0000:02:03.0: PME# disabled
[    0.127628] pci 0000:00:1e.0: transparent bridge
[    0.127634] pci 0000:00:1e.0: bridge io port: [0xd000-0xefff]
[    0.127639] pci 0000:00:1e.0: bridge 32bit mmio: [0xf6000000-0xfbffffff]
[    0.127684] pci_bus 0000:00: on NUMA node 0
[    0.127690] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.127951] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.128048] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.149544] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[    0.149685] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
[    0.149821] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
[    0.149958] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
[    0.150075] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.150218] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.150357] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.150363] vgaarb: loaded
[    0.150522] SCSI subsystem initialized
[    0.150586] libata version 3.00 loaded.
[    0.150685] usbcore: registered new interface driver usbfs
[    0.150701] usbcore: registered new interface driver hub
[    0.150731] usbcore: registered new device driver usb
[    0.150885] ACPI: WMI: Mapper loaded
[    0.150888] PCI: Using ACPI for IRQ routing
[    0.151072] NetLabel: Initializing
[    0.151075] NetLabel:  domain hash size = 128
[    0.151077] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.151095] NetLabel:  unlabeled traffic allowed by default
[    0.151143] Switching to clocksource tsc
[    0.152001] AppArmor: AppArmor Filesystem Enabled
[    0.152001] pnp: PnP ACPI init
[    0.152001] ACPI: bus type pnp registered
[    0.161557] pnp 00:02: io resource (0x800-0x805) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.161563] pnp 00:02: io resource (0x808-0x80f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.161644] pnp 00:03: io resource (0x806-0x807) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.161649] pnp 00:03: io resource (0x810-0x85f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.161653] pnp 00:03: io resource (0x860-0x87f) overlaps 0000:00:1f.0 BAR 13 (0x800-0x87f), disabling
[    0.190765] pnp: PnP ACPI: found 14 devices
[    0.190769] ACPI: ACPI bus type pnp unregistered
[    0.190775] PnPBIOS: Disabled by ACPI PNP
[    0.190792] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[    0.190796] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    0.190801] system 00:00: iomem range 0xc0000-0xcffff could not be reserved
[    0.190805] system 00:00: iomem range 0xe0000-0xfffff could not be reserved
[    0.190809] system 00:00: iomem range 0x100000-0x1ffeffff could not be reserved
[    0.190813] system 00:00: iomem range 0x1fff0000-0x1fffffff has been reserved
[    0.190817] system 00:00: iomem range 0xfeda0000-0xfedfffff has been reserved
[    0.190821] system 00:00: iomem range 0xffb00000-0xffbfffff has been reserved
[    0.190830] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.190837] system 00:03: ioport range 0xf400-0xf4fe has been reserved
[    0.190842] system 00:03: ioport range 0x880-0x8bf has been reserved
[    0.190845] system 00:03: ioport range 0x8c0-0x8df has been reserved
[    0.190849] system 00:03: ioport range 0x8e0-0x8ff has been reserved
[    0.190858] system 00:08: ioport range 0x900-0x97f has been reserved
[    0.225586] pci 0000:01:00.0: BAR 6: no parent found for of device [0x80000000-0x8001ffff]
[    0.225617] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.225621] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.225626] pci 0000:00:01.0:   MEM window: 0xfc000000-0xfdffffff
[    0.225631] pci 0000:00:01.0:   PREFETCH window: 0xf0000000-0xf3ffffff
[    0.225647] pci 0000:02:01.0: CardBus bridge, secondary bus 0000:03
[    0.225651] pci 0000:02:01.0:   IO window: 0x00d000-0x00d0ff
[    0.225656] pci 0000:02:01.0:   IO window: 0x00d400-0x00d4ff
[    0.225661] pci 0000:02:01.0:   PREFETCH window: 0x20000000-0x23ffffff
[    0.225667] pci 0000:02:01.0:   MEM window: 0x2c000000-0x2fffffff
[    0.225672] pci 0000:02:01.1: CardBus bridge, secondary bus 0000:07
[    0.225675] pci 0000:02:01.1:   IO window: 0x00d800-0x00d8ff
[    0.225680] pci 0000:02:01.1:   IO window: 0x00dc00-0x00dcff
[    0.225685] pci 0000:02:01.1:   PREFETCH window: 0x24000000-0x27ffffff
[    0.225691] pci 0000:02:01.1:   MEM window: 0x30000000-0x33ffffff
[    0.225696] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.225700] pci 0000:00:1e.0:   IO window: 0xd000-0xefff
[    0.225707] pci 0000:00:1e.0:   MEM window: 0xf6000000-0xfbffffff
[    0.225712] pci 0000:00:1e.0:   PREFETCH window: 0x20000000-0x27ffffff
[    0.225732] pci 0000:00:1e.0: setting latency timer to 64
[    0.225741] pci 0000:02:01.0: enabling device (0000 -> 0003)
[    0.225937] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    0.225940] PCI: setting IRQ 11 as level-triggered
[    0.225946] pci 0000:02:01.0: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.225960] pci 0000:02:01.1: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.225968] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.225971] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.225975] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    0.225979] pci_bus 0000:01: resource 1 mem: [0xfc000000-0xfdffffff]
[    0.225982] pci_bus 0000:01: resource 2 pref mem [0xf0000000-0xf3ffffff]
[    0.225986] pci_bus 0000:02: resource 0 io:  [0xd000-0xefff]
[    0.225989] pci_bus 0000:02: resource 1 mem: [0xf6000000-0xfbffffff]
[    0.225993] pci_bus 0000:02: resource 2 pref mem [0x20000000-0x27ffffff]
[    0.225997] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.226000] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.226004] pci_bus 0000:03: resource 0 io:  [0xd000-0xd0ff]
[    0.226007] pci_bus 0000:03: resource 1 io:  [0xd400-0xd4ff]
[    0.226010] pci_bus 0000:03: resource 2 pref mem [0x20000000-0x23ffffff]
[    0.226014] pci_bus 0000:03: resource 3 mem: [0x2c000000-0x2fffffff]
[    0.226018] pci_bus 0000:07: resource 0 io:  [0xd800-0xd8ff]
[    0.226021] pci_bus 0000:07: resource 1 io:  [0xdc00-0xdcff]
[    0.226025] pci_bus 0000:07: resource 2 pref mem [0x24000000-0x27ffffff]
[    0.226028] pci_bus 0000:07: resource 3 mem: [0x30000000-0x33ffffff]
[    0.226081] NET: Registered protocol family 2
[    0.226217] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.226624] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.226774] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.226922] TCP: Hash tables configured (established 16384 bind 16384)
[    0.226926] TCP reno registered
[    0.227022] NET: Registered protocol family 1
[    0.227124] pci 0000:01:00.0: Boot video device
[    0.227244] Simple Boot Flag at 0x79 set to 0x1
[    0.227350] cpufreq-nforce2: No nForce2 chipset.
[    0.227379] Scanning for low memory corruption every 60 seconds
[    0.227549] audit: initializing netlink socket (disabled)
[    0.227569] type=2000 audit(1283973005.224:1): initialized
[    0.241023] Trying to unpack rootfs image as initramfs...
[    0.257047] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.259337] VFS: Disk quotas dquot_6.5.2
[    0.259433] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.265032] fuse init (API version 7.13)
[    0.265193] msgmni has been set to 977
[    0.265535] alg: No test for stdrng (krng)
[    0.265630] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.265634] io scheduler noop registered
[    0.265637] io scheduler anticipatory registered
[    0.265639] io scheduler deadline registered
[    0.265705] io scheduler cfq registered (default)
[    0.265875] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.265905] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.266415] ACPI: AC Adapter [AC] (on-line)
[    0.266533] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    0.266867] ACPI: Lid Switch [LID]
[    0.266924] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    0.266930] ACPI: Power Button [PBTN]
[    0.266993] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.266996] ACPI: Sleep Button [SBTN]
[    0.267542] Marking TSC unstable due to TSC halts in idle
[    0.267594] processor LNXCPU:00: registered as cooling_device0
[    0.276854] Switching to clocksource acpi_pm
[    0.291521] thermal LNXTHERM:01: registered as thermal_zone0
[    0.291533] ACPI: Thermal Zone [THM] (56 C)
[    0.300399] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.300509] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.300615] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.301073] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.301265] isapnp: Scanning for PnP cards...
[    0.379978] ACPI: Battery Slot [BAT1] (battery absent)
[    0.380110] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[    0.380115] PCI: setting IRQ 5 as level-triggered
[    0.380122] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[    0.380135] serial 0000:00:1f.6: PCI INT B disabled
[    0.381534] brd: module loaded
[    0.382170] loop: module loaded
[    0.382322] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.382498] ata_piix 0000:00:1f.1: version 2.13
[    0.382514] ata_piix 0000:00:1f.1: enabling device (0005 -> 0007)
[    0.382756] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[    0.382761] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.382828] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.388266] scsi0 : ata_piix
[    0.388481] scsi1 : ata_piix
[    0.389639] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    0.389643] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    0.390181] Fixed MDIO Bus: probed
[    0.390231] PPP generic driver version 2.4.2
[    0.390344] tun: Universal TUN/TAP device driver, 1.6
[    0.390347] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.390472] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.390715] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    0.390721] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    0.390745] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.390750] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.390804] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.390845] ehci_hcd 0000:00:1d.7: debug port 1
[    0.394733] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.400210] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xf4fffc00
[    0.420269] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.420500] usb usb1: configuration #1 chosen from 1 choice
[    0.420553] hub 1-0:1.0: USB hub found
[    0.420573] hub 1-0:1.0: 6 ports detected
[    0.420668] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.420694] uhci_hcd: USB Universal Host Controller Interface driver
[    0.420784] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[    0.420799] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.420803] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.420861] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.420892] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[    0.421028] usb usb2: configuration #1 chosen from 1 choice
[    0.421062] hub 2-0:1.0: USB hub found
[    0.421072] hub 2-0:1.0: 2 ports detected
[    0.421125] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.421132] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.421136] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.421182] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.421204] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40
[    0.421335] usb usb3: configuration #1 chosen from 1 choice
[    0.421368] hub 3-0:1.0: USB hub found
[    0.421379] hub 3-0:1.0: 2 ports detected
[    0.421708] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    0.421714] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.421722] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.421726] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.421776] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.421801] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
[    0.421941] usb usb4: configuration #1 chosen from 1 choice
[    0.421974] hub 4-0:1.0: USB hub found
[    0.421984] hub 4-0:1.0: 2 ports detected
[    0.422115] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.432607] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.432628] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.432855] mice: PS/2 mouse device common for all mice
[    0.433114] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.433135] rtc0: alarms up to one day, 114 bytes nvram
[    0.433366] device-mapper: uevent: version 1.0.3
[    0.433539] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.435609] device-mapper: multipath: version 1.1.0 loaded
[    0.435614] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.436822] EISA: Probing bus 0 at eisa.0
[    0.436851] EISA: Detected 0 cards.
[    0.437945] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.484446] cpuidle: using governor ladder
[    0.484541] cpuidle: using governor menu
[    0.485234] TCP cubic registered
[    0.485484] NET: Registered protocol family 10
[    0.486140] lo: Disabled Privacy Extensions
[    0.486594] NET: Registered protocol family 17
[    0.556683] ata2.00: ATAPI: QSI CD-RW/DVD-ROM SBW242U, UD27, max UDMA/33
[    0.556836] ata1.00: ATA-7: FUJITSU MHV2060AH, 000000A0, max UDMA/100
[    0.556840] ata1.00: 117210240 sectors, multi 8: LBA 
[    0.564549] ata2.00: configured for UDMA/33
[    0.572854] ata1.00: configured for UDMA/100
[    0.573673] Using IPI No-Shortcut mode
[    0.573853] PM: Resume from disk failed.
[    0.573875] registered taskstats version 1
[    0.574209]   Magic number: 10:251:192
[    0.574311] acpi device:1e: hash matches
[    0.574374] rtc_cmos 00:06: setting system clock to 2010-09-08 19:10:06 UTC (1283973006)
[    0.574379] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.574381] EDD information not available.
[    0.656930] ACPI: Battery Slot [BAT0] (battery present)
[    0.912800] Freeing initrd memory: 7784k freed
[    0.969418] usb 1-4: new high speed USB device using ehci_hcd and address 3
[    1.012890] isapnp: No Plug & Play device found
[    1.013142] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2060A 0000 PQ: 0 ANSI: 5
[    1.013419] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.013692] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    1.013753] sd 0:0:0:0: [sda] Write Protect is off
[    1.013756] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.013788] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.013985]  sda:
[    1.016994] scsi 1:0:0:0: CD-ROM            QSI      CDRW/DVD SBW242U UD27 PQ: 0 ANSI: 5
[    1.019868] sr0: scsi3-mmc drive: 4x/24x writer cd/rw xa/form2 cdda tray
[    1.019872] Uniform CD-ROM driver Revision: 3.20
[    1.020043] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.020121] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.041572]  sda1 sda2 < sda5 >
[    1.074857] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.074879] Freeing unused kernel memory: 660k freed
[    1.075595] Write protecting the kernel text: 4680k
[    1.075647] Write protecting the kernel read-only data: 1844k
[    1.095468] udev: starting version 151
[    1.147487] usb 1-4: config 1 interface 0 altsetting 1 bulk endpoint 0x83 has invalid maxpacket 256
[    1.151021] usb 1-4: configuration #1 chosen from 1 choice
[    1.388070] usb 2-1: new full speed USB device using uhci_hcd and address 2
[    1.412325] tg3.c:v3.102 (September 1, 2009)
[    1.412353] tg3 0000:02:00.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    1.488912] eth0: Tigon3 [partno(BCM95705A50) rev 3001] (PCI:33MHz:32-bit) MAC address 00:0d:56:3c:eb:de
[    1.488919] eth0: attached PHY is 5705 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    1.488923] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.488926] eth0: dma_rwctrl[763f0000] dma_mask[64-bit]
[    1.488962] ohci1394 0000:02:01.2: PCI INT A -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    1.544062] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[fafef800-fafeffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    1.606921] usb 2-1: configuration #1 chosen from 1 choice
[    1.609940] hub 2-1:1.0: USB hub found
[    1.611796] hub 2-1:1.0: 4 ports detected
[    1.657897] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    1.893717] usb 2-1.1: new low speed USB device using uhci_hcd and address 3
[    2.031841] usb 2-1.1: configuration #1 chosen from 1 choice
[    2.816253] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[664fc0000760982e]
[   15.068999] udev: starting version 151
[   15.146568] Adding 1489912k swap on /dev/sda5.  Priority:-1 extents:1 across:1489912k 
[   15.538304] Linux agpgart interface v0.103
[   15.546228] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.615087] intel_rng: FWH not detected
[   15.643790] lp: driver loaded but no devices found
[   15.652518] parport_pc 00:0c: reported by Plug and Play ACPI
[   15.652552] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   15.736295] lp0: using parport0 (interrupt-driven).
[   15.767582] irda_init()
[   15.767608] NET: Registered protocol family 23
[   15.797613] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   15.812112] agpgart-intel 0000:00:00.0: Intel 855PM Chipset
[   15.839552] lib80211: common routines for IEEE802.11 drivers
[   15.839558] lib80211_crypt: registered algorithm 'NULL'
[   15.841679] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:1d/LNXVIDEO:00/input/input5
[   15.841845] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   15.850976] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe8000000
[   15.875609] ppdev: user-space parallel port driver
[   15.925306] dell-wmi: No known WMI GUID found
[   15.934815] vga16fb: initializing
[   15.934822] vga16fb: mapped to 0xc00a0000
[   15.935012] fb0: VGA16 VGA frame buffer device
[   15.942940] type=1505 audit(1283973021.865:2):  operation="profile_load" pid=579 name="/sbin/dhclient3"
[   15.943921] type=1505 audit(1283973021.865:3):  operation="profile_load" pid=579 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   15.944988] usbcore: registered new interface driver hiddev
[   15.945835] type=1505 audit(1283973021.869:4):  operation="profile_load" pid=579 name="/usr/lib/connman/scripts/dhclient-script"
[   15.959144] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   15.959151] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   15.961660] input:  USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input6
[   15.961960] generic-usb 0003:15D9:0A4C.0001: input,hidraw0: USB HID v1.11 Mouse [ USB OPTICAL MOUSE] on usb-0000:00:1d.0-1.1/input0
[   15.962014] usbcore: registered new interface driver usbhid
[   15.962304] usbhid: v2.6:USB HID core driver
[   15.967715] yenta_cardbus 0000:02:01.0: CardBus bridge found [1028:014e]
[   15.967735] yenta_cardbus 0000:02:01.0: Using CSCINT to route CSC interrupts to PCI
[   15.967739] yenta_cardbus 0000:02:01.0: Routing CardBus interrupts to PCI
[   15.967745] yenta_cardbus 0000:02:01.0: TI: mfunc 0x012c1202, devctl 0x64
[   16.165458] nvidia: module license 'NVIDIA' taints kernel.
[   16.165463] Disabling lock debugging due to kernel taint
[   16.431629] yenta_cardbus 0000:02:01.0: ISA IRQ mask 0x0458, PCI irq 11
[   16.431636] yenta_cardbus 0000:02:01.0: Socket status: 30000006
[   16.431642] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #02 to #06
[   16.431658] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
[   16.431664] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xd000-0xefff: clean.
[   16.432285] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
[   16.432290] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x27ffffff
[   16.436330] yenta_cardbus 0000:02:01.1: CardBus bridge found [1028:014e]
[   16.710212] yenta_cardbus 0000:02:01.1: ISA IRQ mask 0x0458, PCI irq 11
[   16.710219] yenta_cardbus 0000:02:01.1: Socket status: 30000047
[   16.710225] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[   16.710238] yenta_cardbus 0000:02:01.1: pcmcia: parent PCI bridge I/O window: 0xd000 - 0xefff
[   16.710243] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xd000-0xefff: clean.
[   16.710799] yenta_cardbus 0000:02:01.1: pcmcia: parent PCI bridge Memory window: 0xf6000000 - 0xfbffffff
[   16.710803] yenta_cardbus 0000:02:01.1: pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x27ffffff
[   16.853802] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   16.853807] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   16.853930] ipw2200 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   16.859931] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[   16.860054] ipw2200 0000:02:03.0: firmware: requesting ipw2200-bss.fw
[   16.972996] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x280-0x287
[   16.973996] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   16.974428] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   16.974486] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   16.975016] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   17.071433] input: DualPoint Stick as /devices/platform/i8042/serio1/input/input7
[   17.141333] input: AlpsPS/2 ALPS DualPoint TouchPad as /devices/platform/i8042/serio1/input/input8
[   17.209879] ipw2200: Detected geography ZZA (11 802.11bg channels, 13 802.11a channels)
[   17.228468] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   17.228526] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   17.232154] Console: switching to colour frame buffer device 80x30
[   17.325367] nvidia 0000:01:00.0: PCI INT A -> Link[LNKA] -> GSI 11 (level, low) -> IRQ 11
[   17.325381] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   17.326688] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.17  Thu Apr 15 05:28:41 PDT 2010
[   17.381976] type=1505 audit(1283973023.305:5):  operation="profile_load" pid=755 name="/usr/share/gdm/guest-session/Xsession"
[   17.407348] type=1505 audit(1283973023.329:6):  operation="profile_replace" pid=757 name="/sbin/dhclient3"
[   17.408177] type=1505 audit(1283973023.333:7):  operation="profile_replace" pid=757 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   17.408604] type=1505 audit(1283973023.333:8):  operation="profile_replace" pid=757 name="/usr/lib/connman/scripts/dhclient-script"
[   17.436749] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: excluding 0x280-0x287
[   17.437750] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: clean.
[   17.438183] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
[   17.438242] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
[   17.438778] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[   17.451530] type=1505 audit(1283973023.373:9):  operation="profile_load" pid=763 name="/usr/bin/evince"
[   17.523618] type=1505 audit(1283973023.445:10):  operation="profile_load" pid=763 name="/usr/bin/evince-previewer"
[   17.534109] tg3 0000:02:00.0: firmware: requesting tigon/tg3_tso5.bin
[   17.901430] type=1505 audit(1283973023.825:11):  operation="profile_load" pid=763 name="/usr/bin/evince-thumbnailer"
[   18.009935] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.066359] intel8x0_measure_ac97_clock: measured 55973 usecs (2697 samples)
[   18.066364] intel8x0: clocking to 48000
[   18.949895] agpgart-intel 0000:00:00.0: AGP 2.0 bridge
[   18.949914] agpgart-intel 0000:00:00.0: putting AGP V2 device into 4x mode
[   18.949954] nvidia 0000:01:00.0: putting AGP V2 device into 4x mode
[   19.520163] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   19.520168] tg3: eth0: Flow control is on for TX and on for RX.
[   19.557345] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   28.188030] eth1: no IPv6 routers present
[   30.420029] eth0: no IPv6 routers present
[   79.383749] lo: Disabled Privacy Extensions



---

### Post by rockstarsavin on 2010-09-19
I am also having the same problem with same id(1f71:3301) in ls usb. :mad:
I got this far............ [http://ubuntuforums.org/archive/index.php/t-1501570.html](http://ubuntuforums.org/archive/index.php/t-1501570.html) 

but no luck ...............       :confused:

---

