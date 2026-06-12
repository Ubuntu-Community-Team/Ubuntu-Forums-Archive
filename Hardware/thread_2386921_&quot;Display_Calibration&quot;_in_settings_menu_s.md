---
title: "&quot;Display Calibration&quot; in settings menu seem to do absolutely nothing."
date: 2018-03-12
forum: Hardware
---

### Post by ss141 on 2018-03-12
I've been using Ubuntu Studio since 12.04 and am now using 16.04. In the settings menu there is a "Display Calibration" option which never did anything but give a message, "Plug in Colorimiter before running this," when you hover over it. So I found a Pantone Huey(colorimiter) on Ebay for $15, which works properly using Windows 7. With the Huey plugged in and trying to click on "Display Calibration" in the settings menu still does absolutely nothing. Is there something else I need to do? Any help is appreciated.

---

### Post by genterminl on 2018-03-12
I don't have any personal experience with these, but I'd suggest you post the output of lsusb and the last few lines from dmesg right after you plug in the device.  My guess is that you need some driver or need to load some kernel module for the device to actually function.

---

### Post by ss141 on 2018-03-13
Thanks for your reply.
Ok. As requested.

steve@steve-OptiPlex-960:~/Desktop$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 004: ID 2109:2812 VIA Labs, Inc. VL812 Hub
Bus 009 Device 003: ID 2109:2812 VIA Labs, Inc. VL812 Hub
Bus 009 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 010 Device 006: ID 2109:0812 VIA Labs, Inc. VL812 Hub
Bus 010 Device 005: ID 05dc:b049 Lexar Media, Inc. 
Bus 010 Device 004: ID 1058:1230 Western Digital Technologies, Inc. My Book (WDBFJK0030HBK)
Bus 010 Device 002: ID 2109:0812 VIA Labs, Inc. VL812 Hub
Bus 010 Device 007: ID 1058:1140 Western Digital Technologies, Inc. My Book Essential (WDBACW)
Bus 010 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 03f0:4512 Hewlett-Packard E709n [Officejet 6500 Wireless]
Bus 001 Device 005: ID 041e:3f04 Creative Technology, Ltd E-Mu 0404
Bus 001 Device 003: ID 0bc2:3000 Seagate RSS LLC FreeAgent Desktop
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0971:2005 Gretag-Macbeth AG Huey
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
steve@steve-OptiPlex-960:~/Desktop$ dmesg
... 
[72492.361029] IPv6: ADDRCONF(NETDEV_CHANGE): enp0s25: link becomes ready
[77505.704072] usb 4-2: USB disconnect, device number 2
[77534.654023] usb 4-2: new low-speed USB device number 3 using uhci_hcd
[77534.795062] usb 4-2: New USB device found, idVendor=0971, idProduct=2005
[77534.795066] usb 4-2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
steve@steve-OptiPlex-960:~/Desktop$ 

It may interest you to read this webpage.
[https://help.ubuntu.com/stable/ubuntu-help/color-calibrationdevices.html](https://help.ubuntu.com/stable/ubuntu-help/color-calibrationdevices.html)
Granted, the distro is not what I'm running, but it led me to think that the Ubuntu community is well aware of this hardware.
Ubuntu Studio 16.04 is XFCE based and has seems to be using gnome color manager, unless I'm mistaken.

---

### Post by rbmorse on 2018-03-13
Is the Argyll package installed?

---

### Post by ss141 on 2018-03-14
Yes. Here's a crop of a screenshot from synaptic pacage manager using the search "argyll."

---

