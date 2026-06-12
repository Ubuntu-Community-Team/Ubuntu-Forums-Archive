---
title: "USB 3.0 hub don't work"
date: 2013-11-25
forum: Hardware
---

### Post by shestero on 2013-11-25
I have two USB 3.0 ports on my board under Ubuntu 12.04.
Because I may need more USB 3.0 connections I bought Q3 UPH10-0406S hub, which has 6 USB2.0 sockets and 4 USB3.0 sockets.

My problem is that those four additional USB 3.0 sockets aren't working. At last my external HDD drives aren't recognized when connected to any of them.

PS When I plug in the hub into USB 3.0 I've got the following log in dmesg:```
[73541.740076] usb 8-1: new high-speed USB device number 11 using xhci_hcd[73541.758318] usb 8-1: New USB device found, idVendor=2109, idProduct=0811
[73541.758329] usb 8-1: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[73541.758339] usb 8-1: Product: USB2.0 Hub
[73541.771612] hub 8-1:1.0: USB hub found
[73541.771917] hub 8-1:1.0: 4 ports detected
[73542.051938] usb 8-1.1: new high-speed USB device number 12 using xhci_hcd
[73542.069876] usb 8-1.1: New USB device found, idVendor=1a40, idProduct=0201
[73542.069894] usb 8-1.1: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[73542.069904] usb 8-1.1: Product: USB 2.0 Hub [MTT]
[73542.090972] hub 8-1.1:1.0: USB hub found
[73542.091439] hub 8-1.1:1.0: 7 ports detected
```
Note that it was recognized as USB2.0 hub, not USB 3.0! I don't understand why numbers of detected ports are 4 and 7. As I told, there are 10 sockets totally on the hub.

---

