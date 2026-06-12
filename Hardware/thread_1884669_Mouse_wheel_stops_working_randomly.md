---
title: "Mouse wheel stops working randomly"
date: 2011-11-21
forum: Hardware
---

### Post by Los Frijoles on 2011-11-21
So, I have an interesting problem...my mouse wheel on my bluetooth mouse (it's a rocketfish mouse if that makes a difference) occasionally stops functioning. It happens when using gschem after a little while, but even after closing the program and stuff the scroll wheel doesn't make things scroll. Also, in xinput test the scroll wheel shows up when I move it around so that confuses me further. The scroll spot on the touchpad still works (I'm using and acer aspire one) as well. If I restart the computer twice it starts working again, but that seems a little inconvenient for normal operation. Any ideas?

Here's the syslog for the past 15 minutes (it just failed again like 5-7 minutes ago)
```
Nov 21 17:01:51 kcuzner-AOA150 kernel: [ 4740.608802] input: Rocketfish Bluetooth Mouse as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/bluetooth/hci0/hci0:42/input12
Nov 21 17:01:51 kcuzner-AOA150 kernel: [ 4740.609635] generic-bluetooth 0005:0A5C:0001.0003: input,hidraw1: BLUETOOTH HID v1.29 Mouse [Rocketfish Bluetooth Mouse] on 00:15:83:07:C8:D3
Nov 21 17:10:14 kcuzner-AOA150 kernel: [ 5242.885072] exe (2455): /proc/2455/oom_adj is deprecated, please use /proc/2455/oom_score_adj instead.
```

---

### Post by user333 on 2011-11-21
This is just a wild guess, but could it be that your mouse wheel is clogged? Can you try it out on another OS and see if it works?

---

### Post by Los Frijoles on 2011-11-21
I originally thought that that was the case...that the wheel was clogged. However, the computer was still receiving the signal for it because the xinput test said I was pressing buttons 4 and 5 when I moved the mouse wheel up and down so it physically is still working...its just like the applications aren't receiving it for some reason.

---

