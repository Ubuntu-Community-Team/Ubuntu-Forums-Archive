---
title: "Sddr-09"
date: 2006-09-04
forum: Hardware &amp; Laptops
---

### Post by mkosmo on 2006-09-04
Trying to read a smartmedia card with a SanDisk ImageMate USB... Plug it in, there are two lights.  Green and amber.  Both come on.  While both are on, lsusb shows this:

kosmo@blade:~$ lsusb
Bus 005 Device 002: ID 413c:a005 Dell Computer Corp.
Bus 005 Device 003: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 0781:0200 SanDisk Corp. SDDR-09 (SSFDC) ImageMate SmartMedia Reader [eusb]
Bus 002 Device 001: ID 0000:0000

Wait a few seconds, amber goes out... lsusb reads this:

kosmo@blade:~$ lsusb
Bus 005 Device 002: ID 413c:a005 Dell Computer Corp.
Bus 005 Device 003: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000

A few minutes later, green goes out.  I need to be able to mount this to read the pictures off of it.  Anybody have any ideas?

Thanks.


EDIT:  Figured some dmesg would be in order:

[17183216.508000] usb-storage: device found at 17
[17183216.508000] usb-storage: waiting for device to settle before scanning
[17183221.508000]   Vendor: Sandisk0  Model: ImageMate SDDR-0  Rev: 0100
[17183221.508000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17183225.304000] usb 2-1: reset full speed USB device using uhci_hcd and address 17
[17183225.420000] usb 2-1: device descriptor read/64, error -32
[17183225.640000] usb 2-1: device descriptor read/64, error -32
[17183225.856000] usb 2-1: reset full speed USB device using uhci_hcd and address 17
[17183225.972000] usb 2-1: device descriptor read/64, error -32
[17183226.192000] usb 2-1: device descriptor read/64, error -32
[17183226.408000] usb 2-1: reset full speed USB device using uhci_hcd and address 17
[17183226.816000] usb 2-1: device not accepting address 17, error -32
[17183226.928000] usb 2-1: reset full speed USB device using uhci_hcd and address 17
[17183227.336000] usb 2-1: device not accepting address 17, error -32
[17183227.336000] usb 2-1: USB disconnect, address 17
[17183227.336000] sdb : READ CAPACITY failed.
[17183227.336000] sdb : status=0, message=00, host=1, driver=00
[17183227.336000] sdb : sense not available.
[17183227.336000] sdb: Write Protect is off
[17183227.336000] sdb: Mode Sense: 00 00 00 00
[17183227.336000] sdb: assuming drive cache: write through
[17183227.336000] sdb : READ CAPACITY failed.
[17183227.336000] sdb : status=0, message=00, host=1, driver=00
[17183227.336000] sdb : sense not available.
[17183227.336000] sdb: Write Protect is off
[17183227.336000] sdb: Mode Sense: 00 00 00 00
[17183227.336000] sdb: assuming drive cache: write through
[17183227.336000] sdb : READ CAPACITY failed.
[17183227.336000] sdb : status=0, message=00, host=1, driver=00
[17183227.336000] sdb : sense not available.
[17183227.336000] sdb: Write Protect is off
[17183227.336000] sdb: Mode Sense: 00 00 00 00
[17183227.336000] sdb: assuming drive cache: write through
[17183227.336000]  sdb:<3>Buffer I/O error on device sdb, logical block 0
[17183227.336000] Buffer I/O error on device sdb, logical block 0
[17183227.336000]  unable to read partition table
[17183227.340000] sd 6:0:0:0: Attached scsi removable disk sdb
[17183227.340000] sd 6:0:0:0: Attached scsi generic sg2 type 0
[17183227.340000] usb-storage: device scan complete
[17183227.452000] usb 2-1: new full speed USB device using uhci_hcd and address 18
[17183227.572000] usb 2-1: device descriptor read/64, error -71
[17183227.796000] usb 2-1: device descriptor read/64, error -71
[17183228.012000] usb 2-1: new full speed USB device using uhci_hcd and address 19
[17183228.132000] usb 2-1: device descriptor read/64, error -71
[17183228.356000] usb 2-1: device descriptor read/64, error -71
[17183228.572000] usb 2-1: new full speed USB device using uhci_hcd and address 20
[17183228.980000] usb 2-1: device not accepting address 20, error -71
[17183229.092000] usb 2-1: new full speed USB device using uhci_hcd and address 21
[17183229.500000] usb 2-1: device not accepting address 21, error -71
[17183267.512000] usb 2-1: new full speed USB device using uhci_hcd and address 22
[17183267.664000] scsi7 : SCSI emulation for USB Mass Storage devices
[17183267.664000] usb-storage: device found at 22
[17183267.664000] usb-storage: waiting for device to settle before scanning
[17183272.664000]   Vendor: Sandisk0  Model: ImageMate SDDR-0  Rev: 0100
[17183272.664000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17183276.460000] usb 2-1: reset full speed USB device using uhci_hcd and address 22
[17183276.576000] usb 2-1: device descriptor read/64, error -32
[17183276.796000] usb 2-1: device descriptor read/64, error -32
[17183277.012000] usb 2-1: reset full speed USB device using uhci_hcd and address 22
[17183277.128000] usb 2-1: device descriptor read/64, error -32
[17183277.348000] usb 2-1: device descriptor read/64, error -32
[17183277.564000] usb 2-1: reset full speed USB device using uhci_hcd and address 22
[17183277.972000] usb 2-1: device not accepting address 22, error -32
[17183278.084000] usb 2-1: reset full speed USB device using uhci_hcd and address 22
[17183278.492000] usb 2-1: device not accepting address 22, error -32
[17183278.492000] usb 2-1: USB disconnect, address 22
[17183278.492000] sdb : READ CAPACITY failed.
[17183278.492000] sdb : status=0, message=00, host=1, driver=00
[17183278.492000] sdb : sense not available.
[17183278.492000] sdb: Write Protect is off
[17183278.492000] sdb: Mode Sense: 00 00 00 00
[17183278.492000] sdb: assuming drive cache: write through
[17183278.492000] sdb : READ CAPACITY failed.
[17183278.492000] sdb : status=0, message=00, host=1, driver=00
[17183278.492000] sdb : sense not available.
[17183278.492000] sdb: Write Protect is off
[17183278.492000] sdb: Mode Sense: 00 00 00 00
[17183278.492000] sdb: assuming drive cache: write through
[17183278.492000] sdb : READ CAPACITY failed.
[17183278.492000] sdb : status=0, message=00, host=1, driver=00
[17183278.492000] sdb : sense not available.
[17183278.496000] sdb: Write Protect is off
[17183278.496000] sdb: Mode Sense: 00 00 00 00
[17183278.496000] sdb: assuming drive cache: write through
[17183278.496000]  sdb:<3>Buffer I/O error on device sdb, logical block 0
[17183278.496000] Buffer I/O error on device sdb, logical block 0
[17183278.496000]  unable to read partition table
[17183278.496000] sd 7:0:0:0: Attached scsi removable disk sdb
[17183278.496000] sd 7:0:0:0: Attached scsi generic sg2 type 0
[17183278.496000] usb-storage: device scan complete
[17183278.608000] usb 2-1: new full speed USB device using uhci_hcd and address 23
[17183278.728000] usb 2-1: device descriptor read/64, error -71
[17183278.952000] usb 2-1: device descriptor read/64, error -71
[17183279.168000] usb 2-1: new full speed USB device using uhci_hcd and address 24
[17183279.288000] usb 2-1: device descriptor read/64, error -71
[17183279.512000] usb 2-1: device descriptor read/64, error -71
[17183279.728000] usb 2-1: new full speed USB device using uhci_hcd and address 25
[17183280.136000] usb 2-1: device not accepting address 25, error -71
[17183280.248000] usb 2-1: new full speed USB device using uhci_hcd and address 26
[17183280.656000] usb 2-1: device not accepting address 26, error -71
[17183287.420000] usb 2-1: new full speed USB device using uhci_hcd and address 27

---

### Post by mkosmo on 2006-09-05
Hmm... anybody?  Or should I just drop $40 for a Sandisk 12-in-1?  I've at least 'seen' stories of them working.  I would rather not if at all possible.

---

### Post by mkosmo on 2006-09-06
Is it safe to assume nobody has any idea since this is the only thread to get zero attention?

---

