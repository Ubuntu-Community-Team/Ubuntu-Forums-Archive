---
title: "N80 in Edgy"
date: 2006-12-19
forum: Hardware &amp; Laptops
---

### Post by kitsos on 2006-12-19
Hi I have a nokia N80 and i'm trying to connect it to my Edgy laptop. My main worry at the moment is accessing the phone's memory card. I have read a few success stories but mine refuses to mount giving Buffer IO error. The device shows up correctly with lsusb and i can see it in /dev/sda but my dmesg reveals the following errors:

```

[17179922.080000] usb 2-2: new full speed USB device using ohci_hcd and address 2
[17179922.292000] usb 2-2: configuration #1 chosen from 1 choice
[17179922.492000] usbcore: registered new driver libusual
[17179922.584000] Initializing USB Mass Storage driver...
[17179922.584000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179922.584000] usb-storage: device found at 2
[17179922.584000] usb-storage: waiting for device to settle before scanning
[17179922.584000] usbcore: registered new driver usb-storage
[17179922.584000] USB Mass Storage support registered.
[17179927.584000] usb-storage: device scan complete
[17179927.588000]   Vendor:           Model:                   Rev:     
[17179927.588000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179927.720000] SCSI device sda: 3967240 512-byte hdwr sectors (2031 MB)
[17179927.728000] sda: Write Protect is off
[17179927.728000] sda: Mode Sense: 03 00 00 00
[17179927.728000] sda: assuming drive cache: write through
[17179927.752000] SCSI device sda: 3967240 512-byte hdwr sectors (2031 MB)
[17179927.756000] sda: Write Protect is off
[17179927.756000] sda: Mode Sense: 03 00 00 00
[17179927.756000] sda: assuming drive cache: write through
[17179927.760000]  sda: unknown partition table
[17179927.788000] sd 0:0:0:0: Attached scsi removable disk sda
[17179927.808000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179928.112000] end_request: I/O error, dev sda, sector 3967232
[17179928.112000] Buffer I/O error on device sda, logical block 495904
[17179928.128000] end_request: I/O error, dev sda, sector 3967232
[17179928.128000] Buffer I/O error on device sda, logical block 495904
[17179928.144000] end_request: I/O error, dev sda, sector 3967232
[17179928.144000] Buffer I/O error on device sda, logical block 495904
[17179928.160000] end_request: I/O error, dev sda, sector 3967232
[17179928.160000] Buffer I/O error on device sda, logical block 495904
[17179928.176000] end_request: I/O error, dev sda, sector 3967232
[17179928.176000] Buffer I/O error on device sda, logical block 495904
[17179928.192000] end_request: I/O error, dev sda, sector 3967232
[17179928.192000] Buffer I/O error on device sda, logical block 495904
[17179928.248000] end_request: I/O error, dev sda, sector 0
[17179928.248000] Buffer I/O error on device sda, logical block 0
[17179928.268000] end_request: I/O error, dev sda, sector 0
[17179928.268000] Buffer I/O error on device sda, logical block 0
[17179928.284000] end_request: I/O error, dev sda, sector 0
[17179928.284000] Buffer I/O error on device sda, logical block 0
[17179928.320000] end_request: I/O error, dev sda, sector 0
[17179928.320000] Buffer I/O error on device sda, logical block 0
[17179928.336000] end_request: I/O error, dev sda, sector 0
[17179928.352000] end_request: I/O error, dev sda, sector 0
[17179928.368000] end_request: I/O error, dev sda, sector 0
[17179928.516000] end_request: I/O error, dev sda, sector 40
[17179928.532000] end_request: I/O error, dev sda, sector 0
[17179928.548000] end_request: I/O error, dev sda, sector 0
[17179928.564000] end_request: I/O error, dev sda, sector 0
[17179928.580000] end_request: I/O error, dev sda, sector 0
[17179928.596000] end_request: I/O error, dev sda, sector 0
[17179928.612000] end_request: I/O error, dev sda, sector 0
[17179928.628000] end_request: I/O error, dev sda, sector 0
[17179928.644000] end_request: I/O error, dev sda, sector 0
[17179928.660000] end_request: I/O error, dev sda, sector 0
[17179928.676000] end_request: I/O error, dev sda, sector 0
[17179928.692000] end_request: I/O error, dev sda, sector 0
[17179928.708000] end_request: I/O error, dev sda, sector 0
[17179928.724000] end_request: I/O error, dev sda, sector 0
[17179928.740000] end_request: I/O error, dev sda, sector 0
[17179928.756000] end_request: I/O error, dev sda, sector 0
[17179928.772000] end_request: I/O error, dev sda, sector 0
[17179928.788000] end_request: I/O error, dev sda, sector 0
[17179928.804000] end_request: I/O error, dev sda, sector 0


```

Also, sometimes just plugging the phone in, causes the whole system to freeze and i need to do a hard reboot...

If anybody can help i'd be really grateful as connectivity with my mobile phone is the last thing that keeps me tied down to windows!

Anybody has any ideas?

---

### Post by AndyGZA on 2007-01-30
Hi kitsos, I'm having a similar problem. I mainly connect my phone to ubuntu to use it as a gprs modem using wvdial, but I also have the issue that my system often freezes completely when I connect it using the nokia data cable - it's really frustrating.

Please let me know if you find a solution.

Thanks

---

