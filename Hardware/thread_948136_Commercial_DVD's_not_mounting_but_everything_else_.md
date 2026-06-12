---
title: "Commercial DVD's not mounting but everything else does. Video to prove it."
date: 2008-10-14
forum: Hardware
---

### Post by encompass on 2008-10-14
I will tell you right now, this in not a matter of encrypted dvd's at least in the sense that I have all the software and tools to run encrypted dvd's.
Here's my tests:
[LIST]
[*]I can play dvds with movies on them that I have burned. (No region code etc...)
[*]I can mount/open/burn cd/dvds just fine.
[*]The computer does a funny set of noises when it tries to open the dvd it's as if it is a bad dvd.
[*]This happens ONLY to the commercial dvds.
[*]Could it some how be broken?
[*]I played a dvd not 3 weeks ago just fine with no issues at all.
[*]I use my drives all the time.  It just won't mount the dvd's I have purchased.
[*]I have tried the system on a cold boot too.
[*]This is a SATA dvd burner. On an asus a7f.
[*]I do not use windows.
[/LIST]
To help out, I have a video of it not working here...
[http://memaker.org/vids/](http://memaker.org/vids/)(Vid is uploading now.  It's just over 20.1mb.
Any ideas?
Best Regards,
Jason Brower
Lastly my dmesg:
```

[   31.313749] sd 0:0:0:0: [sda] Attached SCSI disk
[   31.319830] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   31.319851] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   31.540976] sr0: scsi3-mmc drive: 47x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   31.540982] Uniform CD-ROM driver Revision: 3.20
[   31.541032] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   31.729929] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0180003722376]
[   68.614389] Attempting manual resume
[   68.614393] swsusp: Resume From Partition 8:2
[   68.614395] PM: Checking swsusp image.
[   68.614670] PM: Resume from disk failed.
[   68.622911] ReiserFS: sda1: found reiserfs format "3.6" with standard journal
[   68.622924] ReiserFS: sda1: using ordered data mode
[   68.976550] ReiserFS: sda1: journal params: device sda1, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
[   68.976876] ReiserFS: sda1: checking transaction log (sda1)
[   69.054288] ReiserFS: sda1: Using r5 hash to sort names
[   79.781974] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   80.883147] iTCO_vendor_support: vendor-support=0
[   80.923564] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   80.923655] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x0860)
[   80.923689] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   81.122768] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   81.174708] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   81.246548] Linux agpgart interface v0.102
[   81.394304] intel_rng: FWH not detected
[   81.490201] agpgart: Detected an Intel 945GM Chipset.
[   81.490492] agpgart: Detected 7932K stolen memory.
[   81.526126] agpgart: AGP aperture is 256M @ 0xd0000000
[   81.634343] input: Power Button (FF) as /devices/virtual/input/input3
[   81.665893] ACPI: Power Button (FF) [PWRF]
[   81.665989] input: Power Button (CM) as /devices/virtual/input/input4
[   81.693851] ACPI: Power Button (CM) [PWRB]
[   81.693918] input: Sleep Button (CM) as /devices/virtual/input/input5
[   81.725805] ACPI: Sleep Button (CM) [SLPB]
[   81.725876] input: Lid Switch as /devices/virtual/input/input6
[   81.744842] ACPI: Lid Switch [LID]
[   81.864550] asus-laptop: Asus Laptop Support version 0.42
[   81.864806] asus-laptop:   A7F model detected
[   81.866338] Registered led device: asus:phone
[   82.224976] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   82.224980] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   82.225151] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   82.225166] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   82.225191] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   82.541306] ricoh-mmc: Ricoh MMC Controller disabling driver
[   82.541310] ricoh-mmc: Copyright(c) Philip Langdale
[   82.606954] sdhci: Secure Digital Host Controller Interface driver
[   82.606958] sdhci: Copyright(c) Pierre Ossman
[   83.283535] ACPI: AC Adapter [AC0] (on-line)
[   83.480185] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input7
[   83.506943] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   83.534630] ACPI: Battery Slot [BAT0] (battery present)
[   83.719501] Synaptics Touchpad, model: 1, fw: 6.1, id: 0xa3a0b3, caps: 0xa04713/0x10008
[   83.759569] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   84.329592] Linux video capture interface: v2.00
[   84.373494] stk11xx: Syntek USB2.0 webcam driver startup
[   84.373541] stk11xx: Syntek USB2.0 - STK-1135 based webcam found.
[   84.373543] stk11xx: Syntek AVStream USB2.0 1.3M WebCam - Product ID 0xA311.
[   84.373546] stk11xx: Release: 0005
[   84.373547] stk11xx: Number of interfaces : 1
[   84.373971] stk11xx: Initialize USB2.0 Syntek Camera
[   84.582792] stk11xx: Syntek USB2.0 Camera is ready
[   84.582836] stk11xx: Syntek USB2.0 Camera is now controlling video device /dev/video0
[   84.582861] usbcore: registered new interface driver usb_stk11xx_driver
[   84.582864] stk11xx: v1.3.1 : Syntek USB Video Camera
[   85.503782] ricoh-mmc: Ricoh MMC controller found at 0000:06:01.2 [1180:0843] (rev 1)
[   85.503796] ricoh-mmc: Controller is now disabled.
[   85.504124] sdhci: SDHCI controller found at 0000:06:01.1 [1180:0822] (rev 19)
[   85.504151] ACPI: PCI Interrupt 0000:06:01.1[B] -> GSI 17 (level, low) -> IRQ 17
[   85.504170] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   85.504222] mmc0: SDHCI at 0xfe8ff400 irq 17 DMA
[   85.507726] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   85.507743] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   85.541502] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   85.563442] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels
[   85.568615] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   85.905390] lp: driver loaded but no devices found
[   86.081337] Adding 1172736k swap on /dev/sda2.  Priority:-1 extents:1 across:1172736k
[   94.746063] kjournald starting.  Commit interval 5 seconds
[   94.746462] EXT3 FS on sda3, internal journal
[   94.746466] EXT3-fs: mounted filesystem with ordered data mode.
[   95.340350] ip_tables: (C) 2000-2006 Netfilter Core Team
[   95.794014] No dock devices found.
[   97.295581] NET: Registered protocol family 10
[   97.295989] lo: Disabled Privacy Extensions
[   99.615222] apm: BIOS not found.
[   99.992259] ppdev: user-space parallel port driver
[  100.439368] audit(1224030734.693:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5194 profile="/usr/sbin/cupsd" namespace="default"
[  103.544704] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  103.564721] r8169: eth0: link down
[  103.566198] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  103.662370] Bluetooth: Core ver 2.11
[  103.662920] NET: Registered protocol family 31
[  103.662924] Bluetooth: HCI device and connection manager initialized
[  103.662928] Bluetooth: HCI socket layer initialized
[  103.712966] Bluetooth: L2CAP ver 2.9
[  103.712971] Bluetooth: L2CAP socket layer initialized
[  103.846150] Bluetooth: RFCOMM socket layer initialized
[  103.846164] Bluetooth: RFCOMM TTY layer initialized
[  103.846166] Bluetooth: RFCOMM ver 1.8
[  107.149995] [drm] Initialized drm 1.1.0 20060810
[  107.185787] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[  107.185796] PCI: Setting latency timer of device 0000:00:02.0 to 64
[  107.185872] [drm] Initialized i915 1.6.0 20060119 on minor 0
[  151.916385] NET: Registered protocol family 17
[  155.014728] wlan0: Initial auth_alg=0
[  155.014734] wlan0: authenticate with AP 00:17:3f:bd:1b:7a
[  155.017082] wlan0: RX authentication from 00:17:3f:bd:1b:7a (alg=0 transaction=2 status=0)
[  155.017086] wlan0: authenticated
[  155.017088] wlan0: associate with AP 00:17:3f:bd:1b:7a
[  155.036033] wlan0: RX AssocResp from 00:17:3f:bd:1b:7a (capab=0x411 status=0 aid=2)
[  155.036038] wlan0: associated
[  155.037431] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  169.624694] wlan0: no IPv6 routers present
[  456.852852] Clocksource tsc unstable (delta = -25716765285 ns)
[  456.856836] Time: hpet clocksource has been installed.
[  459.441065] cdrom: sr0: mrw address space DMA selected
[  459.441660] cdrom open: mrw_status 'bgformat inactive'
[  459.441664] cdrom: Restarting format
[  459.442403] cdrom: bgformat failed
[  459.560141] cdrom: sr0: mrw address space DMA selected
[  459.560719] cdrom open: mrw_status 'bgformat inactive'
[  459.560723] cdrom: Restarting format
[  459.561454] cdrom: bgformat failed
[  459.765732] UDF-fs: Partition marked readonly; forcing readonly mount
[  459.794427] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'DVD Video Recording', timestamp 2005/12/31 10:00 (1ed4)
[ 1366.536204] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 1366.536218] ata2.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 8 in
[ 1366.536219]          cdb 25 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 1366.536221]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 1366.536224] ata2.00: status: { DRDY }
[ 1371.531677] ata2: port is slow to respond, please be patient (Status 0xd0)
[ 1376.575315] ata2: device not ready (errno=-16), forcing hardreset
[ 1376.575323] ata2: soft resetting link
[ 1377.099187] ata2.00: configured for UDMA/33
[ 1377.099205] ata2: EH complete
[ 1439.374562] ata2.00: qc timeout (cmd 0xa0)
[ 1439.374579] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 1439.374589] ata2.00: cmd a0/00:00:00:0c:00/00:00:00:00:00/a0 tag 0 pio 12 in
[ 1439.374590]          cdb 43 00 00 00 00 00 00 00  0c 00 00 00 00 00 00 00
[ 1439.374592]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[ 1439.374595] ata2.00: status: { DRDY ERR }
[ 1444.418114] ata2: port is slow to respond, please be patient (Status 0xd1)
[ 1449.413784] ata2: device not ready (errno=-16), forcing hardreset
[ 1449.413792] ata2: soft resetting link
[ 1449.937336] ata2.00: configured for UDMA/33
[ 1449.937366] ata2: EH complete
[ 1817.775416] ata2.00: qc timeout (cmd 0xa0)
[ 1817.775433] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 1817.775443] ata2.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 8 in
[ 1817.775444]          cdb 25 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 1817.775446]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[ 1817.775449] ata2.00: status: { DRDY ERR }
[ 1822.822976] ata2: port is slow to respond, please be patient (Status 0xd0)
[ 1827.810656] ata2: device not ready (errno=-16), forcing hardreset
[ 1827.810662] ata2: soft resetting link
[ 1828.334204] ata2.00: configured for UDMA/33
[ 1828.334231] ata2: EH complete
[ 2034.430064] ata2.00: qc timeout (cmd 0xa0)
[ 2034.430081] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 2034.430090] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 2034.430092]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 2034.430093]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[ 2034.430096] ata2.00: status: { DRDY ERR }
[ 2039.474628] ata2: port is slow to respond, please be patient (Status 0xd0)
[ 2044.469297] ata2: device not ready (errno=-16), forcing hardreset
[ 2044.469304] ata2: soft resetting link
[ 2044.992852] ata2.00: configured for UDMA/33
[ 2044.992882] ata2: EH complete
[ 2259.015485] ata2.00: qc timeout (cmd 0xa0)
[ 2259.015501] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 2259.015511] ata2.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 8 in
[ 2259.015512]          cdb 25 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 2259.015513]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[ 2259.015517] ata2.00: status: { DRDY ERR }
[ 2264.047242] ata2: port is slow to respond, please be patient (Status 0xd1)
[ 2269.022769] ata2: device not ready (errno=-16), forcing hardreset
[ 2269.022777] ata2: soft resetting link
[ 2269.554308] ata2.00: configured for UDMA/33
[ 2269.554339] ata2: EH complete
[ 2535.578213] ata2.00: qc timeout (cmd 0xa0)
[ 2535.578231] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 2535.578241] ata2.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 8 in
[ 2535.578242]          cdb 25 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 2535.578243]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[ 2535.578247] ata2.00: status: { DRDY ERR }
[ 2540.617785] ata2: port is slow to respond, please be patient (Status 0xd0)
[ 2545.613460] ata2: device not ready (errno=-16), forcing hardreset
[ 2545.613467] ata2: soft resetting link
[ 2546.136997] ata2.00: configured for UDMA/33
[ 2546.137028] ata2: EH complete
[ 2640.375555] ata2.00: qc timeout (cmd 0xa0)
[ 2640.375572] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 2640.375581] ata2.00: cmd a0/00:00:00:0c:00/00:00:00:00:00/a0 tag 0 pio 12 in
[ 2640.375583]          cdb 43 00 00 00 00 00 00 00  0c 00 00 00 00 00 00 00
[ 2640.375584]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[ 2640.375588] ata2.00: status: { DRDY ERR }
[ 2645.407053] ata2: port is slow to respond, please be patient (Status 0xd1)
[ 2650.382711] ata2: device not ready (errno=-16), forcing hardreset
[ 2650.382718] ata2: soft resetting link
[ 2650.922243] ata2.00: configured for UDMA/33
[ 2650.922273] ata2: EH complete
[ 2775.174709] ata2.00: qc timeout (cmd 0xa0)
[ 2775.174727] ata2.00: limiting speed to UDMA/25:PIO4
[ 2775.174731] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 2775.174741] ata2.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 8 in
[ 2775.174742]          cdb 25 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 2775.174744]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[ 2775.174747] ata2.00: status: { DRDY ERR }
[ 2780.206183] ata2: port is slow to respond, please be patient (Status 0xd0)
[ 2785.181875] ata2: device not ready (errno=-16), forcing hardreset
[ 2785.181883] ata2: soft resetting link
[ 2785.705443] ata2.00: configured for UDMA/25
[ 2785.705473] ata2: EH complete
[ 3141.511588] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 3141.511602] ata2.00: cmd a0/00:00:00:0c:00/00:00:00:00:00/a0 tag 0 pio 12 in
[ 3141.511603]          cdb 43 00 00 00 00 00 00 00  0c 40 00 00 00 00 00 00
[ 3141.511605]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 3141.511608] ata2.00: status: { DRDY }
[ 3146.543169] ata2: port is slow to respond, please be patient (Status 0xd0)
[ 3151.518871] ata2: device not ready (errno=-16), forcing hardreset
[ 3151.518878] ata2: soft resetting link
[ 3152.042417] ata2.00: configured for UDMA/25
[ 3152.042434] ata2: EH complete
[ 3300.310850] ata2.00: qc timeout (cmd 0xa0)
[ 3300.310866] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 3300.310875] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 3300.310876]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 3300.310878]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[ 3300.310881] ata2.00: status: { DRDY ERR }
[ 3305.306373] ata2: port is slow to respond, please be patient (Status 0xd1)
[ 3310.341977] ata2: device not ready (errno=-16), forcing hardreset
[ 3310.341983] ata2: soft resetting link
[ 3310.869507] ata2.00: configured for UDMA/25
[ 3310.869537] ata2: EH complete
[ 3379.195157] ata2.00: qc timeout (cmd 0xa0)
[ 3379.195174] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 3379.195183] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 3379.195184]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 3379.195186]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[ 3379.195189] ata2.00: status: { DRDY ERR }
[ 3384.190808] ata2: port is slow to respond, please be patient (Status 0xd1)
[ 3389.186473] ata2: device not ready (errno=-16), forcing hardreset
[ 3389.186479] ata2: soft resetting link
[ 3389.718149] ata2.00: configured for UDMA/25
[ 3389.718178] ata2: EH complete
[ 3481.967743] ata2.00: qc timeout (cmd 0xa0)
[ 3481.967761] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 3481.967770] ata2.00: cmd a0/00:00:00:0c:00/00:00:00:00:00/a0 tag 0 pio 12 in
[ 3481.967772]          cdb 43 00 00 00 00 00 00 00  0c 00 00 00 00 00 00 00
[ 3481.967773]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[ 3481.967777] ata2.00: status: { DRDY ERR }
[ 3486.999330] ata2: port is slow to respond, please be patient (Status 0xd1)
[ 3491.975144] ata2: device not ready (errno=-16), forcing hardreset
[ 3491.975151] ata2: soft resetting link
[ 3492.506614] ata2.00: configured for UDMA/25
[ 3492.506643] ata2: EH complete
[ 3560.844318] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 3560.844331] ata2.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 8 in
[ 3560.844333]          cdb 25 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 3560.844334]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 3560.844338] ata2.00: status: { DRDY }
[ 3565.839835] ata2: port is slow to respond, please be patient (Status 0xd0)
[ 3570.835503] ata2: device not ready (errno=-16), forcing hardreset
[ 3570.835510] ata2: soft resetting link
[ 3571.367042] ata2.00: configured for UDMA/25
[ 3571.367061] ata2: EH complete
[ 3937.232419] ata2.00: qc timeout (cmd 0xa0)
[ 3937.232436] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 3937.232446] ata2.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 8 in
[ 3937.232447]          cdb 25 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 3937.232449]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[ 3937.232452] ata2.00: status: { DRDY ERR }
[ 3942.271993] ata2: port is slow to respond, please be patient (Status 0xd1)
[ 3947.267657] ata2: device not ready (errno=-16), forcing hardreset
[ 3947.267664] ata2: soft resetting link
[ 3947.791203] ata2.00: configured for UDMA/25
[ 3947.791232] ata2: EH complete
[ 4032.050272] ata2.00: qc timeout (cmd 0xa0)
[ 4032.050288] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 4032.050298] ata2.00: cmd a0/00:00:00:0c:00/00:00:00:00:00/a0 tag 0 pio 12 in
[ 4032.050300]          cdb 43 00 00 00 00 00 00 00  0c 00 00 00 00 00 00 00
[ 4032.050301]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[ 4032.050304] ata2.00: status: { DRDY ERR }
[ 4037.081859] ata2: port is slow to respond, please be patient (Status 0xd1)
[ 4042.077530] ata2: device not ready (errno=-16), forcing hardreset
[ 4042.077537] ata2: soft resetting link
[ 4042.605066] ata2.00: configured for UDMA/25
[ 4042.605095] ata2: EH complete
[ 4134.918701] ata2.00: qc timeout (cmd 0xa0)
[ 4134.918718] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 4134.918727] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 4134.918728]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 4134.918730]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[ 4134.918733] ata2.00: status: { DRDY ERR }
[ 4139.950289] ata2: port is slow to respond, please be patient (Status 0xd1)
[ 4144.925991] ata2: device not ready (errno=-16), forcing hardreset
[ 4144.925998] ata2: soft resetting link
[ 4145.457518] ata2.00: configured for UDMA/25
[ 4145.457547] ata2: EH complete
[ 4175.483044] ata2.00: qc timeout (cmd 0xa0)
[ 4175.483061] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 4175.483072] ata2.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 8 in
[ 4175.483073]          cdb 25 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 4175.483074]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[ 4175.483078] ata2.00: status: { DRDY ERR }
[ 4180.514628] ata2: port is slow to respond, please be patient (Status 0xd1)
[ 4185.502310] ata2: device not ready (errno=-16), forcing hardreset
[ 4185.502317] ata2: soft resetting link
[ 4186.025856] ata2.00: configured for UDMA/25
[ 4186.025885] ata2: EH complete
[ 4236.748859] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 4236.748873] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 4236.748874]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 4236.748875]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 4236.748879] ata2.00: status: { DRDY }
[ 4241.780445] ata2: port is slow to respond, please be patient (Status 0xd0)
[ 4246.760140] ata2: device not ready (errno=-16), forcing hardreset
[ 4246.760147] ata2: soft resetting link
[ 4247.291717] ata2.00: configured for UDMA/25
[ 4247.291736] ata2: EH complete
[ 4311.615991] ata2.00: qc timeout (cmd 0xa0)
[ 4311.616008] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 4311.616018] ata2.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 8 in
[ 4311.616020]          cdb 25 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 4311.616021]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[ 4311.616024] ata2.00: status: { DRDY ERR }
[ 4316.647581] ata2: port is slow to respond, please be patient (Status 0xd0)
[ 4321.631269] ata2: device not ready (errno=-16), forcing hardreset
[ 4321.631276] ata2: soft resetting link
[ 4322.170786] ata2.00: configured for UDMA/25
[ 4322.170815] ata2: EH complete
[ 4370.525736] ata2.00: qc timeout (cmd 0xa0)
[ 4370.525753] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 4370.525763] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 4370.525764]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 4370.525766]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[ 4370.525769] ata2.00: status: { DRDY ERR }
[ 4375.569305] ata2: port is slow to respond, please be patient (Status 0xd0)
[ 4380.564974] ata2: device not ready (errno=-16), forcing hardreset
[ 4380.564981] ata2: soft resetting link
[ 4381.088548] ata2.00: configured for UDMA/25
[ 4381.088577] ata2: EH complete
[ 4421.456791] ata2.00: qc timeout (cmd 0xa0)
[ 4421.456808] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 4421.456817] ata2.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 4421.456819]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 4421.456820]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[ 4421.456823] ata2.00: status: { DRDY ERR }
[ 4426.500362] ata2: port is slow to respond, please be patient (Status 0xd0)
[ 4431.496026] ata2: device not ready (errno=-16), forcing hardreset
[ 4431.496034] ata2: soft resetting link
[ 4432.019567] ata2.00: configured for UDMA/25
[ 4432.019596] ata2: EH complete
[ 4681.996095] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[ 4761.019112] cdrom: sr0: mrw address space DMA selected
[ 4761.019804] cdrom open: mrw_status 'bgformat inactive'
[ 4761.019809] cdrom: Restarting format
[ 4761.020548] cdrom: bgformat failed
[ 4761.051219] cdrom: sr0: mrw address space DMA selected
[ 4761.051713] cdrom open: mrw_status 'bgformat inactive'
[ 4761.051716] cdrom: Restarting format
[ 4761.052391] cdrom: bgformat failed
[ 4761.270129] UDF-fs: Partition marked readonly; forcing readonly mount
[ 4761.299731] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'DVD Video Recording', timestamp 2005/12/31 10:00 (1ed4)
[ 4833.849110] usb 5-2: new high speed USB device using ehci_hcd and address 3
[ 4833.983176] usb 5-2: configuration #1 chosen from 1 choice
[ 4834.402527] usbcore: registered new interface driver libusual
[ 4834.462205] Initializing USB Mass Storage driver...
[ 4834.463489] scsi2 : SCSI emulation for USB Mass Storage devices
[ 4834.466202] usbcore: registered new interface driver usb-storage
[ 4834.466210] USB Mass Storage support registered.
[ 4834.466602] usb-storage: device found at 3
[ 4834.466605] usb-storage: waiting for device to settle before scanning
[ 4837.702681] usb 3-1: new full speed USB device using uhci_hcd and address 2
[ 4837.895512] usb 3-1: configuration #1 chosen from 1 choice
[ 4838.056609] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found.(ZC3XX) 
[ 4838.694189] usbcore: registered new interface driver gspca
[ 4838.694403] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.20 registered
[ 4838.789858] zc0301: V4L2 driver for ZC0301[P] Image Processor and Control Chip v1:1.10
[ 4838.789895] usbcore: registered new interface driver zc0301
[ 4839.455920] usb-storage: device scan complete
[ 4839.457290] scsi 2:0:0:0: Direct-Access     Generic  IC1210        CF 1.9C PQ: 0 ANSI: 0 CCS
[ 4839.458529] scsi 2:0:0:1: Direct-Access     Generic  IC1210        MS 1.9C PQ: 0 ANSI: 0 CCS
[ 4839.729733] scsi 2:0:0:2: Direct-Access     Generic  IC1210    MMC/SD 1.9C PQ: 0 ANSI: 0 CCS
[ 4839.731091] scsi 2:0:0:3: Direct-Access     Generic  IC1210        XD 1.9C PQ: 0 ANSI: 0 CCS
[ 4839.743490] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 4839.743530] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 4839.744633] sd 2:0:0:1: [sdc] Attached SCSI removable disk
[ 4839.744668] sd 2:0:0:1: Attached scsi generic sg3 type 0
[ 4839.745966] sd 2:0:0:2: [sdd] Attached SCSI removable disk
[ 4839.746004] sd 2:0:0:2: Attached scsi generic sg4 type 0
[ 4839.748302] sd 2:0:0:3: [sde] 2048000 512-byte hardware sectors (1049 MB)
[ 4839.749801] sd 2:0:0:3: [sde] Write Protect is off
[ 4839.749806] sd 2:0:0:3: [sde] Mode Sense: 4b 00 00 08
[ 4839.749809] sd 2:0:0:3: [sde] Assuming drive cache: write through
[ 4839.752663] sd 2:0:0:3: [sde] 2048000 512-byte hardware sectors (1049 MB)
[ 4839.754035] sd 2:0:0:3: [sde] Write Protect is off
[ 4839.754039] sd 2:0:0:3: [sde] Mode Sense: 4b 00 00 08
[ 4839.754041] sd 2:0:0:3: [sde] Assuming drive cache: write through
[ 4839.754046]  sde: sde1
[ 4839.983393] sd 2:0:0:3: [sde] Attached SCSI removable disk
[ 4839.983435] sd 2:0:0:3: Attached scsi generic sg5 type 0
[ 4847.773376] usb 4-2: new low speed USB device using uhci_hcd and address 2
[ 4847.954752] usb 4-2: configuration #1 chosen from 1 choice
[ 4848.166868] usbcore: registered new interface driver hiddev
[ 4848.185680] input: Logitech Trackball as /devices/pci0000:00/0000:00:1d.3/usb4/4-2/4-2:1.0/input/input9
[ 4848.213312] input,hidraw0: USB HID v1.10 Mouse [Logitech Trackball] on usb-0000:00:1d.3-2
[ 4848.213333] usbcore: registered new interface driver usbhid
[ 4848.213336] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[ 6045.556146] ata2.00: qc timeout (cmd 0xa0)
[ 6045.556162] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 6045.556172] ata2.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 8 in
[ 6045.556174]          cdb 25 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 6045.556175]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[ 6045.556178] ata2.00: status: { DRDY ERR }
[ 6050.591954] ata2: port is slow to respond, please be patient (Status 0xd1)
[ 6055.571418] ata2: device not ready (errno=-16), forcing hardreset
[ 6055.571425] ata2: soft resetting link
[ 6056.094973] ata2.00: configured for UDMA/25
[ 6056.095001] ata2: EH complete
[ 6088.500517] ata2.00: qc timeout (cmd 0xa0)
[ 6088.500533] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 6088.500543] ata2.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 8 in
[ 6088.500544]          cdb 25 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 6088.500546]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[ 6088.500549] ata2.00: status: { DRDY ERR }
[ 6093.532799] ata2: port is slow to respond, please be patient (Status 0xd0)
[ 6098.519798] ata2: device not ready (errno=-16), forcing hardreset
[ 6098.519804] ata2: soft resetting link
[ 6099.043346] ata2.00: configured for UDMA/25
[ 6099.043374] ata2: EH complete
[ 6546.720378] ata2.00: qc timeout (cmd 0xa0)
[ 6546.720394] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 6546.720404] ata2.00: cmd a0/00:00:00:0c:00/00:00:00:00:00/a0 tag 0 pio 12 in
[ 6546.720405]          cdb 43 00 00 00 00 00 00 00  0c 00 00 00 00 00 00 00
[ 6546.720407]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[ 6546.720410] ata2.00: status: { DRDY ERR }
[ 6551.755858] ata2: port is slow to respond, please be patient (Status 0xd0)
[ 6556.731547] ata2: device not ready (errno=-16), forcing hardreset
[ 6556.731554] ata2: soft resetting link
[ 6557.255090] ata2.00: configured for UDMA/25
[ 6557.255118] ata2: EH complete
[ 6998.973960] ata2.00: qc timeout (cmd 0xa0)
[ 6998.973976] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 6998.973986] ata2.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 8 in
[ 6998.973988]          cdb 25 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 6998.973989]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[ 6998.973992] ata2.00: status: { DRDY ERR }
[ 7004.005542] ata2: port is slow to respond, please be patient (Status 0xd1)
[ 7008.981269] ata2: device not ready (errno=-16), forcing hardreset
[ 7008.981275] ata2: soft resetting link
[ 7009.512781] ata2.00: configured for UDMA/25
[ 7009.512810] ata2: EH complete
[ 7209.572912] sd 2:0:0:3: [sde] 2048000 512-byte hardware sectors (1049 MB)
[ 7209.574284] sd 2:0:0:3: [sde] Write Protect is off
[ 7209.574288] sd 2:0:0:3: [sde] Mode Sense: 4b 00 00 08
[ 7209.574290] sd 2:0:0:3: [sde] Assuming drive cache: write through
[ 7209.575653] sd 2:0:0:3: [sde] 2048000 512-byte hardware sectors (1049 MB)
[ 7209.576979] sd 2:0:0:3: [sde] Write Protect is off
[ 7209.576983] sd 2:0:0:3: [sde] Mode Sense: 4b 00 00 08
[ 7209.576985] sd 2:0:0:3: [sde] Assuming drive cache: write through
[ 7209.576988]  sde: sde1
[ 7376.336692] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 7376.336706] ata2.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 8 in
[ 7376.336707]          cdb 25 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 7376.336709]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 7376.336712] ata2.00: status: { DRDY }
[ 7381.380243] ata2: port is slow to respond, please be patient (Status 0xd0)
[ 7386.356775] ata2: device not ready (errno=-16), forcing hardreset
[ 7386.356782] ata2: soft resetting link
[ 7386.879387] ata2.00: configured for UDMA/25
[ 7386.879407] ata2: EH complete
[ 7427.267932] ata2.00: qc timeout (cmd 0xa0)
[ 7427.267952] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 7427.267962] ata2.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 8 in
[ 7427.267963]          cdb 25 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 7427.267965]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[ 7427.267968] ata2.00: status: { DRDY ERR }
[ 7432.311184] ata2: port is slow to respond, please be patient (Status 0xd1)
[ 7437.302856] ata2: device not ready (errno=-16), forcing hardreset
[ 7437.302863] ata2: soft resetting link
[ 7437.834408] ata2.00: configured for UDMA/25
[ 7437.834440] ata2: EH complete
[ 7793.652528] ata2.00: qc timeout (cmd 0xa0)
[ 7793.652544] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 7793.652554] ata2.00: cmd a0/00:00:00:08:00/00:00:00:00:00/a0 tag 0 pio 8 in
[ 7793.652555]          cdb 25 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 7793.652557]          res 51/20:03:00:00:00/00:00:00:00:00/a0 Emask 0x5 (timeout)
[ 7793.652560] ata2.00: status: { DRDY ERR }
[ 7798.696088] ata2: port is slow to respond, please be patient (Status 0xd1)
[ 7803.687767] ata2: device not ready (errno=-16), forcing hardreset
[ 7803.687774] ata2: soft resetting link
[ 7804.212217] ata2.00: configured for UDMA/25
[ 7804.212245] ata2: EH complete

```

---

### Post by cariboo on 2008-10-15
Could you start your preferred video player in a terminal and post the output. It looks like a bad dvd drive, maybe the output in a terminal will show a different error.

Jim

---

### Post by encompass on 2008-10-15
> **cariboo907 said:**
> Could you start your preferred video player in a terminal and post the output. It looks like a bad dvd drive, maybe the output in a terminal will show a different error.

Jim

It seems that my player totem-xine doesn't show anything, and if I try to running it, with:
```
totem-xine /dev/cdrom
```
it tells me I don't have a disc in the drive.
And the crazy part is all my ordinary CD's and DVD's work just fine.  Just the commercial DVD's don't work.

---

### Post by encompass on 2008-12-05
It seems the issue has resolved itself.  I think it was a hardware issue because it started working after giving it a little flick with my finger.  Wether dust or what, I don't know.  But I don't think it was linux after all this effort.
Thanks to everyone anyway.
Regards,
Jason

---

