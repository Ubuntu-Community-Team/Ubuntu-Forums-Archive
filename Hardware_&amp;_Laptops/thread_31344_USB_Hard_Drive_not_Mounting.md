---
title: "USB Hard Drive not Mounting"
date: 2005-05-02
forum: Hardware &amp; Laptops
---

### Post by jer006 on 2005-05-02
Hi, 
I just switched to Ubuntu from Fedora Core 3 and for the most part am finding things a bit of an improvement.  However I have a USB hard Drive enclosure was detected and automounted perfectly in FC3 but is not detected in Ubuntu.

I have found other information on this topic and have tried a some stuff and had not had any joy getting the hard drive to mount... 

From dmesg I see the following information...
usbcore: registered new driver usbfs
usbcore: registered new driver hub
usb 1-1: new full speed USB device using uhci_hcd and address 2
usbcore: registered new driver usb-storage
usb-storage: device found at 2
usb-storage: waiting for device to settle before scanning
usb-storage: device scan complete

When I run usbview it shows information on the Mass Storage Device and points to a file /proc/bus/usb/devices which contains
T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.10-5-686 uhci_hcd
S:  Product=Intel Corp. 82371AB/EB/MB PIIX4 USB
S:  SerialNumber=0000:00:07.2
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=067b ProdID=2507 Rev= 1.00
S:  Manufacturer=Prolific Technology Inc.
S:  Product=Mass Storage Device
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
E:  Ad=01(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms

Hope that makes sense and someone can help, I'm still a little new at this so any help would be much appreciated !

Thank you

Jeremy.

---

