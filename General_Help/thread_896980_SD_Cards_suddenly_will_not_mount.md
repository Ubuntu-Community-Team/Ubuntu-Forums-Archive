---
title: "SD Cards suddenly will not mount"
date: 2008-08-21
forum: General Help
---

### Post by Monsuco on 2008-08-21
My SD Card reader on my laptop suddenly started refusing to mount. The card reader still works in Windows, but it quit working in Ubuntu. I have tested other SD cards, they don't work so it isn't the SD Card. It isn't something wrong with USB support, since standard flash drives still work. Any idea's?

---

### Post by cariboo on 2008-08-21
Is it that the sd cards are not being read or just not automagically mounted. What is the out put of dmesg when you insert your sd card?

Jim

---

### Post by Monsuco on 2008-08-21
Well, mounding /dev/sdb1 didn't work.

As for dmesg
```
[   29.309668] system 00:08: ioport range 0x40b-0x40b has been reserved
[   29.309670] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   29.309673] system 00:08: ioport range 0x4d6-0x4d6 has been reserved
[   29.309675] system 00:08: ioport range 0x530-0x537 has been reserved
[   29.309678] system 00:08: ioport range 0xc00-0xc01 has been reserved
[   29.309680] system 00:08: ioport range 0xc14-0xc14 has been reserved
[   29.309683] system 00:08: ioport range 0xc50-0xc52 has been reserved
[   29.309685] system 00:08: ioport range 0xc6c-0xc6c has been reserved
[   29.309688] system 00:08: ioport range 0xc6f-0xc6f has been reserved
[   29.309690] system 00:08: ioport range 0xcd0-0xcd1 has been reserved
[   29.309693] system 00:08: ioport range 0xcd2-0xcd3 has been reserved
[   29.309695] system 00:08: ioport range 0xcd4-0xcd5 has been reserved
[   29.309698] system 00:08: ioport range 0xcd6-0xcd7 has been reserved
[   29.309700] system 00:08: ioport range 0xcd8-0xcdf has been reserved
[   29.309703] system 00:08: ioport range 0x8000-0x805f has been reserved
[   29.309705] system 00:08: ioport range 0xf40-0xf47 has been reserved
[   29.309708] system 00:08: ioport range 0x87f-0x87f has been reserved
[   29.309714] system 00:09: iomem range 0xe0000-0xfffff could not be reserved
[   29.309717] system 00:09: iomem range 0xfff00000-0xffffffff could not be reserved
[   29.309720] system 00:09: iomem range 0xffb83020-0xffb8401f has been reserved
[   29.309723] system 00:09: iomem range 0xfed00000-0xfed003ff has been reserved
[   29.309725] system 00:09: iomem range 0x0-0x0 could not be reserved
[   29.340083] PCI: Bridge: 0000:00:01.0
[   29.340085]   IO window: 9000-9fff
[   29.340089]   MEM window: cfd00000-cfefffff
[   29.340091]   PREFETCH window: b0000000-bfffffff
[   29.340094] PCI: Bridge: 0000:00:05.0
[   29.340095]   IO window: disabled.
[   29.340097]   MEM window: disabled.
[   29.340099]   PREFETCH window: disabled.
[   29.340102] PCI: Bridge: 0000:00:06.0
[   29.340103]   IO window: disabled.
[   29.340106]   MEM window: f0200000-f02fffff
[   29.340108]   PREFETCH window: disabled.
[   29.340111] PCI: Bridge: 0000:00:07.0
[   29.340112]   IO window: a000-afff
[   29.340115]   MEM window: f0300000-f03fffff
[   29.340117]   PREFETCH window: 88000000-880fffff
[   29.340120] PCI: Bridge: 0000:00:14.4
[   29.340121]   IO window: disabled.
[   29.340129]   MEM window: disabled.
[   29.340133]   PREFETCH window: disabled.
[   29.340151] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   29.340158] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   29.340165] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   29.340180] NET: Registered protocol family 2
[   29.341170] Time: acpi_pm clocksource has been installed.
[   29.341175] Clockevents: could not switch to one-shot mode:<6>Clockevents: could not switch to one-shot mode: lapic is not functional.
[   29.341564] Could not switch to high resolution mode on CPU 1
[   29.341184]  lapic is not functional.
[   29.341186] Could not switch to high resolution mode on CPU 0
[   29.385543] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   29.385794] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   29.386458] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   29.386776] TCP: Hash tables configured (established 131072 bind 65536)
[   29.386779] TCP reno registered
[   29.401591] checking if image is initramfs... it is
[   30.050958] Freeing initrd memory: 7738k freed
[   30.051672] audit: initializing netlink socket (disabled)
[   30.051684] audit(1219316466.464:1): initialized
[   30.051861] highmem bounce pool size: 64 pages
[   30.053677] VFS: Disk quotas dquot_6.5.1
[   30.053749] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   30.053867] io scheduler noop registered
[   30.053869] io scheduler anticipatory registered
[   30.053871] io scheduler deadline registered
[   30.053880] io scheduler cfq registered (default)

[   30.053952] Boot video device is 0000:01:05.0
[   30.054068] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   30.054088] assign_interrupt_mode Found MSI capability
[   30.054111] Allocate Port Service[0000:00:05.0:pcie00]
[   30.054148] Allocate Port Service[0000:00:05.0:pcie02]
[   30.054206] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   30.054225] assign_interrupt_mode Found MSI capability
[   30.054242] Allocate Port Service[0000:00:06.0:pcie00]
[   30.054304] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   30.054322] assign_interrupt_mode Found MSI capability
[   30.054340] Allocate Port Service[0000:00:07.0:pcie00]
[   30.054575] isapnp: Scanning for PnP cards...
[   30.410433] isapnp: No Plug & Play device found
[   30.440224] Real Time Clock Driver v1.12ac
[   30.440330] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   30.441524] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   30.441592] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   30.441685] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[   30.447234] serio: i8042 KBD port at 0x60,0x64 irq 1
[   30.447239] serio: i8042 AUX port at 0x60,0x64 irq 12
[   30.459707] mice: PS/2 mouse device common for all mice
[   30.459824] EISA: Probing bus 0 at eisa.0
[   30.459831] Cannot allocate resource for EISA slot 1
[   30.459857] Cannot allocate resource for EISA slot 8
[   30.459859] EISA: Detected 0 cards.
[   30.459862] cpuidle: using governor ladder
[   30.459864] cpuidle: using governor menu
[   30.459944] NET: Registered protocol family 1
[   30.459966] Using IPI No-Shortcut mode
[   30.460000] registered taskstats version 1
[   30.460117]   Magic number: 4:716:24
[   30.460120]   hash matches /build/buildd/linux-2.6.24/drivers/base/power/main.c:97
[   30.460266] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   30.460268] EDD information not available.
[   30.460505] Freeing unused kernel memory: 368k freed
[   30.506697] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   31.712361] fuse init (API version 7.9)
[   31.734429] ACPI: Processor [CPU0] (supports 8 throttling states)
[   32.085004] r8169 Gigabit Ethernet driver 2.2LK loaded
[   32.085030] ACPI: PCI Interrupt 0000:0e:00.0[A] -> GSI 19 (level, low) -> IRQ 16
[   32.085049] PCI: Setting latency timer of device 0000:0e:00.0 to 64
[   32.085329] eth0: RTL8101e at 0xf884a000, 00:03:25:50:a0:03, XID 34000000 IRQ 220
[   32.110011] SCSI subsystem initialized
[   32.202484] usbcore: registered new interface driver usbfs
[   32.202505] usbcore: registered new interface driver hub
[   32.202795] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   32.202799] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   32.203382] libata version 3.00 loaded.
[   32.203431] usbcore: registered new device driver usb
[   32.203495] SB600_PATA: IDE controller (0x1002:0x438c rev 0x00) at  PCI slot 0000:00:14.1
[   32.203511] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 17
[   32.203520] SB600_PATA: not 100% native mode: will probe irqs later
[   32.203528]     ide0: BM-DMA at 0x8420-0x8427, BIOS settings: hda:DMA, hdb:pio
[   32.203537] Probing IDE interface ide0...
[   32.257072] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   33.610215] hda: TSSTcorpCD/DVDW TS-T632A, ATAPI CD/DVD-ROM drive
[   33.610247] hda: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[   33.610558] hda: UDMA/33 mode selected
[   33.611185] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   33.635388] ahci 0000:00:12.0: version 3.0
[   33.635414] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 22 (level, low) -> IRQ 18
[   33.635436] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[   33.635438] ahci 0000:00:12.0: controller can't do PMP, turning off CAP_PMP
[   34.636148] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[   34.636154] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pio slum part 
[   34.636525] scsi0 : ahci
[   34.636809] scsi1 : ahci
[   34.636953] scsi2 : ahci
[   34.637091] scsi3 : ahci
[   34.637168] ata1: SATA max UDMA/133 abar m1024@0xf0409000 port 0xf0409100 irq 18
[   34.637172] ata2: SATA max UDMA/133 abar m1024@0xf0409000 port 0xf0409180 irq 18
[   34.637176] ata3: SATA max UDMA/133 abar m1024@0xf0409000 port 0xf0409200 irq 18
[   34.637179] ata4: SATA max UDMA/133 abar m1024@0xf0409000 port 0xf0409280 irq 18
[   35.111306] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   35.112645] ata1.00: ATA-8: Hitachi HTS542525K9SA00, BBFOC31P, max UDMA/133
[   35.112650] ata1.00: 488397168 sectors, multi 0: LBA48 NCQ (not used)
[   35.113766] ata1.00: configured for UDMA/133
[   35.422770] ata2: SATA link down (SStatus 0 SControl 300)
[   35.734664] ata3: SATA link down (SStatus 0 SControl 300)
[   36.045701] ata4: SATA link down (SStatus 0 SControl 300)
[   36.045802] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54252 BBFO PQ: 0 ANSI: 5
[   36.047954] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 16 (level, low) -> IRQ 17
[   36.047969] ohci_hcd 0000:00:13.0: OHCI Host Controller
[   36.048241] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[   36.048263] ohci_hcd 0000:00:13.0: irq 17, io mem 0xf0404000
[   36.057028] Driver 'sd' needs updating - please use bus_type methods
[   36.062098] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   36.062110] sd 0:0:0:0: [sda] Write Protect is off
[   36.062112] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   36.062128] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   36.062173] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[   36.062181] sd 0:0:0:0: [sda] Write Protect is off
[   36.062184] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   36.062197] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   36.062200]  sda: sda1 sda2 sda3 sda4
[   36.101726] usb usb1: configuration #1 chosen from 1 choice
[   36.101750] hub 1-0:1.0: USB hub found
[   36.101762] hub 1-0:1.0: 2 ports detected
[   36.112387] sd 0:0:0:0: [sda] Attached SCSI disk
[   36.117689] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   36.205516] ACPI: PCI Interrupt 0000:00:13.1[B] -> GSI 17 (level, low) -> IRQ 19
[   36.205532] ohci_hcd 0000:00:13.1: OHCI Host Controller
[   36.205554] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[   36.205572] ohci_hcd 0000:00:13.1: irq 19, io mem 0xf0405000
[   36.261453] usb usb2: configuration #1 chosen from 1 choice
[   36.261480] hub 2-0:1.0: USB hub found
[   36.261492] hub 2-0:1.0: 2 ports detected
[   36.365212] ACPI: PCI Interrupt 0000:00:13.2[C] -> GSI 18 (level, low) -> IRQ 20
[   36.365226] ohci_hcd 0000:00:13.2: OHCI Host Controller
[   36.365249] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[   36.365265] ohci_hcd 0000:00:13.2: irq 20, io mem 0xf0406000
[   36.421132] usb usb3: configuration #1 chosen from 1 choice
[   36.421151] hub 3-0:1.0: USB hub found
[   36.421161] hub 3-0:1.0: 2 ports detected
[   36.516887] usb 1-1: new full speed USB device using ohci_hcd and address 2
[   36.524960] ACPI: PCI Interrupt 0000:00:13.3[B] -> GSI 17 (level, low) -> IRQ 19
[   36.524975] ohci_hcd 0000:00:13.3: OHCI Host Controller
[   36.524998] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 4
[   36.525013] ohci_hcd 0000:00:13.3: irq 19, io mem 0xf0407000
[   36.580875] usb usb4: configuration #1 chosen from 1 choice
[   36.580895] hub 4-0:1.0: USB hub found
[   36.580906] hub 4-0:1.0: 2 ports detected
[   36.684641] ACPI: PCI Interrupt 0000:00:13.4[C] -> GSI 18 (level, low) -> IRQ 20
[   36.684650] ohci_hcd 0000:00:13.4: OHCI Host Controller
[   36.684667] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 5
[   36.684678] ohci_hcd 0000:00:13.4: irq 20, io mem 0xf0408000
[   36.740580] usb usb5: configuration #1 chosen from 1 choice
[   36.740598] hub 5-0:1.0: USB hub found

[   36.740604] hub 5-0:1.0: 2 ports detected
[   36.748239] usb 1-1: configuration #1 chosen from 1 choice
[   36.845846] ACPI: PCI Interrupt 0000:00:13.5[D] -> GSI 19 (level, low) -> IRQ 16
[   36.845859] ehci_hcd 0000:00:13.5: EHCI Host Controller
[   36.845889] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 6
[   36.845926] ehci_hcd 0000:00:13.5: debug port 1
[   36.845940] ehci_hcd 0000:00:13.5: irq 16, io mem 0xf0409400
[   36.856337] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   36.856452] usb usb6: configuration #1 chosen from 1 choice
[   36.856476] hub 6-0:1.0: USB hub found
[   36.856483] hub 6-0:1.0: 10 ports detected
[   36.976132] usb 1-1: USB disconnect, address 2
[   36.985246] hda: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache
[   36.985254] Uniform CD-ROM driver Revision: 3.20
[   37.059850] Attempting manual resume
[   37.059854] swsusp: Resume From Partition 8:3
[   37.059856] PM: Checking swsusp image.
[   37.059986] PM: Resume from disk failed.
[   37.091307] kjournald starting.  Commit interval 5 seconds
[   37.091708] EXT3-fs: mounted filesystem with ordered data mode.
[   37.343467] usb 6-1: new high speed USB device using ehci_hcd and address 2
[   37.489255] usb 6-1: configuration #1 chosen from 1 choice
[   37.727208] usb 6-8: new high speed USB device using ehci_hcd and address 3
[   37.874134] usb 6-8: configuration #1 chosen from 1 choice
[   47.974797] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   48.152825] Linux agpgart interface v0.102
[   48.189432] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   48.210163] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   48.277694] input: Power Button (FF) as /devices/virtual/input/input3
[   48.332692] ACPI: Power Button (FF) [PWRF]
[   48.332751] input: Power Button (CM) as /devices/virtual/input/input4
[   48.349168] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device
[   48.400588] ACPI: Power Button (CM) [PWRB]
[   48.400649] input: Sleep Button (CM) as /devices/virtual/input/input5
[   48.444505] ACPI: Sleep Button (CM) [SLPB]
[   48.444564] input: Lid Switch as /devices/virtual/input/input6
[   48.483499] ACPI: Lid Switch [LID]
[   48.526629] ACPI: AC Adapter [AC] (on-line)
[   48.709239] Synaptics Touchpad, model: 1, fw: 5.10, id: 0x258eb1, caps: 0xa04713/0x0
[   48.789532] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   48.830531] ACPI: Battery Slot [BAT0] (battery present)
[   49.164108] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b/LNXVIDEO:00/input/input8
[   49.227601] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   49.395609] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 17
[   49.428107] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   49.464362] [fglrx] Maximum main memory to use for locked dma buffers: 1534 MBytes.
[   49.464396] [fglrx] ASYNCIO init succeed!
[   49.464705] [fglrx] PAT is enabled successfully!
[   49.472113] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   49.485852] usbcore: registered new interface driver libusual
[   49.501104] Linux video capture interface: v2.00
[   49.503793] Initializing USB Mass Storage driver...
[   49.504326] scsi4 : SCSI emulation for USB Mass Storage devices
[   49.504585] usbcore: registered new interface driver usb-storage
[   49.504589] USB Mass Storage support registered.
[   49.504592] usb-storage: device found at 3
[   49.504594] usb-storage: waiting for device to settle before scanning
[   49.507619] ACPI: PCI Interrupt 0000:01:05.2[B] -> GSI 19 (level, low) -> IRQ 16
[   49.520546] uvcvideo: Found UVC 1.00 device Gateway USB 2.0 Webcam (04f2:b027)
[   49.522536] usbcore: registered new interface driver uvcvideo
[   49.522542] USB Video Class driver (v0.1.0)
[   50.875551] lp: driver loaded but no devices found
[   50.952220] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   51.044830] ndiswrapper: driver netmw14x (NETGEAR,10/04/2006, 2.1.4.3) loaded
[   51.044693] ACPI: PCI Interrupt 0000:08:00.0[A] -> GSI 18 (level, low) -> IRQ 20
[   51.044723] PCI: Setting latency timer of device 0000:08:00.0 to 64
[   51.046900] ndiswrapper: using IRQ 20
[   51.381360] wlan0: ethernet device 00:16:44:71:28:3e using NDIS driver: netmw14x, version: 0x2010403, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 11AB:2A08.5.conf
[   51.381383] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   51.381444] usbcore: registered new interface driver ndiswrapper
[   51.440478] Adding 522104k swap on /dev/sda3.  Priority:-1 extents:1 across:522104k
[   51.990856] EXT3 FS on sda4, internal journal
[   52.159946] device-mapper: uevent: version 1.0.3
[   52.159977] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[   53.549190] ip_tables: (C) 2000-2006 Netfilter Core Team
[   54.086487] No dock devices found.
[   54.399132] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-58 processors (2 cpu cores) (version 2.20.00)
[   54.398823] powernow-k8:    0 : fid 0xb (1900 MHz), vid 0x11
[   54.398828] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x12
[   54.398830] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x13
[   54.398833] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1e
[   54.494610] usb-storage: device scan complete
[   54.500841] scsi 4:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[   55.389634] apm: BIOS not found.
[   55.694449] ppdev: user-space parallel port driver
[   55.980684] audit(1219338094.254:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5261 profile="/usr/sbin/cupsd" namespace="default"
[   56.208962] Clocksource tsc unstable (delta = -78674018 ns)
[   56.933931] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   56.933973] sd 4:0:0:0: Attached scsi generic sg1 type 0
[   57.704506] r8169: eth0: link down
[   57.811468] Bluetooth: Core ver 2.11
[   57.812200] NET: Registered protocol family 31
[   57.812203] Bluetooth: HCI device and connection manager initialized
[   57.812207] Bluetooth: HCI socket layer initialized
[   57.857765] Bluetooth: L2CAP ver 2.9
[   57.857771] Bluetooth: L2CAP socket layer initialized
[   57.910203] Bluetooth: RFCOMM socket layer initialized
[   57.910218] Bluetooth: RFCOMM TTY layer initialized
[   57.910219] Bluetooth: RFCOMM ver 1.8
[   59.119090] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 18 (level, low) -> IRQ 20
[   60.168885] [fglrx] GART Table is not in FRAME_BUFFER range 
[   60.168898] [fglrx] Reserve Block - 0 offset =  0X17ffb000 length = 0X5000
[   60.168902] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X1000000
[   60.419988] [fglrx] interrupt source 10000000 successfully enabled
[   60.419996] [fglrx] enable ID = 0x00000008
[   60.420007] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[   65.047887] hda-intel: Invalid position buffer, using LPIB read method instead.
[   77.145893] NET: Registered protocol family 10
[   77.146531] lo: Disabled Privacy Extensions
[   77.147117] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   77.147539] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   84.364546] CPU0 attaching NULL sched-domain.
[   84.364554] CPU1 attaching NULL sched-domain.
[   84.375245] CPU0 attaching sched-domain:
[   84.375249]  domain 0: span 03
[   84.375251]   groups: 01 02
[   84.375255] CPU1 attaching sched-domain:
[   84.375256]  domain 0: span 03
[   84.375258]   groups: 02 01
[   86.957969] NET: Registered protocol family 17
[   96.856799] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  103.575723] wlan0: no IPv6 routers present
[ 2387.854920] APIC error on CPU1: 00(40)
[ 2387.856251] APIC error on CPU0: 00(40)
[ 6726.365527] APIC error on CPU1: 40(40)
[ 6726.368315] APIC error on CPU0: 40(40)
[ 7553.018334] APIC error on CPU1: 40(40)
[ 7553.021492] APIC error on CPU0: 40(40)
[ 9579.297565] APIC error on CPU0: 40(40)
[ 9579.289834] APIC error on CPU1: 40(40)
[ 9817.101099] usb 6-2: new high speed USB device using ehci_hcd and address 4
[ 9817.157025] usb 6-2: configuration #1 chosen from 1 choice
[ 9817.158848] scsi5 : SCSI emulation for USB Mass Storage devices
[ 9817.172471] usb-storage: device found at 4
[ 9817.172478] usb-storage: waiting for device to settle before scanning
[ 9819.273111] usb-storage: device scan complete
[ 9819.273635] scsi 5:0:0:0: Direct-Access     SanDisk  Cruzer Pattern   7.01 PQ: 0 ANSI: 0 CCS
[ 9819.274777] sd 5:0:0:0: [sdc] 3907583 512-byte hardware sectors (2001 MB)
[ 9819.275066] sd 5:0:0:0: [sdc] Write Protect is off
[ 9819.275070] sd 5:0:0:0: [sdc] Mode Sense: 45 00 00 08
[ 9819.275072] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 9819.276245] sd 5:0:0:0: [sdc] 3907583 512-byte hardware sectors (2001 MB)
[ 9819.276560] sd 5:0:0:0: [sdc] Write Protect is off
[ 9819.276563] sd 5:0:0:0: [sdc] Mode Sense: 45 00 00 08
[ 9819.276565] sd 5:0:0:0: [sdc] Assuming drive cache: write through
[ 9819.276570]  sdc: sdc1
[ 9819.277531] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[ 9819.277567] sd 5:0:0:0: Attached scsi generic sg2 type 0
[ 9825.281525] usb 6-2: USB disconnect, address 4
[ 9825.281862] Buffer I/O error on device sdc1, logical block 480
[ 9825.281868] lost page write due to I/O error on sdc1
[ 9825.281873] Buffer I/O error on device sdc1, logical block 481
[ 9825.281875] lost page write due to I/O error on sdc1
[ 9825.440801] scsi 5:0:0:0: rejecting I/O to dead device
[ 9828.889792] usb 6-2: new high speed USB device using ehci_hcd and address 5
[ 9828.945779] usb 6-2: configuration #1 chosen from 1 choice
[ 9828.946325] scsi6 : SCSI emulation for USB Mass Storage devices
[ 9828.955198] usb-storage: device found at 5
[ 9828.955203] usb-storage: waiting for device to settle before scanning
[ 9831.585471] usb-storage: device scan complete
[ 9831.586092] scsi 6:0:0:0: Direct-Access     SanDisk  Cruzer Micro     0.1  PQ: 0 ANSI: 2
[ 9831.581178] sd 6:0:0:0: [sdc] 2001888 512-byte hardware sectors (1025 MB)
[ 9831.581755] sd 6:0:0:0: [sdc] Write Protect is off
[ 9831.581759] sd 6:0:0:0: [sdc] Mode Sense: 03 00 00 00
[ 9831.581762] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[ 9831.584495] sd 6:0:0:0: [sdc] 2001888 512-byte hardware sectors (1025 MB)
[ 9831.585122] sd 6:0:0:0: [sdc] Write Protect is off
[ 9831.585125] sd 6:0:0:0: [sdc] Mode Sense: 03 00 00 00
[ 9831.585127] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[ 9831.585131]  sdc: sdc1
[ 9831.586326] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[ 9831.586369] sd 6:0:0:0: Attached scsi generic sg2 type 0
[ 9835.031063] usb 6-2: USB disconnect, address 5
[ 9835.033683] Buffer I/O error on device sdc1, logical block 1
[ 9835.033688] lost page write due to I/O error on sdc1
[10353.665158] APIC error on CPU0: 40(40)
[10353.656328] APIC error on CPU1: 40(40)
[10830.407597] CPU0 attaching NULL sched-domain.
[10830.407606] CPU1 attaching NULL sched-domain.
[10830.425175] CPU0 attaching sched-domain:
[10830.425180]  domain 0: span 03
[10830.425182]   groups: 01 02
[10830.425185]   domain 1: span 03
[10830.425187]    groups: 03
[10830.425189] CPU1 attaching sched-domain:
[10830.425191]  domain 0: span 03
[10830.425192]   groups: 02 01
[10830.425195]   domain 1: span 03
[10830.425196]    groups: 03
[10835.371147] CPU0 attaching NULL sched-domain.
[10835.371155] CPU1 attaching NULL sched-domain.
[10835.378174] CPU0 attaching sched-domain:
[10835.378179]  domain 0: span 03
[10835.378181]   groups: 01 02
[10835.378184] CPU1 attaching sched-domain:
[10835.378186]  domain 0: span 03
[10835.378187]   groups: 02 01
[11581.166739] CPU0 attaching NULL sched-domain.
[11581.166749] CPU1 attaching NULL sched-domain.
[11581.173076] CPU0 attaching sched-domain:
[11581.173083]  domain 0: span 03
[11581.173085]   groups: 01 02
[11581.173089]   domain 1: span 03
[11581.173090]    groups: 03
[11581.173093] CPU1 attaching sched-domain:
[11581.173094]  domain 0: span 03
[11581.173096]   groups: 02 01
[11581.173098]   domain 1: span 03
[11581.173100]    groups: 03
[11627.932395] CPU0 attaching NULL sched-domain.
[11627.932404] CPU1 attaching NULL sched-domain.
[11627.941229] CPU0 attaching sched-domain:
[11627.941234]  domain 0: span 03
[11627.941238]   groups: 01 02
[11627.941241] CPU1 attaching sched-domain:
[11627.941243]  domain 0: span 03
[11627.941246]   groups: 02 01
[12225.450271] APIC error on CPU1: 40(40)
[12225.467376] APIC error on CPU0: 40(40)
[13700.730553] APIC error on CPU0: 40(40)
[13700.713235] APIC error on CPU1: 40(40)
[14547.600762] CPU0 attaching NULL sched-domain.
[14547.600772] CPU1 attaching NULL sched-domain.
[14547.613765] CPU0 attaching sched-domain:
[14547.613770]  domain 0: span 03
[14547.613773]   groups: 01 02
[14547.613776]   domain 1: span 03
[14547.613778]    groups: 03
[14547.613780] CPU1 attaching sched-domain:
[14547.613781]  domain 0: span 03
[14547.613783]   groups: 02 01
[14547.613785]   domain 1: span 03
[14547.613787]    groups: 03
[14556.261537] CPU0 attaching NULL sched-domain.
[14556.261546] CPU1 attaching NULL sched-domain.
[14556.271254] CPU0 attaching sched-domain:
[14556.271261]  domain 0: span 03
[14556.271266]   groups: 01 02
[14556.271271] CPU1 attaching sched-domain:
[14556.271272]  domain 0: span 03
[14556.271274]   groups: 02 01
[15464.397627] APIC error on CPU0: 40(40)
[15464.378535] APIC error on CPU1: 40(40)

```

---

