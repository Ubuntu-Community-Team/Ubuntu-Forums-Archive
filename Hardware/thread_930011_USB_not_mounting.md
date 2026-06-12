---
title: "USB not mounting"
date: 2008-09-25
forum: Hardware
---

### Post by Forbees on 2008-09-25
i have a new computer, built it myself and i'm afraid ubuntu doesn't know how to handle the usb drives yet

i use a usb mouse no problems but when i try to plug in a flash drive nothing happens

also i've heard lexmark x1270 works fine as a scanner, but when i plug it in nothing happens (printer is supposed to be hard to force)

i had a friend come over who knows more about linux than me, he tried using the code to force mount it, and nothing happened

he than used some other code and apparently (acording to him) ubuntu thinks that my flash drives are 1.5meg floppy disks

idk whats going on, i havent heard of this problem before

i guess we can start from the beginng, tell me some things to try, and i'll let you know if they work

---

### Post by Crafty Kisses on 2008-09-25
Post the results of this command:
```
sudo fdisk -l
```

---

### Post by prshah on 2008-09-25
> **Forbees said:**
> 
tell me some things to try

Plug in your flash drives and printer, turn it on and wait about 10 seconds, then give the below command in the terminal (Applications-Accessories-Terminal) and post the output here:```
dmesg | tail
lsusb
```

---

### Post by lovegreat on 2008-09-25
i have the same problem ,here ie my



