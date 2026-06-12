---
title: "External USB DVD burner &quot;not ready after error recovery&quot;"
date: 2009-12-26
forum: Hardware
---

### Post by tammer on 2009-12-26
Hello all. I recently purchased a USB enclosure for my DVD burner that before resided in my UltraBay device (I'm using a Thinkpad X31). The drive opens and spins up correctly, but Ubuntu doesn't even recognize it well enough to assign it a /dev/* address, so mounting it is out of the question. Here is the relevant info from dmesg: 

```
[ 1520.444176] usb 1-4: new high speed USB device using ehci_hcd and address 10
[ 1520.577805] usb 1-4: configuration #1 chosen from 1 choice
[ 1520.582150] scsi7 : SCSI emulation for USB Mass Storage devices
[ 1520.582454] usb-storage: device found at 10
[ 1520.582461] usb-storage: waiting for device to settle before scanning
[ 1525.580490] usb-storage: device scan complete
[ 1547.112232] scsi 7:0:0:0: Device offlined - not ready after error recovery
[ 1547.112994] usb 1-4: USB disconnect, address 10

```

Any ideas on what other info I should post/what my next step in troubleshooting should be? Thanks!

---

### Post by tammer on 2010-02-05
I'm happy to report a solution, should anyone run into this problem. I can confirm that the Sabrent EIDE to USB enclosure will not work on Ubuntu.

I solved the issue by purchasing [this]("http://www.centrix-intl.com/details.asp?productid=3022") converter board, opening the enclosure and replacing it.

---

