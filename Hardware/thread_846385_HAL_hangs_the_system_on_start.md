---
title: "HAL hangs the system on start"
date: 2008-07-01
forum: Hardware
---

### Post by RazZziel on 2008-07-01
After upgrading my ubuntu from 6.10 to 8.04 and switching from Gnome to KDE (so now it's actually a kubuntu) the system seemed to keep working ok.
I switched the hard drive containing the ubuntu partitions to another, newer computer, and everything seemed to keep working. This computer had an ati card, so I installed the restricted drivers and configured xorg.conf with "aticonfig --initial -f". Everything working.

However, a few days ago, after no major changes in the configuration or updates, the system started to hang on boot, when starting the X system.

I rebooted in recovery mode, went to a shell, and started dbus and hal manually. When starting hal, the system hangs and doesn't reply to the keyboard.

Right now, if I try to apt-get install --reinstall dbus and hal, both daemons are started without problems, and I can start kdm. Everything works without problems. I just tried to just /etc/init.d/dbus and hal, and it worked, but it uses to hang in that situation. Starting with the default kernel, not in recovery mode, still hangs when starting the X system.

uname -a
```

Linux rosana-desktop 2.6.24-19-386 #1 Wed Jun 18 14:09:56 UTC 2008 i686 GNU/Linux

```

lspci
```

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:08.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
05:00.0 VGA compatible controller: ATI Technologies Inc RV380 0x3e50 [Radeon X600]
05:00.1 Display controller: ATI Technologies Inc RV380 [Radeon X600] (Secondary)

```

last lines of dmesg
```

[   27.757587] ACPI: PCI interrupt for device 0000:00:07.0 disabled
[   27.757921] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23
[   27.757979] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 23 (level, low) -> IRQ 16
[   27.758101] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   27.758107] ACPI: PCI interrupt for device 0000:00:08.0 disabled
[   27.760795] pata_amd 0000:00:06.0: version 0.3.10
[   27.760842] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   27.768747] scsi0 : pata_amd
[   27.769832] scsi1 : pata_amd
[   27.770425] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   27.770468] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   27.954697] ata1.01: ATA-5: WDC WD200EB-11BHF0, 15.15M15, max UDMA/100
[   27.954744] ata1.01: 39102336 sectors, multi 16: LBA
[   27.970672] ata1.01: configured for UDMA/100
[   28.136177] scsi 0:0:1:0: Direct-Access     ATA      WDC WD200EB-11BH 15.1 PQ: 0 ANSI: 5
[   28.136405] sata_nv 0000:00:07.0: version 3.5
[   28.136418] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 19
[   28.136530] sata_nv 0000:00:07.0: Using ADMA mode
[   28.136612] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   28.137827] scsi2 : sata_nv
[   28.138545] scsi3 : sata_nv
[   28.138760] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xc800 irq 19
[   28.138802] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xc808 irq 19
[   28.144041] Driver 'sd' needs updating - please use bus_type methods
[   28.144168] sd 0:0:1:0: [sda] 39102336 512-byte hardware sectors (20020 MB)
[   28.144216] sd 0:0:1:0: [sda] Write Protect is off
[   28.144255] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[   28.144269] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.144348] sd 0:0:1:0: [sda] 39102336 512-byte hardware sectors (20020 MB)
[   28.144392] sd 0:0:1:0: [sda] Write Protect is off
[   28.144430] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[   28.144441] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.144485]  sda: sda1 sda2 < sda5 >
[   28.217299] sd 0:0:1:0: [sda] Attached SCSI disk
[   28.222266] sd 0:0:1:0: Attached scsi generic sg0 type 0
[   28.504504] EXT3-fs: INFO: recovery required on readonly filesystem.
[   28.504552] EXT3-fs: write access will be enabled during recovery.
[   28.604442] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   28.612674] ata3.00: ATA-6: ST3160827AS, 3.42, max UDMA/133
[   28.612715] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   28.628574] ata3.00: configured for UDMA/133
[   28.937631] kjournald starting.  Commit interval 5 seconds
[   28.937688] EXT3-fs: recovery complete.
[   28.938056] EXT3-fs: mounted filesystem with ordered data mode.
[   29.095574] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   29.259371] ata4.00: ATAPI: HL-DT-ST DVDRAM GH20NS10, EL00, max UDMA/100
[   29.431076] ata4.00: configured for UDMA/100
[   29.431213] scsi 2:0:0:0: Direct-Access     ATA      ST3160827AS      3.42 PQ: 0 ANSI: 5
[   29.431261] ata3: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary 0xFFFFFFFF, hw segs 61
[   29.431363] sd 2:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   29.431410] sd 2:0:0:0: [sdb] Write Protect is off
[   29.431449] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   29.431462] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.431546] sd 2:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   29.431591] sd 2:0:0:0: [sdb] Write Protect is off
[   29.431630] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   29.431641] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   29.431685]  sdb: sdb1 sdb2 < sdb5 sdb6 >
[   29.458203] sd 2:0:0:0: [sdb] Attached SCSI disk
[   29.458270] sd 2:0:0:0: Attached scsi generic sg1 type 0
[   29.461656] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH20NS10  EL00 PQ: 0 ANSI: 5
[   29.461705] ata4: bounce limit 0xFFFFFFFF, segment boundary 0xFFFF, hw segs 127
[   29.461796] scsi 3:0:0:0: Attached scsi generic sg2 type 5
[   29.461857] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 23 (level, low) -> IRQ 16
[   29.461966] sata_nv 0000:00:08.0: Using ADMA mode
[   29.462048] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   29.462156] scsi4 : sata_nv
[   29.462242] scsi5 : sata_nv
[   29.462432] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xdc00 irq 16
[   29.462473] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xdc08 irq 16
[   29.770375] ata5: SATA link down (SStatus 0 SControl 300)
[   30.081827] ata6: SATA link down (SStatus 0 SControl 300)
[   43.278897] Real Time Clock Driver v1.12ac
[   43.290825] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   44.270573] logips2pp: Detected unknown logitech mouse model 62
[   44.565724] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   44.568885] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   44.679851] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x1c00
[   44.679912] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x1c40
[   44.786650] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input3
[   44.819054] parport_pc 00:0a: reported by Plug and Play ACPI
[   44.819137] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   45.022989] input: Power Button (FF) as /devices/virtual/input/input4
[   45.047420] ACPI: Power Button (FF) [PWRF]
[   45.047529] input: Power Button (CM) as /devices/virtual/input/input5
[   45.079388] ACPI: Power Button (CM) [PWRB]
[   45.799842] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   45.799893] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 20
[   45.838291] phy0: Selected rate control algorithm 'simple'
[   45.896251] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[   45.896299] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCJ] -> GSI 22 (level, low) -> IRQ 17
[   45.896425] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   46.217298] intel8x0_measure_ac97_clock: measured 54670 usecs
[   46.217344] intel8x0: clocking to 46860
[   47.392503] udev: renamed network interface eth0 to eth1
[   47.476479] Driver 'sr' needs updating - please use bus_type methods
[   47.499016] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   47.499066] Uniform CD-ROM driver Revision: 3.20
[   47.499198] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   47.915680] Linux agpgart interface v0.102
[   47.983861] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   48.015815] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
[   48.015894] [fglrx] ASYNCIO init succeed!
[   48.015995] [fglrx] PAT is enabled successfully!
[   48.016055] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
[   48.921732] NET: Registered protocol family 17
[   49.941493] udev: renamed network interface wlan0 to ra0
[   51.073623] lp0: using parport0 (interrupt-driven).
[   51.307385] Adding 562232k swap on /dev/sda5.  Priority:-1 extents:1 across:562232k
[   51.695660] EXT3 FS on sda1, internal journal
[   52.365816] NET: Registered protocol family 10
[   52.366025] lo: Disabled Privacy Extensions
[   53.406706] ip_tables: (C) 2000-2006 Netfilter Core Team
[   63.303042] eth1: no IPv6 routers present
[  172.007470] ADDRCONF(NETDEV_UP): ra0: link is not ready
[  184.206548] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[  184.206557] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 21
[  187.517516] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
[  187.517521] [fglrx] Reserve Block - 1 offset =  0Xffff000 length = 0X1000
[  187.517524] [fglrx] Reserve Block - 2 offset =  0X7fc0000 length = 0X40000
[  187.700254] [fglrx] interrupt source 20008000 successfully enabled
[  187.700259] [fglrx] enable ID = 0x00000004
[  187.700268] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[  187.700329] [fglrx] interrupt source 10000000 successfully enabled
[  187.700331] [fglrx] enable ID = 0x00000005
[  187.700335] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[  234.422110] ra0: Initial auth_alg=0
[  234.422117] ra0: authenticate with AP 00:18:84:27:ac:6e
[  234.428199] ra0: RX authentication from 00:18:84:27:ac:6e (alg=0 transaction=2 status=0)
[  234.428203] ra0: authenticated
[  234.428206] ra0: associate with AP 00:18:84:27:ac:6e
[  234.432125] ra0: RX AssocResp from 00:18:84:27:ac:6e (capab=0x421 status=0 aid=2)
[  234.432130] ra0: associated
[  234.432135] ra0: switched to short barker preamble (BSSID=00:18:84:27:ac:6e)
[  234.432180] ra0: WMM queue=2 aci=0 acm=0 aifs=2 cWmin=15 cWmax=1023 burst=20
[  234.432182] ra0: failed to set TX queue parameters for queue 2
[  234.432185] ra0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[  234.432187] ra0: failed to set TX queue parameters for queue 3
[  234.432190] ra0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[  234.432192] ra0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[  234.432685] ADDRCONF(NETDEV_CHANGE): ra0: link becomes ready
[  234.435211] ra0: association frame received from 00:18:84:27:ac:6e, but not in associate state - ignored
[  234.684860] ra0: deauthenticate(reason=3)
[ 1118.070745] ra0: Initial auth_alg=0
[ 1118.070751] ra0: authenticate with AP 00:18:84:27:ac:6e
[ 1118.072200] ra0: RX authentication from 00:18:84:27:ac:6e (alg=0 transaction=2 status=0)
[ 1118.072203] ra0: authenticated
[ 1118.072205] ra0: associate with AP 00:18:84:27:ac:6e
[ 1118.075938] ra0: RX AssocResp from 00:18:84:27:ac:6e (capab=0x421 status=0 aid=2)
[ 1118.075940] ra0: associated
[ 1118.075944] ra0: switched to short barker preamble (BSSID=00:18:84:27:ac:6e)
[ 1118.075977] ra0: WMM queue=2 aci=0 acm=0 aifs=2 cWmin=15 cWmax=1023 burst=20
[ 1118.075980] ra0: failed to set TX queue parameters for queue 2
[ 1118.075982] ra0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[ 1118.075984] ra0: failed to set TX queue parameters for queue 3
[ 1118.075987] ra0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[ 1118.075990] ra0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[ 1118.076444] ADDRCONF(NETDEV_CHANGE): ra0: link becomes ready
[ 1118.337464] ra0: deauthenticate(reason=3)
[ 1124.088114] ra0: Initial auth_alg=0
[ 1124.088120] ra0: authenticate with AP 00:18:84:27:ac:6d
[ 1124.089446] ra0: RX authentication from 00:18:84:27:ac:6d (alg=0 transaction=2 status=0)
[ 1124.089448] ra0: authenticated
[ 1124.089451] ra0: associate with AP 00:18:84:27:ac:6d
[ 1124.091952] ra0: RX AssocResp from 00:18:84:27:ac:6d (capab=0x421 status=0 aid=1)
[ 1124.091955] ra0: associated
[ 1124.091958] ra0: switched to short barker preamble (BSSID=00:18:84:27:ac:6d)
[ 1124.091995] ra0: WMM queue=2 aci=0 acm=0 aifs=2 cWmin=15 cWmax=1023 burst=20
[ 1124.091998] ra0: failed to set TX queue parameters for queue 2
[ 1124.092000] ra0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[ 1124.092002] ra0: failed to set TX queue parameters for queue 3
[ 1124.092005] ra0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[ 1124.092008] ra0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[ 1124.092473] ADDRCONF(NETDEV_CHANGE): ra0: link becomes ready
[ 1124.189294] ra0: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[ 1124.189299] ra0: failed to set TX queue parameters for queue 2
[ 1124.189302] ra0: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[ 1124.189304] ra0: failed to set TX queue parameters for queue 3
[ 1124.189307] ra0: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[ 1124.189309] ra0: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[ 1124.346813] ra0: deauthenticate(reason=3)

```

last lines of /var/log/messages
```

Jul  1 19:40:08 rosana-desktop kernel: [  130.466875] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
Jul  1 19:40:08 rosana-desktop kernel: [  130.466884] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 20
Jul  1 19:40:08 rosana-desktop kernel: [  130.499062] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
Jul  1 19:40:08 rosana-desktop kernel: [  130.499068] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCJ] -> GSI 22 (level, low) -> IRQ 17
Jul  1 19:40:08 rosana-desktop kernel: [  130.821954] intel8x0_measure_ac97_clock: measured 54667 usecs
Jul  1 19:40:08 rosana-desktop kernel: [  130.821959] intel8x0: clocking to 46857
Jul  1 19:40:08 rosana-desktop kernel: [  131.948768] udev: renamed network interface eth0 to eth1
Jul  1 19:40:08 rosana-desktop kernel: [  132.037177] Driver 'sr' needs updating - please use bus_type methods
Jul  1 19:40:08 rosana-desktop kernel: [  132.059761] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
Jul  1 19:40:08 rosana-desktop kernel: [  132.059767] Uniform CD-ROM driver Revision: 3.20
Jul  1 19:40:08 rosana-desktop kernel: [  132.465144] Linux agpgart interface v0.102
Jul  1 19:40:08 rosana-desktop kernel: [  132.530460] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
Jul  1 19:40:08 rosana-desktop kernel: [  132.562049] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
Jul  1 19:40:08 rosana-desktop kernel: [  132.562084] [fglrx] ASYNCIO init succeed!
Jul  1 19:40:08 rosana-desktop kernel: [  132.562156] [fglrx] PAT is enabled successfully!
Jul  1 19:40:08 rosana-desktop kernel: [  132.564818] [fglrx] module loaded - fglrx 8.47.3 [Feb 25 2008] on minor 0
Jul  1 19:40:08 rosana-desktop kernel: [  133.471204] NET: Registered protocol family 17
Jul  1 19:40:08 rosana-desktop kernel: [  134.540666] udev: renamed network interface wlan0 to ra0
Jul  1 19:40:08 rosana-desktop kernel: [  135.644575] lp0: using parport0 (interrupt-driven).
Jul  1 19:40:08 rosana-desktop kernel: [  135.910478] Adding 562232k swap on /dev/sda5.  Priority:-1 extents:1 across:562232k
Jul  1 19:40:08 rosana-desktop kernel: [  136.499297] EXT3 FS on sda1, internal journal
Jul  1 19:40:08 rosana-desktop kernel: [  137.288500] NET: Registered protocol family 10
Jul  1 19:40:08 rosana-desktop kernel: [  137.288695] lo: Disabled Privacy Extensions
Jul  1 19:40:08 rosana-desktop kernel: [  138.844189] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul  1 19:40:08 rosana-desktop kernel: [  143.235508] No dock devices found.
Jul  1 19:40:08 rosana-desktop kernel: [  143.817574] powernow-k8: Found 1 AMD Processor Model Unknown processors (1 cpu cores) (version 2.20.00)
Jul  1 19:40:10 rosana-desktop kernel: [  147.358880] ppdev: user-space parallel port driver
Jul  1 19:40:11 rosana-desktop kernel: [  148.148961] audit(1214934011.636:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5288 profile="/usr/sbin/cupsd" namespace="default"
Jul  1 19:40:12 rosana-desktop kernel: [  149.031699] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
Jul  1 19:40:12 rosana-desktop kernel: [  149.031711] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 21

```

---

### Post by RazZziel on 2008-07-03
Suddenly, it started working again for two days, but now it's hanging again. I have no idea of what the problem could be.

Can't anyone point me what could be wrong before I move to SuSE or something?

---

### Post by manonam on 2009-01-16
Hi friend,
  I use sony vaio cr35 laptop. And i too am having the same problem. after installing for about a week it was working fine. Then after a software update i get stuck! When i boot into kde, within 5seconds i get a hang and that's it. I have installed using wubi. And also my systems doesn't give the login screen if it's on battery power!
Any reply would be appreciated!

---