[   13.819654] system 00:02: ioport range 0x1000-0x1005 has been reserved
[   13.819656] system 00:02: ioport range 0x1008-0x100f has been reserved
[   13.819663] system 00:03: ioport range 0xf400-0xf4fe has been reserved
[   13.819665] system 00:03: ioport range 0x1006-0x1007 has been reserved
[   13.819668] system 00:03: ioport range 0x100a-0x1059 could not be reserved
[   13.819671] system 00:03: ioport range 0x1060-0x107f has been reserved
[   13.819673] system 00:03: ioport range 0x1080-0x10bf has been reserved
[   13.819676] system 00:03: ioport range 0x10c0-0x10df has been reserved
[   13.819678] system 00:03: ioport range 0x1010-0x102f has been reserved
[   13.819681] system 00:03: ioport range 0x809-0x809 has been reserved
[   13.819688] system 00:08: ioport range 0xc80-0xcff could not be reserved
[   13.819691] system 00:08: ioport range 0x910-0x91f has been reserved
[   13.819693] system 00:08: ioport range 0x920-0x92f has been reserved
[   13.819695] system 00:08: ioport range 0xcb0-0xcbf has been reserved
[   13.819698] system 00:08: ioport range 0x930-0x97f has been reserved
[   13.819705] system 00:0b: iomem range 0xfed00000-0xfed003ff has been reserved
[   13.820151] PCI: Bridge: 0000:00:1c.0
[   13.820153]   IO window: disabled.
[   13.820158]   MEM window: disabled.
[   13.820163]   PREFETCH window: disabled.
[   13.820169] PCI: Bridge: 0000:00:1c.1
[   13.820170]   IO window: disabled.
[   13.820176]   MEM window: efd00000-efdfffff
[   13.820180]   PREFETCH window: disabled.
[   13.820186] PCI: Bridge: 0000:00:1c.3
[   13.820189]   IO window: d000-dfff
[   13.820194]   MEM window: efa00000-efcfffff
[   13.820199]   PREFETCH window: e0000000-e01fffff
[   13.820206] PCI: Bridge: 0000:00:1e.0
[   13.820207]   IO window: disabled.
[   13.820213]   MEM window: ef900000-ef9fffff
[   13.820217]   PREFETCH window: disabled.
[   13.820249] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   13.820256] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   13.820280] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 17 (level, low) -> IRQ 17
[   13.820286] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   13.820310] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   13.820316] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   13.820330] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   13.820339] NET: Registered protocol family 2
[   13.855602] IP route cache hash table entries: 32768 (order: 6, 262144 bytes)
[   13.856048] TCP established hash table entries: 131072 (order: 9, 2097152 bytes)
[   13.857080] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   13.857929] TCP: Hash tables configured (established 131072 bind 65536)
[   13.857932] TCP reno registered
[   13.867702] checking if image is initramfs... it is
[   14.682919] Freeing initrd memory: 7536k freed
[   14.687284] Simple Boot Flag at 0x79 set to 0x1
[   16.535613] audit: initializing netlink socket (disabled)
[   16.535636] audit(1222417442.612:1): initialized
[   16.538082] VFS: Disk quotas dquot_6.5.1
[   16.538162] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   16.538291] io scheduler noop registered
[   16.538293] io scheduler anticipatory registered
[   16.538295] io scheduler deadline registered
[   16.538414] io scheduler cfq registered (default)
[   16.538426] Boot video device is 0000:00:02.0
[   16.539912] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   16.539972] assign_interrupt_mode Found MSI capability
[   16.540022] Allocate Port Service[0000:00:1c.0:pcie00]
[   16.540068] Allocate Port Service[0000:00:1c.0:pcie02]
[   16.540180] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   16.540239] assign_interrupt_mode Found MSI capability
[   16.540285] Allocate Port Service[0000:00:1c.1:pcie00]
[   16.540322] Allocate Port Service[0000:00:1c.1:pcie02]
[   16.540428] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   16.540486] assign_interrupt_mode Found MSI capability
[   16.540532] Allocate Port Service[0000:00:1c.3:pcie00]
[   16.540572] Allocate Port Service[0000:00:1c.3:pcie02]
[   16.569507] Real Time Clock Driver v1.12ac
[   16.569683] hpet_resources: 0xfed00000 is busy
[   16.569735] Linux agpgart interface v0.102
[   16.569737] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   16.570980] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   16.571053] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   16.571157] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   16.573900] serio: i8042 KBD port at 0x60,0x64 irq 1
[   16.573905] serio: i8042 AUX port at 0x60,0x64 irq 12
[   16.590521] mice: PS/2 mouse device common for all mice
[   16.590562] cpuidle: using governor ladder
[   16.590564] cpuidle: using governor menu
[   16.590705] NET: Registered protocol family 1
[   16.590812] registered taskstats version 1
[   16.590939]   Magic number: 8:194:423
[   16.591059] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   16.591062] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   16.591064] EDD information not available.
[   16.591071] Freeing unused kernel memory: 320k freed
[   14.746368] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   17.798721] fuse init (API version 7.9)
[   17.819083] ACPI: SSDT 3F6D4176, 0202 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[   17.819285] ACPI: SSDT 3F6D3F2B, 01C6 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   15.972594] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   15.972600] ACPI: Processor [CPU0] (supports 8 throttling states)
[   15.972841] ACPI: SSDT 3F6D4378, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[   15.973027] ACPI: SSDT 3F6D40F1, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[   17.820932] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   17.820937] ACPI: Processor [CPU1] (supports 8 throttling states)
[   17.825969] ACPI: Thermal Zone [THM] (36 C)
[   16.275210] usbcore: registered new interface driver usbfs
[   16.275237] usbcore: registered new interface driver hub
[   16.275270] usbcore: registered new device driver usb
[   16.278448] USB Universal Host Controller Interface driver v3.0
[   16.278512] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 20 (level, low) -> IRQ 20
[   16.278524] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   16.278528] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   16.278795] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   16.278829] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bf80
[   16.278960] usb usb1: configuration #1 chosen from 1 choice
[   16.278985] hub 1-0:1.0: USB hub found
[   16.278991] hub 1-0:1.0: 2 ports detected
[   18.222396] SCSI subsystem initialized
[   16.379673] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 21 (level, low) -> IRQ 21
[   16.379688] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   16.379692] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   16.379717] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   16.379751] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000bf60
[   16.379868] usb usb2: configuration #1 chosen from 1 choice
[   16.379891] hub 2-0:1.0: USB hub found
[   16.379897] hub 2-0:1.0: 2 ports detected
[   18.255886] libata version 3.00 loaded.
[   16.483532] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 22 (level, low) -> IRQ 22
[   16.483545] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   16.483550] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   16.483575] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   16.483608] uhci_hcd 0000:00:1d.2: irq 22, io base 0x0000bf40
[   16.483730] usb usb3: configuration #1 chosen from 1 choice
[   16.483754] hub 3-0:1.0: USB hub found
[   16.483760] hub 3-0:1.0: 2 ports detected
[   16.587354] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 23 (level, low) -> IRQ 23
[   16.587367] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   16.587371] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   16.587397] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   16.587432] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000bf20
[   16.587548] usb usb4: configuration #1 chosen from 1 choice
[   16.587571] hub 4-0:1.0: USB hub found
[   16.587577] hub 4-0:1.0: 2 ports detected
[   16.691385] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 20 (level, low) -> IRQ 20
[   16.691966] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   16.691973] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   16.692027] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   16.695936] ehci_hcd 0000:00:1d.7: debug port 1
[   16.695943] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   16.695950] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xffa80000
[   16.711044] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   16.711180] usb usb5: configuration #1 chosen from 1 choice
[   16.711205] hub 5-0:1.0: USB hub found
[   16.711212] hub 5-0:1.0: 8 ports detected
[   18.662326] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 19 (level, low) -> IRQ 19
[   18.715409] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[ef9fd800-ef9fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   18.735347] ata_piix 0000:00:1f.2: version 2.12
[   18.735356] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[   18.735391] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
[   18.735427] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   18.736878] scsi0 : ata_piix
[   18.737279] scsi1 : ata_piix
[   18.738087] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[   18.738091] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[   18.759256] ata1.00: ATA-7: ST9120822AS, 3.CDD, max UDMA/133
[   18.759262] ata1.00: 234441648 sectors, multi 8: LBA48 NCQ (depth 0/32)
[   16.912518] Clocksource tsc unstable (delta = -158285655 ns)
[   16.913031] ata1.00: configured for UDMA/133
[   18.792095] ata2.00: ATAPI: PIONEER DVD+/-RW DR-K17Y, 0.95, max UDMA/33
[   16.947124] usb 4-2: new low speed USB device using uhci_hcd and address 2
[   18.808014] ata2.00: configured for UDMA/33
[   18.808125] scsi 0:0:0:0: Direct-Access     ATA      ST9120822AS      3.CD PQ: 0 ANSI: 5
[   16.962562] usb 4-2: configuration #1 chosen from 1 choice
[   18.816649] scsi 1:0:0:0: CD-ROM            PIONEER  DVD+-RW DR-K17Y  0.95 PQ: 0 ANSI: 5
[   16.969469] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   16.978713] usbcore: registered new interface driver hiddev
[   16.981281] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[   16.981291] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[   16.981298] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[   16.981890] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.3/usb4/4-2/4-2:1.0/input/input2
[   16.988426] input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1d.3-2
[   16.988451] usbcore: registered new interface driver usbhid
[   16.988456] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   17.001831] ssb: Sonics Silicon Backplane found on PCI device 0000:02:00.0
[   17.001887] b44.c:v2.0
[   17.006401] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:15:c5:7b:e0:90
[   17.014462] Driver 'sd' needs updating - please use bus_type methods
[   17.014551] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   17.014564] sd 0:0:0:0: [sda] Write Protect is off
[   17.014566] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   17.014583] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   17.014629] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   17.014639] sd 0:0:0:0: [sda] Write Protect is off
[   17.014641] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   17.014657] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   17.014661]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   17.068748]  sda1 sda2 < sda5 sda6 sda7 sda8 sda9 sda10 >
[   17.174690] sd 0:0:0:0: [sda] Attached SCSI disk
[   17.178788] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   17.178809] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   19.071853] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   19.071859] Uniform CD-ROM driver Revision: 3.20
[   19.071912] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   19.313557] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[444fc00022aa145c]
[   19.784955] Attempting manual resume
[   19.784958] swsusp: Resume From Partition 8:8
[   19.784960] PM: Checking swsusp image.
[   19.785144] PM: Resume from disk failed.
[   17.961426] kjournald starting.  Commit interval 5 seconds
[   17.961446] EXT3-fs: mounted filesystem with ordered data mode.
[   28.437003] input: PC Speaker as /devices/platform/pcspkr/input/input3
[   28.628959] agpgart: Detected an Intel 945GM Chipset.
[   28.629978] agpgart: Detected 7932K stolen memory.
[   28.645055] agpgart: AGP aperture is 256M @ 0xd0000000
[   28.729550] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   28.796712] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   30.682024] intel_rng: FWH not detected
[   28.954892] ACPI: AC Adapter [AC] (on-line)
[   30.819590] input: Lid Switch as /devices/virtual/input/input4
[   30.852057] ACPI: Lid Switch [LID]
[   30.852115] input: Power Button (CM) as /devices/virtual/input/input5
[   30.912487] ACPI: Power Button (CM) [PBTN]
[   30.912550] input: Sleep Button (CM) as /devices/virtual/input/input6
[   29.106393] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000
[   30.976370] ACPI: Sleep Button (CM) [SBTN]
[   29.141896] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   31.026897] ACPI: Battery Slot [BAT0] (battery present)
[   31.038806] ACPI: WMI-Acer: Mapper loaded
[   29.210629] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   31.074089] iTCO_vendor_support: vendor-support=0
[   31.116158] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   31.116268] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   31.116311] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   31.226424] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input8
[   31.287907] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   31.288057] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:01/input/input9
[   31.351804] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[   32.237454] ricoh-mmc: Ricoh MMC Controller disabling driver
[   32.237458] ricoh-mmc: Copyright(c) Philip Langdale
[   32.237510] ricoh-mmc: Ricoh MMC controller found at 0000:02:01.2 [1180:0843] (rev 1)
[   32.237523] ricoh-mmc: Controller is now disabled.
[   30.510343] sdhci: Secure Digital Host Controller Interface driver
[   30.510347] sdhci: Copyright(c) Pierre Ossman
[   30.510388] sdhci: SDHCI controller found at 0000:02:01.1 [1180:0822] (rev 19)
[   30.510413] ACPI: PCI Interrupt 0000:02:01.1[B] -> GSI 18 (level, low) -> IRQ 18
[   30.511038] mmc0: SDHCI at 0xef9fd400 irq 18 DMA
[   30.524851] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   30.524855] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   30.524998] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   30.525013] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[   30.525580] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   30.752285] iwl3945: Radio Frequency Kill Switch is On:
[   30.752287] Kill switch must be turned off for wireless networking to work.
[   30.757476] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   30.767603] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   30.787726] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   30.815436] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   30.835595] iwl3945: Tunable channels: 13 802.11bg, 4 802.11a channels
[   30.996409] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 21
[   30.997004] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   31.297755] lp: driver loaded but no devices found
[   33.289561] Adding 192740k swap on /dev/sda8.  Priority:-1 extents:1 across:192740k
[   31.884287] EXT3 FS on sda9, internal journal
[   32.567560] kjournald starting.  Commit interval 5 seconds
[   32.567722] EXT3 FS on sda10, internal journal
[   32.567728] EXT3-fs: mounted filesystem with ordered data mode.
[   32.990052] ip_tables: (C) 2000-2006 Netfilter Core Team
[   33.431284] No dock devices found.
[   34.746178] ppdev: user-space parallel port driver
[   34.933344] audit(1222388664.032:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5063 profile="/usr/sbin/cupsd" namespace="default"
[   38.056265] Bluetooth: Core ver 2.11
[   38.056688] NET: Registered protocol family 31
[   38.056693] Bluetooth: HCI device and connection manager initialized
[   38.056698] Bluetooth: HCI socket layer initialized
[   39.953268] Bluetooth: L2CAP ver 2.9
[   39.953276] Bluetooth: L2CAP socket layer initialized
[   39.996700] Bluetooth: RFCOMM socket layer initialized
[   39.996723] Bluetooth: RFCOMM TTY layer initialized
[   39.996726] Bluetooth: RFCOMM ver 1.8
[   40.222925] b44: eth0: Link is up at 100 Mbps, full duplex.
[   40.222932] b44: eth0: Flow control is off for TX and off for RX.
[   40.402631] [drm] Initialized drm 1.1.0 20060810
[   40.405856] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   40.405869] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   40.405962] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   41.655482] NET: Registered protocol family 17
[   70.519860] CPU0 attaching NULL sched-domain.
[   70.519870] CPU1 attaching NULL sched-domain.
[   70.545881] CPU0 attaching sched-domain:
[   70.545890]  domain 0: span 03
[   70.545893]   groups: 01 02
[   70.545898]   domain 1: span 03
[   70.545900]    groups: 03
[   70.545904] CPU1 attaching sched-domain:
[   70.545907]  domain 0: span 03
[   70.545911]   groups: 02 01
[   70.545916]   domain 1: span 03
[   70.545919]    groups: 03
[  310.634737] usb 5-6: new high speed USB device using ehci_hcd and address 3
[  308.985987] usb 5-6: configuration #1 chosen from 1 choice
[  309.095454] usbcore: registered new interface driver libusual
[  309.110188] Initializing USB Mass Storage driver...
[  309.112488] scsi2 : SCSI emulation for USB Mass Storage devices
[  309.113634] usbcore: registered new interface driver usb-storage
[  309.113640] USB Mass Storage support registered.
[  309.114093] usb-storage: device found at 3
[  309.114096] usb-storage: waiting for device to settle before scanning
[  309.618219] usb-storage: device scan complete
[  309.622200] scsi 2:0:0:0: Direct-Access     TXJ           HS-HD       2.23 PQ: 0 ANSI: 0
[  309.625564] scsi 2:0:0:1: Direct-Access     TXJ           HS-CF       2.23 PQ: 0 ANSI: 0
[  309.628682] scsi 2:0:0:2: Direct-Access     TXJ           HS-MS/SM/SD 2.23 PQ: 0 ANSI: 0
[  310.108328] sd 2:0:0:0: [sdb] 58605120 512-byte hardware sectors (30006 MB)
[  310.110571] sd 2:0:0:0: [sdb] Write Protect is off
[  310.110576] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  310.110578] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  310.114442] sd 2:0:0:0: [sdb] 58605120 512-byte hardware sectors (30006 MB)
[  310.116683] sd 2:0:0:0: [sdb] Write Protect is off
[  310.116688] sd 2:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  310.116690] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  310.116697]  sdb: sdb1
[  311.053694] sd 2:0:0:0: [sdb] Attached SCSI disk
[  311.053764] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  311.057700] sd 2:0:0:1: [sdc] Attached SCSI removable disk
[  311.057769] sd 2:0:0:1: Attached scsi generic sg3 type 0
[  311.062942] sd 2:0:0:2: [sdd] Attached SCSI removable disk
[  311.063009] sd 2:0:0:2: Attached scsi generic sg4 type 0
[  318.110840] usb 5-6: USB disconnect, address 3
[  325.422786] usb 5-6: new high speed USB device using ehci_hcd and address 4
[  323.774073] usb 5-6: configuration #1 chosen from 1 choice
[  323.774694] scsi3 : SCSI emulation for USB Mass Storage devices
[  323.775261] usb-storage: device found at 4
[  323.775269] usb-storage: waiting for device to settle before scanning
[  324.277832] usb-storage: device scan complete
[  324.281931] scsi 3:0:0:0: Direct-Access     TXJ           HS-HD       2.23 PQ: 0 ANSI: 0
[  324.285444] scsi 3:0:0:1: Direct-Access     TXJ           HS-CF       2.23 PQ: 0 ANSI: 0
[  324.288538] scsi 3:0:0:2: Direct-Access     TXJ           HS-MS/SM/SD 2.23 PQ: 0 ANSI: 0
[  324.758339] sd 3:0:0:0: [sdb] 58605120 512-byte hardware sectors (30006 MB)
[  324.760484] sd 3:0:0:0: [sdb] Write Protect is off
[  324.760495] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  324.760509] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  324.764211] sd 3:0:0:0: [sdb] 58605120 512-byte hardware sectors (30006 MB)
[  324.766336] sd 3:0:0:0: [sdb] Write Protect is off
[  324.766346] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  324.766349] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  324.766362]  sdb: sdb1
[  325.698670] sd 3:0:0:0: [sdb] Attached SCSI disk
[  325.698744] sd 3:0:0:0: Attached scsi generic sg2 type 0
[  325.702668] sd 3:0:0:1: [sdc] Attached SCSI removable disk
[  325.702736] sd 3:0:0:1: Attached scsi generic sg3 type 0
[  325.707915] sd 3:0:0:2: [sdd] Attached SCSI removable disk
[  325.707983] sd 3:0:0:2: Attached scsi generic sg4 type 0
[  327.513434] FAT: Filesystem panic (dev sdb1)
[  327.513443]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  327.513448]     File system has been set read-only
[  327.652893] FAT: Filesystem panic (dev sdb1)
[  327.652902]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  327.653045] FAT: Filesystem panic (dev sdb1)
[  327.653048]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  329.142507] FAT: Filesystem panic (dev sdb1)
[  329.142515]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  330.358641] usb 5-6: USB disconnect, address 4
[  358.488628] usb 5-6: new high speed USB device using ehci_hcd and address 5
[  358.688070] usb 5-6: configuration #1 chosen from 1 choice
[  358.694444] scsi4 : SCSI emulation for USB Mass Storage devices
[  358.694985] usb-storage: device found at 5
[  358.694995] usb-storage: waiting for device to settle before scanning
[  361.202376] usb-storage: device scan complete
[  361.205927] scsi 4:0:0:0: Direct-Access     TXJ           HS-HD       2.23 PQ: 0 ANSI: 0
[  361.209170] scsi 4:0:0:1: Direct-Access     TXJ           HS-CF       2.23 PQ: 0 ANSI: 0
[  359.365075] scsi 4:0:0:2: Direct-Access     TXJ           HS-MS/SM/SD 2.23 PQ: 0 ANSI: 0
[  359.838477] sd 4:0:0:0: [sdb] 58605120 512-byte hardware sectors (30006 MB)
[  359.840604] sd 4:0:0:0: [sdb] Write Protect is off
[  359.840614] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  359.840618] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  359.844217] sd 4:0:0:0: [sdb] 58605120 512-byte hardware sectors (30006 MB)
[  359.846323] sd 4:0:0:0: [sdb] Write Protect is off
[  359.846333] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  359.846337] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  359.846349]  sdb: sdb1
[  360.806122] sd 4:0:0:0: [sdb] Attached SCSI disk
[  360.806198] sd 4:0:0:0: Attached scsi generic sg2 type 0
[  360.810003] sd 4:0:0:1: [sdc] Attached SCSI removable disk
[  360.810070] sd 4:0:0:1: Attached scsi generic sg3 type 0
[  360.815631] sd 4:0:0:2: [sdd] Attached SCSI removable disk
[  360.815700] sd 4:0:0:2: Attached scsi generic sg4 type 0
[  361.333529] FAT: Filesystem panic (dev sdb1)
[  361.333539]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  361.333543]     File system has been set read-only
[  362.388471] FAT: Filesystem panic (dev sdb1)
[  362.388480]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  362.388633] FAT: Filesystem panic (dev sdb1)
[  362.388636]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  367.915656] FAT: Filesystem panic (dev sdb1)
[  367.915664]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  581.710998] usb 5-6: USB disconnect, address 5
[  943.472752] usb 5-6: new high speed USB device using ehci_hcd and address 6
[  943.671171] usb 5-6: configuration #1 chosen from 1 choice
[  943.671533] scsi5 : SCSI emulation for USB Mass Storage devices
[  943.671807] usb-storage: device found at 6
[  943.671810] usb-storage: waiting for device to settle before scanning
[  945.637979] usb-storage: device scan complete
[  945.641839] scsi 5:0:0:0: Direct-Access     TXJ           HS-HD       2.23 PQ: 0 ANSI: 0
[  945.644961] scsi 5:0:0:1: Direct-Access     TXJ           HS-CF       2.23 PQ: 0 ANSI: 0
[  945.648064] scsi 5:0:0:2: Direct-Access     TXJ           HS-MS/SM/SD 2.23 PQ: 0 ANSI: 0
[  946.123183] sd 5:0:0:0: [sdb] 58605120 512-byte hardware sectors (30006 MB)
[  946.125429] sd 5:0:0:0: [sdb] Write Protect is off
[  946.125433] sd 5:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  946.125435] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  946.129670] sd 5:0:0:0: [sdb] 58605120 512-byte hardware sectors (30006 MB)
[  946.131794] sd 5:0:0:0: [sdb] Write Protect is off
[  946.131798] sd 5:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  946.131801] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  946.131807]  sdb: sdb1
[  947.079904] sd 5:0:0:0: [sdb] Attached SCSI disk
[  947.079975] sd 5:0:0:0: Attached scsi generic sg2 type 0
[  947.084686] sd 5:0:0:1: [sdc] Attached SCSI removable disk
[  947.084756] sd 5:0:0:1: Attached scsi generic sg3 type 0
[  947.090425] sd 5:0:0:2: [sdd] Attached SCSI removable disk
[  947.090494] sd 5:0:0:2: Attached scsi generic sg4 type 0
[  949.642610] FAT: Filesystem panic (dev sdb1)
[  949.642619]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  949.642623]     File system has been set read-only
[  948.871715] FAT: Filesystem panic (dev sdb1)
[  948.871724]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  950.719588] FAT: Filesystem panic (dev sdb1)
[  950.719593]     fat_get_cluster: invalid cluster chain (i_pos 0)
ycq@ycq-laptop:~$ sudo lsubs
sudo: lsubs: command not found
ycq@ycq-laptop:~$ sudo lsusb
Bus 005 Device 006: ID 0424:223a Standard Microsystems Corp. 8-in-1 Card Reader
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0461:4d15 Primax Electronics, Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by Forbees on 2008-09-25
> **Codename said:**
> Post the results of this command:
```
sudo fdisk -l
```

