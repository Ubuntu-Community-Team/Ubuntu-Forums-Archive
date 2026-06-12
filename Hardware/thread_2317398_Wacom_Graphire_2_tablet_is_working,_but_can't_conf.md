---
title: "Wacom Graphire 2 tablet is working, but can't configure in System Settings"
date: 2016-03-16
forum: Hardware
---

### Post by politas on 2016-03-16
I have an admittedly rather aged Wacom Graphire 2 tablet.

```
$ lsusb | grep Wacom
Bus 005 Device 007: ID 056a:0011 Wacom Co., Ltd Graphire 2 4x5

$ lsmod | grep wacom
wacom                  81920  0 
hid                   110592  4 wacom,hid_generic,hid_logitech,usbhid

$ dpkg -s xserver-xorg-input-wacom
Package: xserver-xorg-input-wacom
Status: install ok installed
Priority: optional
Section: x11
Installed-Size: 301
Maintainer: Ubuntu X-SWAT <ubuntu-x@lists.ubuntu.com>
Architecture: amd64
Source: xf86-input-wacom
Version: 1:0.23.0-0ubuntu2

$ xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech Logitech Illuminated Keyboard  	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=11	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Graphire2 4x5 stylus              	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Graphire2 4x5 eraser              	id=15	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Graphire2 4x5 cursor              	id=16	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=8	[slave  keyboard (3)]
    &#8627; Power Button                            	id=9	[slave  keyboard (3)]
    &#8627; Logitech Logitech Illuminated Keyboard  	id=13	[slave  keyboard (3)]
```

The tablet is controlling my mouse pointer quite happily, stretching across all three 1080P screens. This means that it's 4:3 ratio input surface is not mapping at all usefully for drawing. Opening System Setting / Wacom Tablet shows that "No tablet detected" message. Yet the tablet has been detected by every other layer of the OS.

Can anyone help?

---

