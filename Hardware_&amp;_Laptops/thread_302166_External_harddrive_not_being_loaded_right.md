---
title: "External harddrive not being loaded right"
date: 2006-11-18
forum: Hardware &amp; Laptops
---

### Post by daller on 2006-11-18
Hi there,

I have a problem with my external harddrive.

This is dmesg:

```
[17181181.700000] usbcore: registered new driver libusual
[17181181.864000] SCSI subsystem initialized
[17181181.912000] Initializing USB Mass Storage driver...
[17181181.916000] scsi0 : SCSI emulation for USB Mass Storage devices
[17181181.916000] usb-storage: device found at 7
[17181181.916000] usb-storage: waiting for device to settle before scanning
[17181181.916000] usbcore: registered new driver usb-storage
[17181181.916000] USB Mass Storage support registered.
[17181186.916000] usb-storage: device scan complete
[17181186.920000]   Vendor:  H H HdH  Model:  &#65533;H H H I H l H  Rev: 0811
[17181186.920000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17181187.000000] SCSI device sda: 32320895 512-byte hdwr sectors (16548 MB)
[17181187.004000] sda: test WP failed, assume Write Enabled
[17181187.004000] sda: assuming drive cache: write through
[17181187.012000] SCSI device sda: 32320895 512-byte hdwr sectors (16548 MB)
[17181187.012000] sda: test WP failed, assume Write Enabled
[17181187.012000] sda: assuming drive cache: write through
[17181187.012000]  sda:
```

It ends quite weird! - Just "sda:"

Update: This is what follows (ran dmesg a minute after)

```
[17181187.004000] sda: test WP failed, assume Write Enabled
[17181187.004000] sda: assuming drive cache: write through
[17181187.012000] SCSI device sda: 32320895 512-byte hdwr sectors (16548 MB)
[17181187.012000] sda: test WP failed, assume Write Enabled
[17181187.012000] sda: assuming drive cache: write through
[17181187.012000]  sda:<6>usb 4-6: reset high speed USB device using ehci_hcd and address 7
[17181247.368000] usb 4-6: reset high speed USB device using ehci_hcd and address 7
[17181247.888000] usb 4-6: device not accepting address 7, error -71
[17181248.000000] usb 4-6: reset high speed USB device using ehci_hcd and address 7
[17181248.116000] usb 4-6: device descriptor read/64, error -71
[17181248.332000] usb 4-6: device descriptor read/64, error -71
[17181248.548000] usb 4-6: reset high speed USB device using ehci_hcd and address 7
[17181248.956000] usb 4-6: device not accepting address 7, error -71
[17181249.068000] usb 4-6: reset high speed USB device using ehci_hcd and address 7
[17181249.476000] usb 4-6: device not accepting address 7, error -71
[17181249.476000] usb 4-6: USB disconnect, address 7
[17181249.476000] sd 0:0:0:0: scsi: Device offlined - not ready after error recovery
[17181249.480000] sd 0:0:0:0: SCSI error: return code = 0x10000
[17181249.480000] end_request: I/O error, dev sda, sector 0
[17181249.480000] Buffer I/O error on device sda, logical block 0
[17181249.480000] sd 0:0:0:0: SCSI error: return code = 0x10000
[17181249.480000] end_request: I/O error, dev sda, sector 1
[17181249.480000] Buffer I/O error on device sda, logical block 1
[17181249.480000] sd 0:0:0:0: rejecting I/O to device being removed
[17181249.480000] Buffer I/O error on device sda, logical block 2
[17181249.480000] Buffer I/O error on device sda, logical block 3
[17181249.480000] Buffer I/O error on device sda, logical block 4
[17181249.480000] Buffer I/O error on device sda, logical block 5
[17181249.480000] Buffer I/O error on device sda, logical block 6
[17181249.480000] Buffer I/O error on device sda, logical block 7
[17181249.480000] sd 0:0:0:0: rejecting I/O to device being removed
[17181249.480000] Buffer I/O error on device sda, logical block 0
[17181249.480000] Buffer I/O error on device sda, logical block 1
[17181249.480000]  unable to read partition table
[17181249.484000] sd 0:0:0:0: Attached scsi disk sda
[17181249.596000] usb 4-6: new high speed USB device using ehci_hcd and address 8
[17181249.708000] usb 4-6: device descriptor read/64, error -71
[17181249.924000] usb 4-6: device descriptor read/64, error -71
[17181250.140000] usb 4-6: new high speed USB device using ehci_hcd and address 9
[17181250.252000] usb 4-6: device descriptor read/64, error -71
[17181250.468000] usb 4-6: device descriptor read/64, error -71
[17181250.684000] usb 4-6: new high speed USB device using ehci_hcd and address 10
[17181251.092000] usb 4-6: device not accepting address 10, error -71
[17181251.204000] usb 4-6: new high speed USB device using ehci_hcd and address 11
[17181251.612000] usb 4-6: device not accepting address 11, error -71
```

Any ideas?

It's not doomed! - It's a laptop harddrive from a dell! - Which boots windows just fine! (And it's not password protected)

---

