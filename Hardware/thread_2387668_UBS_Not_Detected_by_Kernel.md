---
title: "UBS Not Detected by Kernel"
date: 2018-03-22
forum: Hardware
---

### Post by holysword on 2018-03-22
Hello there,

I have a particular External HD  (USB) device which has a hard time being detected by the kernel in my Ubuntu laptop. And when I say "by the kernel" I mean "by the kernel", not by the automount system. Plugging the device in while dmesg -w is running shows no reaction. It is quite funny, though:

- External HD is not detected on any of the 3 ports of the Ubuntu laptop
- Other USB Devices are detected on all the 3 ports of the Ubuntu laptop
- External HD is detected on my other laptop (Gentoo Linux)
- External HD is detected if I boot the computer with it plugged in any of the 3 ports of the Ubuntu laptop
- External HD is detected whenever I connect it to an USB HUB, which is in turn connected to my Ubuntu laptop

This is the output whenever I plug the External HD through an USB HUB in my Ubuntu Laptop:
```
[ 4827.512434] usb 2-1.3: new high-speed USB device number 14 using xhci_hcd[ 4827.650250] usb 2-1.3: New USB device found, idVendor=0bc2, idProduct=ab24
[ 4827.650257] usb 2-1.3: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[ 4827.650261] usb 2-1.3: Product: BUP Slim BK
[ 4827.650266] usb 2-1.3: Manufacturer: Seagate
[ 4827.650270] usb 2-1.3: SerialNumber: NA7K0RKB
[ 4827.652251] scsi host4: uas
[ 4827.653254] scsi 4:0:0:0: Direct-Access     Seagate  BUP Slim BK      0302 PQ: 0 ANSI: 6
[ 4827.708728] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 4827.709246] sd 4:0:0:0: [sdb] Spinning up disk...
[ 4828.732434] .
[ 4829.756419] .
[ 4830.780403] .
[ 4830.780520] ready
[ 4830.781240] sd 4:0:0:0: [sdb] 3907029167 512-byte logical blocks: (2.00 TB/1.82 TiB)
[ 4830.781242] sd 4:0:0:0: [sdb] 2048-byte physical blocks
[ 4831.041911] sd 4:0:0:0: [sdb] Write Protect is off
[ 4831.041914] sd 4:0:0:0: [sdb] Mode Sense: 4f 00 00 00
[ 4831.042281] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 4831.091938]  sdb: sdb1
[ 4831.093977] sd 4:0:0:0: [sdb] Attached SCSI disk
```

This sounds very Kernel-related, but I might be wrong. Any ideas here?

---