this only listed information about my hard drive
 ```

forbees@forbees-desktop:~$ sudo fdisk -l
[sudo] password for forbees: 

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1188f42c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14611   117362826    7  HPFS/NTFS
/dev/sda3           14612       24321    77995575    f  W95 Ext'd (LBA)
/dev/sda5           14612       23990    75336786   83  Linux
/dev/sda6           23991       24321     2658726   82  Linux swap / Solaris

```


> **prshah said:**
> Plug in your flash drives and printer, turn it on and wait about 10 seconds, then give the below command in the terminal (Applications-Accessories-Terminal) and post the output here:```
dmesg | tail
lsusb
```

this gave me

```

forbees@forbees-desktop:~$ dmesg | tail
[ 6361.210361] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6361.210366] sr 2:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[ 6361.210369] sr 2:0:0:0: [sr0] Add. Sense: Timeout on logical unit
[ 6361.210372] end_request: I/O error, dev sr0, sector 841024
[ 6361.210375] Buffer I/O error on device sr0, logical block 210256
[ 6372.197715] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6372.197720] sr 2:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[ 6372.197723] sr 2:0:0:0: [sr0] Add. Sense: Timeout on logical unit
[ 6372.197726] end_request: I/O error, dev sr0, sector 841216
[ 6372.197729] Buffer I/O error on device sr0, logical block 210304
forbees@forbees-desktop:~$ lsusb
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 046d:c525 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

which is giberish to me :-p but i know the logitect,inc is my mouse . . . no flashdrive detected >,<

---

### Post by lovegreat on 2008-09-25
ycq@ycq-laptop:~$ sudo fdisk -l
[sudo] password for ycq: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x257d257c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612       14593    96245415    f  W95 Ext'd (LBA)
/dev/sda5            2612        6527    31455238+   b  W95 FAT32
/dev/sda6            6528       10443    31455238+   b  W95 FAT32
/dev/sda7           10444       12738    18434556    7  HPFS/NTFS
/dev/sda8           12739       12762      192748+  82  Linux swap / Solaris
/dev/sda9           12763       13377     4939956   83  Linux
/dev/sda10          13378       14593     9767488+  83  Linux

Disk /dev/sdb: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x50fe3fc8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3648    29302528+   c  W95 FAT32 (LBA)
ycq@ycq-laptop:~$

---

### Post by lovegreat on 2008-09-25
```

