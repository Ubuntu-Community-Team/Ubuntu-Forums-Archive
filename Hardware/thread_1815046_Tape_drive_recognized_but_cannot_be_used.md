---
title: "Tape drive recognized but cannot be used"
date: 2011-07-30
forum: Hardware
---

### Post by scorchgeek on 2011-07-30
Some time ago I purchased a DLT4000 tape drive at a garage sale to use for some simple backups. It worked very well until one day all the lights started flashing and it stopped working, and Google told me that it meant the drive had failed. Since it didn't cost very much to begin with, I decided not to try to repair it, and instead bought a replacement on eBay.

So today I got the drive, and since it was an internal drive, I ripped apart the external case I had the old one in and swapped it in. The new drive is actually a DLT4700, but it appears there's not much difference between the models. I booted it up, the SCSI controller recognized the drive, and an ls /dev showed the st0 devices. 

BUT...running "mt -f /dev/st0 status", a tar command, and such simply causes the machine to hang. At one point during troubleshooting, the st0 devices disappeared, but then I got them back.

Here's the relevant portion of dmesg:

```
[    2.251013] ata2.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.251029] ata2.01: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.251206] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.251216] ata1.01: SATA link down (SStatus 0 SControl 300)
[    2.260128] ata1.00: ATA-8: WDC WD10EADS-00P6B0, 01.00A01, max UDMA/133
[    2.260132] ata1.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.276096] ata1.00: configured for UDMA/133
[    2.276270] scsi 0:0:0:0: Direct-Access     ATA      WDC WD10EADS-00P 01.0 PQ: 0 ANSI: 5
[    2.276409] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.276467] sd 0:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.276496] sd 0:0:0:0: [sda] Write Protect is off
[    2.276498] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.276515] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.285750] ata2.00: ATA-8: WDC WD5000AACS-00ZUB0, 01.01B01, max UDMA/133
[    2.285754] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.285762] ata2.01: ATAPI: HL-DT-ST DVD-RW GSA-H60L, DC07, max UDMA/100
[    2.299475] ata2.00: configured for UDMA/133
[    2.306158]  sda: sda1 sda2 < sda5 sda6 >
[    2.306688] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.314987] ata2.01: configured for UDMA/100
[    2.398761] usb 2-3: new high speed USB device using ehci_hcd and address 4
[    2.426240] scsi 1:0:0:0: Direct-Access     ATA      WDC WD5000AACS-0 01.0 PQ: 0 ANSI: 5
[    2.426373] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.426376] sd 1:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.427897] sd 1:0:0:0: [sdb] Write Protect is off
[    2.427901] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.429400] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.429522] scsi 1:0:1:0: CD-ROM            HL-DT-ST DVD-RW GSA-H60L  DC07 PQ: 0 ANSI: 5
[    2.545995] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.545999] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.546121] sr 1:0:1:0: Attached scsi CD-ROM sr0
[    2.546168] sr 1:0:1:0: Attached scsi generic sg2 type 5
[    2.557223]  sdb: sdb1
[    2.557644] sd 1:0:0:0: [sdb] Attached SCSI disk
[    2.558715] Freeing unused kernel memory: 720k freed
[    2.559375] Write protecting the kernel text: 5352k
[    2.559680] Write protecting the kernel read-only data: 2188k
[    2.559681] NX-protecting the kernel data: 4888k
[    2.577265] <30>udev[97]: starting version 167
[    2.604349] xhci_hcd 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.604366] xhci_hcd 0000:02:00.0: setting latency timer to 64
[    2.604369] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    2.604426] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 9
[    2.607808] pata_jmicron 0000:08:00.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    2.607834] pata_jmicron 0000:08:00.1: setting latency timer to 64
[    2.610488] scsi4 : pata_jmicron
[    2.610559] scsi5 : pata_jmicron
[    2.611081] ata5: PATA max UDMA/100 cmd 0xdf00 ctl 0xde00 bmdma 0xdb00 irq 18
[    2.611083] ata6: PATA max UDMA/100 cmd 0xdd00 ctl 0xdc00 bmdma 0xdb08 irq 18
[    2.611105] pata_jmicron 0000:09:00.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    2.611131] pata_jmicron 0000:09:00.1: setting latency timer to 64
[    2.611425] usbcore: registered new interface driver uas
[    2.611459] scsi6 : pata_jmicron
[    2.611526] scsi7 : pata_jmicron
[    2.612099] ata7: PATA max UDMA/100 cmd 0xbf00 ctl 0xbe00 bmdma 0xbb00 irq 16
[    2.612101] ata8: PATA max UDMA/100 cmd 0xbd00 ctl 0xbc00 bmdma 0xbb08 irq 16
[    2.620884] ahci 0000:01:00.0: version 3.0
[    2.620893] ahci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.620936] ahci 0000:01:00.0: irq 44 for MSI/MSI-X
[    2.620944] ahci 0000:01:00.0: controller can do FBS, turning on CAP_FBS
[    2.623986] aic7xxx 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.625295] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.625307] r8169 0000:0a:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.625338] r8169 0000:0a:00.0: setting latency timer to 64
[    2.625400] r8169 0000:0a:00.0: irq 45 for MSI/MSI-X
[    2.625724] r8169 0000:0a:00.0: eth0: RTL8168d/8111d at 0xf844e000, 6c:f0:49:5f:11:72, XID 083000c0 IRQ 45
[    2.634670] xhci_hcd 0000:02:00.0: irq 16, io mem 0xfbafe000
[    2.634709] xhci_hcd 0000:02:00.0: irq 46 for MSI/MSI-X
[    2.634713] xhci_hcd 0000:02:00.0: irq 47 for MSI/MSI-X
[    2.634718] xhci_hcd 0000:02:00.0: irq 48 for MSI/MSI-X
[    2.634722] xhci_hcd 0000:02:00.0: irq 49 for MSI/MSI-X
[    2.634727] xhci_hcd 0000:02:00.0: irq 50 for MSI/MSI-X
[    2.634731] xhci_hcd 0000:02:00.0: irq 51 for MSI/MSI-X
[    2.634736] xhci_hcd 0000:02:00.0: irq 52 for MSI/MSI-X
[    2.634740] xhci_hcd 0000:02:00.0: irq 53 for MSI/MSI-X
[    2.638032] usb usb9: No SuperSpeed endpoint companion for config 1  interface 0 altsetting 0 ep 129: using minimum values
[    2.638100] xHCI xhci_add_endpoint called for root hub
[    2.638101] xHCI xhci_check_bandwidth called for root hub
[    2.638122] hub 9-0:1.0: USB hub found
[    2.638129] hub 9-0:1.0: 4 ports detected
[    2.638219] ahci 0000:01:00.0: AHCI 0001.0200 32 slots 8 ports 6 Gbps 0xff impl IDE mode
[    2.638222] ahci 0000:01:00.0: flags: 64bit ncq fbs pio 
[    2.638226] ahci 0000:01:00.0: setting latency timer to 64
[    2.639078] scsi8 : ahci
[    2.639227] scsi9 : ahci
[    2.639358] scsi10 : ahci
[    2.639482] scsi11 : ahci
[    2.639612] scsi12 : ahci
[    2.639735] scsi13 : ahci
[    2.639858] scsi14 : ahci
[    2.639979] scsi15 : ahci
[    2.640023] ata9: SATA max UDMA/133 abar m2048@0xfb8ff000 port 0xfb8ff100 irq 44
[    2.640025] ata10: SATA max UDMA/133 abar m2048@0xfb8ff000 port 0xfb8ff180 irq 44
[    2.640027] ata11: SATA max UDMA/133 abar m2048@0xfb8ff000 port 0xfb8ff200 irq 44
[    2.640030] ata12: SATA max UDMA/133 abar m2048@0xfb8ff000 port 0xfb8ff280 irq 44
[    2.640032] ata13: SATA max UDMA/133 abar m2048@0xfb8ff000 port 0xfb8ff300 irq 44
[    2.640034] ata14: SATA max UDMA/133 abar m2048@0xfb8ff000 port 0xfb8ff380 irq 44
[    2.640036] ata15: SATA max UDMA/133 abar m2048@0xfb8ff000 port 0xfb8ff400 irq 44
[    2.640038] ata16: SATA max UDMA/133 abar m2048@0xfb8ff000 port 0xfb8ff480 irq 44
[    2.640060] ahci 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.654466] ahci 0000:08:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    2.654469] ahci 0000:08:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    2.654474] ahci 0000:08:00.0: setting latency timer to 64
[    2.654723] scsi16 : ahci
[    2.654795] scsi17 : ahci
[    2.654867] ata17: SATA max UDMA/133 abar m8192@0xfbefe000 port 0xfbefe100 irq 17
[    2.654870] ata18: SATA max UDMA/133 abar m8192@0xfbefe000 port 0xfbefe180 irq 17
[    2.654886] ahci 0000:09:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.670526] ahci 0000:09:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    2.670529] ahci 0000:09:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[    2.670534] ahci 0000:09:00.0: setting latency timer to 64
[    2.670848] scsi18 : ahci
[    2.671002] scsi19 : ahci
[    2.671083] ata19: SATA max UDMA/133 abar m8192@0xfbdfe000 port 0xfbdfe100 irq 19
[    2.671086] ata20: SATA max UDMA/133 abar m8192@0xfbdfe000 port 0xfbdfe180 irq 19
[    2.778376] usb 6-2: new full speed USB device using uhci_hcd and address 2
[    2.880714] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.958250] ata15: SATA link down (SStatus 0 SControl 300)
[    2.958272] ata14: SATA link down (SStatus 0 SControl 300)
[    2.962185] ata13: SATA link down (SStatus 0 SControl 300)
[    2.962202] ata11: SATA link down (SStatus 0 SControl 300)
[    2.962218] ata12: SATA link down (SStatus 0 SControl 300)
[    2.962233] ata9: SATA link down (SStatus 0 SControl 300)
[    2.962251] ata16: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.962406] ata16.00: ATAPI: MARVELL VIRTUALL, 1.09, max UDMA/66
[    2.962702] ata16.00: configured for UDMA/66
[    2.966156] ata10: SATA link down (SStatus 0 SControl 300)
[    2.974249] ata18: SATA link down (SStatus 0 SControl 300)
[    2.974286] ata17: SATA link down (SStatus 0 SControl 300)
[    2.990220] ata20: SATA link down (SStatus 0 SControl 300)
[    2.990256] ata19: SATA link down (SStatus 0 SControl 300)
[    3.038344] usb 2-1.2: new full speed USB device using ehci_hcd and address 5
[    3.101909] scsi 15:0:0:0: Processor         Marvell  91xx Config      1.01 PQ: 0 ANSI: 5
[    3.101999] scsi 15:0:0:0: Attached scsi generic sg3 type 3
[    3.133006] hub 2-1.2:1.0: USB hub found
[    3.133346] hub 2-1.2:1.0: 4 ports detected
[    3.206124] usb 2-1.3: new low speed USB device using ehci_hcd and address 6
[    3.374005] usb 2-1.4: new low speed USB device using ehci_hcd and address 7
[    3.561691] usb 2-1.7: new low speed USB device using ehci_hcd and address 8
[    3.749978] usb 2-1.2.2: new full speed USB device using ehci_hcd and address 9
[   12.845836] <30>udev[345]: starting version 167
[   12.853757] lp: driver loaded but no devices found
[   12.857365] st: Version 20101219, fixed bufsize 32768, s/g segs 256
[   12.887979] nvidia: module license 'NVIDIA' taints kernel.
[   12.887982] Disabling lock debugging due to kernel taint
[   12.889101] EDAC MC: Ver: 2.1.0 Jun 28 2011
[   12.895511] EDAC i7core: Driver loaded.
[   12.938033] Initializing USB Mass Storage driver...
[   12.939566] scsi21 : usb-storage 2-3:1.0
[   12.939708] usbcore: registered new interface driver usb-storage
[   12.939710] USB Mass Storage support registered.
[   12.975823] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0/input/input2
[   12.975919] generic-usb 0003:046D:C525.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.0-2/input0
[   12.981001] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.1/input/input3
[   12.981251] generic-usb 0003:046D:C525.0002: input,hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.0-2/input1
[   12.986085] input: Ultimarc Button/Joystick/Trackball Interface  as /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.4/2-1.4:1.0/input/input4
[   12.986186] generic-usb 0003:1324:0103.0005: input,hidraw2: USB HID v1.10 Keyboard [Ultimarc Button/Joystick/Trackball Interface ] on usb-0000:00:1d.7-1.4/input0
[   12.993513] input: Ultimarc Button/Joystick/Trackball Interface  as /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.4/2-1.4:1.1/input/input5
[   12.993656] generic-usb 0003:1324:0103.0006: input,hidraw3: USB HID v1.10 Mouse [Ultimarc Button/Joystick/Trackball Interface ] on usb-0000:00:1d.7-1.4/input1
[   13.006134] Adding 5858300k swap on /dev/sda5.  Priority:-1 extents:1 across:5858300k 
[   13.015762] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.015807] HDA Intel 0000:00:1b.0: irq 54 for MSI/MSI-X
[   13.015829] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.019296] type=1400 audit(1312051831.721:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=716 comm="apparmor_parser"
[   13.019807] type=1400 audit(1312051831.721:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=493 comm="apparmor_parser"
[   13.019896] type=1400 audit(1312051831.721:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=716 comm="apparmor_parser"
[   13.020290] type=1400 audit(1312051831.725:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=716 comm="apparmor_parser"
[   13.020411] type=1400 audit(1312051831.725:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=493 comm="apparmor_parser"
[   13.020767] type=1400 audit(1312051831.725:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=493 comm="apparmor_parser"
[   13.060381] hda_codec: ALC889: BIOS auto-probing.
[   13.068961] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   13.367037] nvidia 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.367044] nvidia 0000:03:00.0: setting latency timer to 64
[   13.367048] vgaarb: device changed decodes: PCI:0000:03:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   13.367120] NVRM: loading NVIDIA UNIX x86 Kernel Module  270.41.06  Mon Apr 18 14:54:25 PDT 2011
[   13.375181] SB-XFi 0000:07:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.375348] SB-XFi 0000:07:00.0: setting latency timer to 64
[   13.380012] input: TypeMatrix.com USB Keyboard as /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.7/2-1.7:1.0/input/input7
[   13.380124] generic-usb 0003:1E54:2030.0007: input,hidraw4: USB HID v1.10 Keyboard [TypeMatrix.com USB Keyboard] on usb-0000:00:1d.7-1.7/input0
[   13.395972] input: TypeMatrix.com USB Keyboard as /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.7/2-1.7:1.1/input/input8
[   13.396097] generic-usb 0003:1E54:2030.0008: input,hiddev0,hidraw5: USB HID v1.10 Device [TypeMatrix.com USB Keyboard] on usb-0000:00:1d.7-1.7/input1
[   13.657263] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   13.683432] input: HID 05f3:0007 as /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.2/2-1.2.2/2-1.2.2:1.0/input/input9
[   13.683522] generic-usb 0003:05F3:0007.0009: input,hidraw6: USB HID v1.00 Keyboard [HID 05f3:0007] on usb-0000:00:1d.7-1.2.2/input0
[   13.688854] input: HID 05f3:0007 as /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.2/2-1.2.2/2-1.2.2:1.1/input/input10
[   13.688942] generic-usb 0003:05F3:0007.000A: input,hidraw7: USB HID v1.00 Device [HID 05f3:0007] on usb-0000:00:1d.7-1.2.2/input1
[   13.688959] usbcore: registered new interface driver usbhid
[   13.688961] usbhid: USB HID core driver
[   13.723471] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.3/2-1.3:1.0/input/input11
[   13.723575] logitech 0003:046D:C517.0003: input,hidraw8: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.7-1.3/input0
[   13.728377] logitech 0003:046D:C517.0004: fixing up Logitech keyboard report descriptor
[   13.728724] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.7/usb2/2-1/2-1.3/2-1.3:1.1/input/input12
[   13.728834] logitech 0003:046D:C517.0004: input,hiddev0,hidraw9: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.7-1.3/input1
[   13.746003] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   13.936364] scsi 21:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   13.937120] scsi 21:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   13.937870] scsi 21:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   13.938462] scsi 21:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   13.939290] sd 21:0:0:0: Attached scsi generic sg4 type 0
[   13.939687] sd 21:0:0:1: Attached scsi generic sg5 type 0
[   13.940106] sd 21:0:0:2: Attached scsi generic sg6 type 0
[   13.940304] sd 21:0:0:3: Attached scsi generic sg7 type 0
[   13.944266] sd 21:0:0:0: [sdc] Attached SCSI removable disk
[   13.944889] sd 21:0:0:1: [sdd] Attached SCSI removable disk
[   13.946141] sd 21:0:0:2: [sde] Attached SCSI removable disk
[   13.946764] sd 21:0:0:3: [sdf] Attached SCSI removable disk
[   15.294323] r8169 0000:0a:00.0: eth0: link down
[   15.294329] r8169 0000:0a:00.0: eth0: link down
[   15.294475] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.315773] type=1400 audit(1312051834.021:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1063 comm="apparmor_parser"
[   15.315788] type=1400 audit(1312051834.021:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1068 comm="apparmor_parser"
[   15.315841] type=1400 audit(1312051834.021:10): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1062 comm="apparmor_parser"
[   15.315902] type=1400 audit(1312051834.021:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/freshclam" pid=1066 comm="apparmor_parser"
[   15.580619] vboxdrv: Found 8 processor cores.
[   15.580823] vboxdrv: fAsync=0 offMin=0x273 offMax=0x14247
[   15.580865] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   15.580867] vboxdrv: Successfully loaded version 4.0.4_OSE (interface 0x00160000).
[   15.950857] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   15.952745] EXT4-fs (sda6): re-mounted. Opts: commit=0
[   17.000772] r8169 0000:0a:00.0: eth0: link up
[   17.000955] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   17.819208] scsi20 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 7.0
[   17.819210]         <Adaptec 29160B Ultra160 SCSI adapter>
[   17.819211]         aic7892: Ultra160 Wide Channel A, SCSI Id=7, 32/253 SCBs
[   17.819212] 
[   17.819481] firewire_ohci 0000:0b:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   17.875202] firewire_ohci: Added fw-ohci device 0000:0b:06.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[   17.907076] vesafb: framebuffer at 0xf5000000, mapped to 0xfb580000, using 5120k, total 5120k
[   17.907079] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[   17.907080] vesafb: scrolling: redraw
[   17.907082] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   17.907137] fbcon: VESA VGA (fb0) is primary device
[   17.907246] Console: switching to colour frame buffer device 160x64
[   17.907283] fb0: VESA VGA frame buffer device
[   17.928330] ppdev: user-space parallel port driver
[   18.183813] ioremap error for 0xbfee1000-0xbfee2000, requested 0x10, got 0x0
[   18.378648] firewire_core: created device fw0: GUID 005f3093006cf049, S400
[   19.101384] scsi 20:0:5:0: Sequential-Access Quantum  DLT4700          CD50 PQ: 0 ANSI: 2
[   19.101390] scsi target20:0:5: Beginning Domain Validation
[   19.104915] scsi target20:0:5: FAST-10 SCSI 10.0 MB/s ST (100 ns, offset 15)
[   19.106955] scsi target20:0:5: Domain Validation skipping write tests
[   19.106957] scsi target20:0:5: Ending Domain Validation
[   19.108267] scsi 20:0:5:1: Medium Changer    Quantum  TZ Media Changer CD50 PQ: 0 ANSI: 2
[   19.108271] scsi target20:0:5: FAST-10 SCSI 10.0 MB/s ST (100 ns, offset 15)
[   21.417302] st 20:0:5:0: Attached scsi tape st0
[   21.417304] st 20:0:5:0: st0: try direct i/o: yes (alignment 4 B)
[   21.417349] st 20:0:5:0: Attached scsi generic sg8 type 1
[   21.417523] scsi 20:0:5:1: Attached scsi generic sg9 type 8
[   21.420183] SCSI Media Changer driver v0.25 
[   21.422618] ch0: type #1 (mt): 0x1+1 [medium transport]
[   21.422621] ch0: type #2 (st): 0x100+7 [storage]
[   21.422622] ch0: type #3 (ie): 0x0+0 [import/export]
[   21.422624] ch0: type #4 (dt): 0x10+1 [data transfer]
[   22.975771] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   22.977531] EXT4-fs (sda6): re-mounted. Opts: commit=0
```

