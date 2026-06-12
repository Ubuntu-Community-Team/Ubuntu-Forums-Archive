---
title: "Cannot configure X- and Y- Axis of ThrustMaster HOTAS Cougar"
date: 2008-03-22
forum: Hardware &amp; Laptops
---

### Post by Larissa on 2008-03-22
Hi,



I am trying to get my HOTAS Cougar to work, but regarding to JSCalibrator it only seems to produce values if I move joystick left and/or forward. If I pull back or to the right no value changes at all. After configuration I can move the cross hair only in the upper left hand square - I cannot "reach" the other three sqares.

I am not sure if that explanation is easily understandable - sorry - if not I'll provide a screenshot :KS

BTW: I've tried it on a Dapper amd64 and Gutsy i386 with the same results.

EDIT: In case it helps - the dmesg output:
```
[  236.876247] usb 3-1: new full speed USB device using ohci_hcd and address 2
[  237.088062] usb 3-1: configuration #1 chosen from 1 choice
[  237.099980] input: Thrustmaster Thrustmaster HOTAS Cougar as /class/input/input6
[  237.100017] input: USB HID v1.10 Joystick [Thrustmaster Thrustmaster HOTAS Cougar] on usb-0000:00:03.2-1
[  237.112017] input: Thrustmaster Thrustmaster HOTAS Cougar as /class/input/input7
[  237.112067] input: USB HID v1.00 Keyboard [Thrustmaster Thrustmaster HOTAS Cougar] on usb-0000:00:03.2-1
[  237.123906] input: Thrustmaster Thrustmaster HOTAS Cougar as /class/input/input8
[  237.123971] input: USB HID v1.00 Mouse [Thrustmaster Thrustmaster HOTAS Cougar] on usb-0000:00:03.2-1
```



Thanks for your help,
Larissa

---

### Post by Larissa on 2008-03-23
I found out that actually running jscalibrator messes up the configuration. If I boot the system and do not run jscalibrator before I start a fligh stimulator the axis are just fine.

---

