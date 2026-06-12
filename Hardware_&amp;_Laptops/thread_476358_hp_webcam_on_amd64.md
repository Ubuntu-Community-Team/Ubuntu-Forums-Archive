---
title: "hp webcam on amd64"
date: 2007-06-17
forum: Hardware &amp; Laptops
---

### Post by atararx on 2007-06-17
Hi,
I am unable to get my webcam to work on linux. (kubuntu 7.04). I have an hp dv6000z laptop.

I downloaded (using svn) the latest linux-uvc drivers but the webcam
does not work

$ dmesg
[ 1088.539975] Linux video capture interface: v2.00
[ 1093.620957] uvcvideo: probe of 1-4:1.0 failed with error -110
[ 1093.620722] usb 1-4: USB disconnect, address 2
[ 1093.621143] usbcore: registered new interface driver uvcvideo
[ 1093.621222] USB Video Class driver (v0.1.0)
[ 1093.722640] usb 1-4: new high speed USB device using ehci_hcd and
address 3

$ xawtv
This is xawtv-3.95.dfsg.1, running on Linux/x86_64
(2.6.20-16-lowlatency)
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  67
  Current serial number in output stream:  67

$ lsusb
Bus 002 Device 001: ID 0000:0000
Bus 002 Device 002: ID 0c45:62c0 Microdia
Bus 001 Device 001: ID 0000:0000

Can someone please help me get my webcam working?

Thanks in advance

---

