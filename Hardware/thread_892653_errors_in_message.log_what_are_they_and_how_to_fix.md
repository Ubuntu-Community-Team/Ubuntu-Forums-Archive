---
title: "errors in message.log: what are they and how to fix ?"
date: 2008-08-17
forum: Hardware
---

### Post by Browser_ice on 2008-08-17
I have 2hd : 80Gb for all O/S + 250Gb for data/backups/swap

2 days ago on a IDE cable change the 250Gb was unavailable and data got corrupted. I fixed the problem and re-installed my files on it.

But now, upon booting in my Ubuntu 8.04 for the first after this incident, I saw boot error messages. When I went to check the message.log, I saw a few error messages. Can someone tell me what they are, if they are genuine errors and what should I do ?

Those messages are referring to my first HD now. Until now, I had not seen any errors related to my first HD.  I have the same kind of messages on another Ubuntu 8.04 partition (for the office).

[added comments]
Forgot to mention this happened after I switched from flag IDE cables to rounded ones (80 connectors). I fixed the HD corrupted data by switching back to the old cable. So I think some of those error messages are referring to the ATA type not being detected ok at first.

From doing a goolge on the HD specs, I have found this : my O/S 80GB is an ATA/133 2Mb buffer, my 250Gb is an ATA/133 16Mb buffer. Both have a 40 pin/connectors gray flat cable at the moment.

To spot them, look for :
driver update warning ?  => [   40.965069] 
Driver update warning ?  => [   40.978344] 
HD problems ?  between [   42.178247] - [   50.524066]  
HD problems ?  between [  274.045955] - [  286.748639] 
Ethernet card config problem ?  => 12:46:44 

> [FONT="Courier New"][SIZE="1"]

