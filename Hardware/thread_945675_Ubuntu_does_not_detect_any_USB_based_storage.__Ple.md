---
title: "Ubuntu does not detect any USB based storage.  Please help."
date: 2008-10-12
forum: Hardware
---

### Post by SGFHK321 on 2008-10-12
My new ubuntu (64bit Hardy) machine is almost perfect, except for the fact that USB sticks and HDDs don't work.  As far as I know they can't even be detected by the system (remain un-powered). But my generic USB wireless keyboard and mouse work flawlessly. The usb-based internal card reader work as well.  I stick an SD card in and it automounts.  

Here is what lsusb reports:
> Bus 005 Device 000: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 005 Device 001: ID 0000:0000 
Bus 004 Device 001: ID 0000:0000 
Bus 003 Device 001: ID 0000:0000 
Bus 002 Device 003: ID 04fc:05d8 Sunplus Technology Co., Ltd 
Bus 002 Device 001: ID 0000:0000 
Bus 001 Device 001: ID 0000:0000

dmesg reports some kind of "device descriptor read/..."

I tried the bios and no luck.  It seems to be an ehci thing.  Perhaps linux is not getting the right stuffs from the motherboard, who thinks the OS is windows.

Help much needed and appreciated.

---

### Post by cariboo on 2008-10-12
Please post the output of dmesg when you plug one of the devices in. you should get an output something like this:

```
[11934.493994] usb-storage: device found at 7
[11934.494004] usb-storage: waiting for device to settle before scanning
[11939.492288] usb-storage: device scan complete
[11939.494704] scsi 7:0:0:0: Direct-Access     JetFlash TS2GJFV10        0.00 PQ: 0 ANSI: 2
[11939.497579] sd 7:0:0:0: [sdc] 4030463 512-byte hardware sectors (2064 MB)
[11939.498573] sd 7:0:0:0: [sdc] Write Protect is off
[11939.498582] sd 7:0:0:0: [sdc] Mode Sense: 00 00 00 00
[11939.498584] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[11939.501066] sd 7:0:0:0: [sdc] 4030463 512-byte hardware sectors (2064 MB)
[11939.502604] sd 7:0:0:0: [sdc] Write Protect is off
[11939.502612] sd 7:0:0:0: [sdc] Mode Sense: 00 00 00 00
[11939.502615] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[11939.502992]  sdc: sdc1
[11939.608511] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[11939.609633] sd 7:0:0:0: Attached scsi generic sg3 type 0
```

Jim

---

### Post by SGFHK321 on 2008-10-13
I think, I hope, this is what you are asking for...

> [  121.693517] usb 5-8: new high speed USB device using ehci_hcd and address 4
[  122.217515] usb 5-8: device not accepting address 4, error -71
[  122.329736] usb 5-8: new high speed USB device using ehci_hcd and address 5
[  132.850111] usb 5-8: device not accepting address 5, error -71
[  132.961536] usb 5-8: new high speed USB device using ehci_hcd and address 6
[  138.369534] usb 5-8: device not accepting address 6, error -71
[  138.481972] usb 5-8: new high speed USB device using ehci_hcd and address 7
[  138.503784] usb 5-8: device descriptor read/8, error -71
[  138.624604] usb 5-8: device descriptor read/8, error -71


This happens after a USB stick or USB HDD is inserted.  This has nothing to do with file format I assume.  It is not even detecting properly.

Thanks Jim.

---

### Post by SGFHK321 on 2008-10-15
anyone? :(

---

### Post by Akamashi on 2008-10-17
I have the same problem. This is what I'm getting when I boot up:

> [  235.716948] usb 6-4: reset high speed USB device using ehci_hcd and address 4
[  251.265382] usb 6-4: device not accepting address 4, error -110
[  251.377332] usb 6-4: reset high speed USB device using ehci_hcd and address 4
[  266.925776] usb 6-4: device not accepting address 4, error -110
[  267.038724] usb 6-4: reset high speed USB device using ehci_hcd and address 4
[  277.464656] usb 6-4: device not accepting address 4, error -110
[  277.576604] usb 6-4: reset high speed USB device using ehci_hcd and address 4
[  288.004525] usb 6-4: device not accepting address 4, error -110
[  288.004600] usb 6-4: USB disconnect, address 4
[  288.005058] scsi 6:0:0:0: Device offlined - not ready after error recovery
[  288.008531] scsi 6:0:0:0: [sdc] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK


---

### Post by mgangav on 2008-10-17
I have the same problem, but with a USB mouse in my case. Here is what I got:

> 
[ 1095.451685] usb 4-1: new low speed USB device using uhci_hcd and address 10
[ 1095.571477] usb 4-1: device descriptor read/64, error -71
[ 1095.795078] usb 4-1: device descriptor read/64, error -71
[ 1096.011769] usb 4-1: new low speed USB device using uhci_hcd and address 11
[ 1096.134595] usb 4-1: device descriptor read/64, error -71
[ 1096.358199] usb 4-1: device descriptor read/64, error -71
[ 1096.573870] usb 4-1: new low speed USB device using uhci_hcd and address 12
[ 1096.981239] usb 4-1: device not accepting address 12, error -71
[ 1097.093071] usb 4-1: new low speed USB device using uhci_hcd and address 13
[ 1097.507441] usb 4-1: device not accepting address 13, error -71



---

### Post by gfclement on 2008-10-17
Booting back into the older kernel solves this issue.  Following the directions given earlier to boot into the older kernel.  Anyone know if a bug report has been filed?

---

