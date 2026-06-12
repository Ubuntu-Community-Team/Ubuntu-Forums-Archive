---
title: "/ is mounting ro"
date: 2008-11-30
forum: General Help
---

### Post by clarknova on 2008-11-30
Today I upgraded from 8.04 to 8.10. When the upgrade finished it asked me to reboot and I did. Now my root partition is mounting read only for some reason.

I checked dmesg and didn't see anything unusual. I can't copy it here because I have no way of saving it (well, maybe to another partition perhaps).

I tried remounting / read-write but that failed. I've run xfs_repair on the raid device using a live cd, and all appears normal.

You'll see from my /etc/fstab file that my / partition is a raid device.

```
$ cat etc/fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/md0
UUID=724caad3-93d2-4e04-94fd-75729f06fe31 /               xfs     noatime,nodiratime,logbufs=8        0       1
# /dev/sda1
UUID=6039cec7-832d-4b87-b61a-eaebf745d6fd /boot           ext2    noatime,nodiratime,relatime        0       2
# /dev/sdb1
UUID=ae12a603-cff7-4524-aeea-2213bad710fb /boot-backup-hdb ext2    noatime,nodiratime,relatime        0       2
# /dev/sdc1
UUID=a1adbd77-9410-4cc8-99bf-0e400ef4b8dc /boot-backup-hdc ext2    noatime,nodiratime,relatime        0       2
# /dev/md1
UUID=82559863-5c4a-4cb0-98ec-b1f0ea394d04 /home           xfs     noatime,nodiratime,logbufs=8        0       2
# /dev/sda4
UUID=b25ad7bd-d43d-4233-8789-7ac71c2a377e none            swap    sw              0       0
# /dev/sdb4
UUID=1eeec099-b0d1-4193-b8c3-61838fd46a45 none            swap    sw              0       0
# /dev/sdc4
UUID=243650ab-e3fd-47f4-97df-7ee224f5fff7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

And that md0 is healthy. (mounted via live cd)

```
$ cat /proc/mdstat 
Personalities : [raid6] [raid5] [raid4] 
md0 : active raid5 sda5[0] sdb5[2] sdc5[1]
      15630976 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]
      
