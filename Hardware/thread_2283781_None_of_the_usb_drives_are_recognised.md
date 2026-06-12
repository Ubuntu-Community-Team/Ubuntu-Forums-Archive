---
title: "None of the usb drives are recognised"
date: 2015-06-24
forum: Hardware
---

### Post by chandradeep1981 on 2015-06-24
Since last few days my ubuntu 14.04 is not recognising any of my usb drives. On the contrary my windows pc is recognising them. what to do. whether any upgrade is needed to ubuntu . pl help.

---

### Post by VMC on 2015-06-24
From a Terminal(Alt+Ctrl+t) type '*dmesg*' and see what it states regarding usb.

---

### Post by chandradeep1981 on 2015-06-26
I got these LINES related to usb when i typed dmesg.
I cant understand them. what next ? Pl. help

[   22.265134] ---[ end trace 8da493ecfa45a708 ]---
[   22.469363] usb 3-12: Device not responding to set address.
[   22.673301] usb 3-12: device not accepting address 5, error -71
[   22.785417] usb 3-12: new full-speed USB device number 6 using xhci_hcd
[   22.802675] usb 3-12: New USB device found, idVendor=0cf3, idProduct=311f
[   22.802678] usb 3-12: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[   23.517960] xhci_hcd 0000:00:14.0: xHCI host not responding to stop endpoint command.
[   23.517964] xhci_hcd 0000:00:14.0: Assuming host is dying, halting host.
[   23.517981] Bluetooth: hci0 urb ffff8800a68ad840 failed to resubmit (22)
[   23.517984] Bluetooth: hci0 urb ffff8800a68adc00 failed to resubmit (22)
[   23.517986] Bluetooth: hci0 urb ffff8800a68ad600 failed to resubmit (22)
[   23.517989] xhci_hcd 0000:00:14.0: HC died; cleaning up
[   23.518015] usb 3-5: USB disconnect, device number 2
[   23.518187] usb 3-7: USB disconnect, device number 3
[   23.518435] systemd-udevd[485]: Failed to apply ACL on /dev/video0: No such file or directory
[   23.566312] usb 3-12: USB disconnect, device number 6

Thanking in advance...

---

### Post by VMC on 2015-06-26
What is  xhci_hcd? What kind of usb device is it; wifi,scanner? I don't have that module. I use ehci-pci.

---

