---
title: "USB hard drive docking station will not work through hub"
date: 2017-01-10
forum: Hardware
---

### Post by atconley on 2017-01-10
I am trying to get some hardware to work together. They are:

Gigabyte BRIX GB-BXBT-2807 ([link]("http://www.gigabyte.com.au/products/product-page.aspx?pid=5038#ov"))
Orico 4 Port USB 3.0 Hub (W9PH4-U3-V1) ([link]("http://orico.cc/goods.php?id=4895"))
Orico Dual Bay SATA to USB 3.0 External Hard Drive Docking Station (6629US3-C-BK) ([link]("http://orico.cc/goods.php?id=4836"))

Plugging the _docking station  into the computer_ works fine. The **dmesg** output for that is:
```
[ 5274.457210] usb 2-1: new SuperSpeed USB device number 3 using xhci_hcd
[ 5274.474487] usb 2-1: New USB device found, idVendor=152d, idProduct=9561
[ 5274.474497] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=5
[ 5274.474504] usb 2-1: Product: JMS56x Series
[ 5274.474509] usb 2-1: Manufacturer: JMicron
[ 5274.474514] usb 2-1: SerialNumber: 00000000000000000000
[ 5274.509418] scsi host3: uas
[ 5274.510213] usbcore: registered new interface driver uas
[ 5274.511920] scsi 3:0:0:0: Direct-Access     WDC WD20 EZRX-00D8PB0     0105 PQ: 0 ANSI: 6
[ 5274.518173] scsi 3:0:0:1: Direct-Access     WDC WD20 EZRX-00D8PB0     0105 PQ: 0 ANSI: 6
[ 5274.519398] sd 3:0:0:0: Attached scsi generic sg1 type 0
[ 5274.519579] sd 3:0:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.82 TiB)
[ 5274.520406] sd 3:0:0:1: Attached scsi generic sg2 type 0
[ 5274.520529] sd 3:0:0:0: [sdb] Write Protect is off
[ 5274.520536] sd 3:0:0:0: [sdb] Mode Sense: 67 00 10 08
[ 5274.521042] sd 3:0:0:0: [sdb] Write cache: enabled, read cache: enabled, supports DPO and FUA
[ 5274.522991] sd 3:0:0:1: [sdc] 3907029168 512-byte logical blocks: (2.00 TB/1.82 TiB)
[ 5274.555899] sd 3:0:0:1: [sdc] Write Protect is off
[ 5274.555907] sd 3:0:0:1: [sdc] Mode Sense: 67 00 10 08
[ 5274.556409] sd 3:0:0:1: [sdc] Write cache: enabled, read cache: enabled, supports DPO and FUA
[ 5274.595130]  sdb: sdb1
[ 5274.627930] sd 3:0:0:0: [sdb] Attached SCSI disk
[ 5274.669432]  sdc: sdc1
[ 5274.672024] sd 3:0:0:1: [sdc] Attached SCSI disk
```

Plugging _another USB 3.0 hard drive into to the hub_ works fine. The **dmesg** output for that is:
```
***Hub plugged in to computer:***
[ 5605.628858] usb 2-1: new SuperSpeed USB device number 7 using xhci_hcd
[ 5605.730867] usb 2-1: New USB device found, idVendor=2109, idProduct=0813
[ 5605.730878] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 5605.730884] usb 2-1: Product: USB3.0 Hub             
[ 5605.730890] usb 2-1: Manufacturer: VIA Labs, Inc.         
[ 5605.733215] hub 2-1:1.0: USB hub found
[ 5605.733476] hub 2-1:1.0: 4 ports detected
[ 5606.348936] usb 1-1: new high-speed USB device number 11 using xhci_hcd
[ 5606.480261] usb 1-1: New USB device found, idVendor=2109, idProduct=2813
[ 5606.480271] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 5606.480276] usb 1-1: Product: USB2.0 Hub             
[ 5606.480281] usb 1-1: Manufacturer: VIA Labs, Inc.         
[ 5606.482164] hub 1-1:1.0: USB hub found
[ 5606.482771] hub 1-1:1.0: 4 ports detected

***Hard drive plugged in to hub:***
[ 5617.798512] usb 2-1.2: new SuperSpeed USB device number 8 using xhci_hcd
[ 5617.815965] usb 2-1.2: New USB device found, idVendor=1058, idProduct=0827
[ 5617.815974] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=5
[ 5617.815979] usb 2-1.2: Product: My Passport 0827
[ 5617.815984] usb 2-1.2: Manufacturer: Western Digital
[ 5617.815988] usb 2-1.2: SerialNumber: 575833314142354341593854
[ 5617.817921] usb-storage 2-1.2:1.0: USB Mass Storage device detected
[ 5617.821684] scsi host7: usb-storage 2-1.2:1.0
[ 5618.820196] scsi 7:0:0:0: Direct-Access     WD       My Passport 0827 1012 PQ: 0 ANSI: 6
[ 5618.820436] scsi 7:0:0:1: Enclosure         WD       SES Device       1012 PQ: 0 ANSI: 6
[ 5618.822796] sd 7:0:0:0: Attached scsi generic sg1 type 0
[ 5618.823068] ses 7:0:0:1: Attached Enclosure device
[ 5618.823273] ses 7:0:0:1: Attached scsi generic sg2 type 13
[ 5624.855797] sd 7:0:0:0: [sdb] 3906963456 512-byte logical blocks: (2.00 TB/1.82 TiB)
[ 5624.856225] sd 7:0:0:0: [sdb] Write Protect is off
[ 5624.856231] sd 7:0:0:0: [sdb] Mode Sense: 47 00 10 08
[ 5624.856570] sd 7:0:0:0: [sdb] No Caching mode page found
[ 5624.856576] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 5624.868971]  sdb: sdb1
[ 5624.871279] sd 7:0:0:0: [sdb] Attached SCSI disk
```

