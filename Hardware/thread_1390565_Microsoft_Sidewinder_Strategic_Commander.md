---
title: "Microsoft Sidewinder Strategic Commander"
date: 2010-01-25
forum: Hardware
---

### Post by Noccy on 2010-01-25
Just tried plugging my good ol' Microsoft Sidewinder Strategic Commander, and it doesn't show up. dmesg renders errors, and lsusb doesn't list it at all. Including dmesg output.

How do I enable this fancy gadget in Ubuntu 9.04?

[IMG]http://pnmedia.gamespy.com/planetcnc.gamespy.com/features/reviews/stratcommander/big.jpg[/IMG]

```
[ 4681.441124] hub 2-0:1.0: unable to enumerate USB device on port 1
[ 4692.100052] usb 2-1: new low speed USB device using uhci_hcd and address 11
[ 4692.220075] usb 2-1: device descriptor read/64, error -71
[ 4692.445522] usb 2-1: device descriptor read/64, error -71
[ 4692.660097] usb 2-1: new low speed USB device using uhci_hcd and address 12
[ 4692.784079] usb 2-1: device descriptor read/64, error -71
[ 4693.033119] usb 2-1: device descriptor read/64, error -71
[ 4693.258682] usb 2-1: new low speed USB device using uhci_hcd and address 13
[ 4693.677045] usb 2-1: device not accepting address 13, error -71
[ 4693.789081] usb 2-1: new low speed USB device using uhci_hcd and address 14
[ 4694.204247] usb 2-1: device not accepting address 14, error -71
[ 4694.204290] hub 2-0:1.0: unable to enumerate USB device on port 1
```

---

### Post by wilee-nilee on 2010-01-25
[http://www.google.com/search?hl=en&q=Microsoft+Sidewinder+Strategic+Commander+linux&aq=f&aql=&aqi=&oq=](http://www.google.com/search?hl=en&q=Microsoft+Sidewinder+Strategic+Commander+linux&aq=f&aql=&aqi=&oq=)

In case you get no answers.

---

### Post by Noccy on 2010-01-25
It took me 2 months to find the Windows drivers, so not expecting any miracles :) 

However, wikipedia states "Linux treats this device as a joystick (with all 3 axis and 12 plus 3 buttons) and can be used as one or using various applets can be used as a "joystick action to key press" device (e.g. Joy2Key)" - this is obviously not the case; the device isn't detected at all for me.

---

### Post by Noccy on 2010-01-25
<double post>

---

### Post by Noccy on 2010-01-25
As through magic it decided to work all of a sudden;

```
[12797.812122] usb 3-1: new low speed USB device using uhci_hcd and address 2
[12797.997630] usb 3-1: configuration #1 chosen from 1 choice
[12799.281919] usbcore: registered new interface driver hiddev
[12799.329912] input: Microsoft Microsoft SideWinder Strategic Commander as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input10
[12799.333092] generic-usb 0003:045E:0033.0001: input,hidraw0: USB HID v1.10 Device [Microsoft Microsoft SideWinder Strategic Commander] on usb-0000:00:1d.1-1/input0
[12799.333133] usbcore: registered new interface driver usbhid
[12799.333140] usbhid: v2.6:USB HID core driver
```

I installed the packages joystick and jscalib if that could have had any impact. I have still to get joy2key to work with Warzone2100, but at least it's working now :)

---

### Post by wilee-nilee on 2010-01-26
One of the links on the page I posted about 3/4 of the way down also seems to have linux drivers, that is why I posted it it.

---

