---
title: "Android problem"
date: 2011-02-15
forum: Hardware
---

### Post by Jiawen on 2011-02-15
Tonight, I did a kernel update (linux-headers-2.6.24-28 (2.6.24-28.84) to 2.6.24-28.86, according to Synaptic). After rebooting the machine, my Android phone stopped mounting correctly; when I plug it into the USB connector, it continually brings up the "Connect to PC" menu, then shuts it down, then cycles again. Regardless of what options I choose, the phone just keeps cycling through this. It becomes completely unusable while it's doing this. /var/log/messages shows

```
Feb 15 21:13:46 computer kernel: [ 1704.852424] usb 6-6.3: new high speed USB device using ehci_hcd and address 113
Feb 15 21:13:46 computer kernel: [ 1704.957064] usb 6-6.3: configuration #1 chosen from 1 choice
Feb 15 21:13:46 computer kernel: [ 1705.028320] scsi110 : SCSI emulation for USB Mass Storage devices
Feb 15 21:13:48 computer kernel: [ 1706.444208] usb 6-6.3: USB disconnect, address 113
```

What should I do?

---

### Post by quicloud on 2011-06-28
Had the same issue, turns out it was a USB hub (probably not getting enough juice). Plugged USB cable directly into my machine & problems disappeared.

Cheers,
-r

---

