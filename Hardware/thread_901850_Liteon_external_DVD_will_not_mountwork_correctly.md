---
title: "Liteon external DVD will not mount/work correctly"
date: 2008-08-26
forum: Hardware
---

### Post by nate_2001 on 2008-08-26
I just bought this slim DX-8A1H-05 DVD burner expecting it to be plug and play with 8.04.  It's not.

output of dmesg | tail:

```
[  959.781843] scsi14 : SCSI emulation for USB Mass Storage devices
[  959.784567] usb-storage: device found at 11
[  959.784571] usb-storage: waiting for device to settle before scanning
[  962.894757] usb-storage: device scan complete
[  962.932555] scsi 14:0:0:0: CD-ROM            Slimtype DVD A  DS8A1H    WX14 PQ: 0 ANSI: 0
[  963.555936] sr1: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[  963.556001] sr 14:0:0:0: Attached scsi CD-ROM sr1
[  963.556058] sr 14:0:0:0: Attached scsi generic sg3 type 5
[  964.692899] usb 1-6: reset high speed USB device using ehci_hcd and address 11
[  964.808905] usb 1-6: reset high speed USB device using ehci_hcd and address 11
nathan@nathan-laptop:~$ dmesg | tail
[  963.556001] sr 14:0:0:0: Attached scsi CD-ROM sr1
[  963.556058] sr 14:0:0:0: Attached scsi generic sg3 type 5
[  964.692899] usb 1-6: reset high speed USB device using ehci_hcd and address 11
[  964.808905] usb 1-6: reset high speed USB device using ehci_hcd and address 11
[  971.890400] usb 1-6: reset high speed USB device using ehci_hcd and address 11
[  972.004134] usb 1-6: reset high speed USB device using ehci_hcd and address 11
[  972.064383] sr1: CDROM (ioctl) error, command: Read TOC/PMA/ATIP 43 00 00 00 00 00 00 00 0c 40
[  972.064399] sr: Sense Key : 0xf [deferred] [descriptor]
[  972.064402] sr: ASC=0x7f <<vendor>> ASCQ=0xff
[  972.120180] usb 1-6: reset high speed USB device using ehci_hcd and address 11

```

Which makes sense.  The drive picks up, then makes a little resetting noise and picks up again repeatedly. 

Thanks!

---