unused devices: <none>
```

Any clues as to why this is happening?

db

---

### Post by clarknova on 2008-11-30
Managed to grab dmesg (not including the first part here, but latter portion is intact):

```
[    0.668151] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.669275] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.672095] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.672528] TCP: Hash tables configured (established 524288 bind 65536)
[    0.672531] TCP reno registered
[    0.684109] NET: Registered protocol family 1
[    0.684213] checking if image is initramfs... it is
[    1.511936] Freeing initrd memory: 9064k freed
[    1.515277] audit: initializing netlink socket (disabled)
[    1.515299] type=2000 audit(1228032524.512:1): initialized
[    1.521379] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.523606] VFS: Disk quotas dquot_6.5.1
[    1.523679] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.523770] msgmni has been set to 7501
[    1.523874] io scheduler noop registered
[    1.523876] io scheduler anticipatory registered
[    1.523877] io scheduler deadline registered
[    1.523986] io scheduler cfq registered (default)
[    1.523996] pci 0000:00:02.0: Boot video device
[    1.524421] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.524449] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.524479] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.524521] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.524555] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.524630] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.524657] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.524684] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.524722] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.524757] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.524834] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    1.524861] pcieport-driver 0000:00:1c.2: found MSI capability
[    1.524888] pci_express 0000:00:1c.2:pcie00: allocate port service
[    1.524927] pci_express 0000:00:1c.2:pcie02: allocate port service
[    1.524964] pci_express 0000:00:1c.2:pcie03: allocate port service
[    1.525039] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    1.525066] pcieport-driver 0000:00:1c.3: found MSI capability
[    1.525093] pci_express 0000:00:1c.3:pcie00: allocate port service
[    1.525129] pci_express 0000:00:1c.3:pcie02: allocate port service
[    1.525162] pci_express 0000:00:1c.3:pcie03: allocate port service
[    1.525236] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.525263] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.525291] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.525325] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.525361] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.553966] hpet_resources: 0xfed00000 is busy
[    1.554008] Linux agpgart interface v0.103
[    1.554012] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.555899] brd: module loaded
[    1.555963] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.556117] PNP: No PS/2 controller found. Probing ports directly.
[    1.559008] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.559013] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.580601] mice: PS/2 mouse device common for all mice
[    1.580709] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.580731] rtc0: alarms up to one month, hpet irqs
[    1.580765] cpuidle: using governor ladder
[    1.580767] cpuidle: using governor menu
[    1.581114] TCP cubic registered
[    1.581278] registered taskstats version 1
[    1.581407]   Magic number: 0:198:120
[    1.581495] rtc_cmos 00:03: setting system clock to 2008-11-30 08:08:45 UTC (1228032525)
[    1.581497] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.581499] EDD information not available.
[    1.581555] Freeing unused kernel memory: 536k freed
[    1.581713] Write protecting the kernel read-only data: 4348k
[    1.720558] fuse init (API version 7.9)
[    1.877524] Monitor-Mwait will be used to enter C-1 state
[    1.877582] processor ACPI0007:00: registered as cooling_device0
[    1.877586] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.877794] processor ACPI0007:01: registered as cooling_device1
[    1.877798] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.891608] md: linear personality registered for level -1
[    1.911557] md: multipath personality registered for level -4
[    2.000038] md: raid0 personality registered for level 0
[    2.039016] md: raid1 personality registered for level 1
[    2.069869] xor: automatically using best checksumming function: generic_sse
[    2.087996]    generic_sse:  7211.000 MB/sec
[    2.087998] xor: using function: generic_sse (7211.000 MB/sec)
[    2.089019] async_tx: api initialized (async)
[    2.160003] raid6: int64x1   1773 MB/s
[    2.228021] raid6: int64x2   2434 MB/s
[    2.296012] raid6: int64x4   2300 MB/s
[    2.364003] raid6: int64x8   1711 MB/s
[    2.432004] raid6: sse2x1    3340 MB/s
[    2.499997] raid6: sse2x2    4514 MB/s
[    2.567997] raid6: sse2x4    5744 MB/s
[    2.567998] raid6: using algorithm sse2x4 (5744 MB/s)
[    2.568001] md: raid6 personality registered for level 6
[    2.568003] md: raid5 personality registered for level 5
[    2.568004] md: raid4 personality registered for level 4
[    2.585941] md: raid10 personality registered for level 10
[    2.766361] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
[    2.766364] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    2.766401] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.766409] e1000e 0000:00:19.0: setting latency timer to 64
[    2.780494] usbcore: registered new interface driver usbfs
[    2.780525] usbcore: registered new interface driver hub
[    2.780556] usbcore: registered new device driver usb
[    2.782161] USB Universal Host Controller Interface driver v3.0
[    2.817298] No dock devices found.
[    2.839502] SCSI subsystem initialized
[    2.862476] libata version 3.00 loaded.
[    2.966363] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:19:d1:7f:5c:fc
[    2.966366] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    2.966388] 0000:00:19.0: eth0: MAC: 5, PHY: 6, PBA No: ffffff-0ff
[    2.966531] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.966539] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.966542] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.966578] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    2.966608] uhci_hcd 0000:00:1a.0: irq 18, io base 0x000030e0
[    2.966732] usb usb1: configuration #1 chosen from 1 choice
[    2.966759] hub 1-0:1.0: USB hub found
[    2.966765] hub 1-0:1.0: 2 ports detected
[    3.068717] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    3.068726] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    3.068729] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    3.068752] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    3.068781] uhci_hcd 0000:00:1a.1: irq 21, io base 0x000030c0
[    3.068863] usb usb2: configuration #1 chosen from 1 choice
[    3.068886] hub 2-0:1.0: USB hub found
[    3.068892] hub 2-0:1.0: 2 ports detected
[    3.172699] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 17 (level, low) -> IRQ 17
[    3.172707] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    3.172711] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    3.172732] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[    3.172762] uhci_hcd 0000:00:1a.2: irq 17, io base 0x000030a0
[    3.172841] usb usb3: configuration #1 chosen from 1 choice
[    3.172866] hub 3-0:1.0: USB hub found
[    3.172872] hub 3-0:1.0: 2 ports detected
[    3.277000] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 17 (level, low) -> IRQ 17
[    3.277014] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    3.277017] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    3.277040] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 4
[    3.280935] ehci_hcd 0000:00:1a.7: debug port 1
[    3.280940] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    3.280946] ehci_hcd 0000:00:1a.7: irq 17, io mem 0xe8425c00
[    3.296010] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.296076] usb usb4: configuration #1 chosen from 1 choice
[    3.296101] hub 4-0:1.0: USB hub found
[    3.296107] hub 4-0:1.0: 6 ports detected
[    3.401090] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.401097] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    3.401100] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.401124] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    3.401151] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00003080
[    3.401230] usb usb5: configuration #1 chosen from 1 choice
[    3.401253] hub 5-0:1.0: USB hub found
[    3.401259] hub 5-0:1.0: 2 ports detected
[    3.505019] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    3.505025] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    3.505027] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.505050] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    3.505076] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00003060
[    3.505153] usb usb6: configuration #1 chosen from 1 choice
[    3.505176] hub 6-0:1.0: USB hub found
[    3.505181] hub 6-0:1.0: 2 ports detected
[    3.713079] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    3.713084] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    3.713087] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.713112] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    3.713132] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00003040
[    3.713214] usb usb7: configuration #1 chosen from 1 choice
[    3.713237] hub 7-0:1.0: USB hub found
[    3.713243] hub 7-0:1.0: 2 ports detected
[    3.824009] usb 6-2: new full speed USB device using uhci_hcd and address 2
[    3.920162] e1000e 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.920171] e1000e 0000:01:00.0: setting latency timer to 64
[    3.921120] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.921127] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    3.921130] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.921154] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[    3.925050] ehci_hcd 0000:00:1d.7: debug port 1
[    3.925055] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    3.925060] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe8425800
[    3.948009] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.948085] usb usb8: configuration #1 chosen from 1 choice
[    3.948110] hub 8-0:1.0: USB hub found
[    3.948116] hub 8-0:1.0: 6 ports detected
[    4.098909] 0000:01:00.0: eth1: (PCI Express:2.5GB/s:Width x1) 00:1b:21:05:25:68
[    4.098912] 0000:01:00.0: eth1: Intel(R) PRO/1000 Network Connection
[    4.098995] 0000:01:00.0: eth1: MAC: 1, PHY: 4, PBA No: d50854-003
[    4.157178] ahci 0000:00:1f.2: version 3.0
[    4.157189] ahci 0000:00:1f.2: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    4.157269] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    4.157272] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pmp pio slum part ems 
[    4.157276] ahci 0000:00:1f.2: setting latency timer to 64
[    4.157520] scsi0 : ahci
[    4.157606] scsi1 : ahci
[    4.157660] scsi2 : ahci
[    4.157715] scsi3 : ahci
[    4.157766] scsi4 : ahci
[    4.157818] scsi5 : ahci
[    4.157927] ata1: SATA max UDMA/133 abar m2048@0xe8425000 port 0xe8425100 irq 2298
[    4.157930] ata2: SATA max UDMA/133 abar m2048@0xe8425000 port 0xe8425180 irq 2298
[    4.157932] ata3: SATA max UDMA/133 abar m2048@0xe8425000 port 0xe8425200 irq 2298
[    4.157935] ata4: SATA max UDMA/133 abar m2048@0xe8425000 port 0xe8425280 irq 2298
[    4.157937] ata5: SATA max UDMA/133 abar m2048@0xe8425000 port 0xe8425300 irq 2298
[    4.157939] ata6: SATA max UDMA/133 abar m2048@0xe8425000 port 0xe8425380 irq 2298
[    4.352512] usb 6-2: device not accepting address 2, error -71
[    4.408714] hub 6-0:1.0: unable to enumerate USB device on port 2
[    4.640012] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.671588] ata1.00: ATA-7: ST3808110AS, 2AAA, max UDMA/133
[    4.671591] ata1.00: 156301488 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    4.729898] ata1.00: configured for UDMA/133
[    4.944010] usb 6-2: new full speed USB device using uhci_hcd and address 4
[    5.108817] usb 6-2: configuration #1 chosen from 1 choice
[    5.228013] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.229404] ata2.00: ATA-6: ST380817AS, 3.42, max UDMA/133
[    5.229407] ata2.00: 156301488 sectors, multi 0: LBA48 NCQ (not used)
[    5.230927] ata2.00: configured for UDMA/133
[    5.352011] usb 7-1: new low speed USB device using uhci_hcd and address 2
[    5.536872] usb 7-1: configuration #1 chosen from 1 choice
[    6.132512] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    6.168034] ata3.00: ATA-7: ST3808110AS, 2AAA, max UDMA/133
[    6.168037] ata3.00: 156301488 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    6.226347] ata3.00: configured for UDMA/133
[    6.560512] ata4: SATA link down (SStatus 0 SControl 300)
[    6.896014] ata5: SATA link down (SStatus 0 SControl 300)
[    7.232012] ata6: SATA link down (SStatus 0 SControl 300)
[    7.248094] scsi 0:0:0:0: Direct-Access     ATA      ST3808110AS      2AAA PQ: 0 ANSI: 5
[    7.248544] scsi 1:0:0:0: Direct-Access     ATA      ST380817AS       3.42 PQ: 0 ANSI: 5
[    7.248646] scsi 2:0:0:0: Direct-Access     ATA      ST3808110AS      2AAA PQ: 0 ANSI: 5
[    7.250661] pata_acpi 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    7.250684] pata_acpi 0000:03:00.0: setting latency timer to 64
[    7.250697] pata_acpi 0000:03:00.0: PCI INT A disabled
[    7.252311] pata_marvell 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    7.252330] pata_marvell 0000:03:00.0: setting latency timer to 64
[    7.254211] scsi6 : pata_marvell
[    7.254573] scsi7 : pata_marvell
[    7.254608] ata7: PATA max UDMA/100 cmd 0x1018 ctl 0x1024 bmdma 0x1000 irq 18
[    7.254610] ata8: DUMMY
[    7.274109] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    7.274147] scsi 1:0:0:0: Attached scsi generic sg1 type 0
[    7.274189] scsi 2:0:0:0: Attached scsi generic sg2 type 0
[    7.311497] usbcore: registered new interface driver hiddev
[    7.320348] Driver 'sd' needs updating - please use bus_type methods
[    7.320557] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    7.320575] sd 0:0:0:0: [sda] Write Protect is off
[    7.320577] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.320605] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.320674] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[    7.320689] sd 0:0:0:0: [sda] Write Protect is off
[    7.320691] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.320719] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.320723]  sda:<6>input: Microsoft Microsoft Wireless Optical Desktop&#65533; 1.00 as /devices/pci0000:00/0000:00:1d.2/usb7/7-1/7-1:1.0/input/input1
[    7.343459]  sda1 sda2 < sda5 > sda3 sda4
[    7.348585] input,hidraw0: USB HID v1.11 Keyboard [Microsoft Microsoft Wireless Optical Desktop&#65533; 1.00] on usb-0000:00:1d.2-1
[    7.370450] sd 0:0:0:0: [sda] Attached SCSI disk
[    7.370524] sd 1:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
[    7.370541] sd 1:0:0:0: [sdb] Write Protect is off
[    7.370543] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    7.370571] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.370626] sd 1:0:0:0: [sdb] 156301488 512-byte hardware sectors (80026 MB)
[    7.370642] sd 1:0:0:0: [sdb] Write Protect is off
[    7.370644] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    7.370672] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.370676]  sdb: sdb1 sdb2 < sdb5 > sdb3 sdb4
[    7.398648] sd 1:0:0:0: [sdb] Attached SCSI disk
[    7.402894] sd 2:0:0:0: [sdc] 156301488 512-byte hardware sectors (80026 MB)
[    7.402910] sd 2:0:0:0: [sdc] Write Protect is off
[    7.402913] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    7.402939] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.402993] sd 2:0:0:0: [sdc] 156301488 512-byte hardware sectors (80026 MB)
[    7.403008] sd 2:0:0:0: [sdc] Write Protect is off
[    7.403010] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    7.403036] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.403040]  sdc:<6>input: Microsoft Microsoft Wireless Optical Desktop&#65533; 1.00 as /devices/pci0000:00/0000:00:1d.2/usb7/7-1/7-1:1.1/input/input2
[    7.423854]  sdc1 sdc2 <<6>ata7.00: ATAPI: HL-DT-ST DVDRAM GSA-H10A, JL03, max UDMA/33
[    7.428317]  sdc5 > sdc3 sdc4
[    7.448074] input,hidraw1: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Desktop&#65533; 1.00] on usb-0000:00:1d.2-1
[    7.448090] usbcore: registered new interface driver usbhid
[    7.448092] usbhid: v2.6:USB HID core driver
[    7.450601] sd 2:0:0:0: [sdc] Attached SCSI disk
[    7.452613] ata7.01: ATA-7: ST3802110A, 3.AAD, max UDMA/100
[    7.452616] ata7.01: 156301488 sectors, multi 16: LBA48 
[    7.468854] ata7.00: configured for UDMA/33
[    7.527508] ata7.01: configured for UDMA/100
[    7.531241] scsi 6:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-H10A  JL03 PQ: 0 ANSI: 5
[    7.531341] scsi 6:0:0:0: Attached scsi generic sg3 type 5
[    7.533367] scsi 6:0:1:0: Direct-Access     ATA      ST3802110A       3.AA PQ: 0 ANSI: 5
[    7.533450] scsi 6:0:1:0: Attached scsi generic sg4 type 0
[    7.533531] sd 6:0:1:0: [sdd] 156301488 512-byte hardware sectors (80026 MB)
[    7.533547] sd 6:0:1:0: [sdd] Write Protect is off
[    7.533550] sd 6:0:1:0: [sdd] Mode Sense: 00 3a 00 00
[    7.533576] sd 6:0:1:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.533629] sd 6:0:1:0: [sdd] 156301488 512-byte hardware sectors (80026 MB)
[    7.533644] sd 6:0:1:0: [sdd] Write Protect is off
[    7.533646] sd 6:0:1:0: [sdd] Mode Sense: 00 3a 00 00
[    7.533672] sd 6:0:1:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.533676]  sdd:<4>Driver 'sr' needs updating - please use bus_type methods
[    7.575496]  sdd1 sdd2 < sdd5 > sdd3 sdd4
[    7.614556] sd 6:0:1:0: [sdd] Attached SCSI disk
[    7.617122] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    7.617126] Uniform CD-ROM driver Revision: 3.20
[    7.617191] sr 6:0:0:0: Attached scsi CD-ROM sr0
[    7.836291] md: md1 stopped.
[    7.989337] mdadm[2622]: segfault at 4 ip 0000000000418d7d sp 00007fffbdf1ffd0 error 4 in mdadm[400000+2a000]
[    8.029425] md: md1 stopped.
[    8.168555] md: bind<sdc3>
[    8.168652] md: bind<sdb3>
[    8.168821] md: bind<sdd3>
[    8.168959] md: bind<sda3>
[    8.168980] md: kicking non-fresh sdd3 from array!
[    8.168984] md: unbind<sdd3>
[    8.188017] md: export_rdev(sdd3)
[    8.194948] raid5: device sda3 operational as raid disk 0
[    8.194950] raid5: device sdb3 operational as raid disk 2
[    8.194952] raid5: device sdc3 operational as raid disk 1
[    8.196362] raid5: allocated 3226kB for md1
[    8.196365] raid5: raid level 5 set md1 active with 3 out of 3 devices, algorithm 2
[    8.196367] RAID5 conf printout:
[    8.196368]  --- rd:3 wd:3
[    8.196370]  disk 0, o:1, dev:sda3
[    8.196371]  disk 1, o:1, dev:sdc3
[    8.196373]  disk 2, o:1, dev:sdb3
[    8.196527] md: md0 stopped.
[    8.315501] md: bind<sdc5>
[    8.315640] md: bind<sdb5>
[    8.315805] md: bind<sdd5>
[    8.315980] md: bind<sda5>
[    8.316001] md: kicking non-fresh sdd5 from array!
[    8.316006] md: unbind<sdd5>
[    8.324510] md: export_rdev(sdd5)
[    8.331828] raid5: device sda5 operational as raid disk 0
[    8.331831] raid5: device sdb5 operational as raid disk 2
[    8.331833] raid5: device sdc5 operational as raid disk 1
[    8.332213] raid5: allocated 3226kB for md0
[    8.332215] raid5: raid level 5 set md0 active with 3 out of 3 devices, algorithm 2
[    8.332217] RAID5 conf printout:
[    8.332218]  --- rd:3 wd:3
[    8.332220]  disk 0, o:1, dev:sda5
[    8.332222]  disk 1, o:1, dev:sdc5
[    8.332223]  disk 2, o:1, dev:sdb5
[    8.531732] PM: Starting manual resume from disk
[    8.531735] PM: Resume from partition 8:4
[    8.531737] PM: Checking hibernation image.
[    8.531874] PM: Resume from disk failed.
[    8.538964] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[    8.543436] SGI XFS Quota Management subsystem
[    8.544112] Filesystem "md0": Disabling barriers, trial barrier write failed
[    8.544257] XFS mounting filesystem md0
[    8.678257] Ending clean XFS mount for filesystem: md0
[   15.546857] udevd version 124 started
[   16.041637] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.088926] heci: Intel(R) AMT Management Interface - version 3.2.0.24
[   16.088929] heci: Copyright (c) 2003 - 2007 Intel Corporation.
[   16.088958] heci 0000:00:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.088962] heci 0000:00:03.0: setting latency timer to 64
[   16.089232] heci: link layer has been established.
[   16.195582] heci: heci driver initialization successful.
[   16.195736] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.209932] agpgart-intel 0000:00:00.0: Intel Q35 Chipset
[   16.211645] agpgart-intel 0000:00:00.0: detected 7164K stolen memory
[   16.218673] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xe0000000
[   16.237898] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[   16.264059] ACPI: Power Button (FF) [PWRF]
[   16.264127] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input4
[   16.296016] ACPI: Sleep Button (CM) [SLPB]
[   16.704431] usblp0: USB Bidirectional printer dev 4 if 0 alt 1 proto 2 vid 0x03F0 pid 0x2104
[   16.704454] usbcore: registered new interface driver usblp
[   16.767889] iTCO_vendor_support: vendor-support=0
[   16.865976] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   16.866000] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   16.885280] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   16.892012] iTCO_wdt: Found a ICH9DO TCO device (Version=2, TCOBASE=0x0460)
[   16.892092] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   16.897794] hda_codec: Unknown model for ALC268, trying auto-probe from BIOS...
[   16.905862] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   19.347130] loop: module loaded
[   19.408973] lp: driver loaded but no devices found
[   19.688054] Adding 1783204k swap on /dev/sda4.  Priority:-1 extents:1 across:1783204k
[   19.761963] Adding 1783204k swap on /dev/sdc4.  Priority:-2 extents:1 across:1783204k
[   19.812385] Adding 1783204k swap on /dev/sdb4.  Priority:-3 extents:1 across:1783204k
[   24.804507] heci: unexpected heci reset.
[  132.551877] Filesystem "md1": Disabling barriers, trial barrier write failed
[  132.576468] XFS mounting filesystem md1
[  132.762071] Ending clean XFS mount for filesystem: md1
```

db

---

### Post by fjgaude on 2008-11-30
You have a very interesting setup... not sure I fully understand. You boot from an mdadm raid5, three-disk array, md0? Have another array, md1, assembled from the same three drives?

You boot from a liveCD? or have the system set to boot from only one drive of the three?

On what array or drive is the boot OS?

---

### Post by clarknova on 2008-12-01
I guess I could have been clearer.

I don't normally boot from a live CD, I had just done so to be able to have a working system to visit the forums and run some diagnostics on my filesystem, raid, etc.

/boot is on its own ext2 partition
/ is on a 3-disk raid5, md0, xfs
/home is on a 3-disk raid5, md1, xfs (same 3 disks, different member partitions)
swap partitions on each of the same 3 disks
I have a fourth disk with a couple partitions acting as hot spares for md0 and md1

When I try to boot the system normally from the hdd, I get a maintenance shell and some errors, all indicating that / is read-only. It tells me to manually check my fs for errors, but 'xfs_repair -d /dev/md0' fails. 'xfs_repair -L /dev/md0' should kill the fs jounral, but that also fails.

'mount -o remount,rw /' gives some error (I don't have access to this machine at the moment), and / is still mounted ro. If I do a 'mount'  it shows that / is mounted rw, probably because mtab is not writable. 'cat /proc/mdstat' shows that my raids are healthy.

So unable to get past my maintenance shell, I saved dmesg to a writable partition and booted from a live cd. I used 'mdadm -A /dev/md0' to assemble my array and then ran 'xfs_repair -d /dev/md0'. It made some repairs, I rebooted from the hdd, but / is still ro.

I go back to the live cd, assemble the array, and rerun 'xfs_repair -d /dev/md0' but no errors this time. I try 'xfs_repair -L /dev/md0' to kill the journal, reboot from the hdd, and still / is ro.

So that's where I am. I hope that clarifies things a bit. I don't know why / has decided to mount read-only, but this is a production system and I'll probably just reinstall tomorrow unless somebody has some ideas, because I need this system back on line tomorrow or soon thereafter. Fortunately my /home partition seems to be intact and functioning, so my users will be none the wiser, it's just sad to wipe and go without ever knowing what went wrong.

Thanks for looking.

db

---

### Post by fjgaude on 2008-12-02
I've never done things the way you are. This setup did work at one time?

The /boot is on one of the drives that is part of the raid5 array. Lots to think about here regarding reliability.

This mounting **ro** is strange for sure, maybe somekind of "race" condition at boot time. You could try putting a delay in the "mount" section:

/usr/share/initramfs-tools/init   # to stop a race condition with **md**

```
   187 maybe_break mount
   188 sleep 10
   189 log_begin_msg "Mounting root file system..."
