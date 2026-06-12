---
title: "Microchip USB hardware only accessible as root"
date: 2008-06-05
forum: Hardware
---

### Post by fransfrans on 2008-06-05
I am developing an usb device at [http://usbpicprog.sourceforge.net]("http://usbpicprog.sourceforge.net")
it uses libusb to communicate to a Microchip PIC.

In Ubuntu 7.04 everything was working fine, but since I upgraded to 7.10 and later to 8.04, I could only access the device as root.

I did put the following in /etc/udev/rules.d/26-microchip.rules
```

#PICKit
SYSFS{idVendor}=="04d8", SYSFS{idProduct}=="0032", MODE="0660", GROUP="microchip"
#PICKit2
SYSFS{idVendor}=="04d8", SYSFS{idProduct}=="0033", MODE="0660", GROUP="microchip"
#ICD2
SYSFS{idVendor}=="04d8", SYSFS{idProduct}=="8000", MODE="0660", GROUP="microchip"
#ICD21
SYSFS{idVendor}=="04d8", SYSFS{idProduct}=="8001", MODE="0660", GROUP="microchip"
#Usbpicprog
SYSFS{idVendor}=="04d8", SYSFS{idProduct}=="000e", MODE="0660", GROUP="microchip"
#Picdem USB
SYSFS{idVendor}=="04d8", SYSFS{idProduct}=="000b", MODE="0660", GROUP="microchip"

```
and I did put myself in the microchip group

lsusb shows me this:
```
(...)
Bus 001 Device 004: ID 04d8:000e Microchip Technology, Inc.
(...)
```

according to [http://mcuee.blogspot.com/2008_04_01_archive.html]("http://mcuee.blogspot.com/2008_04_01_archive.html"), ls -la /dev/bus/usb/001 should show me devices which are owned by group "microchip", but they are all owned by group "root".
```

frans@ubuntu:~$ ls -la /dev/bus/usb/001
total 0
drwxr-xr-x 2 root root 100 2008-06-04 19:26 .
drwxr-xr-x 5 root root 100 2008-06-04 19:26 ..
crw-rw-r-- 1 root root 189, 0 2008-06-04 19:26 001
crw-rw-r-- 1 root root 189, 2 2008-06-04 19:26 018

```

What am I doing wrong? Has anything changed in udev since Ubuntu 7.04?

Cheers Frans

---

