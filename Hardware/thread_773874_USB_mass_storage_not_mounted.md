---
title: "USB mass storage not mounted"
date: 2008-04-29
forum: Hardware
---

### Post by Emanuele75 on 2008-04-29
Hi to all!

This is my first Thread...apologize me for any mistake!

I've installed Ubuntu 8.04 on my Compaq nx 6110 and works great!
I've a BIG problem with my external ide disk attached on a usb device.
When i plug in it the system doesn't mount the usb disk.

my dmesg say:
[15511.255096] usb 1-2: USB disconnect, address 9
[11641.936169] usb 5-2: new high speed USB device using ehci_hcd and address 17
[11642.107846] usb 5-2: configuration #1 chosen from 1 choice
[11642.132676] scsi11 : SCSI emulation for USB Mass Storage devices
[11642.148194] usb-storage: device found at 17
[11642.148205] usb-storage: waiting for device to settle before scanning
[15531.076370] usb-storage: device scan complete
[15545.864584] usb 5-2: USB disconnect, address 17
[15545.865037] scsi 11:0:0:0: Device offlined - not ready after error recovery

Can anyone help me, please?
with 7.10 there was no problem...

Thanks to all...

---

### Post by Yellow Onion on 2008-05-03
perhaps it's the same problem this [http://ubuntuforums.org/showthread.php?t=745672](http://ubuntuforums.org/showthread.php?t=745672)

---

