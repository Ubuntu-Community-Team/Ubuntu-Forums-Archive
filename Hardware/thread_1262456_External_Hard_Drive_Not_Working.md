---
title: "External Hard Drive Not Working"
date: 2009-09-09
forum: Hardware
---

### Post by Sickify on 2009-09-09
Hello All,

Recently out of the blue my external hard drive has stopped working completely under Ubuntu on my laptop only. The drive is a Comstar 500gb drive. I went out and bought a new, more reliable, 1tb drive to copy all of my data onto.

Plugging in the 1tb drive works. When I plug in the 500gb drive it fails to show up at all. In my system logs I have the following;

Sep  9 20:17:58 braydon-laptop kernel: [ 6657.888073] usb 1-3: new high speed USB device using ehci_hcd and address 36
Sep  9 20:17:58 braydon-laptop kernel: [ 6658.021177] usb 1-3: configuration #1 chosen from 1 choice
Sep  9 20:17:58 braydon-laptop kernel: [ 6658.022084] scsi10 : SCSI emulation for USB Mass Storage devices
Sep  9 20:17:58 braydon-laptop kernel: [ 6658.022453] usb-storage: device found at 36
Sep  9 20:17:58 braydon-laptop kernel: [ 6658.022459] usb-storage: waiting for device to settle before scanning
Sep  9 20:18:03 braydon-laptop kernel: [ 6663.020292] usb-storage: device scan complete
Sep  9 20:18:03 braydon-laptop kernel: [ 6663.020902] scsi 10:0:0:0: Direct-Access     WDC WD50 00AAVS-00ZTB0         PQ: 0 ANSI: 2 CCS
Sep  9 20:18:03 braydon-laptop kernel: [ 6663.021909] sd 10:0:0:0: Attached scsi generic sg3 type 0
Sep  9 20:18:03 braydon-laptop kernel: [ 6663.023236] sd 10:0:0:0: [sdc] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Sep  9 20:18:03 braydon-laptop kernel: [ 6663.030112] sd 10:0:0:0: [sdc] Write Protect is off
Sep  9 20:18:03 braydon-laptop kernel: [ 6663.030123] sd 10:0:0:0: [sdc] Mode Sense: 34 00 00 00
Sep  9 20:18:03 braydon-laptop kernel: [ 6663.030130] sd 10:0:0:0: [sdc] Assuming drive cache: write through
Sep  9 20:18:03 braydon-laptop kernel: [ 6663.034234] sd 10:0:0:0: [sdc] Assuming drive cache: write through
Sep  9 20:18:03 braydon-laptop kernel: [ 6663.034246]  sdc: sdc1 sdc2 < sdc5 >
Sep  9 20:18:03 braydon-laptop kernel: [ 6663.062608] sd 10:0:0:0: [sdc] Assuming drive cache: write through
Sep  9 20:18:03 braydon-laptop kernel: [ 6663.062620] sd 10:0:0:0: [sdc] Attached SCSI disk
Sep  9 20:18:04 braydon-laptop kernel: [ 6663.264088] usb 1-3: reset high speed USB device using ehci_hcd and address 36
Sep  9 20:18:04 braydon-laptop kernel: [ 6663.388076] usb 1-3: device descriptor read/64, error -71
Sep  9 20:18:04 braydon-laptop kernel: [ 6663.616037] usb 1-3: device descriptor read/64, error -71
Sep  9 20:18:04 braydon-laptop kernel: [ 6663.832087] usb 1-3: reset high speed USB device using ehci_hcd and address 36
Sep  9 20:18:04 braydon-laptop kernel: [ 6663.956089] usb 1-3: device descriptor read/64, error -71
Sep  9 20:18:05 braydon-laptop kernel: [ 6664.184041] usb 1-3: device descriptor read/64, error -71
Sep  9 20:18:05 braydon-laptop kernel: [ 6664.400097] usb 1-3: reset high speed USB device using ehci_hcd and address 36
Sep  9 20:18:05 braydon-laptop kernel: [ 6664.816076] usb 1-3: device not accepting address 36, error -71
Sep  9 20:18:05 braydon-laptop kernel: [ 6664.928085] usb 1-3: reset high speed USB device using ehci_hcd and address 36
Sep  9 20:18:06 braydon-laptop kernel: [ 6665.344057] usb 1-3: device not accepting address 36, error -71
Sep  9 20:18:06 braydon-laptop kernel: [ 6665.344151] usb 1-3: USB disconnect, address 36
Sep  9 20:18:06 braydon-laptop kernel: [ 6665.456084] usb 1-3: new high speed USB device using ehci_hcd and address 37
Sep  9 20:18:06 braydon-laptop kernel: [ 6665.580084] usb 1-3: device descriptor read/64, error -71
Sep  9 20:18:06 braydon-laptop kernel: [ 6665.808152] usb 1-3: device descriptor read/64, error -71
Sep  9 20:18:06 braydon-laptop kernel: [ 6666.024050] usb 1-3: new high speed USB device using ehci_hcd and address 38
Sep  9 20:18:07 braydon-laptop kernel: [ 6666.148133] usb 1-3: device descriptor read/64, error -71
Sep  9 20:18:07 braydon-laptop kernel: [ 6666.376101] usb 1-3: device descriptor read/64, error -71
Sep  9 20:18:07 braydon-laptop kernel: [ 6666.593067] usb 1-3: new high speed USB device using ehci_hcd and address 39
Sep  9 20:18:07 braydon-laptop kernel: [ 6667.008045] usb 1-3: device not accepting address 39, error -71
Sep  9 20:18:08 braydon-laptop kernel: [ 6667.120060] usb 1-3: new high speed USB device using ehci_hcd and address 40
Sep  9 20:18:08 braydon-laptop kernel: [ 6667.536059] usb 1-3: device not accepting address 40, error -71
Sep  9 20:18:08 braydon-laptop kernel: [ 6667.536096] hub 1-0:1.0: unable to enumerate USB device on port 3
Sep  9 20:18:08 braydon-laptop kernel: [ 6667.804068] usb 3-1: new full speed USB device using uhci_hcd and address 10
Sep  9 20:18:08 braydon-laptop kernel: [ 6667.928059] usb 3-1: device descriptor read/64, error -71
Sep  9 20:18:09 braydon-laptop kernel: [ 6668.152085] usb 3-1: device descriptor read/64, error -71
Sep  9 20:18:09 braydon-laptop kernel: [ 6668.368114] usb 3-1: new full speed USB device using uhci_hcd and address 11
Sep  9 20:18:09 braydon-laptop kernel: [ 6668.492037] usb 3-1: device descriptor read/64, error -71
Sep  9 20:18:09 braydon-laptop kernel: [ 6668.716069] usb 3-1: device descriptor read/64, error -71
Sep  9 20:18:09 braydon-laptop kernel: [ 6668.932086] usb 3-1: new full speed USB device using uhci_hcd and address 12
Sep  9 20:18:10 braydon-laptop kernel: [ 6669.348055] usb 3-1: device not accepting address 12, error -71
Sep  9 20:18:10 braydon-laptop kernel: [ 6669.460071] usb 3-1: new full speed USB device using uhci_hcd and address 13
Sep  9 20:18:10 braydon-laptop kernel: [ 6669.876074] usb 3-1: device not accepting address 13, error -71
Sep  9 20:18:10 braydon-laptop kernel: [ 6669.876107] hub 3-0:1.0: unable to enumerate USB device on port 1

