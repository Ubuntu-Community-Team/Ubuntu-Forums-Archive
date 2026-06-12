---
title: "Incorrect usb gamepad detected"
date: 2010-08-20
forum: Hardware
---

### Post by xkjq on 2010-08-20
Hi,

I've got a usb gamepad which when connected is recognised and loads itself, unfortunately the dpad (hat) doesn't work. I'm assuming this is because its being detected as a 4 axis controller instead of a 6 axis one, if so how can I change it?

dmesg output:
```
[11441.157286] input: Jess Technology Co., Ltd. USB Game Controller as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1.1/5-1.1:1.0/input/input17
[11441.157426] generic-usb 0003:22BA:1020.0005: input,hidraw1: USB HID v1.01 Joystick [Jess Technology Co., Ltd. USB Game Controller] on usb-0000:00:1d.0-1.1/input0

```

---