forbees@forbees-desktop:~$ dmesg | tail
[ 6361.210361] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6361.210366] sr 2:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[ 6361.210369] sr 2:0:0:0: [sr0] Add. Sense: Timeout on logical unit
[ 6361.210372] end_request: I/O error, dev sr0, sector 841024
[ 6361.210375] Buffer I/O error on device sr0, logical block 210256
[ 6372.197715] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6372.197720] sr 2:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[ 6372.197723] sr 2:0:0:0: [sr0] Add. Sense: Timeout on logical unit
[ 6372.197726] end_request: I/O error, dev sr0, sector 841216
[ 6372.197729] Buffer I/O error on device sr0, logical block 210304
forbees@forbees-desktop:~$ lsusb
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 046d:c525 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

ycq@ycq-laptop:~$ sudo fdisk -l
[sudo] password for ycq: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x257d257c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612       14593    96245415    f  W95 Ext'd (LBA)
/dev/sda5            2612        6527    31455238+   b  W95 FAT32
/dev/sda6            6528       10443    31455238+   b  W95 FAT32
/dev/sda7           10444       12738    18434556    7  HPFS/NTFS
/dev/sda8           12739       12762      192748+  82  Linux swap / Solaris
/dev/sda9           12763       13377     4939956   83  Linux
/dev/sda10          13378       14593     9767488+  83  Linux