Later in dmesg I got:
```
[  240.952274] INFO: task mt:2159 blocked for more than 120 seconds.
[  240.952278] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  240.952281] mt              D c126740b     0  2159   2158 0x00000004
[  240.952286]  e9d25c90 00200086 e9d25c1c c126740b e9d25c1c 00200282 ea46f42c c1877680
[  240.952293]  ca98e987 0000000d ea46f428 c1877680 c1877680 f78c7680 ea46f1a0 f74b6500
[  240.952299]  f0691020 e9d25c44 e9d25c44 f07b0420 00200292 e9634840 e9d25c84 c137438f
[  240.952305] Call Trace:
[  240.952313]  [<c126740b>] ? __blk_run_queue+0x8b/0x140
[  240.952319]  [<c137438f>] ? __scsi_queue_insert+0x8f/0x110
[  240.952333]  [<f8552fc5>] ? ahc_linux_queue+0xb5/0xd0 [aic7xxx]
[  240.952340]  [<c153065d>] schedule_timeout+0x1ed/0x260
[  240.952345]  [<c126d831>] ? blk_add_timer+0x71/0xb0
[  240.952349]  [<c1531f48>] ? _raw_spin_lock_irq+0x18/0x20
[  240.952352]  [<c13736cb>] ? scsi_request_fn+0xcb/0x440
[  240.952356]  [<c15301e0>] wait_for_common+0xa0/0x130
[  240.952360]  [<c126c45f>] ? blk_execute_rq_nowait+0x6f/0xa0
[  240.952365]  [<c10534c0>] ? default_wake_function+0x0/0x20
[  240.952369]  [<c1530347>] wait_for_completion+0x17/0x20
[  240.952374]  [<f8484656>] st_do_scsi.clone.16+0xf6/0x210 [st]
[  240.952380]  [<f8484b78>] test_ready+0x88/0x150 [st]
[  240.952385]  [<f848664f>] check_tape.clone.13+0x7f/0x550 [st]
[  240.952392]  [<c10f51a6>] ? ondemand_readahead+0x126/0x210
[  240.952397]  [<f8486cae>] st_open+0x18e/0x250 [st]
[  240.952403]  [<c1136295>] chrdev_open+0xa5/0x1c0
[  240.952407]  [<c1130a91>] __dentry_open+0xc1/0x280
[  240.952411]  [<c1131dfe>] nameidata_to_filp+0x6e/0x80
[  240.952414]  [<c11361f0>] ? chrdev_open+0x0/0x1c0
[  240.952419]  [<c113f2af>] finish_open+0xaf/0x1a0
[  240.952422]  [<c113eb58>] ? do_path_lookup+0x68/0x120
[  240.952425]  [<c113f8f7>] do_filp_open+0x207/0x6e0
[  240.952431]  [<c15355a0>] ? do_page_fault+0x0/0x490
[  240.952434]  [<c1131e66>] do_sys_open+0x56/0x120
[  240.952438]  [<c1533320>] ? do_device_not_available+0x0/0x20
[  240.952441]  [<c1131f5e>] sys_open+0x2e/0x40
[  240.952445]  [<c100ab5f>] sysenter_do_call+0x12/0x28
[  321.542993] ch 20:0:5:1: Attempting to queue an ABORT message
[  321.542996] CDB: 0xb8 0x24 0x0 0x10 0x0 0x1 0x0 0x0 0x0 0xff 0x0 0x0
[  321.543018] scsi20: At time of recovery, card was not paused
[  321.543026] >>>>>>>>>>>>>>>>>> Dump Card State Begins <<<<<<<<<<<<<<<<<
[  321.543027] scsi20: Dumping Card State while idle, at SEQADDR 0x8
[  321.543030] Card was paused
[  321.543036] ACCUM = 0x4, SINDEX = 0x57, DINDEX = 0x26, ARG_2 = 0x0
[  321.543040] HCNT = 0x0 SCBPTR = 0x0
[  321.543043] SCSIPHASE[0x0] SCSISIGI[0x0] ERROR[0x0] 
[  321.543051] SCSIBUSL[0x0] LASTPHASE[0x1]:(P_BUSFREE) 
[  321.543058] SCSISEQ[0x12]:(ENAUTOATNP|ENRSELI) 
[  321.543063] SBLKCTL[0x6]:(SELWIDE|ENAB20) SCSIRATE[0x0] 
[  321.543071] SEQCTL[0x10]:(FASTMODE) SEQ_FLAGS[0xc0]:(NO_CDB_SENT|NOT_IDENTIFIED) 
[  321.543079] SSTAT0[0x0] SSTAT1[0x8]:(BUSFREE) 
[  321.543086] SSTAT2[0x0] SSTAT3[0x0] SIMODE0[0x8]:(ENSWRAP) 
[  321.543095] SIMODE1[0xa4]:(ENSCSIPERR|ENSCSIRST|ENSELTIMO) 
[  321.543100] SXFRCTL0[0x80]:(DFON) DFCNTRL[0x0] 
[  321.543107] DFSTATUS[0x89]:(FIFOEMP|HDONE|PRELOAD_AVAIL) 
[  321.543112] STACK: 0x0 0x164 0x179 0x3
[  321.543124] SCB count = 4
[  321.543126] Kernel NEXTQSCB = 3
[  321.543128] Card NEXTQSCB = 3
[  321.543129] QINFIFO entries: 
[  321.543132] Waiting Queue entries: 
[  321.543135] Disconnected Queue entries: 0:2 
[  321.543204] QOUTFIFO entries: 
[  321.543206] Sequencer Free SCB List: 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 
[  321.543264] Sequencer SCB Info: 
[  321.543266]   0 SCB_CONTROL[0x44]:(DISCONNECTED|DISCENB) 
[  321.543273] SCB_SCSIID[0x57] SCB_LUN[0x1] SCB_TAG[0x2] 
[  321.543280]   1 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[  321.543290] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[  321.543295]   2 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[  321.543305] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[  321.543311]   3 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[  321.543321] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[  321.543326]   4 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[  321.543336] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[  321.543342]   5 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[  321.543351] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[  321.543357]   6 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[  321.543367] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[  321.543372]   7 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[  321.543382] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[  321.543388]   8 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[  321.543397] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[  321.543403]   9 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[  321.543413] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[  321.543418]  10 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[  321.543428] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[  321.543434]  11 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[  321.543443] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[  321.543449]  12 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[  321.543459] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[  321.543464]  13 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[  321.543474] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[  321.543480]  14 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[  321.543489] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[  321.543495]  15 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[  321.543505] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[  321.543511]  16 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[  321.543520] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[  321.543526]  17 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[  321.543536] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[  321.543541]  18 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[  321.543551] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[  321.543557]  19 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[  321.543566] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[  321.543572]  20 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[  321.543582] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[  321.543587]  21 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[  321.543597] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[  321.543603]  22 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[  321.543612] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[  321.543618]  23 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[  321.543628] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[  321.543633]  24 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[  321.543643] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[  321.543649]  25 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[  321.543658] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[  321.543664]  26 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[  321.543674] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[  321.543680]  27 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[  321.543689] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[  321.543695]  28 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[  321.543705] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[  321.543710]  29 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[  321.543720] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[  321.543726]  30 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[  321.543735] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[  321.543741]  31 SCB_CONTROL[0x0] SCB_SCSIID[0xff]:(TWIN_CHNLB|OID|TWIN_TID) 
[  321.543751] SCB_LUN[0xff]:(SCB_XFERLEN_ODD|LID) SCB_TAG[0xff] 
[  321.543757] Pending list: 
[  321.543758]   2 SCB_CONTROL[0x40]:(DISCENB) SCB_SCSIID[0x57] 
[  321.543764] SCB_LUN[0x1] 
[  321.543766] Kernel Free SCB list: 1 0 
[  321.543769] Untagged Q(5): 2 
[  321.543772] 
[  321.543772] <<<<<<<<<<<<<<<<< Dump Card State Ends >>>>>>>>>>>>>>>>>>
[  321.543799] (scsi20:A:5:1): Device is disconnected, re-queuing SCB
[  321.543802] Recovery code sleeping
[  321.543837] (scsi20:A:5:1): Abort Message Sent
[  321.544177] (scsi20:A:5:1): SCB 2 - Abort Completed.
[  321.544296] Recovery SCB completes
[  321.544335] Recovery code awake
[  321.544337] aic7xxx_abort returns 0x2002
[  418.689379] ch0: dt 0x10: READ ELEMENT STATUS failed
[  418.689383] ch0: INITIALIZE ELEMENT STATUS, may take some time ...
[  600.742022] INFO: task tar:2664 blocked for more than 120 seconds.
[  600.742025] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  600.742028] tar             D c126740b     0  2664      1 0x00000004
[  600.742033]  e74a7c6c 00200086 e74a7bf8 c126740b e74a7bf8 00200292 e967e78c c1877680
[  600.742040]  f56f4ad6 00000061 e967e788 c1877680 c1877680 f7907680 e967e500 f74f9940
[  600.742046]  f0691020 e74a7c20 e74a7c20 f07b0420 00200296 ecb0e300 e74a7c60 c137438f
[  600.742052] Call Trace:
[  600.742060]  [<c126740b>] ? __blk_run_queue+0x8b/0x140
[  600.742066]  [<c137438f>] ? __scsi_queue_insert+0x8f/0x110
[  600.742081]  [<f8552fc5>] ? ahc_linux_queue+0xb5/0xd0 [aic7xxx]
[  600.742087]  [<c153065d>] schedule_timeout+0x1ed/0x260
[  600.742092]  [<c126d867>] ? blk_add_timer+0xa7/0xb0
[  600.742096]  [<c1531f48>] ? _raw_spin_lock_irq+0x18/0x20
[  600.742099]  [<c13736cb>] ? scsi_request_fn+0xcb/0x440
[  600.742105]  [<c15301e0>] wait_for_common+0xa0/0x130
[  600.742109]  [<c126c45f>] ? blk_execute_rq_nowait+0x6f/0xa0
[  600.742114]  [<c10534c0>] ? default_wake_function+0x0/0x20
[  600.742118]  [<c1530347>] wait_for_completion+0x17/0x20
[  600.742123]  [<f8484656>] st_do_scsi.clone.16+0xf6/0x210 [st]
[  600.742129]  [<f8484b78>] test_ready+0x88/0x150 [st]
[  600.742135]  [<f848664f>] check_tape.clone.13+0x7f/0x550 [st]
[  600.742142]  [<f8486cae>] st_open+0x18e/0x250 [st]
[  600.742147]  [<c1136295>] chrdev_open+0xa5/0x1c0
[  600.742152]  [<c1130a91>] __dentry_open+0xc1/0x280
[  600.742155]  [<c1131dfe>] nameidata_to_filp+0x6e/0x80
[  600.742159]  [<c11361f0>] ? chrdev_open+0x0/0x1c0
[  600.742163]  [<c113f2af>] finish_open+0xaf/0x1a0
[  600.742167]  [<c1531dfd>] ? _raw_spin_lock+0xd/0x10
[  600.742171]  [<c11469cd>] ? dput+0x10d/0x180
[  600.742174]  [<c113f403>] do_last+0x63/0x350
[  600.742178]  [<c113fa2b>] do_filp_open+0x33b/0x6e0
[  600.742183]  [<c15355a0>] ? do_page_fault+0x0/0x490
[  600.742187]  [<c1131e66>] do_sys_open+0x56/0x120
[  600.742190]  [<c1131f5e>] sys_open+0x2e/0x40
[  600.742194]  [<c100ab5f>] sysenter_do_call+0x12/0x28
[  720.620642] INFO: task tar:2664 blocked for more than 120 seconds.
...roughly the same thing happens again.
```

Anyone know what the problem might be?

---