Aug 17 12:46:35 browserice-desktop kernel: [   39.903993] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
Aug 17 12:46:35 browserice-desktop kernel: [   39.903999] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xfc08 irq 15
Aug 17 12:46:35 browserice-desktop kernel: [   40.387599] ata1.00: ATAPI: HL-DT-ST DVDRAM GSA-4163B, A102, max UDMA/33
Aug 17 12:46:35 browserice-desktop kernel: [   40.387633] ata1.01: ATAPI: LG CD-ROM CRD-8522B, 2.03, max MWDMA2
Aug 17 12:46:35 browserice-desktop kernel: [   40.559319] ata1.00: configured for UDMA/33
Aug 17 12:46:35 browserice-desktop kernel: [   40.731237] ata1.01: configured for MWDMA2
Aug 17 12:46:35 browserice-desktop kernel: [   40.903306] ata2.00: ATA-7: Maxtor 6Y080L0, YAR41VW0, max UDMA/133
Aug 17 12:46:35 browserice-desktop kernel: [   40.903312] ata2.00: 160086528 sectors, multi 16: LBA 
Aug 17 12:46:35 browserice-desktop kernel: [   40.904909] ata2.01: ATA-7: Maxtor 6L250R0, BAH41G10, max UDMA/133
Aug 17 12:46:35 browserice-desktop kernel: [   40.904913] ata2.01: 490234752 sectors, multi 16: LBA48 
Aug 17 12:46:35 browserice-desktop kernel: [   40.919157] ata2.00: configured for UDMA/133
Aug 17 12:46:35 browserice-desktop kernel: [   40.936571] ata2.01: configured for UDMA/133
Aug 17 12:46:35 browserice-desktop kernel: [   40.940403] scsi 0:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-4163B A102 PQ: 0 ANSI: 5
Aug 17 12:46:35 browserice-desktop kernel: [   40.941797] scsi 0:0:1:0: CD-ROM            LG       CD-ROM CRD-8522B 2.03 PQ: 0 ANSI: 5
Aug 17 12:46:35 browserice-desktop kernel: [   40.942283] scsi 1:0:0:0: Direct-Access     ATA      Maxtor 6Y080L0   YAR4 PQ: 0 ANSI: 5
Aug 17 12:46:35 browserice-desktop kernel: [   40.942733] scsi 1:0:1:0: Direct-Access     ATA      Maxtor 6L250R0   BAH4 PQ: 0 ANSI: 5
[COLOR="Red"]Aug 17 12:46:35 browserice-desktop kernel: [   40.965069] Driver 'sr' needs updating - please use bus_type methods
Aug 17 12:46:35 browserice-desktop kernel: [   40.978344] Driver 'sd' needs updating - please use bus_type methods[/COLOR]
Aug 17 12:46:35 browserice-desktop kernel: [   40.986065] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
Aug 17 12:46:35 browserice-desktop kernel: [   40.986075] Uniform CD-ROM driver Revision: 3.20
Aug 17 12:46:35 browserice-desktop kernel: [   40.991755] sr1: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
Aug 17 12:46:35 browserice-desktop kernel: [   40.992463] sd 1:0:0:0: [sda] 160086528 512-byte hardware sectors (81964 MB)
Aug 17 12:46:35 browserice-desktop kernel: [   40.999078] sd 1:0:0:0: [sda] Write Protect is off
Aug 17 12:46:35 browserice-desktop kernel: [   41.003669] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 17 12:46:35 browserice-desktop kernel: [   41.003784] sd 1:0:0:0: [sda] 160086528 512-byte hardware sectors (81964 MB)
Aug 17 12:46:35 browserice-desktop kernel: [   41.003804] sd 1:0:0:0: [sda] Write Protect is off
Aug 17 12:46:35 browserice-desktop kernel: [   41.003834] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 17 12:46:35 browserice-desktop kernel: [   41.003841]  sda:<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
Aug 17 12:46:35 browserice-desktop kernel: [   41.005701] sr 0:0:1:0: Attached scsi generic sg1 type 5
Aug 17 12:46:35 browserice-desktop kernel: [   41.005730] sd 1:0:0:0: Attached scsi generic sg2 type 0
Aug 17 12:46:35 browserice-desktop kernel: [   41.005757] scsi 1:0:1:0: Attached scsi generic sg3 type 0
Aug 17 12:46:35 browserice-desktop kernel: [   41.069126]          res 51/84:00:00:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
Aug 17 12:46:35 browserice-desktop kernel: [   41.069167] ata2: soft resetting link
Aug 17 12:46:35 browserice-desktop kernel: [   41.078671] usb 1-1: new low speed USB device using uhci_hcd and address 3
Aug 17 12:46:35 browserice-desktop kernel: [   41.254853] ata2.00: configured for UDMA/133
Aug 17 12:46:35 browserice-desktop kernel: [   41.258088] usb 1-1: configuration #1 chosen from 1 choice
Aug 17 12:46:35 browserice-desktop kernel: [   41.272253] ata2.01: configured for UDMA/133
Aug 17 12:46:35 browserice-desktop kernel: [   41.272288] ata2: EH complete
Aug 17 12:46:35 browserice-desktop kernel: [   41.343975]          res 51/84:00:00:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
Aug 17 12:46:35 browserice-desktop kernel: [   41.344021] ata2: soft resetting link
Aug 17 12:46:35 browserice-desktop kernel: [   41.498498] usb 1-2: new low speed USB device using uhci_hcd and address 4
Aug 17 12:46:35 browserice-desktop kernel: [   41.530608] ata2.00: configured for UDMA/133
Aug 17 12:46:35 browserice-desktop kernel: [   41.548010] ata2.01: configured for UDMA/133
Aug 17 12:46:35 browserice-desktop kernel: [   41.548037] ata2: EH complete
Aug 17 12:46:35 browserice-desktop kernel: [   41.610456]          res 51/84:00:00:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
Aug 17 12:46:35 browserice-desktop kernel: [   41.610489] ata2: soft resetting link
Aug 17 12:46:35 browserice-desktop kernel: [   41.678671] usb 1-2: configuration #1 chosen from 1 choice
Aug 17 12:46:35 browserice-desktop kernel: [   41.681688] usbcore: registered new interface driver hiddev
Aug 17 12:46:35 browserice-desktop kernel: [   41.695920] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:10.0/usb1/1-1/1-1:1.0/input/input1
Aug 17 12:46:35 browserice-desktop kernel: [   41.706150] input,hidraw0: USB HID v1.10 Keyboard [Logitech Logitech USB Keyboard] on usb-0000:00:10.0-1
Aug 17 12:46:35 browserice-desktop kernel: [   41.737604] input: Logitech Logitech USB Keyboard as /devices/pci0000:00/0000:00:10.0/usb1/1-1/1-1:1.1/input/input2
Aug 17 12:46:35 browserice-desktop kernel: [   41.746082] input,hidraw1: USB HID v1.10 Device [Logitech Logitech USB Keyboard] on usb-0000:00:10.0-1
Aug 17 12:46:35 browserice-desktop kernel: [   41.797136] input: Microsoft Microsoft Wireless Optical Mouse® 1.00 as /devices/pci0000:00/0000:00:10.0/usb1/1-2/1-2:1.0/input/input3
Aug 17 12:46:35 browserice-desktop kernel: [   41.798384] ata2.00: configured for UDMA/133
Aug 17 12:46:35 browserice-desktop kernel: [   41.806041] input,hidraw2: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Mouse® 1.00] on usb-0000:00:10.0-2
Aug 17 12:46:35 browserice-desktop kernel: [   41.806071] usbcore: registered new interface driver usbhid
Aug 17 12:46:35 browserice-desktop kernel: [   41.806078] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Aug 17 12:46:35 browserice-desktop kernel: [   41.815848] ata2.01: configured for UDMA/133
Aug 17 12:46:35 browserice-desktop kernel: [   41.815884] ata2: EH complete
Aug 17 12:46:35 browserice-desktop kernel: [   41.885305] ata2.00: limiting speed to UDMA/100:PIO4
Aug 17 12:46:35 browserice-desktop kernel: [   41.885334]          res 51/84:00:00:00:00/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
Aug 17 12:46:35 browserice-desktop kernel: [   41.885379] ata2: soft resetting link
Aug 17 12:46:35 browserice-desktop kernel: [   42.070115] ata2.00: configured for UDMA/100
Aug 17 12:46:35 browserice-desktop kernel: [   42.087553] ata2.01: configured for UDMA/133
Aug 17 12:46:35 browserice-desktop kernel: [   42.087579] ata2: EH complete
Aug 17 12:46:35 browserice-desktop kernel: [   42.110280]  sda1 sda2 <<5>sd 1:0:0:0: [sda] 160086528 512-byte hardware sectors (81964 MB)
Aug 17 12:46:35 browserice-desktop kernel: [   42.119546] sd 1:0:0:0: [sda] Write Protect is off
Aug 17 12:46:35 browserice-desktop kernel: [   42.119579] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 17 12:46:35 browserice-desktop kernel: [   42.119609] sd 1:0:0:0: [sda] 160086528 512-byte hardware sectors (81964 MB)
Aug 17 12:46:35 browserice-desktop kernel: [   42.119625] sd 1:0:0:0: [sda] Write Protect is off
Aug 17 12:46:35 browserice-desktop kernel: [   42.119652] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 17 12:46:35 browserice-desktop kernel: [   42.119660]  sda5 sda6 sda7 sda8 sda9 >
Aug 17 12:46:35 browserice-desktop kernel: [   42.176413] sd 1:0:0:0: [sda] Attached SCSI disk
Aug 17 12:46:35 browserice-desktop kernel: [   42.178058] sd 1:0:1:0: [sdb] 490234752 512-byte hardware sectors (251000 MB)
Aug 17 12:46:35 browserice-desktop kernel: [   42.178080] sd 1:0:1:0: [sdb] Write Protect is off
Aug 17 12:46:35 browserice-desktop kernel: [   42.178111] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 17 12:46:35 browserice-desktop kernel: [   42.178197] sd 1:0:1:0: [sdb] 490234752 512-byte hardware sectors (251000 MB)
Aug 17 12:46:35 browserice-desktop kernel: [   42.178213] sd 1:0:1:0: [sdb] Write Protect is off
Aug 17 12:46:35 browserice-desktop kernel: [   42.178241] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[COLOR="Red"]Aug 17 12:46:35 browserice-desktop kernel: [   42.178247]  sdb:<3>ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
Aug 17 12:46:35 browserice-desktop kernel: [   42.195905]          res 51/84:08:00:00:00/00:00:00:00:00/f0 Emask 0x10 (ATA bus error)
Aug 17 12:46:35 browserice-desktop kernel: [   42.195949] ata2: soft resetting link
Aug 17 12:46:35 browserice-desktop kernel: [   42.381853] ata2.00: configured for UDMA/100
Aug 17 12:46:35 browserice-desktop kernel: [   42.399233] ata2.01: configured for UDMA/133
Aug 17 12:46:35 browserice-desktop kernel: [   42.399250] ata2: EH complete
Aug 17 12:46:35 browserice-desktop kernel: [   42.404080]          res 51/84:08:00:00:00/00:00:00:00:00/f0 Emask 0x10 (ATA bus error)
Aug 17 12:46:35 browserice-desktop kernel: [   42.404110] ata2: soft resetting link
Aug 17 12:46:35 browserice-desktop kernel: [   42.589650] ata2.00: configured for UDMA/100
Aug 17 12:46:35 browserice-desktop kernel: [   42.607060] ata2.01: configured for UDMA/133
Aug 17 12:46:35 browserice-desktop kernel: [   42.607076] ata2: EH complete
Aug 17 12:46:35 browserice-desktop kernel: [   42.607173] sd 1:0:0:0: [sda] 160086528 512-byte hardware sectors (81964 MB)
Aug 17 12:46:35 browserice-desktop kernel: [   42.612261]          res 51/84:08:00:00:00/00:00:00:00:00/f0 Emask 0x10 (ATA bus error)
Aug 17 12:46:35 browserice-desktop kernel: [   42.612291] ata2: soft resetting link
Aug 17 12:46:35 browserice-desktop kernel: [   42.797474] ata2.00: configured for UDMA/100
Aug 17 12:46:35 browserice-desktop kernel: [   42.814851] ata2.01: configured for UDMA/133
Aug 17 12:46:35 browserice-desktop kernel: [   42.814867] ata2: EH complete
Aug 17 12:46:35 browserice-desktop kernel: [   42.814964] sd 1:0:0:0: [sda] Write Protect is off
Aug 17 12:46:35 browserice-desktop kernel: [   42.837080] ata2.01: limiting speed to UDMA/100:PIO4
Aug 17 12:46:35 browserice-desktop kernel: [   42.837102]          res 51/84:08:00:00:00/00:00:00:00:00/f0 Emask 0x10 (ATA bus error)
Aug 17 12:46:35 browserice-desktop kernel: [   42.837132] ata2: soft resetting link
Aug 17 12:46:35 browserice-desktop kernel: [   43.025283] ata2.00: configured for UDMA/100
Aug 17 12:46:35 browserice-desktop kernel: [   43.042684] ata2.01: configured for UDMA/100
Aug 17 12:46:35 browserice-desktop kernel: [   43.042700] ata2: EH complete
Aug 17 12:46:35 browserice-desktop kernel: [   43.046020]  sdb1 sdb2 sdb3 sdb4
Aug 17 12:46:35 browserice-desktop kernel: [   43.046112] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 17 12:46:35 browserice-desktop kernel: [   43.046216] sd 1:0:1:0: [sdb] 490234752 512-byte hardware sectors (251000 MB)
Aug 17 12:46:35 browserice-desktop kernel: [   43.046236] sd 1:0:1:0: [sdb] Write Protect is off
Aug 17 12:46:35 browserice-desktop kernel: [   43.046264] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 17 12:46:35 browserice-desktop kernel: [   43.046290] sd 1:0:0:0: [sda] 160086528 512-byte hardware sectors (81964 MB)
Aug 17 12:46:35 browserice-desktop kernel: [   43.046306] sd 1:0:0:0: [sda] Write Protect is off
Aug 17 12:46:35 browserice-desktop kernel: [   43.046333] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 17 12:46:35 browserice-desktop kernel: [   43.046358] sd 1:0:1:0: [sdb] 490234752 512-byte hardware sectors (251000 MB)
Aug 17 12:46:35 browserice-desktop kernel: [   43.046373] sd 1:0:1:0: [sdb] Write Protect is off
Aug 17 12:46:35 browserice-desktop kernel: [   43.046400] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 17 12:46:35 browserice-desktop kernel: [   43.046572] sd 1:0:1:0: [sdb] Attached SCSI disk
Aug 17 12:46:35 browserice-desktop kernel: [   49.514354]          res 51/84:00:20:5a:b1/00:00:00:00:00/e3 Emask 0x10 (ATA bus error)
Aug 17 12:46:35 browserice-desktop kernel: [   49.514533] ata2: soft resetting link
Aug 17 12:46:35 browserice-desktop kernel: [   49.699400] ata2.00: configured for UDMA/100
Aug 17 12:46:35 browserice-desktop kernel: [   49.716795] ata2.01: configured for UDMA/100
Aug 17 12:46:35 browserice-desktop kernel: [   49.716809] ata2: EH complete
Aug 17 12:46:35 browserice-desktop kernel: [   49.780826]          res 51/84:00:20:5a:b1/00:00:00:00:00/e3 Emask 0x10 (ATA bus error)
Aug 17 12:46:35 browserice-desktop kernel: [   49.780988] ata2: soft resetting link
Aug 17 12:46:35 browserice-desktop kernel: [   49.967172] ata2.00: configured for UDMA/100
Aug 17 12:46:35 browserice-desktop kernel: [   49.984557] ata2.01: configured for UDMA/100
Aug 17 12:46:35 browserice-desktop kernel: [   49.984565] ata2: EH complete
Aug 17 12:46:35 browserice-desktop kernel: [   50.047339]          res 51/84:00:20:5a:b1/00:00:00:00:00/e3 Emask 0x10 (ATA bus error)
Aug 17 12:46:35 browserice-desktop kernel: [   50.047500] ata2: soft resetting link
Aug 17 12:46:35 browserice-desktop kernel: [   50.234935] ata2.00: configured for UDMA/100
Aug 17 12:46:35 browserice-desktop kernel: [   50.252298] ata2.01: configured for UDMA/100
Aug 17 12:46:35 browserice-desktop kernel: [   50.252305] ata2: EH complete
Aug 17 12:46:35 browserice-desktop kernel: [   50.322090] ata2.00: limiting speed to UDMA/33:PIO4
Aug 17 12:46:35 browserice-desktop kernel: [   50.322198]          res 51/84:00:20:5a:b1/00:00:00:00:00/e3 Emask 0x10 (ATA bus error)
Aug 17 12:46:35 browserice-desktop kernel: [   50.322359] ata2: soft resetting link
Aug 17 12:46:35 browserice-desktop kernel: [   50.506691] ata2.00: configured for UDMA/33
Aug 17 12:46:35 browserice-desktop kernel: [   50.524059] ata2.01: configured for UDMA/100
Aug 17 12:46:35 browserice-desktop kernel: [   50.524066] ata2: EH complete[/COLOR]
. . .
. . .
Aug 17 12:46:42 browserice-desktop kernel: [   80.049205] [fglrx] Internal AGP support requested, but kernel AGP support active.
Aug 17 12:46:42 browserice-desktop kernel: [   80.049219] [fglrx] Have to use kernel AGP support to avoid conflicts.
Aug 17 12:46:42 browserice-desktop kernel: [   80.049227] [fglrx] AGP detected, AgpState   = 0x1f000a1b (hardware caps of chipset)
Aug 17 12:46:42 browserice-desktop kernel: [   80.050231] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
Aug 17 12:46:42 browserice-desktop kernel: [   80.050514] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
Aug 17 12:46:42 browserice-desktop kernel: [   80.050815] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
Aug 17 12:46:42 browserice-desktop kernel: [   80.051086] [fglrx] AGP enabled,  AgpCommand = 0x1f000312 (selected caps)
Aug 17 12:46:42 browserice-desktop kernel: [   80.056244] [fglrx] GART Table is not in FRAME_BUFFER range 
Aug 17 12:46:42 browserice-desktop kernel: [   80.056262] [fglrx] Reserve Block - 0 offset =  0X0 length = 0X40000
Aug 17 12:46:42 browserice-desktop kernel: [   80.056267] [fglrx] Reserve Block - 1 offset =  0X7fff000 length = 0X1000
Aug 17 12:46:42 browserice-desktop kernel: [   80.210111] [fglrx] interrupt source 20008000 successfully enabled
Aug 17 12:46:42 browserice-desktop kernel: [   80.210124] [fglrx] enable ID = 0x00000004
Aug 17 12:46:42 browserice-desktop kernel: [   80.210667] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
Aug 17 12:46:42 browserice-desktop kernel: [   80.211023] [fglrx] interrupt source 10000000 successfully enabled
Aug 17 12:46:42 browserice-desktop kernel: [   80.211029] [fglrx] enable ID = 0x00000005
Aug 17 12:46:42 browserice-desktop kernel: [   80.211386] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[COLOR="Red"]Aug 17 12:46:44 browserice-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Aug 17 12:46:44 browserice-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Aug 17 12:46:44 browserice-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Aug 17 12:46:44 browserice-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu[/COLOR]
Aug 17 12:46:45 browserice-desktop kernel: [   82.984932] NET: Registered protocol family 10
Aug 17 12:46:45 browserice-desktop kernel: [   82.985639] lo: Disabled Privacy Extensions
[COLOR="Red"]Aug 17 12:49:56 browserice-desktop kernel: [  274.045955] end_request: I/O error, dev fd0, sector 0
Aug 17 12:49:56 browserice-desktop kernel: [  274.073930] end_request: I/O error, dev fd0, sector 0
Aug 17 12:50:08 browserice-desktop kernel: [  285.883723]          res 51/84:2a:61:7f:92/00:00:00:00:00/f4 Emask 0x10 (ATA bus error)
Aug 17 12:50:08 browserice-desktop kernel: [  285.883769] ata2: soft resetting link
Aug 17 12:50:08 browserice-desktop kernel: [  286.071748] ata2.00: configured for UDMA/33
Aug 17 12:50:08 browserice-desktop kernel: [  286.090442] ata2.01: configured for UDMA/100
Aug 17 12:50:08 browserice-desktop kernel: [  286.090475] ata2: EH complete
Aug 17 12:50:08 browserice-desktop kernel: [  286.098730]          res 51/84:2a:61:7f:92/00:00:00:00:00/f4 Emask 0x10 (ATA bus error)
Aug 17 12:50:08 browserice-desktop kernel: [  286.098776] ata2: soft resetting link
Aug 17 12:50:08 browserice-desktop kernel: [  286.287572] ata2.00: configured for UDMA/33
Aug 17 12:50:08 browserice-desktop kernel: [  286.305836] ata2.01: configured for UDMA/100
Aug 17 12:50:08 browserice-desktop kernel: [  286.305872] ata2: EH complete
Aug 17 12:50:08 browserice-desktop kernel: [  286.307789] sd 1:0:0:0: [sda] 160086528 512-byte hardware sectors (81964 MB)
Aug 17 12:50:08 browserice-desktop kernel: [  286.331018]          res 51/84:2a:61:7f:92/00:00:00:00:00/f4 Emask 0x10 (ATA bus error)
Aug 17 12:50:08 browserice-desktop kernel: [  286.331063] ata2: soft resetting link
Aug 17 12:50:09 browserice-desktop kernel: [  286.519405] ata2.00: configured for UDMA/33
Aug 17 12:50:09 browserice-desktop kernel: [  286.537594] ata2.01: configured for UDMA/100
Aug 17 12:50:09 browserice-desktop kernel: [  286.537627] ata2: EH complete
Aug 17 12:50:09 browserice-desktop kernel: [  286.538066] sd 1:0:0:0: [sda] Write Protect is off
Aug 17 12:50:09 browserice-desktop kernel: [  286.547585] ata2.01: limiting speed to UDMA/33:PIO4
Aug 17 12:50:09 browserice-desktop kernel: [  286.547619]          res 51/84:2a:61:7f:92/00:00:00:00:00/f4 Emask 0x10 (ATA bus error)
Aug 17 12:50:09 browserice-desktop kernel: [  286.547664] ata2: soft resetting link
Aug 17 12:50:09 browserice-desktop kernel: [  286.731413] ata2.00: configured for UDMA/33
Aug 17 12:50:09 browserice-desktop kernel: [  286.748603] ata2.01: configured for UDMA/33
Aug 17 12:50:09 browserice-desktop kernel: [  286.748639] ata2: EH complete[/COLOR]
Aug 17 12:50:09 browserice-desktop kernel: [  286.756212] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 17 12:50:09 browserice-desktop kernel: [  286.765789] sd 1:0:1:0: [sdb] 490234752 512-byte hardware sectors (251000 MB)
Aug 17 12:50:09 browserice-desktop kernel: [  286.766474] sd 1:0:1:0: [sdb] Write Protect is off
Aug 17 12:50:09 browserice-desktop kernel: [  286.766520] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 17 12:50:09 browserice-desktop kernel: [  286.766557] sd 1:0:0:0: [sda] 160086528 512-byte hardware sectors (81964 MB)
Aug 17 12:50:09 browserice-desktop kernel: [  286.766574] sd 1:0:0:0: [sda] Write Protect is off
Aug 17 12:50:09 browserice-desktop kernel: [  286.766601] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Aug 17 12:50:09 browserice-desktop kernel: [  286.766627] sd 1:0:1:0: [sdb] 490234752 512-byte hardware sectors (251000 MB)
Aug 17 12:50:09 browserice-desktop kernel: [  286.766642] sd 1:0:1:0: [sdb] Write Protect is off
Aug 17 12:50:09 browserice-desktop kernel: [  286.766668] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[/SIZE][/FONT]


