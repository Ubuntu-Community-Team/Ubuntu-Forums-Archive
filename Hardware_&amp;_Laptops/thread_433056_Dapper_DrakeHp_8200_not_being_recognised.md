---
title: "Dapper Drake:Hp 8200 not being recognised"
date: 2007-05-04
forum: Hardware &amp; Laptops
---

### Post by HwH on 2007-05-04
Ubuntu 6.06 fails reconise external hp-8200 cd-writer so cannot burn CDs. :( 

A quote for dmesg:
> [4300410.248000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[4300410.589000] SCSI subsystem initialized
[4300410.614000] Initializing USB Mass Storage driver...
[4300414.576000] scsi0 : SCSI emulation for USB Mass Storage devices
[4300414.577000] usb-storage: device found at 2
[4300414.577000] usb-storage: waiting for device to settle before scanning
[4300414.577000] usbcore: registered new driver usb-storage
[4300414.577000] USB Mass Storage support registered.
[4300419.578000] Vendor: HP Model: CD-Writer+ 8200e Rev: 0001
[4300419.578000] Type: Direct-Access ANSI SCSI revision: 00
[4300419.581000] usb-storage: device scan complete
[4300419.668000] Driver 'sd' needs updating - please use bus_type methods
[4300425.502000] not responding...
[4300425.667000] sda : READ CAPACITY failed.
[4300425.667000] sda : status=1, message=00, host=0, driver=08
[4300425.667000] sd: Current: sense key: Unit Attention
[4300425.668000] Additional sense: Not ready to ready change, medium may have changed
[4300425.669000] sda: test WP failed, assume Write Enabled
[4300425.669000] sda: assuming drive cache: write through
[4300431.562000] not responding...
[4300431.727000] sda : READ CAPACITY failed.
[4300431.727000] sda : status=1, message=00, host=0, driver=08
[4300431.727000] sd: Current: sense key: Unit Attention
[4300431.727000] Additional sense: Not ready to ready change, medium may have changed
[4300431.728000] sda: test WP failed, assume Write Enabled
[4300431.728000] sda: assuming drive cache: write through
[4300437.587000] not responding...
:mad: 

Im not the most computer literate person alive so could suggestions be simple.
Thanks in advance for any help i get.

---

### Post by bokkie on 2007-12-31
I have had a similar problem with my HP 8200 CD-writer on a laptop.  Have you found a solution yet?

---

