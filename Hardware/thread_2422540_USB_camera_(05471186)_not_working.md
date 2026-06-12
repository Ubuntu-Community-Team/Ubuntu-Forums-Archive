---
title: "USB camera (0547:1186) not working"
date: 2019-07-09
forum: Hardware
---

### Post by dasc95 on 2019-07-09
Hey guys,

I would like to read out the Bresser Mikrocam 1.3 (producing company is Anchor Chips) using OpenCV.
The problem is that the camera is not detected in video devices, nevertheless, lsusb lists the camera, the ID is 0547:1186.
Apparently, it is not UVC compatible. I searched for drivers but wasn't successful.

Has anybody encountered this problem before?
Or does anybody know a workaround? 

An idea would be to use the USB camera as an IP camera and stream it to a URL, then read out the data. But also this seems not possible as long as the camera is not detected in video devices.

Thank you for any suggestions!

---

### Post by him610 on 2019-07-09
You can check for possibly more information by running this command
```

less  /proc/bus/input/devices

```
Mine shows up with this information....
```

I: Bus=0003 Vendor=046d Product=0807 Version=0009
N: Name="UVC Camera (046d:0807)"
P: Phys=usb-0000:00:14.0-7/button
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.0/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

```
Also shows up with *xinput*.
I have no suggestions as to drivers. Did you try to get it to work with *cheese*?

---

