---
title: "Problem with SATA HDD"
date: 2012-04-12
forum: Hardware
---

### Post by Hellfish03 on 2012-04-12
I have 2 internal drives. The first has 2 partitions, one with my file system and the other for data. On the second drive there is a single partition with only data.

Recently my second drive has been failing when copying files. Whenever I move or rename files the drive becomes read only, and sometimes shows only empty folders with no files. To begin with it only happened with large files, but now with all. The drive is just over a year old.

Any ideas greatly appreciated!

---

### Post by Mark Phelps on 2012-04-12
How is the second drive formatted? If it is NTFS, filsystem corruption will force Linux to mount it ONLY read-only -- preventing you from writing to it.  And, the same corruption will cause previously written files to disappear.

---

### Post by Hellfish03 on 2012-04-13
It's ext4. It used to be NTFS, but when I installed ubuntu it was wiped and reformatted. 

$ dmesg /dev/sdb1 
[    0.330592] pci 0000:00:02.0: setting latency timer to 64
[    0.330597] pci 0000:00:05.0: setting latency timer to 64
[    0.330602] pci 0000:00:06.0: setting latency timer to 64
[    0.330611] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.330613] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.330616] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    0.330618] pci_bus 0000:01: resource 1 mem: [0xfa000000-0xfe8fffff]
[    0.330621] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.330623] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.330626] pci_bus 0000:02: resource 1 mem: [0xfe900000-0xfe9fffff]
[    0.330628] pci_bus 0000:03: resource 1 mem: [0xfea00000-0xfeafffff]
[    0.330631] pci_bus 0000:04: resource 0 io:  [0xe000-0xefff]
[    0.330633] pci_bus 0000:04: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.330635] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]
[    0.330638] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.330678] NET: Registered protocol family 2
[    0.330804] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.331711] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.333912] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.334506] TCP: Hash tables configured (established 262144 bind 65536)
[    0.334509] TCP reno registered
[    0.334627] NET: Registered protocol family 1
[    0.334666]   alloc irq_desc for 16 on node 0
[    0.334668]   alloc kstat_irqs on node 0
[    0.334676] pci 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.400028] pci 0000:00:12.0: PCI INT A disabled
[    0.400035] pci 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.430019] pci 0000:00:12.1: PCI INT A disabled
[    0.430029]   alloc irq_desc for 17 on node 0
[    0.430030]   alloc kstat_irqs on node 0
[    0.430034] pci 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.430048] pci 0000:00:12.2: PCI INT B disabled
[    0.430054]   alloc irq_desc for 18 on node 0
[    0.430055]   alloc kstat_irqs on node 0
[    0.430058] pci 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.460020] pci 0000:00:13.0: PCI INT A disabled
[    0.460027] pci 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.490019] pci 0000:00:13.1: PCI INT A disabled
[    0.490028]   alloc irq_desc for 19 on node 0
[    0.490030]   alloc kstat_irqs on node 0
[    0.490033] pci 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.490048] pci 0000:00:13.2: PCI INT B disabled
[    0.490060] pci 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.520018] pci 0000:00:14.5: PCI INT C disabled
[    0.520040] pci 0000:01:00.0: Boot video device
[    0.521142] Scanning for low memory corruption every 60 seconds
[    0.521268] audit: initializing netlink socket (disabled)
[    0.521282] type=2000 audit(1334307985.520:1): initialized
[    0.528684] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.530073] VFS: Disk quotas dquot_6.5.2
[    0.530125] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.530757] fuse init (API version 7.13)
[    0.530846] msgmni has been set to 4000
[    0.531057] alg: No test for stdrng (krng)
[    0.531116] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.531119] io scheduler noop registered
[    0.531120] io scheduler anticipatory registered
[    0.531122] io scheduler deadline registered
[    0.531184] io scheduler cfq registered (default)
[    0.531344]   alloc irq_desc for 24 on node 0
[    0.531346]   alloc kstat_irqs on node 0
[    0.531354] pcieport 0000:00:02.0: irq 24 for MSI/MSI-X
[    0.531359] pcieport 0000:00:02.0: setting latency timer to 64
[    0.531457]   alloc irq_desc for 25 on node 0
[    0.531459]   alloc kstat_irqs on node 0
[    0.531463] pcieport 0000:00:05.0: irq 25 for MSI/MSI-X
[    0.531467] pcieport 0000:00:05.0: setting latency timer to 64
[    0.531552]   alloc irq_desc for 26 on node 0
[    0.531553]   alloc kstat_irqs on node 0
[    0.531557] pcieport 0000:00:06.0: irq 26 for MSI/MSI-X
[    0.531561] pcieport 0000:00:06.0: setting latency timer to 64
[    0.531617] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.531641] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.531743] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.531752] ACPI: Power Button [PWRB]
[    0.531797] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.531800] ACPI: Power Button [PWRF]
[    0.532124] processor LNXCPU:00: registered as cooling_device0
[    0.532159] processor LNXCPU:01: registered as cooling_device1
[    0.537229] thermal LNXTHERM:01: registered as thermal_zone0
[    0.537239] ACPI: Thermal Zone [THRM] (40 C)
[    0.538310] Freeing initrd memory: 8174k freed
[    0.538684] Linux agpgart interface v0.103
[    0.538737] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.539141]   alloc irq_desc for 21 on node 0
[    0.539143]   alloc kstat_irqs on node 0
[    0.539153] serial 0000:04:06.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.539323] 0000:04:06.0: ttyS0 at I/O 0xe808 (irq = 21) is a 16450
[    0.539403] 0000:04:06.0: ttyS1 at I/O 0xe810 (irq = 21) is a 8250
[    0.539479] 0000:04:06.0: ttyS2 at I/O 0xe818 (irq = 21) is a 16450
[    0.539556] 0000:04:06.0: ttyS3 at I/O 0xe820 (irq = 21) is a 8250
[    0.539576] Couldn't register serial port 0000:04:06.0: -28
[    0.540749] brd: module loaded
[    0.541253] loop: module loaded
[    0.541375] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.541692] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.541755] pata_acpi 0000:00:14.1: setting latency timer to 64
[    0.542155] Fixed MDIO Bus: probed
[    0.542191] PPP generic driver version 2.4.2
[    0.542244] tun: Universal TUN/TAP device driver, 1.6
[    0.542246] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.542354] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.542404] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.542431] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    0.542470] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    0.542512] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    0.542526] ehci_hcd 0000:00:12.2: debug port 1
[    0.542562] ehci_hcd 0000:00:12.2: irq 17, io mem 0xf9fff000
[    0.560033] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    0.560116] usb usb1: configuration #1 chosen from 1 choice
[    0.560143] hub 1-0:1.0: USB hub found
[    0.560151] hub 1-0:1.0: 6 ports detected
[    0.560289] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.560300] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.560335] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    0.560359] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    0.560372] ehci_hcd 0000:00:13.2: debug port 1
[    0.560390] ehci_hcd 0000:00:13.2: irq 19, io mem 0xf9ffa800
[    0.580023] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.580086] usb usb2: configuration #1 chosen from 1 choice
[    0.580109] hub 2-0:1.0: USB hub found
[    0.580115] hub 2-0:1.0: 6 ports detected
[    0.580201] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.580251] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.580263] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    0.580297] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    0.580328] ohci_hcd 0000:00:12.0: irq 16, io mem 0xf9ffe000
[    0.644094] usb usb3: configuration #1 chosen from 1 choice
[    0.644118] hub 3-0:1.0: USB hub found
[    0.644127] hub 3-0:1.0: 3 ports detected
[    0.644223] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.644234] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    0.644270] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    0.644289] ohci_hcd 0000:00:12.1: irq 16, io mem 0xf9ffd000
[    0.704097] usb usb4: configuration #1 chosen from 1 choice
[    0.704123] hub 4-0:1.0: USB hub found
[    0.704133] hub 4-0:1.0: 3 ports detected
[    0.704226] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.704239] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.704272] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    0.704299] ohci_hcd 0000:00:13.0: irq 18, io mem 0xf9ffc000
[    0.764098] usb usb5: configuration #1 chosen from 1 choice
[    0.764126] hub 5-0:1.0: USB hub found
[    0.764135] hub 5-0:1.0: 3 ports detected
[    0.764231] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.764242] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.764280] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    0.764299] ohci_hcd 0000:00:13.1: irq 18, io mem 0xf9ffb000
[    0.824092] usb usb6: configuration #1 chosen from 1 choice
[    0.824117] hub 6-0:1.0: USB hub found
[    0.824127] hub 6-0:1.0: 3 ports detected
[    0.824227] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.824239] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    0.824272] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    0.824292] ohci_hcd 0000:00:14.5: irq 18, io mem 0xf9ff9000
[    0.880055] usb 1-4: new high speed USB device using ehci_hcd and address 2
[    0.884092] usb usb7: configuration #1 chosen from 1 choice
[    0.884118] hub 7-0:1.0: USB hub found
[    0.884127] hub 7-0:1.0: 2 ports detected
[    0.884191] uhci_hcd: USB Universal Host Controller Interface driver
[    0.884265] PNP: PS/2 Controller [PNP0f03:PS2M] at 0x60,0x64 irq 12
[    0.884267] PNP: PS/2 controller doesn't have KBD irq; using default 1
[    0.884669] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.884675] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.884786] mice: PS/2 mouse device common for all mice
[    0.884893] rtc_cmos 00:02: RTC can wake from S4
[    0.884932] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.884959] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.885077] device-mapper: uevent: version 1.0.3
[    0.885216] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.885353] device-mapper: multipath: version 1.1.0 loaded
[    0.885356] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.885606] cpuidle: using governor ladder
[    0.885608] cpuidle: using governor menu
[    0.885938] TCP cubic registered
[    0.886074] NET: Registered protocol family 10
[    0.886768] NET: Registered protocol family 17
[    0.886818] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 5000+ processors (2 cpu cores) (version 2.20.00)
[    0.886872] powernow-k8:    0 : fid 0x12 (2600 MHz), vid 0x9
[    0.886874] powernow-k8:    1 : fid 0x10 (2400 MHz), vid 0xb
[    0.886876] powernow-k8:    2 : fid 0xe (2200 MHz), vid 0xd
[    0.886878] powernow-k8:    3 : fid 0xc (2000 MHz), vid 0xf
[    0.886880] powernow-k8:    4 : fid 0xa (1800 MHz), vid 0x11
[    0.886882] powernow-k8:    5 : fid 0x2 (1000 MHz), vid 0x12
[    0.887007] PM: Resume from disk failed.
[    0.887019] registered taskstats version 1
[    0.887391]   Magic number: 8:979:120
[    0.887394] misc device-mapper: hash matches
[    0.887484] rtc_cmos 00:02: setting system clock to 2012-04-13 09:06:26 UTC (1334307986)
[    0.887487] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.887488] EDD information not available.
[    0.887556] Freeing unused kernel memory: 884k freed
[    0.887999] Write protecting the kernel read-only data: 7720k
[    0.906389] udev: starting version 151
[    1.006483] ahci 0000:00:11.0: version 3.0
[    1.006505]   alloc irq_desc for 22 on node 0
[    1.006507]   alloc kstat_irqs on node 0
[    1.006515] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.006569]   alloc irq_desc for 27 on node 0
[    1.006570]   alloc kstat_irqs on node 0
[    1.006581] ahci 0000:00:11.0: irq 27 for MSI/MSI-X
[    1.006682] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.006685] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck led clo pmp pio ccc 
[    1.018558] scsi0 : ahci
[    1.025486] scsi1 : ahci
[    1.025662] sky2 driver version 1.25
[    1.025706] scsi2 : ahci
[    1.025765] scsi3 : ahci
[    1.025896] ata1: SATA max UDMA/133 abar m1024@0xf9fff800 port 0xf9fff900 irq 27
[    1.025900] ata2: SATA max UDMA/133 abar m1024@0xf9fff800 port 0xf9fff980 irq 27
[    1.025903] ata3: SATA max UDMA/133 abar m1024@0xf9fff800 port 0xf9fffa00 irq 27
[    1.025907] ata4: SATA max UDMA/133 abar m1024@0xf9fff800 port 0xf9fffa80 irq 27
[    1.026032] sky2 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.026045] sky2 0000:02:00.0: setting latency timer to 64
[    1.026076] sky2 0000:02:00.0: Yukon-2 Extreme chip revision 2
[    1.026149]   alloc irq_desc for 28 on node 0
[    1.026151]   alloc kstat_irqs on node 0
[    1.026163] sky2 0000:02:00.0: irq 28 for MSI/MSI-X
[    1.026748] sky2 eth0: addr 00:1f:e2:3b:0d:3d
[    1.026883] scsi4 : pata_atiixp
[    1.026946] scsi5 : pata_atiixp
[    1.028192] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.028194] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.028506] ohci1394 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.028512] ohci1394 0000:03:00.0: setting latency timer to 64
[    1.052220] usb 1-4: configuration #1 chosen from 1 choice
[    1.081086] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[feaff800-feafffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    1.370056] ata2: SATA link down (SStatus 0 SControl 300)
[    1.550025] ata1: softreset failed (device not ready)
[    1.550029] ata1: applying SB600 PMP SRST workaround and retrying
[    1.550038] ata4: softreset failed (device not ready)
[    1.550042] ata4: applying SB600 PMP SRST workaround and retrying
[    1.550051] ata3: softreset failed (device not ready)
[    1.550054] ata3: applying SB600 PMP SRST workaround and retrying
[    1.610019] usb 5-1: new low speed USB device using ohci_hcd and address 2
[    1.730043] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.730046] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.730076] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.730906] ata1.00: ATA-8: WDC WD3200AAJS-22B4A0, 01.03A01, max UDMA/133
[    1.730909] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.731864] ata1.00: configured for UDMA/133
[    1.732022] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200AAJS-2 01.0 PQ: 0 ANSI: 5
[    1.732198] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.732269] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.732310] sd 0:0:0:0: [sda] Write Protect is off
[    1.732312] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.732333] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.732468]  sda:
[    1.733066] ata3.00: ATAPI: HL-DT-ST DVDRAM GH22NS50, TN03, max UDMA/100
[    1.736468] ata4.00: ATA-7: SAMSUNG HD502IJ, 1AA01113, max UDMA7
[    1.736471] ata4.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.736896] ata3.00: configured for UDMA/100
[    1.742978] ata4.00: configured for UDMA/133
[    1.744438]  sda1 sda2
[    1.744655] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.745476] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS50  TN03 PQ: 0 ANSI: 5
[    1.766458] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.766461] Uniform CD-ROM driver Revision: 3.20
[    1.766564] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.766629] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    1.766740] scsi 3:0:0:0: Direct-Access     ATA      SAMSUNG HD502IJ  1AA0 PQ: 0 ANSI: 5
[    1.766879] sd 3:0:0:0: Attached scsi generic sg2 type 0
[    1.766928] sd 3:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.766971] sd 3:0:0:0: [sdb] Write Protect is off
[    1.766974] sd 3:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.766994] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.767182]  sdb: sdb1
[    1.775094] sd 3:0:0:0: [sdb] Attached SCSI disk
[    1.792070] usb 5-1: configuration #1 chosen from 1 choice
[    1.937785] usbcore: registered new interface driver hiddev
[    1.942335] input: Genius Optical Mouse as /devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.0/input/input3
[    1.942439] generic-usb 0003:0458:003A.0001: input,hidraw0: USB HID v1.11 Mouse [Genius Optical Mouse] on usb-0000:00:13.0-1/input0
[    1.942470] usbcore: registered new interface driver usbhid
[    1.942473] usbhid: v2.6:USB HID core driver
[    2.101279] usb 5-2: new low speed USB device using ohci_hcd and address 3
[    2.163173] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    2.295085] usb 5-2: configuration #1 chosen from 1 choice
[    2.302274] input: Chicony USB Keyboard as /devices/pci0000:00/0000:00:13.0/usb5/5-2/5-2:1.0/input/input4
[    2.302338] generic-usb 0003:04F2:0760.0002: input,hidraw1: USB HID v1.11 Keyboard [Chicony USB Keyboard] on usb-0000:00:13.0-2/input0
[    2.313046] input: Chicony USB Keyboard as /devices/pci0000:00/0000:00:13.0/usb5/5-2/5-2:1.1/input/input5
[    2.313159] generic-usb 0003:04F2:0760.0003: input,hiddev96,hidraw2: USB HID v1.11 Device [Chicony USB Keyboard] on usb-0000:00:13.0-2/input1
[    2.401472] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[008436ba00016c20]
[    2.621277] usb 6-2: new full speed USB device using ohci_hcd and address 2
[    2.814057] usb 6-2: configuration #1 chosen from 1 choice
[   15.123209] udev: starting version 151
[   15.365528] vga16fb: initializing
[   15.365532] vga16fb: mapped to 0xffff8800000a0000
[   15.365598] fb0: VGA16 VGA frame buffer device
[   15.417420] lp: driver loaded but no devices found
[   15.422660] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   15.434673] type=1505 audit(1334308001.043:2):  operation="profile_load" pid=624 name="/sbin/dhclient3"
[   15.434908] type=1505 audit(1334308001.043:3):  operation="profile_load" pid=624 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   15.435045] type=1505 audit(1334308001.043:4):  operation="profile_load" pid=624 name="/usr/lib/connman/scripts/dhclient-script"
[   15.438215] type=1505 audit(1334308001.043:5):  operation="profile_replace" pid=697 name="/sbin/dhclient3"
[   15.438464] type=1505 audit(1334308001.043:6):  operation="profile_replace" pid=697 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   15.438606] type=1505 audit(1334308001.043:7):  operation="profile_replace" pid=697 name="/usr/lib/connman/scripts/dhclient-script"
[   15.494051] ata4.00: exception Emask 0x50 SAct 0x1 SErr 0x280900 action 0x6 frozen
[   15.494109] ata4.00: irq_stat 0x08000000, interface fatal error
[   15.494162] ata4: SError: { UnrecovData HostInt 10B8B BadCRC }
[   15.494215] ata4.00: failed command: READ FPDMA QUEUED
[   15.494269] ata4.00: cmd 60/08:00:78:08:00/00:00:00:00:00/40 tag 0 ncq 4096 in
[   15.494270]          res 40/00:04:78:08:00/00:00:00:00:00/40 Emask 0x50 (ATA bus error)
[   15.494376] ata4.00: status: { DRDY }
[   15.494428] ata4: hard resetting link
[   15.863508] nvidia: module license 'NVIDIA' taints kernel.
[   15.863512] Disabling lock debugging due to kernel taint
[   16.020024] ata4: softreset failed (device not ready)
[   16.020079] ata4: applying SB600 PMP SRST workaround and retrying
[   16.213306] Initializing USB Mass Storage driver...
[   16.219278] scsi6 : SCSI emulation for USB Mass Storage devices
[   16.219403] usbcore: registered new interface driver usb-storage
[   16.219405] USB Mass Storage support registered.
[   16.220011] usb-storage: device found at 2
[   16.220013] usb-storage: waiting for device to settle before scanning
[   16.223791] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   16.236742] ata4.00: configured for UDMA/133
[   16.236751] ata4: EH complete
[   16.298363] Linux video capture interface: v2.00
[   16.321413] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62e0)
[   16.328850] input: USB 2.0 Camera as /devices/pci0000:00/0000:00:12.2/usb1/1-4/1-4:1.0/input/input6
[   16.328993] usbcore: registered new interface driver uvcvideo
[   16.329538] USB Video Class driver (v0.1.0)
[   16.334845] EDAC MC: Ver: 2.1.0 Mar 29 2012
[   16.347606] EDAC amd64_edac:  Ver: 3.2.0 Mar 29 2012
[   16.436788] acer-wmi: Acer Laptop ACPI-WMI Extras
[   16.436800] acer-wmi: No or unsupported WMI interface, unable to load
[   16.448892] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   16.449089] nvidia 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   16.449098] nvidia 0000:01:00.0: setting latency timer to 64
[   16.449103] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   16.449442] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  195.36.24  Thu Apr 22 19:10:14 PDT 2010
[   16.450827] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[   16.450837] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   16.450839]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   16.450840]  (Note that use of the override may cause unknown side effects.)
[   16.450966] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   16.685076] Console: switching to colour frame buffer device 80x30
[   16.867226] EXT4-fs (sda2): warning: maximal mount count reached, running e2fsck is recommended
[   16.868080] EXT4-fs (sda2): mounted filesystem with ordered data mode
[   16.949623] EXT4-fs (sdb1): mounted filesystem with ordered data mode
[   17.025877] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.077725] 2:3:1: cannot get freq at ep 0x84
[   17.089201] usbcore: registered new interface driver snd-usb-audio
[   17.154074] sky2 eth0: enabling interface
[   17.154386] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.277689] type=1505 audit(1334308002.882:8):  operation="profile_replace" pid=914 name="/sbin/dhclient3"
[   17.277942] type=1505 audit(1334308002.882:9):  operation="profile_replace" pid=914 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   17.278084] type=1505 audit(1334308002.882:10):  operation="profile_replace" pid=914 name="/usr/lib/connman/scripts/dhclient-script"
[   17.282508] type=1505 audit(1334308002.892:11):  operation="profile_load" pid=913 name="/usr/share/gdm/guest-session/Xsession"
[   17.319254] hda_codec: ALC1200: BIOS auto-probing.
[   17.320916] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input7
[   19.057443] ppdev: user-space parallel port driver
[   19.371221] CPU0 attaching NULL sched-domain.
[   19.371229] CPU1 attaching NULL sched-domain.
[   19.620081] CPU0 attaching sched-domain:
[   19.620085]  domain 0: span 0-1 level MC
[   19.620088]   groups: 0 1
[   19.620093] CPU1 attaching sched-domain:
[   19.620095]  domain 0: span 0-1 level MC
[   19.620096]   groups: 1 0
[   20.177676] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   20.177978] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   21.102512] 2:3:1: cannot get freq at ep 0x84
[   21.134622] 2:3:1: cannot get freq at ep 0x84
[   21.234258] usb-storage: device scan complete
[   21.239116] scsi 6:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   21.245119] scsi 6:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   21.251123] scsi 6:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   21.257116] scsi 6:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   21.257563] sd 6:0:0:0: Attached scsi generic sg3 type 0
[   21.257685] sd 6:0:0:1: Attached scsi generic sg4 type 0
[   21.257792] sd 6:0:0:2: Attached scsi generic sg5 type 0
[   21.257900] sd 6:0:0:3: Attached scsi generic sg6 type 0
[   21.324117] sd 6:0:0:2: [sde] Attached SCSI removable disk
[   21.475130] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[   21.485113] sd 6:0:0:1: [sdd] Attached SCSI removable disk
[   21.508125] sd 6:0:0:3: [sdf] Attached SCSI removable disk
[   22.102682] CPU0 attaching NULL sched-domain.
[   22.102692] CPU1 attaching NULL sched-domain.
[   22.152862] CPU0 attaching sched-domain:
[   22.152867]  domain 0: span 0-1 level MC
[   22.152869]   groups: 0 1
[   22.152875] CPU1 attaching sched-domain:
[   22.152877]  domain 0: span 0-1 level MC
[   22.152878]   groups: 1 0
[   25.228851] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[   29.280523] 2:3:1: cannot get freq at ep 0x84
[   30.580587] eth0: no IPv6 routers present
[   80.011299] Clocksource tsc unstable (delta = -99947165 ns)
[  136.325567] EXT4-fs (sdb1): mounted filesystem with ordered data mode
[  162.855227] ata4.00: exception Emask 0x50 SAct 0x1 SErr 0x280900 action 0x6 frozen
[  162.855239] ata4.00: irq_stat 0x08000000, interface fatal error
[  162.855249] ata4: SError: { UnrecovData HostInt 10B8B BadCRC }
[  162.855259] ata4.00: failed command: READ FPDMA QUEUED
[  162.855273] ata4.00: cmd 60/00:00:10:5c:a9/01:00:35:00:00/40 tag 0 ncq 131072 in
[  162.855276]          res 40/00:04:10:5c:a9/00:00:35:00:00/40 Emask 0x50 (ATA bus error)
[  162.855282] ata4.00: status: { DRDY }
[  162.855295] ata4: hard resetting link
[  163.380044] ata4: softreset failed (device not ready)
[  163.380054] ata4: applying SB600 PMP SRST workaround and retrying
[  163.560098] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  163.573262] ata4.00: configured for UDMA/133
[  163.573297] ata4: EH complete
[  185.276592] ata4.00: exception Emask 0x50 SAct 0x1 SErr 0x280900 action 0x6 frozen
[  185.276604] ata4.00: irq_stat 0x08000000, interface fatal error
[  185.276615] ata4: SError: { UnrecovData HostInt 10B8B BadCRC }
[  185.276624] ata4.00: failed command: READ FPDMA QUEUED
[  185.276639] ata4.00: cmd 60/00:00:10:0f:99/01:00:35:00:00/40 tag 0 ncq 131072 in
[  185.276641]          res 40/00:04:10:0f:99/00:00:35:00:00/40 Emask 0x50 (ATA bus error)
[  185.276648] ata4.00: status: { DRDY }
[  185.276661] ata4: hard resetting link
[  185.801293] ata4: softreset failed (device not ready)
[  185.801304] ata4: applying SB600 PMP SRST workaround and retrying
[  185.981338] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  185.994473] ata4.00: configured for UDMA/133
[  185.994506] ata4: EH complete
[  248.736763] ata4: limiting SATA link speed to 1.5 Gbps
[  248.736777] ata4.00: exception Emask 0x50 SAct 0x1 SErr 0x280900 action 0x6 frozen
[  248.736786] ata4.00: irq_stat 0x08000000, interface fatal error
[  248.736795] ata4: SError: { UnrecovData HostInt 10B8B BadCRC }
[  248.736805] ata4.00: failed command: READ FPDMA QUEUED
[  248.736819] ata4.00: cmd 60/00:00:10:5f:99/01:00:35:00:00/40 tag 0 ncq 131072 in
[  248.736822]          res 40/00:04:10:5f:99/00:00:35:00:00/40 Emask 0x50 (ATA bus error)
[  248.736828] ata4.00: status: { DRDY }
[  248.736840] ata4: hard resetting link
[  258.751328] ata4: softreset failed (device not ready)
[  258.751340] ata4: hard resetting link
[  268.760041] ata4: softreset failed (device not ready)
[  268.760053] ata4: hard resetting link
[  274.330060] ata4: softreset failed (device not ready)
[  274.330070] ata4: applying SB600 PMP SRST workaround and retrying
[  279.560033] ata4: link is slow to respond, please be patient (ready=0)
[  303.811304] ata4: softreset failed (device not ready)
[  303.811319] ata4: hard resetting link