Disk /dev/sdb: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x50fe3fc8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3648    29302528+   c  W95 FAT32 (LBA)



ycq@ycq-laptop:~$ lsusb
Bus 005 Device 006: ID 0424:223a Standard Microsystems Corp. 8-in-1 Card Reader
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0461:4d15 Primax Electronics, Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


ycq@ycq-laptop:~$ dmesg | tail
[  947.084756] sd 5:0:0:1: Attached scsi generic sg3 type 0
[  947.090425] sd 5:0:0:2: [sdd] Attached SCSI removable disk
[  947.090494] sd 5:0:0:2: Attached scsi generic sg4 type 0
[  949.642610] FAT: Filesystem panic (dev sdb1)
[  949.642619]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  949.642623]     File system has been set read-only
[  948.871715] FAT: Filesystem panic (dev sdb1)
[  948.871724]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  950.719588] FAT: Filesystem panic (dev sdb1)
[  950.719593]     fat_get_cluster: invalid cluster chain (i_pos 0)



one usb is computer card reader  anther is my usb mouse ,

---

### Post by prshah on 2008-09-25
> **Forbees said:**
> ```

forbees@forbees-desktop:~$ dmesg | tail
[ 6361.210361] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6361.210366] sr 2:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[ 6361.210369] sr 2:0:0:0: [sr0] Add. Sense: Timeout on logical unit
[ 6361.210372] end_request: I/O error, dev sr0, sector 841024
[ 6361.210375] Buffer I/O error on device sr0, logical block 210256
[ 6372.197715] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 6372.197720] sr 2:0:0:0: [sr0] Sense Key : Hardware Error [current] 
[ 6372.197723] sr 2:0:0:0: [sr0] Add. Sense: Timeout on logical unit
[ 6372.197726] end_request: I/O error, dev sr0, sector 841216
[ 6372.197729] Buffer I/O error on device sr0, logical block 210304

```


