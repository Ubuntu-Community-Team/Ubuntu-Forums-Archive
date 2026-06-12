---
title: "unstable internal card reader operation"
date: 2009-06-12
forum: Hardware
---

### Post by lvm on 2009-06-12
hardy 64, nforce 430 motherboard (Gigabyte GA-M61P-S3). Internal card reader  identified as

Bus 001 Device 006: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)

works very unreliably with cards - transfer rate is well below 100k/sec, sometimes not ready errors pop up. What baffles me is that USB 2.0 port on this reader works just fine. When the reader is plugged into a different PC with intel chipset and running windows it also works fine - cards included. Any ideas?

Some logs:

```

# grep -i usb<dmesg
[   93.997664] usbcore: registered new interface driver usbfs
[   93.997691] usbcore: registered new interface driver hub
[   93.997725] usbcore: registered new device driver usb
[   94.000699] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[   94.003812] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   94.014663] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   94.014807] usb usb1: configuration #1 chosen from 1 choice
[   94.014834] hub 1-0:1.0: USB hub found
[   94.119479] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[   94.178035] usb usb2: configuration #1 chosen from 1 choice
[   94.178067] hub 2-0:1.0: USB hub found
[   94.574386] usb 1-9: new high speed USB device using ehci_hcd and address 3
[   94.704594] usb 1-9: configuration #1 chosen from 1 choice
[   95.005899] usb 2-3: new low speed USB device using ohci_hcd and address 2
[   95.230333] usb 2-3: configuration #1 chosen from 1 choice
[   95.237653] usbcore: registered new interface driver libusual
[   95.242915] Initializing USB Mass Storage driver...
[   95.243006] scsi2 : SCSI emulation for USB Mass Storage devices
[   95.243082] usbcore: registered new interface driver usb-storage
[   95.243086] USB Mass Storage support registered.
[   95.243253] usb-storage: device found at 3
[   95.243256] usb-storage: waiting for device to settle before scanning
[   95.249629] usbcore: registered new interface driver hiddev
[   96.669636] hiddev96hidraw0: USB HID v1.10 Device [American Power Conversion Smart-UPS 1000 FW:652.18.I USB FW:7.3] on usb-0000:00:02.0-3
[   96.669657] usbcore: registered new interface driver usbhid
[   96.669662] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[  100.238536] usb-storage: device scan complete
[  100.239143] scsi 2:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[  100.239635] scsi 2:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[  100.240134] scsi 2:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[  100.240632] scsi 2:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0

```

Looks fine to me, but then it start filling up syslog with

```

Jun 12 14:00:28 server kernel: [488426.352596] usb 1-9: reset high speed USB device using ehci_hcd and address 6
Jun 12 14:01:42 server kernel: [488458.510969] usb 1-9: reset high speed USB device using ehci_hcd and address 6
Jun 12 14:02:01 server kernel: [488466.767305] usb 1-9: reset high speed USB device using ehci_hcd and address 6
Jun 12 14:04:13 server kernel: [488524.130184] usb 1-9: reset high speed USB device using ehci_hcd and address 6
Jun 12 14:04:15 server kernel: [488524.996253] usb 1-9: reset high speed USB device using ehci_hcd and address 6
Jun 12 14:04:21 server kernel: [488527.603503] usb 1-9: reset high speed USB device using ehci_hcd and address 6
Jun 12 14:06:33 server kernel: [488584.968238] usb 1-9: reset high speed USB device using ehci_hcd and address 6

```

And when the card is inserted

```

Jun 12 13:47:32 server kernel: [488085.306301] sd 11:0:0:0: [sda] 494080 512-byte hardware sectors (253 MB)
Jun 12 13:47:32 server kernel: [488085.306952] sd 11:0:0:0: [sda] Write Protect is off
Jun 12 13:47:32 server kernel: [488085.306955] sd 11:0:0:0: [sda] Mode Sense: 03 00 00 00
Jun 12 13:47:32 server kernel: [488085.306957] sd 11:0:0:0: [sda] Assuming drive cache: write through
Jun 12 13:47:32 server kernel: [488085.307711] sd 11:0:0:0: [sda] 494080 512-byte hardware sectors (253 MB)
Jun 12 13:47:32 server kernel: [488085.308199] sd 11:0:0:0: [sda] Write Protect is off
Jun 12 13:47:32 server kernel: [488085.308202] sd 11:0:0:0: [sda] Mode Sense: 03 00 00 00
Jun 12 13:47:32 server kernel: [488085.308204] sd 11:0:0:0: [sda] Assuming drive cache: write through
Jun 12 13:47:32 server kernel: [488085.308209]  sda: sda1
Jun 12 13:47:33 server kernel: [488085.561802] usb 1-9: reset high speed USB device using ehci_hcd and address 6
Jun 12 13:47:33 server kernel: [488085.861220] usb 1-9: reset high speed USB device using ehci_hcd and address 6
Jun 12 13:47:34 server kernel: [488086.160209] usb 1-9: reset high speed USB device using ehci_hcd and address 6
Jun 12 13:47:35 server kernel: [488086.460935] usb 1-9: reset high speed USB device using ehci_hcd and address 6
Jun 12 13:47:35 server kernel: [488086.746012] usb 1-9: reset high speed USB device using ehci_hcd and address 6
Jun 12 13:47:35 server kernel: [488086.804147] sd 11:0:0:0: [sda] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Jun 12 13:47:35 server kernel: [488086.804153] end_request: I/O error, dev sda, sector 494061
Jun 12 13:47:35 server kernel: [488086.804158] Buffer I/O error on device sda1, logical block 493960
Jun 12 13:47:35 server kernel: [488086.804165] Buffer I/O error on device sda1, logical block 493961
Jun 12 13:47:35 server kernel: [488086.804169] Buffer I/O error on device sda1, logical block 493962
Jun 12 13:47:35 server kernel: [488086.804172] Buffer I/O error on device sda1, logical block 493963
Jun 12 13:47:35 server kernel: [488086.804175] Buffer I/O error on device sda1, logical block 493964
Jun 12 13:47:35 server kernel: [488086.804179] Buffer I/O error on device sda1, logical block 493965

and so on, and so forth...

```

I personally think it is a motherboard/chipset problem but still give it a try here.

---

