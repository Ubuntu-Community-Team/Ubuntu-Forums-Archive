---
title: "Palm not even connecting: not in /dev, not changing in dmesg"
date: 2006-12-21
forum: Hardware &amp; Laptops
---

### Post by jumpjet on 2006-12-21
Hello all!

 I have been wrestling with this palm for the better part of a week now.  I have tried almost every fix I have come across in various forums, I think it may be worse than when I started.

It is a Palm Zire 31, On my laptop (ubuntu edgy), when I plug it in, I at least see it connecting and disconnecting in dmesg.  On the desktop (kubuntu edgy), it doesn't show up in dmesg at all.  
I also looked in /dev and didn't ever see /dev/ttyUSB anything, or /dev/pilot.
I tried every option while hotsynching on the unit and while not hotsynching...
What's the deal?    Where do I start!

Thanks in advance for all the help!

---

### Post by jumpjet on 2006-12-21
By the by, where I should be getting something like this:

```
kernel: visor ttyUSB0: Handspring Visor / Palm OS converter now disconnected from ttyUSB0
kernel: visor ttyUSB1: Handspring Visor / Palm OS converter now disconnected from ttyUSB1
```

I instead get this:

```
Dec 21 11:52:16 oomfoofoo kernel: [17201364.608000] usbcore: registered new driver usbserial
Dec 21 11:52:16 oomfoofoo kernel: [17201364.608000] drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
Dec 21 11:52:16 oomfoofoo kernel: [17201364.612000] usbcore: registered new driver usbserial_generic
Dec 21 11:52:16 oomfoofoo kernel: [17201364.612000] drivers/usb/serial/usb-serial.c: USB Serial Driver core
Dec 21 11:52:16 oomfoofoo kernel: [17201364.616000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Handspring Visor / Palm OS
Dec 21 11:52:16 oomfoofoo kernel: [17201364.616000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 3.5
Dec 21 11:52:16 oomfoofoo kernel: [17201364.620000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 5.0
Dec 21 11:52:16 oomfoofoo kernel: [17201364.620000] usbcore: registered new driver visor
Dec 21 11:52:16 oomfoofoo kernel: [17201364.620000] drivers/usb/serial/visor.c: USB HandSpring Visor / Palm OS driver
```

---

### Post by benyau on 2006-12-22
It looks like your desktop loaded the visor module but udev did not create the ports.  If you have not tried these yet : 

- do a "cat /proc/bus/usb/devices" to check how your palm is described, esp. "Manufacturer= ???..."
- ensure /etc/udev/rules.d/, esp. SYSFS{product}=="???*", do match such that udev can detect your palm.

good luck.

---

### Post by jumpjet on 2006-12-25
> **benyau said:**
> It looks like your desktop loaded the visor module but udev did not create the ports.  If you have not tried these yet : 

- do a "cat /proc/bus/usb/devices" to check how your palm is described, esp. "Manufacturer= ???..."
- ensure /etc/udev/rules.d/, esp. SYSFS{product}=="???*", do match such that udev can detect your palm.

good luck.

Thanks for the help, Benyau!

Palm plugged in or not, syncing or not, i get this from cat:

```
T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc=  0/900 us ( 0%), #Int=  0, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.17-10-386 uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1f.4
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
B:  Alloc= 93/900 us (10%), #Int=  1, #Iso=  0
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0000 ProdID=0000 Rev= 2.06
S:  Manufacturer=Linux 2.6.17-10-386 uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:1f.2
C:* #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=  0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
E:  Ad=81(I) Atr=03(Int.) MxPS=   2 Ivl=255ms

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=03f0 ProdID=7404 Rev= 1.00
S:  Manufacturer=HP
S:  Product=Deskjet 3740
S:  SerialNumber=CN48N150V1045Y
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=  2mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=07(print) Sub=01 Prot=02 Driver=usblp
E:  Ad=01(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms

T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=02 Dev#=  3 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=045e ProdID=0040 Rev= 3.00
S:  Manufacturer=Microsoft
S:  Product=Microsoft 3-Button Mouse with IntelliEye(TM)
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=03(HID  ) Sub=01 Prot=02 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   4 Ivl=10ms
```

---

