---
title: "Vantec SATA/IDE to USB mass storage issue"
date: 2009-07-22
forum: Hardware
---

### Post by wonderfullyrich on 2009-07-22
I have a Vantec SATA to USB Adapter (CB-ISATA-U2) which I'm using with an Seagate 1.5TB drive (NTFS formatted), that works just fine while in a Thermaltake SATA to USB dock, but isn't working with the Vantec device.   It's not showing up in a 
```
ls -l /dev/disk/by-uuid 
```
but dmesg reports

```
[17404.408019] usb 5-7: new high speed USB device using ehci_hcd and address 105
[17404.542346] usb 5-7: configuration #1 chosen from 1 choice
[17404.589950] scsi44 : SCSI emulation for USB Mass Storage devices
[17404.596271] usb-storage: device found at 105
[17404.596277] usb-storage: waiting for device to settle before scanning
[17409.599112] usb-storage: device scan complete

```

Anyone have any inspiration that might help?

Thanks
Rich

---

