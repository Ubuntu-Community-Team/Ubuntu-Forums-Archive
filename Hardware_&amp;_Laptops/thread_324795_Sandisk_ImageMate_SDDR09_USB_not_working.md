---
title: "Sandisk ImageMate SDDR09 USB not working"
date: 2006-12-24
forum: Hardware &amp; Laptops
---

### Post by xgiannak on 2006-12-24
Strangely enough, 
I cannot manage to plug my card reader on Ubuntu 6.06 LTS, as detailed below.
It was working fine on my older RedHat 9.0, but inbetween, a lot of things happen (devices to begin with, I cannot find /dev/sda anymore).
Redhat log is below.
Thanks for any help, and merry christmas
xavier g.

UBUNTU LOG
=============

Nov 19 23:03:17 localhost kernel: [17401031.380000] usb 4-2: new full speed USB device using uhci_hcd and address 27
Nov 19 23:03:17 localhost kernel: [17401031.532000] scsi8 : SCSI emulation for USB Mass Storage devices
Nov 19 23:03:22 localhost kernel: [17401036.532000]   Vendor: Sandisk0  Model: ImageMate SDDR09  Rev: 0100
Nov 19 23:03:22 localhost kernel: [17401036.532000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Nov 19 23:03:26 localhost kernel: [17401040.312000] usb 4-2: reset full speed USB device using uhci_hcd and address 27
Nov 19 23:03:26 localhost kernel: [17401040.872000] usb 4-2: reset full speed USB device using uhci_hcd and address 27
Nov 19 23:03:27 localhost kernel: [17401041.432000] usb 4-2: reset full speed USB device using uhci_hcd and address 27
Nov 19 23:03:27 localhost kernel: [17401041.952000] usb 4-2: reset full speed USB device using uhci_hcd and address 27
Nov 19 23:03:28 localhost kernel: [17401042.360000] usb 4-2: USB disconnect, address 27
Nov 19 23:03:28 localhost kernel: [17401042.360000] sda : READ CAPACITY failed.
Nov 19 23:03:28 localhost kernel: [17401042.360000] sda : status=0, message=00, host=1, driver=00 
Nov 19 23:03:28 localhost kernel: [17401042.360000] sda : sense not available. 
Nov 19 23:03:28 localhost kernel: [17401042.360000] sda: Write Protect is off
Nov 19 23:03:28 localhost kernel: [17401042.372000] sda : READ CAPACITY failed.
Nov 19 23:03:28 localhost kernel: [17401042.372000] sda : status=0, message=00, host=1, driver=00 
Nov 19 23:03:28 localhost kernel: [17401042.372000] sda : sense not available. 
Nov 19 23:03:28 localhost kernel: [17401042.372000] sda: Write Protect is off
Nov 19 23:03:28 localhost kernel: [17401042.384000] sda : READ CAPACITY failed.
Nov 19 23:03:28 localhost kernel: [17401042.384000] sda : status=0, message=00, host=1, driver=00 
Nov 19 23:03:28 localhost kernel: [17401042.384000] sda : sense not available. 
Nov 19 23:03:28 localhost kernel: [17401042.384000] sda: Write Protect is off
Nov 19 23:03:28 localhost kernel: [17401042.384000]  sda:<3>Buffer I/O error on device sda, logical block 0
Nov 19 23:03:28 localhost kernel: [17401042.384000]  unable to read partition table
Nov 19 23:03:28 localhost kernel: [17401042.388000] sd 8:0:0:0: Attached scsi removable disk sda
Nov 19 23:03:28 localhost kernel: [17401042.388000] sd 8:0:0:0: Attached scsi generic sg1 type 0
Nov 19 23:03:28 localhost kernel: [17401042.512000] usb 4-2: new full speed USB device using uhci_hcd and address 28
Nov 19 23:03:29 localhost kernel: [17401043.072000] usb 4-2: new full speed USB device using uhci_hcd and address 29
Nov 19 23:03:29 localhost kernel: [17401043.632000] usb 4-2: new full speed USB device using uhci_hcd and address 30
Nov 19 23:03:30 localhost kernel: [17401044.152000] usb 4-2: new full speed USB device using uhci_hcd and address 31


REDHAT LOG
============
Nov 20 22:00:10 linuxav kernel: hub.c: new USB device 00:10.3-1, assigned address 4
Nov 20 22:00:10 linuxav kernel: usb.c: USB device 4 (vend/prod 0x4e6/0x3) is not claimed by any active driver.
Nov 20 22:00:13 linuxav /etc/hotplug/usb.agent: Setup usb-storage for USB product 4e6/3/100
Nov 20 22:00:13 linuxav kernel: Initializing USB Mass Storage driver...
Nov 20 22:00:13 linuxav kernel: usb.c: registered new driver usb-storage
Nov 20 22:00:13 linuxav kernel: scsi1 : SCSI emulation for USB Mass Storage devices
Nov 20 22:00:13 linuxav kernel:   Vendor: Sandisk   Model: ImageMate SDDR09  Rev: 0100
Nov 20 22:00:13 linuxav kernel:   Type:   Direct-Access                      ANSI SCSI revision: 02
Nov 20 22:00:13 linuxav kernel: Attached scsi removable disk sda at scsi1, channel 0, id 0, lun 0
Nov 20 22:00:17 linuxav kernel: usb-uhci.c: interrupt, status 3, frame# 989
Nov 20 22:00:17 linuxav kernel: SCSI device sda: 8192 512-byte hdwr sectors (4 MB)
Nov 20 22:00:17 linuxav kernel: sda: Write Protect is on
Nov 20 22:00:17 linuxav kernel:  sda: sda1
Nov 20 22:00:17 linuxav kernel: USB Mass Storage support registered.
Nov 20 22:00:18 linuxav devlabel: devlabel service started/restarted

---