---

### Post by Browser_ice on 2008-08-17
Here are some infos about my HD drives :

> sudo hdparm -cudagiI /dev/sda
[sudo] password for browserice: 

/dev/sda:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 readahead     = 256 (on)
 geometry      = 9964/255/63, sectors = 160086528, start = 0

 Model=Maxtor 6Y080L0                          , FwRev=YAR41VW0, SerialNo=Y30BYEAE            
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=57
 BuffType=DualPortCache, BuffSize=2048kB, MaxMultSect=16, MultSect=?16?
 CurCHS=4047/16/255, CurSects=16511760, LBA=yes, LBAsects=160086528
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 udma3 udma4 udma5 udma6 
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-7 T13 1532D revision 0:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode


ATA device, with non-removable media
	Model Number:       Maxtor 6Y080L0                          
	Serial Number:      Y30BYEAE            
	Firmware Revision:  YAR41VW0
Standards:
	Used: ATA/ATAPI-7 T13 1532D revision 0 
	Supported: 7 6 5 4 
Configuration:
	Logical		max	current
	cylinders	16383	4047
	heads		16	16
	sectors/track	63	255
	--
	CHS current addressable sectors:   16511760
	LBA    user addressable sectors:  160086528
	device size with M = 1024*1024:       78167 MBytes
	device size with M = 1000*1000:       81964 MBytes (81 GB)