?

---

### Post by recluce on 2012-04-13
dmesg show that you have a lot of communication errors with your Samsung HD502IJ drive. This could be due to bad cabling, a controller issue or the drive going bad.

Please install smartmontools and use "blkid -o list" to find your HD502IJ drive. If we assume that it is "sdb", the command "sudo smartctl -a /dev/sdb" will give you the drives overall health status. Feel free to post it here.

---

### Post by Hellfish03 on 2012-04-14
thanks. installed smartontools and ran the command:

smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

=== START OF INFORMATION SECTION ===
Device Model:     SAMSUNG HD502IJ
Serial Number:    S13TJ9DQA03987
Firmware Version: 1AA01113
User Capacity:    500,107,862,016 bytes
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 3b
Local Time is:    Sat Apr 14 11:06:15 2012 ICT

==> WARNING: May need -F samsung or -F samsung2 enabled; see manual for details.

SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)	Offline data collection activity
					was never started.
					Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)	The previous self-test routine completed
					without error or no self-test has ever 
					been run.
Total time to complete Offline 
data collection: 		 (7236) seconds.
Offline data collection
capabilities: 			 (0x7b) SMART execute Offline immediate.
					Auto Offline data collection on/off support.
					Suspend Offline collection upon new
					command.
					Offline surface scan supported.
					Self-test supported.
					Conveyance Self-test supported.
					Selective Self-test supported.
