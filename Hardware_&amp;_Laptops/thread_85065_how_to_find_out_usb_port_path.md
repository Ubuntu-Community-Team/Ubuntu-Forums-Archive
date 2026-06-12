---
title: "how to find out usb port path"
date: 2005-11-01
forum: Hardware &amp; Laptops
---

### Post by Cyrus on 2005-11-01
I have connected a serial port to usb port converter to my system. Now I want to access the device. I need to have the path to that device? How can I find out?

usbview has found the Keyspan converter:
Intel Corporation 82801FB/FBM/FR/FW/FRW(ICH6 Family) USB UHCI #3
- keyspan

What kind of information do you also need?

---

### Post by ranf on 2005-11-01
Run this in a Terminal:
```

dmesg | grep usb

```
What sort of device do you want to use with this converter?

---

### Post by Cyrus on 2005-11-01
Something like this: [http://www.copypro.com](http://www.copypro.com)

Through the serial port you can controll the arm which gets and puts cds. We need a usb solution, it already worked with a normal serial port connection.

---

### Post by ranf on 2005-11-01
The USB-serial converter I have can be accessed thru: /dev/ttyUSB0
But `dmesg' should tell you.

---