```
```

sudo /usr/sbin/update-initramfs -uk all
```    # run to rebuild the image

Let us know if this works with the 10 second delay.

---

### Post by clarknova on 2008-12-04
Thanks for the suggestion. This setup worked great on 8.04 for 6 months; It's an ltsp server that I put together as soon as 8.04 was released.

I had to get things running so yesterday I reinstalled using the 8.10 alternate CD. I formatted / and /boot, leaving the other fs intact. I didn't alter a single partition and so far after 24 hours things are working fine. For some reason the upgrade broke something. I filed a bug, but I had to move on, so unless somebody else has something to contribute to the bug, it's not likely to go anywhere.

As to the risks of keeping my /boot partition on a drive used for raid, that's why I have mirrored /boot partitions on the other disks with a cron job to update them daily. If the drive with my /boot partition dies, I can install grub on another drive's mbr and redirect the bios to that drive.

[https://bugs.launchpad.net/ubuntu/+bug/304298](https://bugs.launchpad.net/ubuntu/+bug/304298)

Thanks again.

db

---

### Post by fjgaude on 2008-12-04
Well, over the years, I've never been completely happy with upgrading an OS. So, we fresh install as needed.

Glad things seem to be working correctly for you now.

---

### Post by clarknova on 2008-12-25
I'm resurrecting this thread because the exact same thing has happened under totally different circumstances.

I installed Xubuntu 8.04.1 i386 on a Toshiba laptop. It's a dual-boot setup. Windows XP Pro was installed on the first partition. The second partition was used for backup, and I repartitioned the second partition for the xubuntu install thus:

sda1- ntfs, windows
sda2- ext2, /boot
sda5- jfs, /
sda6- swap

Nothing fancy in the xubuntu install, just added openssh-server, vlc, nothing else I can think of. I did all this 2 days ago.

Last night I shut it down. This morning when I started it up X failed to start. I logged in on vc1 and all indications are that / is mounted read-only.

I'm frankly amazed that this has happedened to me twice in such a short time under totally different circumstances, while nobody else seems to know what I'm talking about.

The only similarities I see between the two incidents are 1) me, and 2) I keep my /boot on a separate partition.

I should note that I have other ubuntu installs, all of them with /boot on its own ext2 partition, all of them assembled by me, but only these 2 suffering from this problem.

Ideas please?

db

edit: workaround: acpi=off
Really not sure why this becomes an issue only after many reboots. How does a system tick along happily for days or months with acpi and then suddenly poops a brick with it? A package update perhaps?

---

### Post by fjgaude on 2008-12-25
I'm not much of an expect on these kinds of issues. Have you tried from a liveCD to change the ro status of / using **chroot**, or something like that? It would seem from liveCD that you from root change the r/w status of / on an unmounted filesystem.

Package updates could be an issue with a setup like yours, can't say for sure, or which packages it might be.

Keep us informed at what you find out. Thanks.

---

### Post by clarknova on 2009-01-14
> **fjgaude said:**
> It would seem from liveCD that you from root change the r/w status of / on an unmounted filesystem.

I booted from a liveCD and I can mount the partition rw no problem. There's something about the installed system that just won't do it and doesn't leave a lot of clues.

As for the second system, the laptop running Xubuntu, when it first happened I was able to reboot it somewhat normally by using acpi=off, but that generated error messages during boot suggesting I should use the boot option pnpbios=off.

After a couple reboots using both those options, the root partition again starting mounting ro. I just wiped it clean and installed Ubuntu 8.10. I haven't had a recurrence of the problem since then, around the new year. Bizarre.

db

---

### Post by fjgaude on 2009-01-15
Well, I'm happy things are okay, but we didn't learn anything new did we?

---

