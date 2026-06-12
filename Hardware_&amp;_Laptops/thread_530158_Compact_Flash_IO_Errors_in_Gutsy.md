---
title: "Compact Flash I/O Errors in Gutsy"
date: 2007-08-20
forum: Hardware &amp; Laptops
---

### Post by alexsb on 2007-08-20
Hey,

I'm running gutsy (compatibility for new notebook) and have problem mounting my 4GB Compact Flash Card with my Nikon D200 Camera:

In Dapper on my old computer it worked perfect, now when I connect the Camera I get the following log (dmesg):

```

[ 2513.384000] usb 6-3: new high speed USB device using ehci_hcd and address 4
[ 2513.516000] usb 6-3: configuration #1 chosen from 1 choice
[ 2514.108000] usbcore: registered new interface driver libusual
[ 2514.204000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[ 2514.204000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[ 2514.212000] Initializing USB Mass Storage driver...
[ 2514.212000] scsi2 : SCSI emulation for USB Mass Storage devices
[ 2514.212000] usb-storage: device found at 4
[ 2514.212000] usb-storage: waiting for device to settle before scanning
[ 2514.216000] usbcore: registered new interface driver usb-storage
[ 2514.216000] USB Mass Storage support registered.
[ 2519.212000] usb-storage: device scan complete
[ 2519.212000] scsi 2:0:0:0: Direct-Access     NIKON    D200             2.00 PQ: 0 ANSI: 2
[ 2519.216000] sd 2:0:0:0: [sdb] 8027713 512-byte hardware sectors (4110 MB)
[ 2519.216000] sd 2:0:0:0: [sdb] Write Protect is off
[ 2519.216000] sd 2:0:0:0: [sdb] Mode Sense: 0f 00 00 00
[ 2519.216000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 2519.216000] sd 2:0:0:0: [sdb] 8027713 512-byte hardware sectors (4110 MB)
[ 2519.216000] sd 2:0:0:0: [sdb] Write Protect is off
[ 2519.216000] sd 2:0:0:0: [sdb] Mode Sense: 0f 00 00 00
[ 2519.216000] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 2519.216000]  sdb: sdb1
[ 2519.220000] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 2519.220000] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 2519.392000] end_request: I/O error, dev sdb, sector 8027712
[ 2519.392000] Buffer I/O error on device sdb, logical block 8027712
[ 2519.392000] end_request: I/O error, dev sdb, sector 8027712
[ 2519.392000] Buffer I/O error on device sdb, logical block 8027712
[ 2519.396000] end_request: I/O error, dev sdb, sector 8027712
[ 2519.396000] Buffer I/O error on device sdb, logical block 8027712
[ 2519.400000] end_request: I/O error, dev sdb, sector 8027712
[ 2519.400000] Buffer I/O error on device sdb, logical block 8027712
[ 2519.400000] end_request: I/O error, dev sdb, sector 8027712
[ 2519.400000] Buffer I/O error on device sdb, logical block 8027712
[ 2519.420000] end_request: I/O error, dev sdb, sector 8027712
[ 2519.420000] Buffer I/O error on device sdb, logical block 8027712
[ 2519.424000] end_request: I/O error, dev sdb, sector 8027712
[ 2519.424000] Buffer I/O error on device sdb, logical block 8027712
[ 2519.424000] end_request: I/O error, dev sdb, sector 40
[ 2519.424000] Buffer I/O error on device sdb, logical block 40
[ 2519.424000] end_request: I/O error, dev sdb, sector 41
[ 2519.424000] Buffer I/O error on device sdb, logical block 41
[ 2519.424000] Buffer I/O error on device sdb, logical block 42
[ 2519.428000] end_request: I/O error, dev sdb, sector 40
[ 2519.428000] end_request: I/O error, dev sdb, sector 41

```

It might by a gutsy bug, but I checked the reported bugs and haven't seen anything fo that type.

Any Ideas?

Thx,  Alex

---

### Post by drop669 on 2007-12-27
The same thing here with D200. What is wrong?

---

### Post by los santos on 2007-12-30
[https://bugs.launchpad.net/ubuntu/+bug/145153](https://bugs.launchpad.net/ubuntu/+bug/145153)

temporary workaround would be to use an external flash reader. you could also try using mtp/ptp instead of msc...I was able to transfer from a d40x in msc mode using digikam.

---

