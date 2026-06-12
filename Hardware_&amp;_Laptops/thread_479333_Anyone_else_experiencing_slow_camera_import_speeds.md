---
title: "Anyone else experiencing slow camera import speeds?"
date: 2007-06-20
forum: Hardware &amp; Laptops
---

### Post by AriciU on 2007-06-20
I have a Canon Digital Ixus and i'm experiencing very slow copying speeds compared to Windows.

For example 10 pictures, worth 8mb, take around 4 minutes to copy in Ubuntu compared to the 20-30secs in Windows.

Any ideas?

---

### Post by ukripper on 2007-06-20
Check USB controller whether it is showing as USB 1.1 or USB 2.0. If it is showing 1.1 then you probably need to get 2.0 drivers for usb controller.

Can you post output of:
```
sudo lsusb
```

Also have you updated after installation of ubuntu?

---

### Post by AriciU on 2007-06-20
> root@mlz:~# lsusb
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 005: ID 04a9:309b Canon, Inc. Digital IXUS (ptp)
Bus 002 Device 002: ID 03f0:1104 Hewlett-Packard DeskJet 959c
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 1532:0101
Bus 001 Device 001: ID 0000:0000


I don't know if i have USB 1.1 or 2.0. How do i check and how do i upgrade if i don't have it?

> root@mlz:~# dmesg | tail
[  143.880631] Bluetooth: L2CAP socket layer initialized
[  143.891102] Bluetooth: RFCOMM socket layer initialized
[  143.891318] Bluetooth: RFCOMM TTY layer initialized
[  143.891320] Bluetooth: RFCOMM ver 1.8
[  123.664000] Time: acpi_pm clocksource has been installed.
[  158.296000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[  158.296000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[  158.296000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[  836.228000] usb 2-4: new full speed USB device using ohci_hcd and address 3
[  836.440000] usb 2-4: configuration #1 chosen from 1 choice


If 2-4 = USB 2.0 then i have it :)

Thanks

---

### Post by AriciU on 2007-06-20
Ok. I checked in Device manager and it's USB 1.1. How do i upgrade to 2.0 ?

---

### Post by ukripper on 2007-06-20
Can you post output of following as well:

```
cat /proc/bus/usb/devices
```

---

### Post by AriciU on 2007-06-20
> cat /proc/bus/usb/devices

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
B:  Alloc=  0/800 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.20-16-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:02.2
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=256ms

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 4
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.20-16-generic ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:02.1
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=02 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 1.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=03f0 ProdID=1104 Rev= 1.00
S:  Manufacturer=Hewlett-Packard
S:  Product=DeskJet 950C
S:  SerialNumber=ES12J170Q5DF
C:* #Ifs= 1 Cfg#= 1 Atr=40 MxPwr=  2mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=07(print) Sub=01 Prot=01 Driver=usblp
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
I:  If#= 0 Alt= 1 #EPs= 2 Cls=07(print) Sub=01 Prot=02 Driver=usblp
E:  Ad=01(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 4
B:  Alloc= 44/900 us ( 5%), #Int=  2, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.20-16-generic ohci_hcd
S:  Product=OHCI Host Controller
S:  SerialNumber=0000:00:02.0
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  3 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=1532 ProdID=0101 Rev=21.00
S:  Manufacturer=Razer
S:  Product=Razer Copperhead Laser Mouse
C:* #Ifs= 2 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=00 Prot=02 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=  16 Ivl=1ms
I:  If#= 1 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=01 Driver=usbhid
E:  Ad=82(I) Atr=03(Int.) MxPS=  16 Ivl=1ms

T:  Bus=01 Lev=01 Prnt=01 Port=03 Cnt=02 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=32 #Cfgs=  1
P:  Vendor=04a9 ProdID=309b Rev= 0.01
S:  Manufacturer=Canon Inc.
S:  Product=Canon Digital Camera
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=06(still) Sub=01 Prot=01 Driver=(none)
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   8 Ivl=96ms


I have no idea what the EHCI Host Controller is (only one showing as USB 2.0).

---

### Post by AriciU on 2007-06-21
bump

---

### Post by ukripper on 2007-06-21
EHCI based are fastest USB type controllers.

Looking at your devices output canon is set to 12Mb/s which is full speed but not Hi speed which is USB2.0. You need to set it to hi speed


USB supports three data rates:

    * A Low Speed rate of 1.5 Mbit/s (187.5 kB/s) that is mostly used for Human Interface Devices (HID) such as keyboards, mice, and joysticks.
    * A Full Speed rate of 12 Mbit/s (1.5 MB/s). Full Speed was the fastest rate before the USB 2.0 specification and many devices fall back to Full Speed. Full Speed devices divide the USB bandwidth between them in a first-come first-served basis and it is not uncommon to run out of bandwidth with several isochronous devices. All USB Hubs support Full Speed.
    * A Hi-Speed rate of 480 Mbit/s (60 MB/s).

For more information look at this link:

[http://en.wikipedia.org/wiki/USB#Host_controllers](http://en.wikipedia.org/wiki/USB#Host_controllers)

---

### Post by ukripper on 2007-06-21
Also there are few such problems resolved in this thread [http://ubuntuforums.org/showthread.php?t=150026](http://ubuntuforums.org/showthread.php?t=150026) using modprobe and rmmod

Check this as well: 

[http://www.linuxquestions.org/questions/showthread.php?p=2792799#post2792799](http://www.linuxquestions.org/questions/showthread.php?p=2792799#post2792799)

---

### Post by AriciU on 2007-06-21
Thanks.

I will give it a try when i get back home.

---

### Post by AriciU on 2007-06-21
Didn't work. It seems like there is nothing on the EHCI (high speed). If i disable OHCI thru modprobe -r i lose the mouse and everything. Bleh

---

### Post by ukripper on 2007-06-21
```
T: Bus=02 Lev=00 [COLOR="Red"]Prnt=00 Port=00 Cnt=00 [/COLOR]Dev#= 1 Spd=12 MxCh= 4
B: Alloc= 0/900 us ( 0%), #Int= 0, #Iso= 0
D: Ver= 1.10 Cls=09(hub ) Sub=00 Prot=00 MxPS=64 #Cfgs= 1
P: Vendor=0000 ProdID=0000 Rev= 2.06
S: Manufacturer=Linux 2.6.20-16-generic [COLOR="Red"]ohci_hcd[/COLOR]
S: Product=OHCI Host Controller
S: SerialNumber=0000:00:02.1
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr= 0mA
I: If#= 0 Alt= 0 #EPs= 1 Cls=09(hub ) Sub=00 Prot=00 Driver=hub
E: Ad=81(I) Atr=03(Int.) MxPS= 2 Ivl=255ms
```


The problem you are having is your hub is 1.1 but your canon device is usb2.0.

Try connecting you canon directly to your machine without using hub as your hub is behaving as 2nd usb controller which shows ohci_hcd, therefore capping your transfer rate down. post your /usb/devices output here after connecting your cannon directly.

---

### Post by AriciU on 2007-06-21
I have 4 USB ports on the back of the mobo. I checked the manual and they are 2 x USB 1.1 and 2 x USB 2.0. I also have 4 other ports in the same configuration. 

I tried connecting the camera to every single one of them and it only saw it under ohci_hdb -> 12mbit -> USB 1.1. 

Here is a picture of the KInfoCenter with the camera plugged in. It shows it like this no mather witch USB port i connect it to.

I'm assuming the problem comes from the kernel with doesn't know/use EHCI_HDB usb 2.0 ports or some drivers that need to be updated.

No mather witch USB slot i connect it to i can't get it to get detected under EHCI_HDB

---

