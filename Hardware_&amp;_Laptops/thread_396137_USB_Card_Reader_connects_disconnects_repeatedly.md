---
title: "USB Card Reader connects disconnects repeatedly"
date: 2007-03-29
forum: Hardware &amp; Laptops
---

### Post by Plecebo on 2007-03-29
I have an annoying problem that continues to plague me. My USB card reader continually disconnects then immediately after it re-connects. It seems to happen every few minutes (2-4) and of course it is usually when I have just started a transfer of gigs of files from the card to the computer. 

I've been trying to troubleshoot and think I have an indication what the problem is... but no idea how to troubleshoot further and/or fix it. 

here is my dmsg output right after one disconnect: 
```
[17182453.540000] SCSI device sdd: 8040448 512-byte hdwr sectors (4117 MB)
[17182453.544000] sdd: Write Protect is off
[17182453.544000] sdd: Mode Sense: 03 00 00 00
[17182453.544000] sdd: assuming drive cache: write through
[17182453.548000] SCSI device sdd: 8040448 512-byte hdwr sectors (4117 MB)
[17182453.552000] sdd: Write Protect is off
[17182453.552000] sdd: Mode Sense: 03 00 00 00
[17182453.552000] sdd: assuming drive cache: write through
[17182453.552000]  sdd: sdd1
[17182455.556000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17182455.672000] usb 2-1: reset high speed USB device using ehci_hcd and address 12
[17182456.660000] usb 2-1: reset high speed USB device using ehci_hcd and address 12
[17182469.192000] set_rtc_mmss: can't update from 58 to 11
[17182470.192000] set_rtc_mmss: can't update from 58 to 11
[17182471.192000] set_rtc_mmss: can't update from 58 to 11
[17182472.192000] set_rtc_mmss: can't update from 58 to 11
[17182473.192000] set_rtc_mmss: can't update from 58 to 11
[17182474.192000] set_rtc_mmss: can't update from 58 to 11
[17182475.192000] set_rtc_mmss: can't update from 58 to 11
[17182476.192000] set_rtc_mmss: can't update from 58 to 11
[17182477.192000] set_rtc_mmss: can't update from 58 to 11
[17182478.192000] set_rtc_mmss: can't update from 58 to 11
[17182479.192000] set_rtc_mmss: can't update from 58 to 11
[17182480.192000] set_rtc_mmss: can't update from 58 to 11
[17182481.192000] set_rtc_mmss: can't update from 58 to 11
[17182482.192000] set_rtc_mmss: can't update from 58 to 11
[17182483.192000] set_rtc_mmss: can't update from 58 to 12
[17182483.836000] usb 2-1: reset high speed USB device using ehci_hcd and address 12
[17182484.192000] set_rtc_mmss: can't update from 58 to 12
[17182485.192000] set_rtc_mmss: can't update from 58 to 12
[17182486.192000] set_rtc_mmss: can't update from 58 to 12
[17182487.192000] set_rtc_mmss: can't update from 58 to 12
[17182488.192000] set_rtc_mmss: can't update from 58 to 12
[17182489.192000] set_rtc_mmss: can't update from 58 to 12
[17182497.072000] usb 2-1: reset high speed USB device using ehci_hcd and address 12
[17182498.176000] usb 2-1: reset high speed USB device using ehci_hcd and address 12
[17182508.192000] set_rtc_mmss: can't update from 58 to 12
[17182511.192000] set_rtc_mmss: can't update from 58 to 12
[17182512.192000] set_rtc_mmss: can't update from 58 to 12
[17182513.192000] set_rtc_mmss: can't update from 58 to 12
[17182514.192000] set_rtc_mmss: can't update from 58 to 12
[17182515.192000] set_rtc_mmss: can't update from 58 to 12
[17182516.192000] set_rtc_mmss: can't update from 58 to 12
[17182517.192000] set_rtc_mmss: can't update from 58 to 12
[17182518.192000] set_rtc_mmss: can't update from 58 to 12
[17182519.192000] set_rtc_mmss: can't update from 58 to 12
[17182520.192000] set_rtc_mmss: can't update from 58 to 12
[17182521.192000] set_rtc_mmss: can't update from 58 to 12
[17182522.192000] set_rtc_mmss: can't update from 58 to 12
[17182523.192000] set_rtc_mmss: can't update from 58 to 12
[17182524.192000] set_rtc_mmss: can't update from 58 to 12
[17182525.192000] set_rtc_mmss: can't update from 58 to 12
[17182526.192000] set_rtc_mmss: can't update from 58 to 12
[17182527.192000] set_rtc_mmss: can't update from 58 to 12
[17182528.192000] set_rtc_mmss: can't update from 58 to 12
[17182529.192000] set_rtc_mmss: can't update from 58 to 12
[17182530.192000] set_rtc_mmss: can't update from 58 to 12
[17182564.432000] usb 2-1: reset high speed USB device using ehci_hcd and address 12
[17182568.716000] usb 2-1: reset high speed USB device using ehci_hcd and address 12
[17182601.188000] usb 2-1: reset high speed USB device using ehci_hcd and address 12
[17182621.640000] usb 2-1: reset high speed USB device using ehci_hcd and address 12
[17182679.792000] usb 2-1: reset high speed USB device using ehci_hcd and address 12
[17182679.924000] usb 2-1: device firmware changed
[17182679.924000] usb 2-1: USB disconnect, address 12
[17182679.924000] sdd : READ CAPACITY failed.
[17182679.924000] sdd : status=0, message=00, host=7, driver=00 
[17182679.924000] sdd : sense not available. 
[17182679.924000] sdf : READ CAPACITY failed.
[17182679.924000] sdf : status=0, message=00, host=7, driver=00 
[17182679.924000] sdf : sense not available. 
[17182679.928000] sdd: Write Protect is off
[17182679.928000] sdd: Mode Sense: 00 00 00 00
[17182679.928000] sdd: assuming drive cache: write through
[17182679.928000] sdf: Write Protect is off
[17182679.928000] sdf: Mode Sense: 00 00 00 00
[17182679.928000] sdf: assuming drive cache: write through
[17182679.928000] sdf : READ CAPACITY failed.
[17182679.928000] sdf : status=0, message=00, host=1, driver=00 
[17182679.928000] sdf : sense not available. 
[17182679.928000] sdf: Write Protect is off
[17182679.928000] sdf: Mode Sense: 00 00 00 00
[17182679.928000] sdf: assuming drive cache: write through
[17182679.928000]  sdf:<3>Buffer I/O error on device sdf, logical block 0
[17182679.928000] Buffer I/O error on device sdf, logical block 0
[17182679.928000]  unable to read partition table
[17182680.052000] usb 2-1: new high speed USB device using ehci_hcd and address 13
[17182680.188000] usb 2-1: configuration #1 chosen from 1 choice
[17182680.188000] scsi12 : SCSI emulation for USB Mass Storage devices
[17182680.188000] usb-storage: device found at 13
[17182680.188000] usb-storage: waiting for device to settle before scanning
[17182685.188000] usb-storage: device scan complete
[17182685.188000]   Vendor: Generic   Model: USB SD Reader     Rev: 1.00
[17182685.188000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17182685.192000]   Vendor: Generic   Model: USB CF Reader     Rev: 1.01
[17182685.192000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17182685.192000]   Vendor: Generic   Model: USB SM Reader     Rev: 1.02
[17182685.192000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17182685.192000]   Vendor: Generic   Model: USB MS Reader     Rev: 1.03
[17182685.192000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17182685.536000] SCSI device sdd: 8040448 512-byte hdwr sectors (4117 MB)
[17182685.540000] sdd: Write Protect is off
[17182685.540000] sdd: Mode Sense: 03 00 00 00
[17182685.540000] sdd: assuming drive cache: write through
[17182685.544000] SCSI device sdd: 8040448 512-byte hdwr sectors (4117 MB)
[17182685.548000] sdd: Write Protect is off
[17182685.548000] sdd: Mode Sense: 03 00 00 00
[17182685.548000] sdd: assuming drive cache: write through
[17182685.548000]  sdd: sdd1
[17182685.548000] sd 12:0:0:0: Attached scsi removable disk sdd
[17182685.548000] sd 12:0:0:0: Attached scsi generic sg3 type 0
[17182685.556000] sd 12:0:0:1: Attached scsi removable disk sde
[17182685.556000] sd 12:0:0:1: Attached scsi generic sg4 type 0
[17182685.564000] sd 12:0:0:2: Attached scsi removable disk sdf
[17182685.564000] sd 12:0:0:2: Attached scsi generic sg5 type 0
[17182685.576000] sd 12:0:0:3: Attached scsi removable disk sdg
[17182685.576000] sd 12:0:0:3: Attached scsi generic sg6 type 0
[17182686.092000] usb 2-1: reset high speed USB device using ehci_hcd and address 13
[17182688.468000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

``` 

The problem seems to be this line... it may be the cause of the disconnects.... 
```

[17182679.924000] usb 2-1: device firmware changed

```

I have no idea what to try next. 

The card/card reader combo works well on my laptop that runs 6.10 like my desktop does (where i'm having the trouble). 
Other USB devices (keyboard/mouse) seem to work fine all the time. 
I've tried all the USB ports on this computer (8 in total) and all give the same behavior. 

The board is nforce4 based... so has whatever the nforce4 chipset for USB controllers is. 

Any help that anyone can provide would be splendid... and I thank you in advance for it.

---

### Post by Plecebo on 2007-03-29
Anyone have any advice?

---

