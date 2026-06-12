---
title: "Cannot mount USB CDRW Drive"
date: 2004-10-31
forum: Hardware &amp; Laptops
---

### Post by jdusablon on 2004-10-31
Relative newbie here, can't see or use my external USB 2.0 CDRW drive.

Where do I start?? I can post any info required to fix this.

---

### Post by jdong on 2004-10-31
Unplug and replug the drive, then post the last 20 or so lines from the command **dmesg** (run it from a Terminal)

---

### Post by jdusablon on 2004-10-31
Ok, this looks promising. Seems like the system sees the drive fine.

```
usb 3-2: new high speed USB device using address 3
SCSI subsystem initialized
Initializing USB Mass Storage driver...
scsi0 : SCSI emulation for USB Mass Storage devices
USB Mass Storage device found at 3
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
usb 3-2: USB disconnect, address 3
usb 3-2: new high speed USB device using address 4
scsi1 : SCSI emulation for USB Mass Storage devices
  Vendor: AOPEN     Model: CD-RW CRW5232     Rev: 1.03
  Type:   CD-ROM                             ANSI SCSI revision: 02
USB Mass Storage device found at 4
sr0: scsi-1 drive
Attached scsi CD-ROM sr0 at scsi1, channel 0, id 0, lun 0
usb 3-2: USB disconnect, address 4
usb 3-2: new high speed USB device using address 5
scsi2 : SCSI emulation for USB Mass Storage devices
  Vendor: AOPEN     Model: CD-RW CRW5232     Rev: 1.03
  Type:   CD-ROM                             ANSI SCSI revision: 02
sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Attached scsi CD-ROM sr0 at scsi2, channel 0, id 0, lun 0
USB Mass Storage device found at 5
```

Looks like I don't know how to mount devices properly. Also, how would I make the device auto-mount on plug-in?

---

