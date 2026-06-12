---
title: "Panasonic Lumix DMC-FZ30"
date: 2006-06-18
forum: Hardware &amp; Laptops
---

### Post by Berduchwal on 2006-06-18
Non of the applications(digiKam, F-Spot, gtkam) detects this camera. Camera is detected as Panasonic Lumix DMC-FZ20 (alternate id) and it does not work.

You can still transfer pictures by going to: /media/usbdisk/dcim/100_pana/

I do not have much of the programing knowdlege but can I help somehow to help make this model supported?

dmesg gives:
```

[17180487.764000] Initializing USB Mass Storage driver...
[17180487.764000] scsi0 : SCSI emulation for USB Mass Storage devices
[17180487.764000] usb-storage: device found at 3
[17180487.764000] usb-storage: waiting for device to settle before scanning
[17180487.764000] usbcore: registered new driver usb-storage
[17180487.764000] USB Mass Storage support registered.
[17180492.768000]   Vendor: MATSHITA  Model: DMC-FZ30          Rev: 0100
[17180492.768000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17180492.772000] usb-storage: device scan complete
[17180492.840000] Driver 'sd' needs updating - please use bus_type methods
[17180492.852000] SCSI device sda: 1935360 512-byte hdwr sectors (991 MB)
[17180492.856000] sda: Write Protect is off
[17180492.856000] sda: Mode Sense: 04 00 00 00
[17180492.856000] sda: assuming drive cache: write through
[17180492.864000] SCSI device sda: 1935360 512-byte hdwr sectors (991 MB)
[17180492.868000] sda: Write Protect is off
[17180492.868000] sda: Mode Sense: 04 00 00 00
[17180492.868000] sda: assuming drive cache: write through
[17180492.868000]  sda: sda1
[17180492.884000] sd 0:0:0:0: Attached scsi removable disk sda
[17180492.904000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17180493.924000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17180750.724000] usb 2-1: USB disconnect, address 3
[17180765.580000] usb 2-1: new full speed USB device using uhci_hcd and address 4
[17180765.724000] scsi1 : SCSI emulation for USB Mass Storage devices
[17180765.724000] usb-storage: device found at 4
[17180765.724000] usb-storage: waiting for device to settle before scanning
[17180770.728000]   Vendor: MATSHITA  Model: DMC-FZ30          Rev: 0100
[17180770.728000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17180770.740000] SCSI device sda: 1935360 512-byte hdwr sectors (991 MB)
[17180770.744000] sda: Write Protect is off
[17180770.744000] sda: Mode Sense: 04 00 00 00
[17180770.744000] sda: assuming drive cache: write through
[17180770.752000] SCSI device sda: 1935360 512-byte hdwr sectors (991 MB)
[17180770.756000] sda: Write Protect is off
[17180770.756000] sda: Mode Sense: 04 00 00 00
[17180770.756000] sda: assuming drive cache: write through
[17180770.756000]  sda: sda1
[17180770.768000] sd 1:0:0:0: Attached scsi removable disk sda
[17180770.768000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[17180770.768000] usb-storage: device scan complete
[17180771.664000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

```

---

### Post by howlingmadhowie on 2007-03-02
my panasonic dmc fz5 (lumix) has a pict-bridge usb-mode. setting this allows photos to be imported without any trouble on my system

---