Messages;

Sep  9 20:17:58 braydon-laptop kernel: [ 6657.888073] usb 1-3: new high speed USB device using ehci_hcd and address 36
Sep  9 20:17:58 braydon-laptop kernel: [ 6658.021177] usb 1-3: configuration #1 chosen from 1 choice
Sep  9 20:17:58 braydon-laptop kernel: [ 6658.022084] scsi10 : SCSI emulation for USB Mass Storage devices
Sep  9 20:18:03 braydon-laptop kernel: [ 6663.020902] scsi 10:0:0:0: Direct-Access     WDC WD50 00AAVS-00ZTB0         PQ: 0 ANSI: 2 CCS
Sep  9 20:18:03 braydon-laptop kernel: [ 6663.021909] sd 10:0:0:0: Attached scsi generic sg3 type 0
Sep  9 20:18:03 braydon-laptop kernel: [ 6663.023236] sd 10:0:0:0: [sdc] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Sep  9 20:18:03 braydon-laptop kernel: [ 6663.030112] sd 10:0:0:0: [sdc] Write Protect is off
Sep  9 20:18:03 braydon-laptop kernel: [ 6663.034246]  sdc: sdc1 sdc2 < sdc5 >

Any help getting this device to read and mount would be much appreciated. Thank you.

---

### Post by Truefire on 2009-09-09
Whew. Looks like it's getting quite a few read errors there. Was the 500GB ever dropped? Do you leave it plugged in? They're not all that durable, and I hope the answer to both is negative. Sounds like hardware to me. Does it work in any other computers?

---

### Post by Sickify on 2009-09-09
Nope, never dropped. Apparently the comstar interface is fairly flaky and tends to fail after awhile, but the drive works on my girlfriends laptop (also running Ubuntu) flawlessly.

---

