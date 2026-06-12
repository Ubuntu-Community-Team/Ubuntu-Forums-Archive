---
title: "Installation of Mouse like bluetooth device"
date: 2011-04-21
forum: Hardware
---

### Post by scott36 on 2011-04-21
Hello,

I am having a mouse like device - a "power point" remote control which I like to get working under Ubuntu.

The device has only 4 buttons, probably: forward, backward, play, menu.

In the manual it states that it uses "advanced radio frequency" (RF).

Here the dmesg output when I connect it:

```

[ 7689.660019] usb 3-6: new low speed USB device using ohci_hcd and address 10
[ 7689.908037] input: HID-compliant Mouse HID-compliant Mouse as /devices/pci0000:00/0000:00:02.0/usb3/3-6/3-6:1.0/input/input11
[ 7689.908184] generic-usb 0003:1223:3F07.0009: input,hidraw0: USB HID v1.10 Keyboard [HID-compliant Mouse HID-compliant Mouse] on usb-0000:00:02.0-6/input0

```Looks like bluetooth device there?! Or does "low speed" mean its RF?

I can not connect the device via the bluetooth manager, nor does ```
hidd --search
``` or ```
hcitool -scan
``` deliver any results.

Any idea how I get this to work?

Thanks,

Scott

---