But plugging the _docking station into the hub_ does *not* work. The **dmesg** output for that is:
```
[ 5839.154453] xhci_hcd 0000:00:14.0: Timeout while waiting for setup device command
[ 5844.378102] xhci_hcd 0000:00:14.0: Timeout while waiting for setup device command
[ 5844.582787] usb 2-1.3: device not accepting address 10, error -62
[ 5849.907028] xhci_hcd 0000:00:14.0: Timeout while waiting for setup device command
[ 5855.131059] xhci_hcd 0000:00:14.0: Timeout while waiting for setup device command
[ 5855.335382] usb 2-1.3: device not accepting address 11, error -62
[ 5860.659596] xhci_hcd 0000:00:14.0: Timeout while waiting for setup device command
[ 5865.883321] xhci_hcd 0000:00:14.0: Timeout while waiting for setup device command
[ 5866.087926] usb 2-1.3: device not accepting address 12, error -62
[ 5871.412175] xhci_hcd 0000:00:14.0: Timeout while waiting for setup device command
[ 5876.636258] xhci_hcd 0000:00:14.0: Timeout while waiting for setup device command
[ 5876.840495] usb 2-1.3: device not accepting address 13, error -62
[ 5876.842632] usb 2-1-port3: unable to enumerate USB device
[ 5882.276591] xhci_hcd 0000:00:14.0: Timeout while waiting for setup device command
[ 5887.500792] xhci_hcd 0000:00:14.0: Timeout while waiting for setup device command
[ 5887.705302] usb 2-1.3: device not accepting address 14, error -62
[ 5893.029262] xhci_hcd 0000:00:14.0: Timeout while waiting for setup device command
[ 5898.253580] xhci_hcd 0000:00:14.0: Timeout while waiting for setup device command
[ 5898.457479] usb 2-1.3: device not accepting address 15, error -62
[ 5903.782104] xhci_hcd 0000:00:14.0: Timeout while waiting for setup device command
[ 5909.005752] xhci_hcd 0000:00:14.0: Timeout while waiting for setup device command
[ 5909.210047] usb 2-1.3: device not accepting address 16, error -62
[ 5914.534376] xhci_hcd 0000:00:14.0: Timeout while waiting for setup device command
[ 5919.759239] xhci_hcd 0000:00:14.0: Timeout while waiting for setup device command
[ 5919.962662] usb 2-1.3: device not accepting address 17, error -62
[ 5919.963819] usb 2-1-port3: unable to enumerate USB device
[ 5925.399079] xhci_hcd 0000:00:14.0: Timeout while waiting for setup device command
[ 5930.623494] xhci_hcd 0000:00:14.0: Timeout while waiting for setup device command
[ 5930.827804] usb 2-1.3: device not accepting address 18, error -62
[ 5936.151654] xhci_hcd 0000:00:14.0: Timeout while waiting for setup device command
[ 5941.376120] xhci_hcd 0000:00:14.0: Timeout while waiting for setup device command
[ 5941.580405] usb 2-1.3: device not accepting address 19, error -62
[ 5946.904688] xhci_hcd 0000:00:14.0: Timeout while waiting for setup device command
[ 5952.128758] xhci_hcd 0000:00:14.0: Timeout while waiting for setup device command
[ 5952.333015] usb 2-1.3: device not accepting address 20, error -62
[ 5957.656935] xhci_hcd 0000:00:14.0: Timeout while waiting for setup device command
[ 5962.881369] xhci_hcd 0000:00:14.0: Timeout while waiting for setup device command
[ 5963.085236] usb 2-1.3: device not accepting address 21, error -62
[ 5963.087054] usb 2-1-port3: unable to enumerate USB device
```
-- and so on.

I am running Ubuntu 16.04. I would be grateful if anyone could provide me with any assistance with getting the docking station to work with the hub.

---

### Post by TheFu on 2017-01-11
Nested hubs often don't work.  I've had USB drives that wouldn't work with a hub too - had to be plugged directly into the computer port.  Contacted the company for support (it was a reputable brand) and they were aware of the problem and suggested plugging the problem devices directly into the computer.

There have been a few bugs around USB3 uas support. One fix that works for some is to disable that extension. Doing that didn't help my situation.

Sorry I don't have better news.  In my case, a 4-port USB3 card was added to the system which provided enough USB3 ports. On another box, I added a USB3 front panel with 2 ports connected internally to 2 internal USB3 headers. Works great!  Don't think these are options with a BRIX.

---

### Post by atconley on 2017-01-13
Thank you **TheFu**. I’ve had a look at the manufacturer’s website and their approach is the same as yours. I’m going to give up on trying to find a fix for this one.

---

