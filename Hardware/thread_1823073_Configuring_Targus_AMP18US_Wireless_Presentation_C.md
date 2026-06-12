---
title: "Configuring Targus AMP18US Wireless Presentation Controller for LibreOffice Impress"
date: 2011-08-11
forum: Hardware
---

### Post by nhwilson on 2011-08-11
Hello.  I'm trying to get a [Targus AMP18US wireless presentation controller]("http://www.targus.com/us/productdetail.aspx?regionId=7&sku=AMP18US") working with LibreOffice Impress.  I'm using Kubuntu 11.04 on an Acer Dual-boot laptop (w/Windows 7).

The problem is that although Ubuntu can see the device (via lsusb) pressing the forward and back buttons on the controller does nothing (i.e., there's no output in Xev.)

Over on the windows side of my dual-boot, using the device requires specialized drivers (that aren't listed by Targus for Linux).  Is there some open equivalent I can use?

Here's my relevant dmesg output from when I connect the device's wireless dongle:

```
[68425.417341] usb 2-1.2: new low speed USB device using ehci_hcd and address 6
[68425.521108] input: Targus Presentation Remote as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input17
[68425.521360] generic-usb 0003:1048:07D4.0008: input,hidraw3: USB HID v1.10 Keyboard [Targus Presentation Remote] on usb-0000:00:1d.0-1.2/input0
[68425.526586] input: Targus Presentation Remote as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.1/input/input18
[68425.526914] generic-usb 0003:1048:07D4.0009: input,hidraw4: USB HID v1.10 Mouse [Targus Presentation Remote] on usb-0000:00:1d.0-1.2/input1

```And here's my lsusb output once it's connected:
```

Bus 002 Device 006: ID 1048:07d4 Targus Group International 
Bus 002 Device 003: ID 045e:0745 Microsoft Corp. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 04f2:b1d8 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```Thanks in advance for your suggestions.

---