SMART capabilities:            (0x0003)	Saves SMART data before entering
					power-saving mode.
					Supports SMART auto save timer.
Error logging capability:        (0x01)	Error logging supported.
					General Purpose Logging supported.
Short self-test routine 
recommended polling time: 	 (   2) minutes.
Extended self-test routine
recommended polling time: 	 ( 121) minutes.
Conveyance self-test routine
recommended polling time: 	 (  13) minutes.
SCT capabilities: 	       (0x003f)	SCT Status supported.
					SCT Feature Control supported.
					SCT Data Table supported.

SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   099   051    Pre-fail  Always       -       0
  3 Spin_Up_Time            0x0007   086   086   011    Pre-fail  Always       -       5210
  4 Start_Stop_Count        0x0032   096   096   000    Old_age   Always       -       3773
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   100   100   051    Pre-fail  Always       -       0
  8 Seek_Time_Performance   0x0025   100   100   015    Pre-fail  Offline      -       10352
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -       10001
 10 Spin_Retry_Count        0x0033   100   100   051    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x0012   100   100   000    Old_age   Always       -       0
 12 Power_Cycle_Count       0x0032   097   097   000    Old_age   Always       -       3191
 13 Read_Soft_Error_Rate    0x000e   100   099   000    Old_age   Always       -       0