/dev/sr0 is the CDROM/DVD/Optical drive. Post your /etc/fstab file for more analysis.


> **lovegreat said:**
> 
ycq@ycq-laptop:~$ dmesg | tail
[  949.642610] FAT: Filesystem panic (dev sdb1)
[  949.642619]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  949.642623]     File system has been set read-only
[  948.871715] FAT: Filesystem panic (dev sdb1)
[  948.871724]     fat_get_cluster: invalid cluster chain (i_pos 0)
[  950.719588] FAT: Filesystem panic (dev sdb1)
[  950.719593]     fat_get_cluster: invalid cluster chain (i_pos 0)


Your USB stick has some logical damage to the filesystem. It's easy to repair.

[indent]a) Plug in the usb stick, wait for device to settle
b) give the command ```
dmesg | tail
``` and see which device has been assigned to your usb stick (probably /dev/sdb1?)
c) unmount that device and run a check```
sudo umount /dev/sdb1 && sudo fsck -a /dev/sdb1
```
d) Post back error messages if any. If there are no error messages, the stick is ready for use. Simply pull it out, wait 10 seconds, and plug it back in.
e) In the future, _always unmount_ the stick before you unplug it from the computer. To unmount, right-click the icon for the stick and choose "Unmount volume"
[/indent]