Capabilities:
	LBA, IORDY(can be disabled)
	Standby timer values: spec'd by Standard, no device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
	Advanced power management level: disabled
	Recommended acoustic management value: 192, current value: 254
	DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2 udma3 udma4 udma5 udma6 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	    	Security Mode feature set
	   *	Power Management feature set
	   *	Write cache
	   *	Look-ahead
	   *	Host Protected Area feature set
	   *	WRITE_VERIFY command
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	NOP cmd
	   *	DOWNLOAD_MICROCODE
	    	Advanced Power Management feature set
	    	SET_MAX security extension
	   *	Automatic Acoustic Management feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
	not	frozen
	not	expired: security count
	not	supported: enhanced erase
HW reset results:
	CBLID- above Vih
	Device num = 0 determined by the jumper
Checksum: correct


> sudo hdparm -cudagiI /dev/sdb

/dev/sdb:
 IO_support    =  0 (default) 
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 readahead     = 256 (on)
 geometry      = 30515/255/63, sectors = 490234752, start = 0

 Model=Maxtor 6L250R0                          , FwRev=BAH41G10, SerialNo=L596PT9G            
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=57
 BuffType=DualPortCache, BuffSize=16384kB, MaxMultSect=16, MultSect=?16?
 CurCHS=4047/16/255, CurSects=16511760, LBA=yes, LBAsects=490234752
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 udma3 udma4 udma5 udma6 
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-7 T13 1532D revision 0:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode


ATA device, with non-removable media
	Model Number:       Maxtor 6L250R0                          
	Serial Number:      L596PT9G            
	Firmware Revision:  BAH41G10
Standards:
	Used: ATA/ATAPI-7 T13 1532D revision 0 
	Supported: 7 6 5 4 & some of 8
Configuration:
	Logical		max	current
	cylinders	16383	4047
	heads		16	16
	sectors/track	63	255
	--
	CHS current addressable sectors:   16511760
	LBA    user addressable sectors:  268435455
	LBA48  user addressable sectors:  490234752
	device size with M = 1024*1024:      239372 MBytes
	device size with M = 1000*1000:      251000 MBytes (251 GB)
Capabilities:
	LBA, IORDY(can be disabled)
	Standby timer values: spec'd by Standard, no device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 16
	Advanced power management level: disabled
	Recommended acoustic management value: 192, current value: 254
	DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2 udma3 udma4 udma5 udma6 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	    	Security Mode feature set
	   *	Power Management feature set
	   *	Write cache
	   *	Look-ahead
	   *	Host Protected Area feature set
	   *	WRITE_VERIFY command
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	NOP cmd
	   *	DOWNLOAD_MICROCODE
	    	Advanced Power Management feature set
	    	SET_MAX security extension
	   *	Automatic Acoustic Management feature set
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	    	Media Card Pass-Through
	   *	General Purpose Logging feature set
	   *	WRITE_{DMA|MULTIPLE}_FUA_EXT
	   *	URG for READ_STREAM[_DMA]_EXT
	   *	URG for WRITE_STREAM[_DMA]_EXT
	   *	SMART Command Transport (SCT) feature set
	   *	SCT Data Tables (AC5)
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
	not	frozen
	not	expired: security count
	not	supported: enhanced erase
HW reset results:
	CBLID- above Vih
	Device num = 1 determined by the jumper
Checksum: correct


> 00:11.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06) (prog-if 8a [Master SecP PriP])
	Subsystem: Micro-Star International Co., Ltd. Unknown device [1462:7120]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32
	Interrupt: pin A routed to IRQ 255
	Region 0: [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	Region 1: [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	Region 2: [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	Region 3: [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	Region 4: I/O ports at fc00 [size=16]
	Capabilities: [c0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-


My MB specs says:
>      The mainboard has a 32-bit Enhanced PCI IDE and Ultra DMA 33/66/
100/133 controller that provides PIO mode 0~4, Bus Master, and Ultra DMA
33/66/100/133 function


And my booting screen says both HD are Ultra DMA 2. This matches which UDMA ?  66 ???

---

### Post by cariboo on 2008-08-17
Where you getting any of these errors before your cable change?

Jim

---

