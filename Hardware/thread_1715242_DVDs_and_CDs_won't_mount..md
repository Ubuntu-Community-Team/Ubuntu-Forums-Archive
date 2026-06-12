---
title: "DVDs and CDs won't mount."
date: 2011-03-26
forum: Hardware
---

### Post by STUMPOFWAR on 2011-03-26
OK...I have a HP Pavilion DV6000 laptop. I noticed over time that CDs and DVD wouldn't always mount. Now it won't mount at all. I figured at the time that the drive was fried so I replaced and I have the same problem. When I insert a blank CD or DVD the drive spins up and the light goes on as if it were reading the disk but then nothing. When I hit the side button it ejects on both drives. 

So......

```
mount /media/cdrom0
```

gets

```
mount: can't find /media/cdrom0 in /etc/fstab or /etc/mtab

```

I saw several posts with suggestions but I'm not really sure what to do.

```
sudo gedit /etc/fstab
```

gets 

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
# Commented out by Dropbox
# UUID=dc5bdd82-b412-417d-8473-db8cdbd476e1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3f681a8e-37db-481c-bf8f-6b089ace7b8f none            swap    sw              0       0
UUID=dc5bdd82-b412-417d-8473-db8cdbd476e1 / ext4 errors=remount-ro,user_xattr 0 1
```
```

