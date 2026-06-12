---
title: "Bluetooth Broadcom"
date: 2012-08-08
forum: Hardware
---

### Post by lioncub on 2012-08-08
Doesn't work Bluetooth Broadcom!!!
Ubuntu 12.04 3.2.0-27-generic x86_64
```
# lsusb
Bus 002 Device 017: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 018: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 002 Device 019: ID 0a5c:4503 Broadcom Corp. Mouse (Boot Interface Subclass)
```
```
# usb-devices
T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#= 17 Spd=12  MxCh= 3
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0a5c ProdID=4500 Rev=01.00
S:  Manufacturer=Broadcom
S:  Product=BCM2046B1
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=94mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
```
```
# hciconfig dev
Can't get device info: No such device

```

---

