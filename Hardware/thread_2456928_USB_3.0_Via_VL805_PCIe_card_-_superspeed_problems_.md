---
title: "USB 3.0 Via VL805 PCIe card - superspeed problems with SSD"
date: 2021-01-21
forum: Hardware
---

### Post by jmorrison-w on 2021-01-21
I installed a VL805 PCIe USB 3.0 card and I'm having performance problems with certain devices.

It's alright on some USB 3 devices like external hard drives but with a USB3 to SATA cable and SSD it's slow.
With the SSD get kB/s and error messages logged
USB3 hard disk get 100 MB/s

I have tested the USB3 SATA cable + SSD on another system and I get over 400 MB/s


```
 hdparm -I /dev/sdh


/dev/sdh:


ATA device, with non-removable media
        Model Number:       KINGSTON SA400S37120G
        Serial Number:       xxx
        Firmware Revision:  SBFK71E0
        Transport:          Serial, ATA8-AST, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6, SATA Rev 3.0


]hdparm -t /dev/sdh


/dev/sdh:
 Timing buffered disk reads:  10 MB in 32.93 seconds =   310.98 kB/sec

```

```
dmesg
[ 9906.028803] usb 4-2: reset SuperSpeed USB device number 3 using xhci_hcd
[10357.740050] sd 7:0:0:0: [sdh] tag#0 uas_eh_abort_handler 0 uas-tag 1 inflight: CMD IN
[10357.740062] sd 7:0:0:0: [sdh] tag#0 CDB: Read(10) 28 00 00 01 b8 00 00 04 00 00
[10357.740144] sd 7:0:0:0: [sdh] tag#1 uas_eh_abort_handler 0 uas-tag 2 inflight: CMD IN
[10357.740149] sd 7:0:0:0: [sdh] tag#1 CDB: Read(10) 28 00 00 01 b4 00 00 04 00 00
[10357.752120] scsi host7: uas_eh_device_reset_handler start
[10357.880734] usb 4-3: reset SuperSpeed USB device number 5 using xhci_hcd
[10357.904153] scsi host7: uas_eh_device_reset_handler success


```

On the same controller and USB 3 harddrive I get 94 MB/s


```
/dev/sdg:
ATA device, with non-removable media
        Model Number:       WDC WD30NMZW-11GX6S1
        Serial Number:      xxx
        Firmware Revision:  01.01A01
        Transport:          Serial, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6, SATA Rev 3.0

hdparm -t /dev/sdg


/dev/sdg:
 Timing buffered disk reads: 284 MB in  3.01 seconds =  94.45 MB/sec







```

---

