---
title: "External USB2.0 HD"
date: 2006-03-31
forum: Hardware &amp; Laptops
---

### Post by aabeuge on 2006-03-31
I have an external LaCie 160GB USB2 drive that works fine in windows and in SystemRescueCD ([www.sysresccd.org](www.sysresccd.org), Knoppix based?)  Ubuntu see's it in DMESG but gives this output:      Note the unknown partition table error.

 usb 2-1.3: new full speed USB device using uhci_hcd and address 7
[4365524.133000] scsi4 : SCSI emulation for USB Mass Storage devices
[4365524.135000] usb-storage: device found at 7
[4365524.135000] usb-storage: waiting for device to settle before scanning
[4365529.138000]   Vendor: Maxtor    Model: 6Y160P0           Rev: YAR4
[4365529.138000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[4365529.146000] SCSI device sda: 320173056 512-byte hdwr sectors (163929 MB)
[4365529.146000] sda: assuming drive cache: write through
[4365529.152000] SCSI device sda: 320173056 512-byte hdwr sectors (163929 MB)
[4365529.152000] sda: assuming drive cache: write through
[4365529.152000]  /dev/scsi/host4/bus0/target0/lun0: unknown partition table
[4365529.189000] Attached scsi disk sda at scsi4, channel 0, id 0, lun 0
[4365529.191000] Attached scsi generic sg0 at scsi4, channel 0, id 0, lun 0,  type 0
[4365529.193000] usb-storage: device scan complete


/dev/ only shows sda.  No sda1, sda2, etc.

Any suggestions?

Thanks

---

