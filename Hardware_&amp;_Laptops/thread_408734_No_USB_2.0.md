---
title: "No USB 2.0"
date: 2007-04-13
forum: Hardware &amp; Laptops
---

### Post by lucky sevin on 2007-04-13
After installing Edgy on my Compaq Presario laptop I noticed that transfering my data onto it from a usb drive was taking about 10-20x slower than putting it on from my desktop.  I installed a program called USBViewer.  It listed all three ports on my computer, two as OHCI Host Controller with 1.1 drivers and one EHCI Host Controller with 2.0 drivers.  No matter which port I plug a USB device into, it lists it on one of the OHCI ports.  How can I get 2.0 working?

---

### Post by lucky sevin on 2007-04-13
By reading other thread, I think you might also like to know the following:

When I run dmesg I get:
```

[17246616.624000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17246848.944000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17247003.832000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17247158.680000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17247459.824000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17247692.128000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17247847.020000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17248079.336000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17248234.288000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17248389.216000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17248690.404000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17248931.360000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17249086.280000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17249310.052000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17249464.992000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17249619.944000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17249929.764000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17250153.512000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17250308.372000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17250540.688000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17250695.600000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17250850.444000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17251160.228000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17251383.972000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17251538.912000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17251771.196000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17251926.060000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17252080.952000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17252390.668000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17252623.000000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17252777.880000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17253010.208000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17253165.128000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17253320.072000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17253621.296000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17253862.280000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17254017.180000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17254240.964000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17254395.868000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17254550.772000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17254860.540000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17255084.356000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17255239.256000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17255471.660000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17255626.592000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17255781.528000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17256091.384000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17256315.188000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17256470.168000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17256702.612000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17256857.520000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17257012.456000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17257322.260000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17257546.072000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17257701.024000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17258036.700000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17258191.596000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17258553.152000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17258785.580000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17258940.476000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17259164.208000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17259465.424000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17259783.876000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17259938.780000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17260093.616000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17260403.428000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17260856.820000] ohci_hcd 0000:00:13.0: wakeup
[17260857.204000] usb 1-1: new full speed USB device using ohci_hcd and address 2
[17260857.404000] usb 1-1: not running at top speed; connect to a high speed hub
[17260857.424000] usb 1-1: configuration #1 chosen from 1 choice
[17260858.172000] usbcore: registered new driver libusual
[17260858.240000] Initializing USB Mass Storage driver...
[17260858.240000] scsi0 : SCSI emulation for USB Mass Storage devices
[17260858.244000] usb-storage: device found at 2
[17260858.244000] usb-storage: waiting for device to settle before scanning
[17260858.244000] usbcore: registered new driver usb-storage
[17260858.244000] USB Mass Storage support registered.
[17260863.244000] usb-storage: device scan complete
[17260863.248000]   Vendor:           Model: USB Flash Memory  Rev: 1.00
[17260863.248000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17260863.808000] SCSI device sda: 246272 512-byte hdwr sectors (126 MB)
[17260863.812000] sda: Write Protect is off
[17260863.812000] sda: Mode Sense: 23 00 00 00
[17260863.812000] sda: assuming drive cache: write through
[17260863.836000] SCSI device sda: 246272 512-byte hdwr sectors (126 MB)
[17260863.844000] sda: Write Protect is off
[17260863.844000] sda: Mode Sense: 23 00 00 00
[17260863.844000] sda: assuming drive cache: write through
[17260863.844000]  sda: sda1
[17260863.856000] sd 0:0:0:0: Attached scsi removable disk sda
[17260863.876000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17260865.084000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17260866.384000] usb 1-1: USB disconnect, address 2
[17260866.420000]  0:0:0:0: rejecting I/O to dead device
[17260866.420000]  0:0:0:0: rejecting I/O to dead device
[17260866.420000]  0:0:0:0: rejecting I/O to dead device
[17260866.420000]  0:0:0:0: rejecting I/O to dead device
[17260866.420000] sda : READ CAPACITY failed.
[17260866.420000] sda : status=0, message=00, host=1, driver=00 
[17260866.420000] sda : sense not available. 
[17260866.420000]  0:0:0:0: rejecting I/O to dead device
[17260866.420000] sda: Write Protect is off
[17260866.420000] sda: Mode Sense: 00 00 00 00
[17260866.420000] sda: assuming drive cache: write through
[17260866.440000]  0:0:0:0: rejecting I/O to dead device
[17260866.440000] FAT: FAT read failed (blocknr 1)
[17260866.584000]  0:0:0:0: rejecting I/O to dead device
[17260866.584000] FAT: Directory bread(block 243) failed
[17260866.584000]  0:0:0:0: rejecting I/O to dead device
[17260866.584000] FAT: Directory bread(block 244) failed
[17260866.584000]  0:0:0:0: rejecting I/O to dead device
[17260866.584000] FAT: Directory bread(block 245) failed
[17260866.584000]  0:0:0:0: rejecting I/O to dead device
[17260866.584000] FAT: Directory bread(block 246) failed
[17260866.584000]  0:0:0:0: rejecting I/O to dead device
[17260866.584000] FAT: Directory bread(block 247) failed
[17260866.584000]  0:0:0:0: rejecting I/O to dead device
[17260866.584000] FAT: Directory bread(block 248) failed
[17260866.584000]  0:0:0:0: rejecting I/O to dead device
[17260866.584000] FAT: Directory bread(block 249) failed
[17260866.584000]  0:0:0:0: rejecting I/O to dead device
[17260866.584000] FAT: Directory bread(block 250) failed
[17260866.584000]  0:0:0:0: rejecting I/O to dead device
[17260866.584000] FAT: Directory bread(block 251) failed
[17260866.584000]  0:0:0:0: rejecting I/O to dead device
[17260866.584000] FAT: Directory bread(block 252) failed
[17260866.584000]  0:0:0:0: rejecting I/O to dead device
[17260866.588000] FAT: Directory bread(block 253) failed
[17260866.588000]  0:0:0:0: rejecting I/O to dead device
[17260866.588000] FAT: Directory bread(block 254) failed
[17260866.588000]  0:0:0:0: rejecting I/O to dead device
[17260866.588000] FAT: Directory bread(block 255) failed
[17260866.588000]  0:0:0:0: rejecting I/O to dead device
[17260866.588000] FAT: Directory bread(block 256) failed
[17260866.588000]  0:0:0:0: rejecting I/O to dead device
[17260866.588000] FAT: Directory bread(block 257) failed
[17260866.588000]  0:0:0:0: rejecting I/O to dead device
[17260866.588000] FAT: Directory bread(block 258) failed
[17260866.588000]  0:0:0:0: rejecting I/O to dead device
[17260866.588000] FAT: Directory bread(block 259) failed
[17260866.588000]  0:0:0:0: rejecting I/O to dead device
[17260866.588000] FAT: Directory bread(block 260) failed
[17260866.588000]  0:0:0:0: rejecting I/O to dead device
[17260866.588000] FAT: Directory bread(block 261) failed
[17260866.588000]  0:0:0:0: rejecting I/O to dead device
[17260866.588000] FAT: Directory bread(block 262) failed
[17260866.588000]  0:0:0:0: rejecting I/O to dead device
[17260866.588000] FAT: Directory bread(block 263) failed
[17260866.588000]  0:0:0:0: rejecting I/O to dead device
[17260866.588000] FAT: Directory bread(block 264) failed
[17260866.588000]  0:0:0:0: rejecting I/O to dead device
[17260866.588000] FAT: Directory bread(block 265) failed
[17260866.588000]  0:0:0:0: rejecting I/O to dead device
[17260866.588000] FAT: Directory bread(block 266) failed
[17260866.588000]  0:0:0:0: rejecting I/O to dead device
[17260866.588000] FAT: Directory bread(block 267) failed
[17260866.588000]  0:0:0:0: rejecting I/O to dead device
[17260866.588000] FAT: Directory bread(block 268) failed
[17260866.588000]  0:0:0:0: rejecting I/O to dead device
[17260866.588000] FAT: Directory bread(block 269) failed
[17260866.588000]  0:0:0:0: rejecting I/O to dead device
[17260866.588000] FAT: Directory bread(block 270) failed
[17260866.588000]  0:0:0:0: rejecting I/O to dead device
[17260866.588000] FAT: Directory bread(block 271) failed
[17260866.588000]  0:0:0:0: rejecting I/O to dead device
[17260866.588000] FAT: Directory bread(block 272) failed
[17260866.588000]  0:0:0:0: rejecting I/O to dead device
[17260866.588000] FAT: Directory bread(block 273) failed
[17260866.588000]  0:0:0:0: rejecting I/O to dead device
[17260866.588000] FAT: Directory bread(block 274) failed
[17260867.024000]  0:0:0:0: rejecting I/O to dead device
[17260867.024000] FAT: Directory bread(block 243) failed
[17260867.024000]  0:0:0:0: rejecting I/O to dead device
[17260867.024000] FAT: Directory bread(block 244) failed
[17260867.024000]  0:0:0:0: rejecting I/O to dead device
[17260867.024000] FAT: Directory bread(block 245) failed
[17260867.024000]  0:0:0:0: rejecting I/O to dead device
[17260867.024000] FAT: Directory bread(block 246) failed
[17260867.024000]  0:0:0:0: rejecting I/O to dead device
[17260867.024000] FAT: Directory bread(block 247) failed
[17260867.024000]  0:0:0:0: rejecting I/O to dead device
[17260867.024000] FAT: Directory bread(block 248) failed
[17260867.024000]  0:0:0:0: rejecting I/O to dead device
[17260867.024000] FAT: Directory bread(block 249) failed
[17260867.024000]  0:0:0:0: rejecting I/O to dead device
[17260867.028000] FAT: Directory bread(block 250) failed
[17260867.028000]  0:0:0:0: rejecting I/O to dead device
[17260867.028000] FAT: Directory bread(block 251) failed
[17260867.028000]  0:0:0:0: rejecting I/O to dead device
[17260867.028000] FAT: Directory bread(block 252) failed
[17260867.028000]  0:0:0:0: rejecting I/O to dead device
[17260867.028000] FAT: Directory bread(block 253) failed
[17260867.028000]  0:0:0:0: rejecting I/O to dead device
[17260867.028000] FAT: Directory bread(block 254) failed
[17260867.028000]  0:0:0:0: rejecting I/O to dead device
[17260867.028000] FAT: Directory bread(block 255) failed
[17260867.028000]  0:0:0:0: rejecting I/O to dead device
[17260867.028000] FAT: Directory bread(block 256) failed
[17260867.028000]  0:0:0:0: rejecting I/O to dead device
[17260867.028000] FAT: Directory bread(block 257) failed
[17260867.028000]  0:0:0:0: rejecting I/O to dead device
[17260867.028000] FAT: Directory bread(block 258) failed
[17260867.028000]  0:0:0:0: rejecting I/O to dead device
[17260867.028000] FAT: Directory bread(block 259) failed
[17260867.028000]  0:0:0:0: rejecting I/O to dead device
[17260867.028000] FAT: Directory bread(block 260) failed
[17260867.028000]  0:0:0:0: rejecting I/O to dead device
[17260867.028000] FAT: Directory bread(block 261) failed
[17260867.028000]  0:0:0:0: rejecting I/O to dead device
[17260867.028000] FAT: Directory bread(block 262) failed
[17260867.028000]  0:0:0:0: rejecting I/O to dead device
[17260867.028000] FAT: Directory bread(block 263) failed
[17260867.028000]  0:0:0:0: rejecting I/O to dead device
[17260867.028000] FAT: Directory bread(block 264) failed
[17260867.028000]  0:0:0:0: rejecting I/O to dead device
[17260867.028000] FAT: Directory bread(block 265) failed
[17260867.028000]  0:0:0:0: rejecting I/O to dead device
[17260867.028000] FAT: Directory bread(block 266) failed
[17260867.028000]  0:0:0:0: rejecting I/O to dead device
[17260867.028000] FAT: Directory bread(block 267) failed
[17260867.028000]  0:0:0:0: rejecting I/O to dead device
[17260867.028000] FAT: Directory bread(block 268) failed
[17260867.028000]  0:0:0:0: rejecting I/O to dead device
[17260867.028000] FAT: Directory bread(block 269) failed
[17260867.028000]  0:0:0:0: rejecting I/O to dead device
[17260867.028000] FAT: Directory bread(block 270) failed
[17260867.028000]  0:0:0:0: rejecting I/O to dead device
[17260867.028000] FAT: Directory bread(block 271) failed
[17260867.028000]  0:0:0:0: rejecting I/O to dead device
[17260867.028000] FAT: Directory bread(block 272) failed
[17260867.028000]  0:0:0:0: rejecting I/O to dead device
[17260867.028000] FAT: Directory bread(block 273) failed
[17260867.028000]  0:0:0:0: rejecting I/O to dead device
[17260867.028000] FAT: Directory bread(block 274) failed
[17260867.040000]  0:0:0:0: rejecting I/O to dead device
[17260867.040000] FAT: Directory bread(block 243) failed
[17260867.040000]  0:0:0:0: rejecting I/O to dead device
[17260867.040000] FAT: Directory bread(block 244) failed
[17260867.040000]  0:0:0:0: rejecting I/O to dead device
[17260867.040000] FAT: Directory bread(block 245) failed
[17260867.040000]  0:0:0:0: rejecting I/O to dead device
[17260867.040000] FAT: Directory bread(block 246) failed
[17260867.040000]  0:0:0:0: rejecting I/O to dead device
[17260867.040000] FAT: Directory bread(block 247) failed
[17260867.040000]  0:0:0:0: rejecting I/O to dead device
[17260867.040000] FAT: Directory bread(block 248) failed
[17260867.040000]  0:0:0:0: rejecting I/O to dead device
[17260867.040000] FAT: Directory bread(block 249) failed
[17260867.040000]  0:0:0:0: rejecting I/O to dead device
[17260867.040000] FAT: Directory bread(block 250) failed
[17260867.040000]  0:0:0:0: rejecting I/O to dead device
[17260867.040000] FAT: Directory bread(block 251) failed
[17260867.040000]  0:0:0:0: rejecting I/O to dead device
[17260867.040000] FAT: Directory bread(block 252) failed
[17260867.040000]  0:0:0:0: rejecting I/O to dead device
[17260867.040000] FAT: Directory bread(block 253) failed
[17260867.040000]  0:0:0:0: rejecting I/O to dead device
[17260867.040000] FAT: Directory bread(block 254) failed
[17260867.040000]  0:0:0:0: rejecting I/O to dead device
[17260867.040000] FAT: Directory bread(block 255) failed
[17260867.040000]  0:0:0:0: rejecting I/O to dead device
[17260867.040000] FAT: Directory bread(block 256) failed
[17260867.040000]  0:0:0:0: rejecting I/O to dead device
[17260867.040000] FAT: Directory bread(block 257) failed
[17260867.040000]  0:0:0:0: rejecting I/O to dead device
[17260867.040000] FAT: Directory bread(block 258) failed
[17260867.040000]  0:0:0:0: rejecting I/O to dead device
[17260867.040000] FAT: Directory bread(block 259) failed
[17260867.040000]  0:0:0:0: rejecting I/O to dead device
[17260867.040000] FAT: Directory bread(block 260) failed
[17260867.040000]  0:0:0:0: rejecting I/O to dead device
[17260867.040000] FAT: Directory bread(block 261) failed
[17260867.040000]  0:0:0:0: rejecting I/O to dead device
[17260867.040000] FAT: Directory bread(block 262) failed
[17260867.040000]  0:0:0:0: rejecting I/O to dead device
[17260867.040000] FAT: Directory bread(block 263) failed
[17260867.040000]  0:0:0:0: rejecting I/O to dead device
[17260867.040000] FAT: Directory bread(block 264) failed
[17260867.040000]  0:0:0:0: rejecting I/O to dead device
[17260867.040000] FAT: Directory bread(block 265) failed
[17260867.040000]  0:0:0:0: rejecting I/O to dead device
[17260867.040000] FAT: Directory bread(block 266) failed
[17260867.040000]  0:0:0:0: rejecting I/O to dead device
[17260867.040000] FAT: Directory bread(block 267) failed
[17260867.040000]  0:0:0:0: rejecting I/O to dead device
[17260867.040000] FAT: Directory bread(block 268) failed
[17260867.040000]  0:0:0:0: rejecting I/O to dead device
[17260867.040000] FAT: Directory bread(block 269) failed
[17260867.040000]  0:0:0:0: rejecting I/O to dead device
[17260867.040000] FAT: Directory bread(block 270) failed
[17260867.040000]  0:0:0:0: rejecting I/O to dead device
[17260867.040000] FAT: Directory bread(block 271) failed
[17260867.040000]  0:0:0:0: rejecting I/O to dead device
[17260867.040000] FAT: Directory bread(block 272) failed
[17260867.040000]  0:0:0:0: rejecting I/O to dead device
[17260867.040000] FAT: Directory bread(block 273) failed
[17260867.040000]  0:0:0:0: rejecting I/O to dead device
[17260867.040000] FAT: Directory bread(block 274) failed
[17260867.052000]  0:0:0:0: rejecting I/O to dead device
[17260867.060000] FAT: Directory bread(block 243) failed
[17260867.060000]  0:0:0:0: rejecting I/O to dead device
[17260867.060000] FAT: Directory bread(block 244) failed
[17260867.060000]  0:0:0:0: rejecting I/O to dead device
[17260867.060000] FAT: Directory bread(block 245) failed
[17260867.060000]  0:0:0:0: rejecting I/O to dead device
[17260867.060000] FAT: Directory bread(block 246) failed
[17260867.060000]  0:0:0:0: rejecting I/O to dead device
[17260867.060000] FAT: Directory bread(block 247) failed
[17260867.060000]  0:0:0:0: rejecting I/O to dead device
[17260867.060000] FAT: Directory bread(block 248) failed
[17260867.060000]  0:0:0:0: rejecting I/O to dead device
[17260867.060000] FAT: Directory bread(block 249) failed
[17260867.060000]  0:0:0:0: rejecting I/O to dead device
[17260867.060000] FAT: Directory bread(block 250) failed
[17260867.060000]  0:0:0:0: rejecting I/O to dead device
[17260867.060000] FAT: Directory bread(block 251) failed
[17260867.060000]  0:0:0:0: rejecting I/O to dead device
[17260867.060000] FAT: Directory bread(block 252) failed
[17260867.060000]  0:0:0:0: rejecting I/O to dead device
[17260867.060000] FAT: Directory bread(block 253) failed
[17260867.060000]  0:0:0:0: rejecting I/O to dead device
[17260867.060000] FAT: Directory bread(block 254) failed
[17260867.060000]  0:0:0:0: rejecting I/O to dead device
[17260867.060000] FAT: Directory bread(block 255) failed
[17260867.060000]  0:0:0:0: rejecting I/O to dead device
[17260867.060000] FAT: Directory bread(block 256) failed
[17260867.060000]  0:0:0:0: rejecting I/O to dead device
[17260867.060000] FAT: Directory bread(block 257) failed
[17260867.060000]  0:0:0:0: rejecting I/O to dead device
[17260867.060000] FAT: Directory bread(block 258) failed
[17260867.060000]  0:0:0:0: rejecting I/O to dead device
[17260867.060000] FAT: Directory bread(block 259) failed
[17260867.060000]  0:0:0:0: rejecting I/O to dead device
[17260867.060000] FAT: Directory bread(block 260) failed
[17260867.060000]  0:0:0:0: rejecting I/O to dead device
[17260867.060000] FAT: Directory bread(block 261) failed
[17260867.060000]  0:0:0:0: rejecting I/O to dead device
[17260867.060000] FAT: Directory bread(block 262) failed
[17260867.060000]  0:0:0:0: rejecting I/O to dead device
[17260867.060000] FAT: Directory bread(block 263) failed
[17260867.060000]  0:0:0:0: rejecting I/O to dead device
[17260867.060000] FAT: Directory bread(block 264) failed
[17260867.060000]  0:0:0:0: rejecting I/O to dead device
[17260867.060000] FAT: Directory bread(block 265) failed
[17260867.060000]  0:0:0:0: rejecting I/O to dead device
[17260867.060000] FAT: Directory bread(block 266) failed
[17260867.060000]  0:0:0:0: rejecting I/O to dead device
[17260867.060000] FAT: Directory bread(block 267) failed
[17260867.060000]  0:0:0:0: rejecting I/O to dead device
[17260867.060000] FAT: Directory bread(block 268) failed
[17260867.060000]  0:0:0:0: rejecting I/O to dead device
[17260867.060000] FAT: Directory bread(block 269) failed
[17260867.060000]  0:0:0:0: rejecting I/O to dead device
[17260867.060000] FAT: Directory bread(block 270) failed
[17260867.060000]  0:0:0:0: rejecting I/O to dead device
[17260867.060000] FAT: Directory bread(block 271) failed
[17260867.060000]  0:0:0:0: rejecting I/O to dead device
[17260867.060000] FAT: Directory bread(block 272) failed
[17260867.060000]  0:0:0:0: rejecting I/O to dead device
[17260867.060000] FAT: Directory bread(block 273) failed
[17260867.060000]  0:0:0:0: rejecting I/O to dead device
[17260867.060000] FAT: Directory bread(block 274) failed
[17260867.468000]  0:0:0:0: rejecting I/O to dead device
[17260867.468000] FAT: FAT read failed (blocknr 1)
[17260880.468000] ohci_hcd 0000:00:13.0: wakeup
[17260880.852000] usb 1-2: new full speed USB device using ohci_hcd and address 3
[17260881.052000] usb 1-2: not running at top speed; connect to a high speed hub
[17260881.072000] usb 1-2: configuration #1 chosen from 1 choice
[17260881.072000] scsi1 : SCSI emulation for USB Mass Storage devices
[17260881.072000] usb-storage: device found at 3
[17260881.072000] usb-storage: waiting for device to settle before scanning
[17260886.072000] usb-storage: device scan complete
[17260886.076000]   Vendor:           Model: USB Flash Memory  Rev: 1.00
[17260886.076000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17260886.392000] SCSI device sda: 246272 512-byte hdwr sectors (126 MB)
[17260886.396000] sda: Write Protect is off
[17260886.396000] sda: Mode Sense: 23 00 00 00
[17260886.396000] sda: assuming drive cache: write through
[17260886.420000] SCSI device sda: 246272 512-byte hdwr sectors (126 MB)
[17260886.428000] sda: Write Protect is off
[17260886.428000] sda: Mode Sense: 23 00 00 00
[17260886.428000] sda: assuming drive cache: write through
[17260886.428000]  sda: sda1
[17260886.436000] sd 1:0:0:0: Attached scsi removable disk sda
[17260886.436000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[17260887.112000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17260903.228000] usb 1-2: USB disconnect, address 3
[17260907.928000] usb 3-1: new full speed USB device using ohci_hcd and address 3
[17260908.124000] usb 3-1: not running at top speed; connect to a high speed hub
[17260908.148000] usb 3-1: configuration #1 chosen from 1 choice
[17260908.148000] scsi2 : SCSI emulation for USB Mass Storage devices
[17260908.148000] usb-storage: device found at 3
[17260908.148000] usb-storage: waiting for device to settle before scanning
[17260913.148000] usb-storage: device scan complete
[17260913.152000]   Vendor:           Model: USB Flash Memory  Rev: 1.00
[17260913.152000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17260913.548000] SCSI device sda: 246272 512-byte hdwr sectors (126 MB)
[17260913.552000] sda: Write Protect is off
[17260913.552000] sda: Mode Sense: 23 00 00 00
[17260913.552000] sda: assuming drive cache: write through
[17260913.564000] SCSI device sda: 246272 512-byte hdwr sectors (126 MB)
[17260913.568000] sda: Write Protect is off
[17260913.568000] sda: Mode Sense: 23 00 00 00
[17260913.568000] sda: assuming drive cache: write through
[17260913.568000]  sda: sda1
[17260913.580000] sd 2:0:0:0: Attached scsi removable disk sda
[17260913.580000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[17260914.264000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17260932.068000] usb 3-1: USB disconnect, address 3
[17260937.632000] ohci_hcd 0000:00:13.0: wakeup
[17260938.016000] usb 1-2: new full speed USB device using ohci_hcd and address 4
[17260938.216000] usb 1-2: not running at top speed; connect to a high speed hub
[17260938.236000] usb 1-2: configuration #1 chosen from 1 choice
[17260938.236000] scsi3 : SCSI emulation for USB Mass Storage devices
[17260938.236000] usb-storage: device found at 4
[17260938.236000] usb-storage: waiting for device to settle before scanning
[17260943.236000] usb-storage: device scan complete
[17260943.240000]   Vendor:           Model: USB Flash Memory  Rev: 1.00
[17260943.240000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17260943.652000] SCSI device sda: 246272 512-byte hdwr sectors (126 MB)
[17260943.656000] sda: Write Protect is off
[17260943.656000] sda: Mode Sense: 23 00 00 00
[17260943.656000] sda: assuming drive cache: write through
[17260943.680000] SCSI device sda: 246272 512-byte hdwr sectors (126 MB)
[17260943.688000] sda: Write Protect is off
[17260943.688000] sda: Mode Sense: 23 00 00 00
[17260943.688000] sda: assuming drive cache: write through
[17260943.688000]  sda: sda1
[17260943.696000] sd 3:0:0:0: Attached scsi removable disk sda
[17260943.696000] sd 3:0:0:0: Attached scsi generic sg0 type 0
[17260944.416000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17261040.352000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17261060.940000] usb 1-2: USB disconnect, address 4
[17261068.912000] ohci_hcd 0000:00:13.0: wakeup
[17261069.296000] usb 1-1: new full speed USB device using ohci_hcd and address 5
[17261069.588000] usb 1-1: configuration #1 chosen from 1 choice
[17261070.212000] usbcore: registered new driver snd-usb-audio
[17261085.676000] usb 1-2: new full speed USB device using ohci_hcd and address 6
[17261085.876000] usb 1-2: not running at top speed; connect to a high speed hub
[17261085.896000] usb 1-2: configuration #1 chosen from 1 choice
[17261085.896000] scsi4 : SCSI emulation for USB Mass Storage devices
[17261085.896000] usb-storage: device found at 6
[17261085.896000] usb-storage: waiting for device to settle before scanning
[17261090.896000] usb-storage: device scan complete
[17261090.900000]   Vendor:           Model: USB Flash Memory  Rev: 1.00
[17261090.900000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17261091.312000] SCSI device sda: 246272 512-byte hdwr sectors (126 MB)
[17261091.316000] sda: Write Protect is off
[17261091.316000] sda: Mode Sense: 23 00 00 00
[17261091.316000] sda: assuming drive cache: write through
[17261091.340000] SCSI device sda: 246272 512-byte hdwr sectors (126 MB)
[17261091.348000] sda: Write Protect is off
[17261091.348000] sda: Mode Sense: 23 00 00 00
[17261091.348000] sda: assuming drive cache: write through
[17261091.348000]  sda: sda1
[17261091.356000] sd 4:0:0:0: Attached scsi removable disk sda
[17261091.356000] sd 4:0:0:0: Attached scsi generic sg0 type 0
[17261092.020000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17261634.220000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
[17261740.824000] usb 1-1: USB disconnect, address 5
[17261753.388000] usb 3-1: new full speed USB device using ohci_hcd and address 4
[17261753.684000] usb 3-1: configuration #1 chosen from 1 choice
[17261771.480000] usb 3-1: USB disconnect, address 4
[17261823.608000] SoftMAC: Open Authentication completed with 00:17:3f:7f:d4:24
```

and when I run lsusb I get:

```
Bus 001 Device 007: ID 0930:651c Toshiba Corp. 
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 03f0:011d Hewlett-Packard 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000
```

---

### Post by lucky sevin on 2007-04-13
OK, never mind.  From another post I tried this:

sudo rmmod ohci_hcd
sudo rmmod ehci_hcd
sudo modprobe ehci_hcd
sudo modprobe ohci_hcd

worked like a charm

Thanks anyways.

---

