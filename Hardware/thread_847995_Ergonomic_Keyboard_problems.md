---
title: "Ergonomic Keyboard problems"
date: 2008-07-03
forum: Hardware
---

### Post by cash1981 on 2008-07-03
Hello.

I have a Contour Rollermouse Pro which I really need to make working so that I can do my job. I have Rev 1.

I google a bit and found a page where it said you needed no drivers, but only needed to put this part in your xorg.conf:

Section "InputDevice"
        Identifier "Mouse0"
        Driver "mouse"
        Option "Protocol" "imPS/2"
        Option "Device" "/dev/input/mice"
        Option "ZAxisMapping" "4 5" 
EndSection
I tried this but this didnt work.

dmesg says:[ 1558.785777] usb 2-2: new low speed USB device using uhci_hcd and address 27
[ 1558.907498] usb 2-2: device not accepting address 27, error -71
[ 1558.949388] usb 2-2: new low speed USB device using uhci_hcd and address 28
[ 1559.083035] usb 2-2: device not accepting address 28, error -71
[ 1559.118294] usb 2-2: new low speed USB device using uhci_hcd and address 29
[ 1559.149050] usb 2-2: device descriptor read/64, error -71
[ 1559.251018] usb 2-2: device descriptor read/64, error -71
[ 1559.332553] usb 2-2: new low speed USB device using uhci_hcd and address 30
[ 1559.368922] usb 2-2: device descriptor read/64, error -71
[ 1559.459692] usb 2-2: device descriptor read/64, error -71

and /var/log/messages when I plug in

Jul  3 10:26:41 shervin kernel: [ 1631.636529] usb 2-2: new low speed USB device using uhci_hcd and address 36
Jul  3 10:26:42 shervin kernel: [ 1631.830786] usb 2-2: new low speed USB device using uhci_hcd and address 37
Jul  3 10:26:42 shervin kernel: [  652.582622] usb 2-2: new low speed USB device using uhci_hcd and address 38
Jul  3 10:26:43 shervin kernel: [ 1632.299799] usb 2-2: new low speed USB device using uhci_hcd and address 39


Now my questions.
**Do I need to remove my old mouse identifier stuff in xorg.conf to make this work?**
**Can anybody spot something wrong?**
**Does anybody use something similar to this ergonomic keyboard that works in Ubuntu?**

Thanks

---

