---
title: "C-Media Card Reader 0d8c:5200 not working"
date: 2006-06-15
forum: Hardware &amp; Laptops
---

### Post by JeffreyRatcliffe on 2006-06-15
lshw gives:

```
              *-usb:2 UNCLAIMED
                   description: Generic USB device
                   vendor: C-Media Electronics, Inc.
                   physical id: 4
                   bus info: usb@5:4
                   version: 1.00
                   capabilities: usb-2.00
                   configuration: maxpower=100mA speed=480.0MB/s
```

cat /proc/bus/usb/devices gives:

```
T:  Bus=05 Lev=01 Prnt=01 Port=03 Cnt=03 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0d8c ProdID=5200 Rev= 1.00
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=01(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=84(I) Atr=03(Int.) MxPS=   4 Ivl=32ms
```

lsusb gives:

```
Bus 005 Device 005: ID 0d8c:5200 C-Media Electronics, Inc.
```

I don't hold out much hope because it didn't work under Breezy either.

Googling around finds several people struggling to get it working and not one success. This is the closest I've found:

[http://www.qbik.ch/usb/devices/showdev.php?id=2588](http://www.qbik.ch/usb/devices/showdev.php?id=2588)

Any ideas?

Jeff

---

### Post by Tiftof on 2006-12-27
Any solution for this yet? I want to make my card reader work too

---

### Post by Ploes on 2007-08-21
Same issue for me.

```
Bus 004 Device 002: ID 0d8c:5200 C-Media Electronics, Inc. 
```

I'd love for this to work as I'm still having to use a USB MicroSD reader at the moment :(

---