183 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       174
184 Unknown_Attribute       0x0033   001   001   000    Pre-fail  Always       -       300
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       55
188 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   071   049   000    Old_age   Always       -       29 (Lifetime Min/Max 24/29)
194 Temperature_Celsius     0x0022   064   048   000    Old_age   Always       -       36 (Lifetime Min/Max 24/36)
195 Hardware_ECC_Recovered  0x001a   100   100   000    Old_age   Always       -       5284
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   100   016   000    Old_age   Always       -       19910
200 Multi_Zone_Error_Rate   0x000a   100   100   000    Old_age   Always       -       4
201 Soft_Read_Error_Rate    0x000a   253   253   000    Old_age   Always       -       0

SMART Error Log Version: 1
ATA Error Count: 2
	CR = Command Register [HEX]
	FR = Features Register [HEX]
	SC = Sector Count Register [HEX]
	SN = Sector Number Register [HEX]
	CL = Cylinder Low Register [HEX]
	CH = Cylinder High Register [HEX]
	DH = Device/Head Register [HEX]
	DC = Device Command Register [HEX]
	ER = Error register [HEX]
	ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 2 occurred at disk power-on lifetime: 0 hours (0 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  00 d0 00 01 00 00 a0   at LBA = 0x00000001 = 1

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  c8 20 01 01 00 00 a0 00      00:00:10.150  READ DMA
  ef 03 46 01 4f c2 a0 00      00:00:10.150  SET FEATURES [Set transfer mode]
  ef 03 0c 01 4f c2 a0 00      00:00:10.150  SET FEATURES [Set transfer mode]
  c6 da 10 01 4f c2 a0 00      00:00:10.150  SET MULTIPLE MODE
  b0 da 00 01 4f c2 a0 00      00:00:10.150  SMART RETURN STATUS

Error 1 occurred at disk power-on lifetime: 0 hours (0 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  00 58 20 76 12 00 e0   at LBA = 0x00001276 = 4726

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  30 00 3d 59 12 00 e0 00      01:12:30.520  WRITE SECTOR(S)
  ea 00 00 00 00 00 a0 00      01:12:29.290  FLUSH CACHE EXIT
  ef 02 00 00 00 00 a0 00      01:12:29.290  SET FEATURES [Enable write cache]
  f5 00 00 00 00 00 a0 00      01:12:29.260  SECURITY FREEZE LOCK
  ef 66 00 00 00 00 a0 00      01:12:29.250  SET FEATURES [Disable revert defaults]

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      9988         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

---

### Post by recluce on 2012-04-14
I took a peek a your SMART results and this is my take on the situation: the overall mechanical health of your drive is good. However, two parameters point at a cabling or controller issue and the drive's own controller board:

184 Unknown_Attribute 0x0033 001 001 000 Pre-fail Always - 300

This parameter, according to SMART documentation, reflects the "end-to-end error rate", a measure of parity errors encountered while writing from internal cache ram to the media. "001" is the worst possible, normalized SMART value. Since 000 will never be reached, the threshold value of 000 prevents the drive from being flagged as "failing now". As this is a "Pre-fail" parameter on your drive, you should get your drive replaced if it is still under warranty.

199 UDMA_CRC_Error_Count 0x003e 100 016 000 Old_age Always - 19910

The raw number of UDMA CRC errors (19910) is very high. Also, the normalized value was all the way down to 016 in the past, even though it recovered to be at the full 100 currently (100 or 200 being the best normalized SMART values for most drives). These errors are communication errors between the drive and the host and do usually not indicate a problem with the drive, but rather a cabling or host controller problem.

Bottom line: the rock-bottom value of parameter 184 indicates a problem with the drive's electronics. Get it replaced if under warranty. The high parameter 199 error count may be a conseqence of the first problem or indicate a separate cabling or host controller problem.

---

