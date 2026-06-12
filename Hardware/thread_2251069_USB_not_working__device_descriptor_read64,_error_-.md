---
title: "USB not working:  device descriptor read/64, error -110"
date: 2014-11-01
forum: Hardware
---

### Post by Ryan_Reilly on 2014-11-01
Anybody see this before?  I couldn't find it on the forums or google.  
syslog generates this:

-----------------------

Nov  1 16:28:40 reilly-server kernel: [ 1166.952032] usb 6-1: new full-speed USB device number 46 using uhci_hcd
Nov  1 16:28:51 reilly-server kernel: [ 1177.360030] usb 6-1: device not accepting address 46, error -110
Nov  1 16:28:51 reilly-server kernel: [ 1177.360061] hub 6-0:1.0: unable to enumerate USB device on port 1
Nov  1 16:28:51 reilly-server kernel: [ 1177.716026] usb 6-1: new full-speed USB device number 47 using uhci_hcd
Nov  1 16:29:06 reilly-server kernel: [ 1192.828022] usb 6-1: device descriptor read/64, error -110

-----------------------

What I can't find is error -110

Thanks.

---

### Post by bashiergui on 2014-11-02
Look at post #2 [here]("http://answers.launchpad.net/ubuntu/+question/248889"), it says[TABLE]
[TR]
[TD]> The error code error -110 indicates, that the power pool for the devices is exceeded. This usually happens when you are using a passive hub and the devices connected request more than 500mA (USB 2.0) or 900mA (USB3.0). You should use an active USB hub (with power supply) or try to plug the device into other ports.[/TD]
[/TR]
[/TABLE]
If you want to see the power consumption of the devices, run the command
lsusb -v
Look for lines with "MaxPower".

---