WARNING: You can possibly lose some data, (but the files lost will be corrupted and unusable in any case), so you do this at your own risk.

---

### Post by lovegreat on 2008-09-26
ycq@ycq-laptop:~$ dmesg | tail
[ 1344.455215] sd 2:0:0:1: Attached scsi generic sg3 type 0
[ 1344.460418] sd 2:0:0:2: [sdd] Attached SCSI removable disk
[ 1344.460470] sd 2:0:0:2: Attached scsi generic sg4 type 0
[ 1347.059799] FAT: Filesystem panic (dev sdb1)
[ 1347.059809]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1347.059813]     File system has been set read-only
[ 1347.186901] FAT: Filesystem panic (dev sdb1)
[ 1347.186910]     fat_get_cluster: invalid cluster chain (i_pos 0)
[ 1347.187043] FAT: Filesystem panic (dev sdb1)
[ 1347.187046]     fat_get_cluster: invalid cluster chain (i_pos 0)
ycq@ycq-laptop:~$ sudo umount /dev/sdb1 && sudo fsck -a /dev/sdb1
[sudo] password for ycq: 
fsck 1.40.8 (13-Mar-2008)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:01/00
  Not automatically fixing this.
/255609
  Contains a free cluster (720898). Assuming EOF.
/Recycled/Di6/GREYS/SEASON 2/greys.0201.rmvb
  Contains a free cluster (1474050). Assuming EOF.
/Recycled/Di6/GREYS/SEASON 2/greys.0201.rmvb
  File size is 157214571 bytes, cluster chain length is 0 bytes.
  Truncating file to 0 bytes.
/Recycled/Di7.HOUSE/season 4/0409.rmvb
  Contains a free cluster (1452570). Assuming EOF.
/Recycled/Di7.HOUSE/season 4/0409.rmvb
  File size is 180849458 bytes, cluster chain length is 94322688 bytes.
  Truncating file to 94322688 bytes.
/Recycled/Di7.HOUSE/season 1/[:8ng:6Ml:5Cx:7KV].house.1x11.detox.FRM.rmvb
  Contains a free cluster (1804272). Assuming EOF.
/DY/:60d:4uE:6Nf:9aGDVD/:60d:4uE:6Nf:9aGDVD.rmvb
  File size is 0 bytes, cluster chain length is > 0 bytes.
  Truncating file to 0 bytes.


Paused the very long time from this

---

### Post by lovegreat on 2008-09-26
[IMG]http://forum.ubuntu.org.cn/download/file.php?id=44187&mode=view/Screenshot-1.png[/IMG]

the usb can open and  show free space also ,but not work.

---

### Post by prshah on 2008-09-26
> **lovegreat said:**
> ycq@ycq-laptop:~$ sudo umount /dev/sdb1 && sudo fsck -a /dev/sdb1
[sudo] password for ycq: 
fsck 1.40.8 (13-Mar-2008)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:01/00
  Not automatically fixing this.



