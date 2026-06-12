---
title: "Ubuntu 16.04LTS disable a USB port"
date: 2016-11-18
forum: Hardware
---

### Post by egandt on 2016-11-18
I have a bad USB port as it throws:
Nov 18 13:25:43 workstation kernel: [ 1365.029043] usb 7-1: device descriptor read/64, error -71
Nov 18 13:25:43 workstation kernel: [ 1365.245053] usb 7-1: new full-speed USB device number 73 using uhci_hcd
Nov 18 13:25:43 workstation kernel: [ 1365.365054] usb 7-1: device descriptor read/64, error -71
Nov 18 13:25:43 workstation kernel: [ 1365.589066] usb 7-1: device descriptor read/64, error -71
Nov 18 13:25:44 workstation kernel: [ 1365.805075] usb 7-1: new full-speed USB device number 74 using uhci_hcd
Nov 18 13:25:44 workstation kernel: [ 1366.213092] usb 7-1: device not accepting address 74, error -71
Nov 18 13:25:44 workstation kernel: [ 1366.325097] usb 7-1: new full-speed USB device number 75 using uhci_hcd
Nov 18 13:25:44 workstation kernel: [ 1366.733111] usb 7-1: device not accepting address 75, error -71
Nov 18 13:25:44 workstation kernel: [ 1366.733128] usb usb7-port1: unable to enumerate USB device
Nov 18 13:25:47 workstation kernel: [ 1369.213211] usb 7-1: new full-speed USB device number 76 using uhci_hcd

I need to disable this port on bootup, however the normal methods to do so:
# echo suspend | tee /sys/bus/usb/drivers/usb/usb7/power/level
    or
# echo 7-1 | tee /sys/bus/usb/drivers/usb/unbind

Both do not work as I have no permissions to write to unbind and writing "suspend" returns:

#  echo suspend | tee /sys/bus/usb/drivers/usb/usb7/power/level
suspend
tee: /sys/bus/usb/drivers/usb/usb7/power/level: Invalid argument

The entire system is entirely unusable until I can disable this port, but I've found mo way to do so in 16.04, the methods above worked in 14.04 however.


I've also tried:

# echo suspend | /sys/bus/usb/drivers/usb/usb7/7-0:1.0/usb7-port1/power/control
echo: write error: Invalid argument

Since
# echo auto | /sys/bus/usb/drivers/usb/usb7/7-0:1.0/usb7-port1/power/control

works I'm assuming that the value is no longer suspend, but soemething else, but I do not know what that something is in 16.04

Thanks,
ERIC

---

### Post by egandt on 2016-11-18
It seems that I need to execute:

echo "7-0:1.0" > /sys/bus/usb/drivers/hub/unbind

The trick is that while it is 7-1, the naming changed at some point so I need to pass 7-0:1.0 or usb bus 7 device 1 if I understand it, next question, where best to add this, I put it in rc.local, but that is executed later than I'd like.

Thanks,
ERIC

---

