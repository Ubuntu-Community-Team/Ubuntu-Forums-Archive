---
title: "USB floppy drive is running without floppy"
date: 2015-02-04
forum: Hardware
---

### Post by P_Aleksandrov on 2015-02-04
When I connect USB floppy drive (Gembird) without floppy under Ubuntu, the drive engine seems to be running (the floppy drive LED is on and the drive is sounding). The same behaviour takes place if I connect the drive with a floppy and then remove the floppy. It seems that the system accesses the drive permanently when there is no floppy. Under Windows XP it works normally - when there is no floppy, the LED and engine are switched off. How can I solve the problem? I have tried Ubuntu 14.10 with LXQt and KDE 5 - the same behaviour.

---

### Post by P_Aleksandrov on 2015-02-19
The output from dmesg:

[  963.125481] usb 5-1.3: new full-speed USB device number 10 using xhci_hcd
[  963.233017] usb 5-1.3: New USB device found, idVendor=0644, idProduct=0000
[  963.233036] usb 5-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[  963.233045] usb 5-1.3: Product: TEACV1.0
[  963.233053] usb 5-1.3: Manufacturer: TEACV1.0
[  963.233664] usb 5-1.3: ep 0x81 - rounding interval to 512 microframes, ep desc says 1016 microframes
[  963.235149] usb-storage 5-1.3:1.0: USB Mass Storage device detected
[  963.235476] scsi8 : usb-storage 5-1.3:1.0
[  964.248569] scsi 8:0:0:0: Direct-Access     TEAC     USB UF000x       1.00 PQ: 0 ANSI: 0 CCS
[  964.249878] sd 8:0:0:0: Attached scsi generic sg1 type 0
[  964.376544] sd 8:0:0:0: [sdb] Attached SCSI removable disk

"lsof /dev/sdb" outputs nothing.

---