```

So fstab doesn't have an entry for my CDROM....right? What do I do to fix this? UGH!

---

### Post by STUMPOFWAR on 2011-03-26
```
dmesg
```

gets

```
[    0.390278] pci 0000:00:0d.0:   bridge window [io  disabled]
[    0.390281] pci 0000:00:0d.0:   bridge window [mem 0xf6000000-0xf60fffff]
[    0.390284] pci 0000:00:0d.0:   bridge window [mem pref disabled]
[    0.390294] pci 0000:00:08.0: setting latency timer to 64
[    0.390300] pci 0000:00:0c.0: setting latency timer to 64
[    0.390305] pci 0000:00:0d.0: setting latency timer to 64
[    0.390309] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.390311] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.390314] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.390317] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.390319] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.390322] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.390324] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff]
[    0.390327] pci_bus 0000:00: resource 11 [mem 0x000d4000-0x000d7fff]
[    0.390329] pci_bus 0000:00: resource 12 [mem 0x000d8000-0x000dbfff]
[    0.390332] pci_bus 0000:00: resource 13 [mem 0x000dc000-0x000dffff]
[    0.390335] pci_bus 0000:00: resource 14 [mem 0x000e0000-0x000e3fff]
[    0.390337] pci_bus 0000:00: resource 15 [mem 0x000e4000-0x000e7fff]
[    0.390340] pci_bus 0000:00: resource 16 [mem 0x000e8000-0x000ebfff]
[    0.390342] pci_bus 0000:00: resource 17 [mem 0x000ec000-0x000effff]
[    0.390345] pci_bus 0000:00: resource 18 [mem 0x000f0000-0x000fffff]
[    0.390348] pci_bus 0000:00: resource 19 [mem 0xfed40000-0xfed44fff]
[    0.390350] pci_bus 0000:00: resource 20 [mem 0xd0000000-0xfebfffff]
[    0.390353] pci_bus 0000:02: resource 1 [mem 0xf6100000-0xf61fffff]
[    0.390356] pci_bus 0000:02: resource 4 [io  0x0000-0x0cf7]
[    0.390358] pci_bus 0000:02: resource 5 [io  0x0d00-0xffff]
[    0.390361] pci_bus 0000:02: resource 6 [mem 0x000a0000-0x000bffff]
[    0.390363] pci_bus 0000:02: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.390366] pci_bus 0000:02: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.390369] pci_bus 0000:02: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.390371] pci_bus 0000:02: resource 10 [mem 0x000cc000-0x000cffff]
[    0.390374] pci_bus 0000:02: resource 11 [mem 0x000d4000-0x000d7fff]
[    0.390377] pci_bus 0000:02: resource 12 [mem 0x000d8000-0x000dbfff]
[    0.390379] pci_bus 0000:02: resource 13 [mem 0x000dc000-0x000dffff]
[    0.390382] pci_bus 0000:02: resource 14 [mem 0x000e0000-0x000e3fff]
[    0.390384] pci_bus 0000:02: resource 15 [mem 0x000e4000-0x000e7fff]
[    0.390387] pci_bus 0000:02: resource 16 [mem 0x000e8000-0x000ebfff]
[    0.390390] pci_bus 0000:02: resource 17 [mem 0x000ec000-0x000effff]
[    0.390392] pci_bus 0000:02: resource 18 [mem 0x000f0000-0x000fffff]
[    0.390395] pci_bus 0000:02: resource 19 [mem 0xfed40000-0xfed44fff]
[    0.390397] pci_bus 0000:02: resource 20 [mem 0xd0000000-0xfebfffff]
[    0.390400] pci_bus 0000:04: resource 0 [io  0x4000-0x4fff]
[    0.390403] pci_bus 0000:04: resource 1 [mem 0xf2000000-0xf3ffffff]
[    0.390406] pci_bus 0000:04: resource 2 [mem 0xf0000000-0xf1ffffff 64bit pref]
[    0.390408] pci_bus 0000:03: resource 1 [mem 0xf6000000-0xf60fffff]
[    0.390453] NET: Registered protocol family 2
[    0.390655] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.392462] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.396821] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.397329] TCP: Hash tables configured (established 524288 bind 65536)
[    0.397333] TCP reno registered
[    0.397348] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.397406] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.397545] NET: Registered protocol family 1
[    0.397725] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.397776] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.397832] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.397894] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.397959] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.398028] pci 0000:00:00.0: Found enabled HT MSI Mapping
[    0.398036] pci 0000:00:12.0: Boot video device
[    0.398060] PCI: CLS 64 bytes, default 64
[    0.410977] PCI-DMA: Disabling AGP.
[    0.411094] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    0.411096] PCI-DMA: using GART IOMMU.
[    0.411101] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.414553] Simple Boot Flag at 0x36 set to 0x1
[    0.414760] Scanning for low memory corruption every 60 seconds
[    0.414970] audit: initializing netlink socket (disabled)
[    0.414988] type=2000 audit(1301171074.410:1): initialized
[    0.429955] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.431714] VFS: Disk quotas dquot_6.5.2
[    0.431781] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.432515] fuse init (API version 7.14)
[    0.432617] msgmni has been set to 7394
[    0.595023] Freeing initrd memory: 10756k freed
[    0.603609] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.603613] io scheduler noop registered
[    0.603616] io scheduler deadline registered
[    0.603666] io scheduler cfq registered (default)
[    0.603845] pcieport 0000:00:0c.0: setting latency timer to 64
[    0.603864]   alloc irq_desc for 40 on node 0
[    0.603866]   alloc kstat_irqs on node 0
[    0.603875] pcieport 0000:00:0c.0: irq 40 for MSI/MSI-X
[    0.604009] pcieport 0000:00:0d.0: setting latency timer to 64
[    0.604024]   alloc irq_desc for 41 on node 0
[    0.604026]   alloc kstat_irqs on node 0
[    0.604031] pcieport 0000:00:0d.0: irq 41 for MSI/MSI-X
[    0.604141] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.604171] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.604854] ACPI: AC Adapter [ACAD] (on-line)
[    0.604950] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0
[    0.604957] ACPI: Sleep Button [SLPB]
[    0.605012] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.605288] ACPI: Lid Switch [LID]
[    0.605354] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input2
[    0.605358] ACPI: Power Button [PWRB]
[    0.605410] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.605414] ACPI: Power Button [PWRF]
[    0.605773] ACPI: acpi_idle registered with cpuidle
[    0.605821] ACPI: processor limited to max C-state 1
[    0.609393] [Firmware Bug]: Invalid critical threshold (0)
[    0.609971] thermal LNXTHERM:01: registered as thermal_zone0
[    0.609979] ACPI: Thermal Zone [THRM] (57 C)
[    0.610081] ERST: Table is not found!
[    0.610438] Linux agpgart interface v0.103
[    0.610443] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.612419] brd: module loaded
[    0.613129] loop: module loaded
[    0.613770] ACPI: PCI Interrupt Link [LSI0] enabled at IRQ 23
[    0.613775]   alloc irq_desc for 23 on node 0
[    0.613777]   alloc kstat_irqs on node 0
[    0.613786] pata_acpi 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 23 (level, low) -> IRQ 23
[    0.613817] pata_acpi 0000:00:09.0: setting latency timer to 64
[    0.613829] pata_acpi 0000:00:09.0: PCI INT A disabled
[    0.614229] Fixed MDIO Bus: probed
[    0.614268] PPP generic driver version 2.4.2
[    0.614305] tun: Universal TUN/TAP device driver, 1.6
[    0.614307] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.614382] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.614737] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 22
[    0.614740]   alloc irq_desc for 22 on node 0
[    0.614742]   alloc kstat_irqs on node 0
[    0.614750] ehci_hcd 0000:00:02.1: PCI INT B -> Link[LUS2] -> GSI 22 (level, low) -> IRQ 22
[    0.614781] ehci_hcd 0000:00:02.1: setting latency timer to 64
[    0.614784] ehci_hcd 0000:00:02.1: EHCI Host Controller
[    0.614852] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.614884] ehci_hcd 0000:00:02.1: debug port 1
[    0.614892] ehci_hcd 0000:00:02.1: cache line size of 64 is not supported
[    0.614917] ehci_hcd 0000:00:02.1: irq 22, io mem 0xf6489000
[    0.640029] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00
[    0.640160] hub 1-0:1.0: USB hub found
[    0.640165] hub 1-0:1.0: 7 ports detected
[    0.640617] ACPI: PCI Interrupt Link [Z019] enabled at IRQ 22
[    0.640622] ehci_hcd 0000:00:04.1: PCI INT B -> Link[Z019] -> GSI 22 (level, low) -> IRQ 22
[    0.640639] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    0.640642] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    0.640690] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 2
[    0.640715] ehci_hcd 0000:00:04.1: debug port 1
[    0.640722] ehci_hcd 0000:00:04.1: cache line size of 64 is not supported
[    0.640730] ehci_hcd 0000:00:04.1: irq 22, io mem 0xf6489400
[    0.660025] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    0.660133] hub 2-0:1.0: USB hub found
[    0.660137] hub 2-0:1.0: 2 ports detected
[    0.660221] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.660612] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 18
[    0.660615]   alloc irq_desc for 18 on node 0
[    0.660617]   alloc kstat_irqs on node 0
[    0.660627] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 18 (level, low) -> IRQ 18
[    0.660640] ohci_hcd 0000:00:02.0: setting latency timer to 64
[    0.660643] ohci_hcd 0000:00:02.0: OHCI Host Controller
[    0.660689] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 3
[    0.660719] ohci_hcd 0000:00:02.0: irq 18, io mem 0xf6486000
[    0.712134] hub 3-0:1.0: USB hub found
[    0.712140] hub 3-0:1.0: 7 ports detected
[    0.712613] ACPI: PCI Interrupt Link [Z018] enabled at IRQ 18
[    0.712618] ohci_hcd 0000:00:04.0: PCI INT A -> Link[Z018] -> GSI 18 (level, low) -> IRQ 18
[    0.712632] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    0.712636] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    0.712682] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 4
[    0.712696] ohci_hcd 0000:00:04.0: irq 18, io mem 0xf6487000
[    0.772147] hub 4-0:1.0: USB hub found
[    0.772153] hub 4-0:1.0: 2 ports detected
[    0.772240] uhci_hcd: USB Universal Host Controller Interface driver
[    0.772361] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    0.793193] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.793200] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.793282] mice: PS/2 mouse device common for all mice
[    0.793452] rtc_cmos 00:07: RTC can wake from S4
[    0.793496] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    0.793537] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.793638] device-mapper: uevent: version 1.0.3
[    0.793739] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.793814] device-mapper: multipath: version 1.1.1 loaded
[    0.793817] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.793981] cpuidle: using governor ladder
[    0.793983] cpuidle: using governor menu
[    0.794291] TCP cubic registered
[    0.794447] NET: Registered protocol family 10
[    0.794865] lo: Disabled Privacy Extensions
[    0.795098] NET: Registered protocol family 17
[    0.795142] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-60 (2 cpu cores) (version 2.20.00)
[    0.795197] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x12
[    0.795200] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x13
[    0.795202] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x14
[    0.795205] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1e
[    0.795380] PM: Resume from disk failed.
[    0.795400] registered taskstats version 1
[    0.795652]   Magic number: 3:432:448
[    0.795692] pci 0000:02:05.2: hash matches
[    0.795758] rtc_cmos 00:07: setting system clock to 2011-03-26 20:24:35 UTC (1301171075)
[    0.795761] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.795763] EDD information not available.
[    0.795865] Freeing unused kernel memory: 912k freed
[    0.796306] Write protecting the kernel read-only data: 10240k
[    0.796491] Freeing unused kernel memory: 408k freed
[    0.796809] Freeing unused kernel memory: 1640k freed
[    0.813127] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.820283] udev[107]: starting version 163
[    0.872969] ACPI: Battery Slot [BAT0] (battery present)
[    1.186402] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.186785] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    1.186791]   alloc irq_desc for 20 on node 0
[    1.186793]   alloc kstat_irqs on node 0
[    1.186806] forcedeth 0000:00:0a.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, low) -> IRQ 20
[    1.186811] forcedeth 0000:00:0a.0: setting latency timer to 64
[    1.199255] sdhci: Secure Digital Host Controller Interface driver
[    1.199259] sdhci: Copyright(c) Pierre Ossman
[    1.202315] firewire_ohci 0000:02:05.0: enabling device (0100 -> 0102)
[    1.202699] ACPI: PCI Interrupt Link [LNK1] enabled at IRQ 5
[    1.202714] firewire_ohci 0000:02:05.0: PCI INT A -> Link[LNK1] -> GSI 5 (level, low) -> IRQ 5
[    1.280031] usb 3-4: new full speed USB device using ohci_hcd and address 2
[    1.460029] firewire_ohci: Added fw-ohci device 0000:02:05.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x0
[    1.460114] sdhci-pci 0000:02:05.1: SDHCI controller found [1180:0822] (rev 22)
[    1.460629] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 7
[    1.460642] sdhci-pci 0000:02:05.1: PCI INT B -> Link[LNK2] -> GSI 7 (level, low) -> IRQ 7
[    1.461691] sdhci-pci 0000:02:05.1: Will use DMA mode even though HW doesn't fully claim to support it.
[    1.462746] Registered led device: mmc0::
[    1.463782] mmc0: SDHCI controller on PCI [0000:02:05.1] using DMA
[    1.711028] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1e:68:51:db:e1
[    1.711034] forcedeth 0000:00:0a.0: highdma pwrctl mgmt lnktim msi desc-v3
[    1.711110] ahci 0000:00:09.0: version 3.0
[    1.711124] ahci 0000:00:09.0: PCI INT A -> Link[LSI0] -> GSI 23 (level, low) -> IRQ 23
[    1.711168] ahci 0000:00:09.0: controller can do NCQ, turning on CAP_NCQ
[    1.711171] ahci 0000:00:09.0: controller can't do PMP, turning off CAP_PMP
[    1.711235] ahci 0000:00:09.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[    1.711240] ahci 0000:00:09.0: flags: 64bit ncq sntf led clo pio slum part 
[    1.711245] ahci 0000:00:09.0: setting latency timer to 64
[    1.711854] scsi0 : ahci
[    1.712018] scsi1 : ahci
[    1.712123] scsi2 : ahci
[    1.712218] scsi3 : ahci
[    1.712381] ata1: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 23
[    1.712385] ata2: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484180 irq 23
[    1.712388] ata3: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484200 irq 23
[    1.712392] ata4: SATA max UDMA/133 abar m8192@0xf6484000 port 0xf6484280 irq 23
[    1.940116] firewire_core: created device fw0: GUID 00241b006960e100, S400
[    2.050028] ata4: SATA link down (SStatus 0 SControl 300)
[    2.050046] ata2: SATA link down (SStatus 0 SControl 300)
[    2.050056] ata3: SATA link down (SStatus 0 SControl 300)
[    2.460031] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.463748] ata1.00: ATA-8: WDC WD7500BPKT-00PK4T0, 01.01A01, max UDMA/133
[    2.463751] ata1.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.467767] ata1.00: configured for UDMA/133
[    2.467925] scsi 0:0:0:0: Direct-Access     ATA      WDC WD7500BPKT-0 01.0 PQ: 0 ANSI: 5
[    2.468112] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.468210] sd 0:0:0:0: [sda] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[    2.468214] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    2.468270] sd 0:0:0:0: [sda] Write Protect is off
[    2.468273] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.468298] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.468515]  sda: sda1 sda2 < sda5 >
[    2.545789] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.839423] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    4.744872] Adding 11127804k swap on /dev/sda5.  Priority:-1 extents:1 across:11127804k 
[    6.860663] udev[380]: starting version 163
[    7.010020] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,user_xattr
[    8.370235] i2c i2c-0: nForce2 SMBus adapter at 0x3040
[    8.370364] i2c i2c-1: nForce2 SMBus adapter at 0x3000
[    8.425195] [drm] Initialized drm 1.1.0 20060810
[    8.433564] Bluetooth: Core ver 2.15
[    8.433626] NET: Registered protocol family 31
[    8.433628] Bluetooth: HCI device and connection manager initialized
[    8.433632] Bluetooth: HCI socket layer initialized
[    8.488534] input: HP WMI hotkeys as /devices/virtual/input/input5
[    8.493135] Bluetooth: Generic Bluetooth USB driver ver 0.6
[    8.496428] usbcore: registered new interface driver btusb
[    8.563336] acpi device:23: registered as cooling_device2
[    8.563729] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input6
[    8.563912] ACPI: Video Device [UVGA] (multi-head: yes  rom: no  post: no)
[    8.618992] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[    8.691739] cfg80211: Calling CRDA to update world regulatory domain
[    8.904562] EDAC MC: Ver: 2.1.0 Mar  1 2011
[    8.909384] lp: driver loaded but no devices found
[    9.018203] ACPI: PCI Interrupt Link [LGPU] enabled at IRQ 16
[    9.018210]   alloc irq_desc for 16 on node 0
[    9.018213]   alloc kstat_irqs on node 0
[    9.018225] nouveau 0000:00:12.0: PCI INT A -> Link[LGPU] -> GSI 16 (level, low) -> IRQ 16
[    9.018230] nouveau 0000:00:12.0: setting latency timer to 64
[    9.023461] [drm] nouveau 0000:00:12.0: Detected an NV40 generation card (0x067000a1)
[    9.025522] [drm] nouveau 0000:00:12.0: Attempting to load BIOS image from PRAMIN
[    9.028196] EDAC amd64_edac:  Ver: 3.3.0 Mar  1 2011
[    9.067925] [drm] nouveau 0000:00:12.0: ... appears to be valid
[    9.067930] [drm] nouveau 0000:00:12.0: BIT BIOS found
[    9.067933] [drm] nouveau 0000:00:12.0: Bios version 05.67.32.16
[    9.067937] [drm] nouveau 0000:00:12.0: TMDS table script pointers not stubbed
[    9.067940] [drm] nouveau 0000:00:12.0: BIT table 'd' not found
[    9.067942] [drm] nouveau 0000:00:12.0: Found Display Configuration Block version 3.0
[    9.067946] [drm] nouveau 0000:00:12.0: Raw DCB entry 0: 03015323 00000004
[    9.067949] [drm] nouveau 0000:00:12.0: Raw DCB entry 1: 01000310 00000023
[    9.067952] [drm] nouveau 0000:00:12.0: Raw DCB entry 2: 020223f1 0040c080
[    9.067956] [drm] nouveau 0000:00:12.0: DCB connector table: VHER 0x30 5 10 2
[    9.067960] [drm] nouveau 0000:00:12.0:   0: 0x00000000: type 0x00 idx 0 tag 0xff
[    9.067963] [drm] nouveau 0000:00:12.0:   1: 0x00001161: type 0x61 idx 1 tag 0x07
[    9.067966] [drm] nouveau 0000:00:12.0:   2: 0x00000210: type 0x10 idx 2 tag 0xff
[    9.067969] [drm] nouveau 0000:00:12.0:   3: 0x00000211: type 0x11 idx 3 tag 0xff
[    9.067972] [drm] nouveau 0000:00:12.0:   4: 0x00000213: type 0x13 idx 4 tag 0xff
[    9.067976] [drm] nouveau 0000:00:12.0:   5: 0x00000340: type 0x40 idx 5 tag 0xff
[    9.067982] [drm] nouveau 0000:00:12.0: Parsing VBIOS init table 0 at offset 0xE333
[    9.068003] [drm] nouveau 0000:00:12.0: ======= misaligned reg 0x001020FB =======
[    9.068064] [drm] nouveau 0000:00:12.0: ======= misaligned reg 0x001020FB =======
[    9.068145] [drm] nouveau 0000:00:12.0: Parsing VBIOS init table 1 at offset 0xE484
[    9.068148] [drm] nouveau 0000:00:12.0: Parsing VBIOS init table 2 at offset 0xE485
[    9.068164] [drm] nouveau 0000:00:12.0: Parsing VBIOS init table 3 at offset 0xE607
[    9.068172] [drm] nouveau 0000:00:12.0: Parsing VBIOS init table 4 at offset 0xE687
[    9.068178] [drm] nouveau 0000:00:12.0: Detected 64MiB VRAM
[    9.073216] [TTM] Zone  kernel: Available graphics memory: 1899874 kiB.
[    9.073218] [TTM] Initializing pool allocator.
[    9.074075] [drm] nouveau 0000:00:12.0: 64 MiB GART (aperture)
[    9.074383] [drm] nouveau 0000:00:12.0: Allocating FIFO number 0
[    9.074705] [drm] nouveau 0000:00:12.0: nouveau_channel_alloc: initialised FIFO 0
[    9.074713] [drm] nouveau 0000:00:12.0: Initial CRTC_OWNER is 0
[    9.074719] [drm] nouveau 0000:00:12.0: Saving VGA fonts
[    9.113713] [drm] nouveau 0000:00:12.0: Detected a LVDS connector
[    9.215944] [drm] nouveau 0000:00:12.0: Detected a VGA connector
[    9.215986] [drm] nouveau 0000:00:12.0: Detected a TV connector
[    9.216958] [drm] nouveau 0000:00:12.0: Setting dpms mode 3 on lvds encoder (output 0)
[    9.216962] [drm] nouveau 0000:00:12.0: Calling LVDS script 6:
[    9.216966] [drm] nouveau 0000:00:12.0: 0xD680: Parsing digital output script table
[    9.216973] [drm] nouveau 0000:00:12.0: Setting dpms mode 3 on vga encoder (output 1)
[    9.216977] [drm] nouveau 0000:00:12.0: Setting dpms mode 3 on TV encoder (output 2)
[    9.265817] r852 0000:02:05.3: PCI INT B -> Link[LNK2] -> GSI 7 (level, low) -> IRQ 7
[    9.266199] r852: Non dma capable device detected, dma disabled
[    9.266217] r852: driver loaded succesfully
[    9.333621] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04711/0xa00000/0x0
[    9.337050] ACPI: PCI Interrupt Link [LK4E] enabled at IRQ 19
[    9.337056]   alloc irq_desc for 19 on node 0
[    9.337058]   alloc kstat_irqs on node 0
[    9.337070] ath5k 0000:03:00.0: PCI INT A -> Link[LK4E] -> GSI 19 (level, low) -> IRQ 19
[    9.337078] ath5k 0000:03:00.0: setting latency timer to 64
[    9.337157] ath5k 0000:03:00.0: registered as 'phy0'
[    9.410170] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[    9.833334] ath: EEPROM regdomain: 0x64
[    9.833336] ath: EEPROM indicates we should expect a direct regpair map
[    9.833340] ath: Country alpha2 being used: 00
[    9.833342] ath: Regpair used: 0x64
[    9.834232] [drm] nouveau 0000:00:12.0: allocated 1280x800 fb: 0x49000, bo ffff880129b1b000
[    9.848325] [drm] nouveau 0000:00:12.0: Output LVDS-1 is running on CRTC 0 using output A
[    9.848328] [drm] nouveau 0000:00:12.0: Calling LVDS script 2:
[    9.848332] [drm] nouveau 0000:00:12.0: 0xD6D8: Parsing digital output script table
[    9.888628] phy0: Selected rate control algorithm 'minstrel'
[    9.889387] Registered led device: ath5k-phy0::rx
[    9.889413] Registered led device: ath5k-phy0::tx
[    9.889417] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   10.030029] [drm] nouveau 0000:00:12.0: Setting dpms mode 0 on lvds encoder (output 0)
[   10.030034] [drm] nouveau 0000:00:12.0: Calling LVDS script 5:
[   10.030037] [drm] nouveau 0000:00:12.0: 0xD676: Parsing digital output script table
[   10.030043] [drm] nouveau 0000:00:12.0: Output LVDS-1 is running on CRTC 0 using output A
[   10.031252] Console: switching to colour frame buffer device 160x50
[   10.032717] fb0: nouveaufb frame buffer device
[   10.032720] drm: registered panic notifier
[   10.032724] Slow work thread pool: Starting up
[   10.032837] Slow work thread pool: Ready
[   10.032846] [drm] Initialized nouveau 0.0.16 20090420 for 0000:00:12.0 on minor 0
[   10.035473] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[   10.035485] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   10.035487]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   10.035488]  (Note that use of the override may cause unknown side effects.)
[   10.035517] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   10.178314] cfg80211: World regulatory domain updated:
[   10.178318]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.178322]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.178325]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.178328]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.178331]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.178333]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.238417] type=1400 audit(1301171084.931:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=628 comm="apparmor_parser"
[   10.238443] type=1400 audit(1301171084.931:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=619 comm="apparmor_parser"
[   10.238725] type=1400 audit(1301171084.931:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=628 comm="apparmor_parser"
[   10.238754] type=1400 audit(1301171084.931:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=619 comm="apparmor_parser"
[   10.238893] type=1400 audit(1301171084.931:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=628 comm="apparmor_parser"
[   10.238933] type=1400 audit(1301171084.931:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=619 comm="apparmor_parser"
[   10.239572] type=1400 audit(1301171084.931:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=757 comm="apparmor_parser"
[   10.239882] type=1400 audit(1301171084.931:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=757 comm="apparmor_parser"
[   10.240070] type=1400 audit(1301171084.931:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=757 comm="apparmor_parser"
[   11.706952] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[   11.706959]   alloc irq_desc for 21 on node 0
[   11.706961]   alloc kstat_irqs on node 0
[   11.706974] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
[   11.706978] hda_intel: Disable MSI for Nvidia chipset
[   11.707053] HDA Intel 0000:00:07.0: setting latency timer to 64
[   13.190136] input: HDA NVidia Headphone as /devices/pci0000:00/0000:00:07.0/sound/card0/input8
[   13.278509] type=1400 audit(1301171087.971:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=915 comm="apparmor_parser"
[   14.326166]   alloc irq_desc for 42 on node 0
[   14.326171]   alloc kstat_irqs on node 0
[   14.326182] forcedeth 0000:00:0a.0: irq 42 for MSI/MSI-X
[   14.406113] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.526697] ppdev: user-space parallel port driver
[   21.274531] [drm] nouveau 0000:00:12.0: Allocating FIFO number 1
[   21.274851] [drm] nouveau 0000:00:12.0: nouveau_channel_alloc: initialised FIFO 1
[   22.220768] Bluetooth: L2CAP ver 2.14
[   22.220772] Bluetooth: L2CAP socket layer initialized
[   22.335986] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.335990] Bluetooth: BNEP filters: protocol multicast
[   22.345225] Bluetooth: SCO (Voice Link) ver 0.6
[   22.345228] Bluetooth: SCO socket layer initialized
[   22.652640] Bluetooth: RFCOMM TTY layer initialized
[   22.652648] Bluetooth: RFCOMM socket layer initialized
[   22.652650] Bluetooth: RFCOMM ver 1.11
[   23.812425] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
[   25.020023] eth0: no IPv6 routers present
[   31.363153] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,user_xattr,commit=0
[   31.395039] CPUFREQ: Per core ondemand sysfs interface is deprecated - up_threshold
[   32.012555] Clocksource tsc unstable (delta = -279418229 ns)
[  263.902937] lo: Disabled Privacy Extensions
[  384.024992] lo: Disabled Privacy Extensions

```

---

