---
title: "Anker USB3 hub shows as Via USB2 hub"
date: 2016-02-04
forum: Hardware
---

### Post by uMinded on 2016-02-04
I got an Anker 7 port USB3 hub [https://www.anker.com/products/A7515111](https://www.anker.com/products/A7515111) and It is not showing up as USB3 when plugged into my motherboards USB3 port. No devices on the hub show up either.

Ubuntu 14.04, the usual dumps follow:

$ uname -a
````
Linux uminded-desktop 3.13.0-77-generic #121-Ubuntu SMP Wed Jan 20 10:50:42 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
````


$ lsusb


````
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 004 Device 003: ID 046d:c219 Logitech, Inc. Cordless RumblePad 2
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 005: ID 2109:2812  
Bus 010 Device 004: ID 2109:2812  
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
````


$ dmesg  


````
[14211.572902] usb 10-2: new high-speed USB device number 2 using xhci_hcd
[14211.590455] usb 10-2: New USB device found, idVendor=2109, idProduct=2812
[14211.590462] usb 10-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[14211.590468] usb 10-2: Product: USB2.0 Hub             
[14211.590472] usb 10-2: Manufacturer: VIA Labs, Inc.         
[14211.591629] hub 10-2:1.0: USB hub found
[14211.591928] hub 10-2:1.0: 4 ports detected
[14211.881444] usb 10-2.4: new high-speed USB device number 3 using xhci_hcd
[14211.898880] usb 10-2.4: New USB device found, idVendor=2109, idProduct=2812
[14211.898904] usb 10-2.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[14211.898921] usb 10-2.4: Product: USB2.0 Hub             
[14211.898934] usb 10-2.4: Manufacturer: VIA Labs, Inc.         
[14211.900177] hub 10-2.4:1.0: USB hub found
[14211.900477] hub 10-2.4:1.0: 4 ports detected
[14347.441935] usb 10-2: USB disconnect, device number 2
[14347.441944] usb 10-2.4: USB disconnect, device number 3
[14359.907837] usb 10-2: new high-speed USB device number 4 using xhci_hcd
[14359.925521] usb 10-2: New USB device found, idVendor=2109, idProduct=2812
[14359.925528] usb 10-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[14359.925534] usb 10-2: Product: USB2.0 Hub             
[14359.925538] usb 10-2: Manufacturer: VIA Labs, Inc.         
[14359.926570] hub 10-2:1.0: USB hub found
[14359.926889] hub 10-2:1.0: 4 ports detected
[14360.216358] usb 10-2.4: new high-speed USB device number 5 using xhci_hcd
[14360.233932] usb 10-2.4: New USB device found, idVendor=2109, idProduct=2812
[14360.233935] usb 10-2.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[14360.233937] usb 10-2.4: Product: USB2.0 Hub             
[14360.233938] usb 10-2.4: Manufacturer: VIA Labs, Inc.         
[14360.234776] hub 10-2.4:1.0: USB hub found
[14360.234937] hub 10-2.4:1.0: 4 ports detected
````


$ usb-devices  


````
T:  Bus=10 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 2
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=03.13
S:  Manufacturer=Linux 3.13.0-77-generic xhci_hcd
S:  Product=xHCI Host Controller
S:  SerialNumber=0000:04:00.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


T:  Bus=10 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  4 Spd=480 MxCh= 4
D:  Ver= 2.10 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=2109 ProdID=2812 Rev=0b.e0
S:  Manufacturer=VIA Labs, Inc.         
S:  Product=USB2.0 Hub             
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
````

---

### Post by uMinded on 2016-02-04
Solved. Hub needs to be plugged into USB3 port #1 and any other ports cause it to display as a USB2 hub. Maybe you can's chain USB3 hubs?

---