OK Auto-fix will not work in this case. now, repeat the same command, but remove the "-a" (autofix) option, ie```
sudo umount /dev/sdb1 && sudo fsck /dev/sdb1

``` This will run a check which require manual intervention. Answer "y" to all questions. You will also be asked to "replace" boot sector with backup and vice versa. Choose replace "boot sector" with "backup".

If you don't have any essential data on this, it may be simpler to just format it using gparted, or the command```
mkfs.vfat -v /dev/sdb1
``` Warning this will erase all data on the USB stick.

---

### Post by lovegreat on 2008-09-26
ycq@ycq-laptop:~$ sudo umount /dev/sdb1 &&sudo fsck /dev/sdb1
[sudo] password for ycq: 
Sorry, try again.
[sudo] password for ycq: 
fsck 1.40.8 (13-Mar-2008)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:01/00
1) Copy original to backup
2) Copy backup to original
3) No action
? y
Invalid input.
? 1
/:5uu:7Ke:8zl:4xs
  Bad file name.
1) Drop file
2) Rename file
3) Auto-rename
4) Keep it

---

### Post by Forbees on 2008-09-26
> **prshah said:**
> /dev/sr0 is the CDROM/DVD/Optical drive. Post your /etc/fstab file for more analysis.


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=63d73897-55dd-498f-a9ff-30b296f3ee57 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=18239db6-75fc-49d0-a769-694d91d64f0f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```


i did this with my usb plugged in . .  and i notice /media/floppy0 . . . . . i have NO floppy drive on this computer >,< 
 
so whats that mean?

---

### Post by lovegreat on 2008-09-26
it si mine
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb9
UUID=208e780d-cbcc-4903-a5db-de4f1aee1ef1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/hdb10
UUID=3ed81623-b277-4e47-bd2c-c6085fa2787c /home           ext3    relatime        0       2
# /dev/hdb8
UUID=438882ff-ac29-4334-bb1f-930a60c03afb none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
maybe you can delete it ,

---

### Post by lovegreat on 2008-09-26
> **prshah said:**
> OK Auto-fix will not work in this case. now, repeat the same command, but remove the "-a" (autofix) option, ie```
sudo umount /dev/sdb1 && sudo fsck /dev/sdb1

``` This will run a check which require manual intervention. Answer "y" to all questions. You will also be asked to "replace" boot sector with backup and vice versa. Choose replace "boot sector" with "backup".

If you don't have any essential data on this, it may be simpler to just format it using gparted, or the command```
mkfs.vfat -v /dev/sdb1
``` Warning this will erase all data on the USB stick.

thank you very much.i have mkfs it ,then it works.

a)but i  don't know why it can works in windows system and can't at linux.
b)why auto-fix don't work?

---

### Post by lovegreat on 2008-09-26
> **prshah said:**
> OK Auto-fix will not work in this case. now, repeat the same command, but remove the "-a" (autofix) option, ie```
sudo umount /dev/sdb1 && sudo fsck /dev/sdb1

``` This will run a check which require manual intervention. Answer "y" to all questions. You will also be asked to "replace" boot sector with backup and vice versa. Choose replace "boot sector" with "backup".

If you don't have any essential data on this, it may be simpler to just format it using gparted, or the command```
mkfs.vfat -v /dev/sdb1
``` Warning this will erase all data on the USB stick.

thank you very mucu.i mkfs the usb stick ,it works well.

but i don't know
a)why it works in windosw system ,but it can't work in linux?
b)why  autofix can't work ?

i have another problem ,i installed "smaba" ,but i can't open every computer shared in "workgroup"? if i input the computer ip in address,it can open,but i don't know everyone,please help me,thanks

---

### Post by Forbees on 2008-09-27
> **lovegreat said:**
> maybe you can delete it ,

i guess i could try . . . but idk if it would do anything . . . it seems that it thinks my flashdrive is a floppy . . . so if i delete it, i asume it would just come back as soon as i plug my drive back in

---

### Post by lovegreat on 2008-09-27
you may be need "mkfs" your flash,then try again ,

---

### Post by Forbees on 2008-09-27
> **lovegreat said:**
> you may be need "mkfs" your flash,then try again ,

```
forbees@forbees-desktop:~$ mkfs.vfat -v /dev/fd0
mkfs.vfat 2.11 (12 Mar 2005)
mkfs.vfat: unable to open /dev/fd0

```

/dev/fd0 is my flashdrive . . . but fd is meant for floppies . . .  i need to figure out how to tell my computer that my flashdrive isn't a floppy >,<

---

### Post by lovegreat on 2008-09-27
> **Forbees said:**
> ```
forbees@forbees-desktop:~$ mkfs.vfat -v /dev/fd0
mkfs.vfat 2.11 (12 Mar 2005)
mkfs.vfat: unable to open /dev/fd0

```

/dev/fd0 is my flashdrive . . . but fd is meant for floppies . . .  i need to figure out how to tell my computer that my flashdrive isn't a floppy >,<

it  need "root"user

---

### Post by Forbees on 2008-09-28
> **lovegreat said:**
> it  need "root"user

```
forbees@forbees-desktop:~$ sudo mkfs.vfat -v /dev/fd0
[sudo] password for forbees: 
mkfs.vfat 2.11 (12 Mar 2005)
mkfs.vfat: unable to open /dev/fd0

```

---

