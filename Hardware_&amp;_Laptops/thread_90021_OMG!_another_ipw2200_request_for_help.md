---
title: "OMG! another ipw2200 request for help"
date: 2005-11-14
forum: Hardware &amp; Laptops
---

### Post by bosqueG on 2005-11-14
i have a dell inspiron 9300 which includes an intel 2200. i put ubuntu 5.10 on there. it didn't see the wireless card. only networking devices were lo, eth0 and sit0.

so i installed the 80211 and ipw2200 (and firmware) modules per the "HOWTO: ipw2200 + wpa" tutorial. 

(recap:  
I downloaded the latest ipw2200-fw: 2.3, ieee80211: 1.1.6 package, and ipw2200 package: 1.0.8
uncompressed each archive.  
copied firmware files (.fw) to 'usr/lib/hotplug/firmware'
ran' make', then 'sudo make install' on ieee80211 and ipw2200.
compiled without errors. the ipw2200 install concluded by reminding me to put firmware files in the 'usr/lib/hotplug/firmware' directory. i'm assuming that's normal.)

when i try 'sudo modprobe ipw2200' i get this:
> 
bosque00@charlotte:~/Desktop/ieee80211-1.1.6$ sudo modprobe ipw2200
FATAL: Error inserting ipw2200 (/lib/modules/2.6.12-9-386/kernel/drivers/net/wireless/ipw2200.ko): Unknown symbol in module, or unknown parameter (see dmesg) 

dmesg output (pertaining to relevant modules, full dmesg in next post):

