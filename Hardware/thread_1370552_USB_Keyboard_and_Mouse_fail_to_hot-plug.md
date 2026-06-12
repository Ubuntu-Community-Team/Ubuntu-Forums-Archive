---
title: "USB Keyboard and Mouse fail to hot-plug"
date: 2010-01-02
forum: Hardware
---

### Post by drive_guy on 2010-01-02
Running Mythbuntu 9.10 with Karmic Koala.

Sometimes when I hot-plug my keyboard and mouse or use an IOGear KVM ([http://www.iogear.com/product/GCS24U/](http://www.iogear.com/product/GCS24U/)) they do not respond after being re-connected. I have tried this with and without the KVM and the same problem occurs intermittently.  Sometimes they are found and work after hot-plug and sometimes they fail to respond.  

Here is the output from a KVM switch event.

$ tail -f /var/log/messages
Jan  2 10:56:26 myth-backend kernel: [ 3253.928035] usb 5-1: USB disconnect, address 4
Jan  2 10:56:26 myth-backend kernel: [ 3254.080026] usb 5-2: USB disconnect, address 3
Jan  2 10:59:14 myth-backend kernel: [ 3421.724701] usb 5-1: new low speed USB device using uhci_hcd and address 5
Jan  2 10:59:14 myth-backend kernel: [ 3421.878609] usb 5-1: configuration #1 chosen from 1 choice
Jan  2 10:59:14 myth-backend kernel: [ 3421.895768] input: HID 045e:000b as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.0/input/input28
Jan  2 10:59:14 myth-backend kernel: [ 3421.895836] generic-usb 0003:045E:000B.0012: input,hidraw0: USB HID v1.00 Keyboard [HID 045e:000b] on usb-0000:00:1a.2-1/input0
Jan  2 10:59:14 myth-backend kernel: [ 3422.132019] usb 5-2: new low speed USB device using uhci_hcd and address 6
Jan  2 10:59:14 myth-backend kernel: [ 3422.314610] usb 5-2: configuration #1 chosen from 1 choice
Jan  2 10:59:14 myth-backend kernel: [ 3422.332788] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input29
Jan  2 10:59:14 myth-backend kernel: [ 3422.332876] generic-usb 0003:045E:0040.0013: input,hidraw1: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1a.2-2/input0
Jan  2 11:03:58 myth-backend kernel: [ 3706.032037] usb 5-1: USB disconnect, address 5
Jan  2 11:03:58 myth-backend kernel: [ 3706.184527] usb 5-2: USB disconnect, address 6
Jan  2 11:04:05 myth-backend kernel: [ 3712.772014] usb 5-1: new low speed USB device using uhci_hcd and address 7
Jan  2 11:04:05 myth-backend kernel: [ 3712.926172] usb 5-1: configuration #1 chosen from 1 choice
Jan  2 11:04:05 myth-backend kernel: [ 3712.943336] input: HID 045e:000b as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.0/input/input30
Jan  2 11:04:05 myth-backend kernel: [ 3712.943398] generic-usb 0003:045E:000B.0014: input,hidraw0: USB HID v1.00 Keyboard [HID 045e:000b] on usb-0000:00:1a.2-1/input0
Jan  2 11:04:05 myth-backend kernel: [ 3713.180516] usb 5-2: new low speed USB device using uhci_hcd and address 8
Jan  2 11:04:05 myth-backend kernel: [ 3713.361202] usb 5-2: configuration #1 chosen from 1 choice
Jan  2 11:04:05 myth-backend kernel: [ 3713.379374] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input31
Jan  2 11:04:05 myth-backend kernel: [ 3713.379451] generic-usb 0003:045E:0040.0015: input,hidraw1: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1a.2-2/input0

---

