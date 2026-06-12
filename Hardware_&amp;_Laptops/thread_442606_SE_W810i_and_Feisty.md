---
title: "SE W810i and Feisty"
date: 2007-05-13
forum: Hardware &amp; Laptops
---

### Post by shacky on 2007-05-13
Hello,
on feisty(generic 2.6.20 x86_64) when I connect my cellphone as modem, kernel doesn't detect it as ACM device, but as scsi device...
DMESG:
```

[   83.331922] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   83.508171] usb 2-1: configuration #1 chosen from 1 choice
[   83.690882] usbcore: registered new interface driver libusual
[   83.728208] Initializing USB Mass Storage driver...
[   83.728426] scsi2 : SCSI emulation for USB Mass Storage devices
[   83.728617] usb-storage: device found at 2
[   83.728619] usb-storage: waiting for device to settle before scanning
[   83.728658] scsi3 : SCSI emulation for USB Mass Storage devices
[   83.728778] usbcore: registered new interface driver usb-storage
[   83.728781] USB Mass Storage support registered.
[   83.729291] usb-storage: device found at 2
[   83.729293] usb-storage: waiting for device to settle before scanning
[   88.724995] usb-storage: device scan complete
[   88.725308] usb-storage: device scan complete
[   88.728015] scsi 2:0:0:0: Direct-Access     SEMC     Int.Memory       0000 PQ: 0 ANSI: 0
[   88.728176] scsi 3:0:0:0: Direct-Access     SEMC     Mem-Stick        0000 PQ: 0 ANSI: 0
[   88.743078] sd 2:0:0:0: Attached scsi removable disk sdb
[   88.743268] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   88.759052] sd 3:0:0:0: Attached scsi removable disk sdc
[   88.759222] sd 3:0:0:0: Attached scsi generic sg3 type 0

```

If I load cdc_acm module manually, nothing changes.
On edgy and older kernel everything worked fine...

Please help,
Paul Bukowski

---