>  [4295713.453000] ieee80211_crypt: registered algorithm 'NULL'
[4295713.493000] ieee80211: disagrees about version of symbol ieee80211_get_crypto_ops
[4295713.494000] ieee80211: Unknown symbol ieee80211_get_crypto_ops
[4295713.494000] ieee80211: disagrees about version of symbol ieee80211_crypt_deinit_entries
[4295713.494000] ieee80211: Unknown symbol ieee80211_crypt_deinit_entries
[4295713.494000] ieee80211: disagrees about version of symbol ieee80211_crypt_delayed_deinit
[4295713.494000] ieee80211: Unknown symbol ieee80211_crypt_delayed_deinit
[4295713.494000] ieee80211: disagrees about version of symbol ieee80211_crypt_quiescing
[4295713.494000] ieee80211: Unknown symbol ieee80211_crypt_quiescing
[4295713.531000] ieee80211: 802.11 data/management/control stack, 1.0.3
[4295713.531000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[4295713.536000] ipw2200: disagrees about version of symbol ieee80211_get_crypto_ops
[4295713.537000] ipw2200: Unknown symbol ieee80211_get_crypto_ops
[4295713.537000] ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
[4295713.537000] ipw2200: Unknown symbol ieee80211_wx_set_encode
[4295713.537000] ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
[4295713.537000] ipw2200: Unknown symbol ieee80211_wx_get_encode
[4295713.537000] ipw2200: disagrees about version of symbol ieee80211_txb_free
[4295713.537000] ipw2200: Unknown symbol ieee80211_txb_free
[4295713.537000] ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
[4295713.537000] ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
[4295713.537000] ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
[4295713.537000] ipw2200: Unknown symbol ieee80211_wx_get_scan
[4295713.537000] ipw2200: Unknown symbol escape_essid
[4295713.538000] ipw2200: disagrees about version of symbol ieee80211_rx
[4295713.538000] ipw2200: Unknown symbol ieee80211_rx
[4295713.538000] ipw2200: disagrees about version of symbol ieee80211_rx_mgt
[4295713.538000] ipw2200: Unknown symbol ieee80211_rx_mgt
[4296052.623000] ipw2200: disagrees about version of symbol ieee80211_get_crypto_ops
[4296052.623000] ipw2200: Unknown symbol ieee80211_get_crypto_ops
[4296052.623000] ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
[4296052.624000] ipw2200: Unknown symbol ieee80211_wx_set_encode
[4296052.624000] ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
[4296052.624000] ipw2200: Unknown symbol ieee80211_wx_get_encode
[4296052.624000] ipw2200: disagrees about version of symbol ieee80211_txb_free
[4296052.624000] ipw2200: Unknown symbol ieee80211_txb_free
[4296052.624000] ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
[4296052.624000] ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
[4296052.624000] ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
[4296052.624000] ipw2200: Unknown symbol ieee80211_wx_get_scan
[4296052.624000] ipw2200: Unknown symbol escape_essid
[4296052.624000] ipw2200: disagrees about version of symbol ieee80211_rx
[4296052.625000] ipw2200: Unknown symbol ieee80211_rx
[4296052.625000] ipw2200: disagrees about version of symbol ieee80211_rx_mgt
[4296052.625000] ipw2200: Unknown symbol ieee80211_rx_mgt

---

### Post by bosqueG on 2005-11-14
bosque00@charlotte:~/Desktop/ieee80211-1.1.6$ dmesg
0] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[4294672.957000] ata1: SATA max UDMA/133 cmd 0x1F0 ctl 0x3F6 bmdma 0xBFA0 irq 14
[4294673.112000] ata1: dev 0 cfg 49:2b00 82:346b 83:5b29 84:6003 85:3469 86:9a09 87:6003 88:203f
[4294673.112000] ata1: dev 0 ATA, max UDMA/100, 156301488 sectors:
[4294673.112000] ata1(0): applying bridge limits
[4294673.285000] ata1: dev 0 configured for UDMA/100
[4294673.285000] scsi0 : ata_piix
[4294673.285000]   Vendor: ATA       Model: FUJITSU MHV2080A  Rev: 0000
[4294673.285000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[4294673.285000] ata2: SATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xBFA8 irq 15
[4294673.590000] ata2: dev 0 cfg 49:0b00 82:0210 83:1000 84:0000 85:0000 86:0000 87:0000 88:0407
[4294673.590000] ata2: dev 0 ATAPI, max UDMA/33
[4294673.590000] ata2: dev 0 configured for UDMA/33
[4294673.590000] scsi1 : ata_piix
[4294673.591000]   Vendor: SONY      Model: DVD+-RW DW-D56A   Rev: PDS3
[4294673.591000]   Type:   CD-ROM                             ANSI SCSI revision: 05
[4294673.602000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294673.602000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[4294673.602000] ACPI: bus type ide registered
[4294673.602000] ide0: I/O resource 0x1F0-0x1F7 not free.
[4294673.602000] ide0: ports already in use, skipping probe
[4294673.602000] ide1: I/O resource 0x170-0x177 not free.
[4294673.602000] ide1: ports already in use, skipping probe
[4294673.602000] Probing IDE interface ide2...
[4294674.115000] Probing IDE interface ide3...
[4294674.627000] Probing IDE interface ide4...
[4294675.139000] Probing IDE interface ide5...
[4294675.654000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[4294675.654000] SCSI device sda: drive cache: write back
[4294675.654000] SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
[4294675.654000] SCSI device sda: drive cache: write back
[4294675.654000]  /dev/scsi/host0/bus0/target0/lun0: p1 p2 p3 < p5 >
[4294675.766000] Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
[4294675.905000] Attempting manual resume
[4294675.905000] swsusp: Suspend partition has wrong signature?
[4294675.927000] usbcore: registered new driver usbfs
[4294675.927000] usbcore: registered new driver hub
[4294675.928000] USB Universal Host Controller Interface driver v2.2
[4294675.928000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 16 (level, low) -> IRQ 16
[4294675.928000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[4294675.928000] uhci_hcd 0000:00:1d.0: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1
[4294675.990000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[4294675.990000] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000bf80
[4294675.990000] hub 1-0:1.0: USB hub found
[4294675.990000] hub 1-0:1.0: 2 ports detected
[4294675.993000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 17
[4294675.993000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[4294675.993000] uhci_hcd 0000:00:1d.1: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2
[4294676.055000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[4294676.055000] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000bf60
[4294676.055000] hub 2-0:1.0: USB hub found
[4294676.055000] hub 2-0:1.0: 2 ports detected
[4294676.058000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[4294676.058000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[4294676.058000] uhci_hcd 0000:00:1d.2: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3
[4294676.120000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[4294676.120000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000bf40
[4294676.120000] hub 3-0:1.0: USB hub found
[4294676.120000] hub 3-0:1.0: 2 ports detected
[4294676.123000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 19 (level, low) -> IRQ 19
[4294676.123000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[4294676.123000] uhci_hcd 0000:00:1d.3: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4
[4294676.185000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[4294676.185000] uhci_hcd 0000:00:1d.3: irq 19, io base 0x0000bf20
[4294676.185000] hub 4-0:1.0: USB hub found
[4294676.185000] hub 4-0:1.0: 2 ports detected
[4294676.215000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 16 (level, low) -> IRQ 16
[4294676.215000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[4294676.215000] ehci_hcd 0000:00:1d.7: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller
[4294676.215000] ehci_hcd 0000:00:1d.7: debug port 1
[4294676.215000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[4294676.215000] ehci_hcd 0000:00:1d.7: irq 16, io mem 0xffa80800
[4294676.220000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[4294676.220000] ehci_hcd 0000:00:1d.7: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[4294676.220000] hub 5-0:1.0: USB hub found
[4294676.220000] hub 5-0:1.0: 8 ports detected
[4294676.295000] b44.c:v0.95 (Aug 3, 2004)
[4294676.295000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[4294676.298000] eth0: Broadcom 4400 10/100BaseT Ethernet 00:11:43:7a:fe:f3
[4294676.769000] usb 5-8: new high speed USB device using ehci_hcd and address 3
[4294677.022000] usb 4-1: new low speed USB device using uhci_hcd and address 2
[4294678.359000] usbcore: registered new driver hiddev
[4294678.379000] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.3-1
[4294678.379000] usbcore: registered new driver usbhid
[4294678.379000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294678.393000] Initializing USB Mass Storage driver...
[4294678.394000] scsi2 : SCSI emulation for USB Mass Storage devices
[4294678.394000] usb-storage: device found at 3
[4294678.394000] usb-storage: waiting for device to settle before scanning
[4294678.394000] usbcore: registered new driver usb-storage
[4294678.394000] USB Mass Storage support registered.
[4294678.716000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[4294678.716000] ACPI: Processor [CPU0] (supports 8 throttling states)
[4294678.720000] ACPI: Thermal Zone [THM] (43 C)
[4294678.915000] Attempting manual resume
[4294678.915000] swsusp: Suspend partition has wrong signature?
[4294678.947000] kjournald starting.  Commit interval 5 seconds
[4294678.947000] EXT3-fs: mounted filesystem with ordered data mode.
[4294680.152000] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294683.013000] Adding 1510068k swap on /dev/sda5.  Priority:-1 extents:1
[4294683.341000] EXT3 FS on sda2, internal journal
[4294683.394000]   Vendor: Memorex   Model: TD 2C             Rev: 1.04
[4294683.394000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294683.396000] SCSI device sdb: 2007040 512-byte hdwr sectors (1028 MB)
[4294683.397000] sdb: Write Protect is off
[4294683.397000] sdb: Mode Sense: 23 00 00 00
[4294683.397000] sdb: assuming drive cache: write through
[4294683.401000] SCSI device sdb: 2007040 512-byte hdwr sectors (1028 MB)
[4294683.402000] sdb: Write Protect is off
[4294683.402000] sdb: Mode Sense: 23 00 00 00
[4294683.402000] sdb: assuming drive cache: write through
[4294683.402000]  /dev/scsi/host2/bus0/target0/lun0: p1
[4294683.404000] Attached scsi removable disk sdb at scsi2, channel 0, id 0, lun 0
[4294683.408000] usb-storage: device scan complete
[4294690.564000] lp: driver loaded but no devices found
[4294690.590000] mice: PS/2 mouse device common for all mice
[4294690.650000] ieee1394: Initialized config rom entry `ip1394'
[4294690.657000] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[4294691.130000] alps.c: Enabling hardware tapping
[4294691.218000] input: PS/2 Mouse on isa0060/serio1
[4294691.219000] input: AlpsPS/2 ALPS GlidePoint on isa0060/serio1
[4294691.380000] ts: Compaq touchscreen protocol output
[4294694.527000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[4294697.688000] Linux agpgart interface v0.101 (c) Dave Jones
[4294697.693000] agpgart: Detected an Intel 915GM Chipset.
[4294697.722000] agpgart: AGP aperture is 256M @ 0x0
[4294697.785000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294697.789000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294697.789000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294698.044000] hw_random: cannot enable RNG, aborting
[4294698.191000] ACPI: PCI Interrupt 0000:00:1e.2[A] -> GSI 16 (level, low) -> IRQ 16
[4294698.191000] PCI: Setting latency timer of device 0000:00:1e.2 to 64
[4294699.000000] intel8x0_measure_ac97_clock: measured 49497 usecs
[4294699.000000] intel8x0: clocking to 48000
[4294699.679000] Linux Kernel Card Services
[4294699.679000]   options:  [pci] [cardbus] [pm]
[4294699.688000] PCI: Enabling device 0000:03:01.0 (0000 -> 0002)
[4294699.688000] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 19 (level, low) -> IRQ 19
[4294699.688000] Yenta: CardBus bridge found at 0000:03:01.0 [1028:0189]
[4294699.808000] Yenta: ISA IRQ mask 0x04b8, PCI irq 19
[4294699.808000] Socket status: 30000006
[4294699.898000] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[4294699.898000] ACPI: PCI Interrupt 0000:03:01.1[B] -> GSI 18 (level, low) -> IRQ 18
[4294699.953000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[dfcfb800-dfcfbfff]  Max Packet=[2048]
[4294701.221000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[424fc000245f3ce1]
[4294701.635000] Real Time Clock Driver v1.12
[4294701.695000] input: PC Speaker
[4294702.192000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[4294702.192000] Uniform CD-ROM driver Revision: 3.20
[4294702.195000] Attached scsi CD-ROM sr0 at scsi1, channel 0, id 0, lun 0
[4294702.225000] Attached scsi generic sg0 at scsi0, channel 0, id 0, lun 0,  type 0
[4294702.230000] Attached scsi generic sg1 at scsi1, channel 0, id 0, lun 0,  type 5
[4294702.233000] Attached scsi generic sg2 at scsi2, channel 0, id 0, lun 0,  type 0
[4294702.808000] NET: Registered protocol family 17
[4294703.795000] b44: eth0: Link is down.
[4294705.795000] b44: eth0: Link is up at 100 Mbps, full duplex.
[4294705.795000] b44: eth0: Flow control is off for TX and off for RX.
[4294708.837000] NET: Registered protocol family 10
[4294708.837000] Disabled Privacy Extensions on device c02eb280(lo)
[4294708.839000] IPv6 over IPv4 tunneling driver
[4294710.431000] ACPI: AC Adapter [AC] (on-line)
[4294710.737000] ACPI: Battery Slot [BAT0] (battery present)
[4294710.754000] ACPI: Lid Switch [LID]
[4294710.754000] ACPI: Power Button (CM) [PBTN]
[4294710.754000] ACPI: Sleep Button (CM) [SBTN]
[4294710.843000] ibm_acpi: ec object not found
[4294710.943000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[4294718.177000] apm: BIOS not found.
[4294719.143000] eth0: no IPv6 routers present
[4294719.616000] cs: IO port probe 0x100-0x4ff: excluding 0x370-0x377 0x3f0-0x3f7
[4294719.618000] cs: IO port probe 0xc00-0xcf7: clean.
[4294719.619000] cs: IO port probe 0xa00-0xaff: clean.
[4294720.382000] Bluetooth: Core ver 2.7
[4294720.382000] NET: Registered protocol family 31
[4294720.382000] Bluetooth: HCI device and connection manager initialized
[4294720.382000] Bluetooth: HCI socket layer initialized
[4294720.406000] Bluetooth: L2CAP ver 2.7
[4294720.406000] Bluetooth: L2CAP socket layer initialized
[4294720.432000] Bluetooth: RFCOMM ver 1.5
[4294720.432000] Bluetooth: RFCOMM socket layer initialized
[4294720.432000] Bluetooth: RFCOMM TTY layer initialized
[4294746.443000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4294816.331000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[4294816.331000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
[4294818.658000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[4294818.658000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
[4294820.752000] atkbd.c: Unknown key pressed (translated set 2, code 0x88 on isa0060/serio0).
[4294820.752000] atkbd.c: Use 'setkeycodes e008 <keycode>' to make it known.
[4295713.453000] ieee80211_crypt: registered algorithm 'NULL'
[4295713.493000] ieee80211: disagrees about version of symbol ieee80211_get_crypto_ops
[4295713.494000] ieee80211: Unknown symbol ieee80211_get_crypto_ops
[4295713.494000] ieee80211: disagrees about version of symbol ieee80211_crypt_deinit_entries
[4295713.494000] ieee80211: Unknown symbol ieee80211_crypt_deinit_entries
[4295713.494000] ieee80211: disagrees about version of symbol ieee80211_crypt_delayed_deinit
[4295713.494000] ieee80211: Unknown symbol ieee80211_crypt_delayed_deinit
[4295713.494000] ieee80211: disagrees about version of symbol ieee80211_crypt_quiescing
[4295713.494000] ieee80211: Unknown symbol ieee80211_crypt_quiescing
[4295713.531000] ieee80211: 802.11 data/management/control stack, 1.0.3
[4295713.531000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[4295713.536000] ipw2200: disagrees about version of symbol ieee80211_get_crypto_ops
[4295713.537000] ipw2200: Unknown symbol ieee80211_get_crypto_ops
[4295713.537000] ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
[4295713.537000] ipw2200: Unknown symbol ieee80211_wx_set_encode
[4295713.537000] ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
[4295713.537000] ipw2200: Unknown symbol ieee80211_wx_get_encode
[4295713.537000] ipw2200: disagrees about version of symbol ieee80211_txb_free
[4295713.537000] ipw2200: Unknown symbol ieee80211_txb_free
[4295713.537000] ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
[4295713.537000] ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
[4295713.537000] ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
[4295713.537000] ipw2200: Unknown symbol ieee80211_wx_get_scan
[4295713.537000] ipw2200: Unknown symbol escape_essid
[4295713.538000] ipw2200: disagrees about version of symbol ieee80211_rx
[4295713.538000] ipw2200: Unknown symbol ieee80211_rx
[4295713.538000] ipw2200: disagrees about version of symbol ieee80211_rx_mgt
[4295713.538000] ipw2200: Unknown symbol ieee80211_rx_mgt
[4296052.623000] ipw2200: disagrees about version of symbol ieee80211_get_crypto_ops
[4296052.623000] ipw2200: Unknown symbol ieee80211_get_crypto_ops
[4296052.623000] ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
[4296052.624000] ipw2200: Unknown symbol ieee80211_wx_set_encode
[4296052.624000] ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
[4296052.624000] ipw2200: Unknown symbol ieee80211_wx_get_encode
[4296052.624000] ipw2200: disagrees about version of symbol ieee80211_txb_free
[4296052.624000] ipw2200: Unknown symbol ieee80211_txb_free
[4296052.624000] ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
[4296052.624000] ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
[4296052.624000] ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
[4296052.624000] ipw2200: Unknown symbol ieee80211_wx_get_scan
[4296052.624000] ipw2200: Unknown symbol escape_essid
[4296052.624000] ipw2200: disagrees about version of symbol ieee80211_rx
[4296052.625000] ipw2200: Unknown symbol ieee80211_rx
[4296052.625000] ipw2200: disagrees about version of symbol ieee80211_rx_mgt
[4296052.625000] ipw2200: Unknown symbol ieee80211_rx_mgt

---

### Post by bosqueG on 2005-11-14
bosque00@charlotte:~/Desktop/ieee80211-1.1.6$ lsmod
Module                  Size  Used by
firmware_class          9472  0
ieee80211              27012  0
ieee80211_crypt         5636  1 ieee80211
nls_utf8                2176  1
nls_cp437               5888  1
vfat                   12288  1
fat                    46492  1 vfat
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
speedstep_centrino      7380  1
cpufreq_userspace       4444  1
cpufreq_stats           5124  0
freq_table              4484  2 speedstep_centrino,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
pcmcia                 24584  2
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
i2c_core               19728  1 i2c_acpi_ec
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  6
af_packet              20232  2
sg                     33696  0
sr_mod                 15652  0
cdrom                  33952  1 sr_mod
pcspkr                  3652  0
rtc                    11832  0
ohci1394               30644  0
yenta_socket           22540  1
rsrc_nonstatic         12032  1 yenta_socket
pcmcia_core            44932  3 pcmcia,yenta_socket,rsrc_nonstatic
tpm_nsc                 6528  0
tpm                     9504  1 tpm_nsc
snd_intel8x0           30144  1
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
pci_hotplug            24628  0
intel_agp              21276  1
agpgart                32328  1 intel_agp
dm_mod                 50364  1
joydev                  9280  0
tsdev                   7616  0
evdev                   9088  1
sbp2                   21128  0
ieee1394               90936  2 ohci1394,sbp2
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  0
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  1
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  2 speedstep_centrino,thermal
fan                     4740  0
usb_storage            64704  2
usbhid                 30688  0
b44                    19204  0
mii                     5248  1 b44
ehci_hcd               29448  0
uhci_hcd               28048  0
usbcore               104188  5 usb_storage,usbhid,ehci_hcd,uhci_hcd
sd_mod                 17424  5
ide_generic             1664  0
ide_core              125268  2 usb_storage,ide_generic
ata_piix                9476  5
ahci                   11268  0
libata                 47876  2 ata_piix,ahci
scsi_mod              124872  7 sg,sr_mod,sbp2,usb_storage,sd_mod,ahci,libata
unix                   24624  717
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon

---

