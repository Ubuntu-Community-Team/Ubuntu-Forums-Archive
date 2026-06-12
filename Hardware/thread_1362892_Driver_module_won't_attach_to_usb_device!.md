---
title: "Driver module won't attach to usb device!"
date: 2009-12-23
forum: Hardware
---

### Post by Skerit on 2009-12-23
I have a Terratec T USB XXS device. It used to work FINE in Ubuntu 9.10, but a few updates ago something went wrong. This is the proc output of the device:

```
T:  Bus=02 Lev=01 Prnt=01 Port=05 Cnt=02 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0ccd ProdID=00ab Rev= 1.00
S:  Manufacturer=TerraTec GmbH
S:  Product=Cinergy T XXS
S:  SerialNumber=0000000001
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=500mA
I:* If#= 0 Alt= 0 #EPs= 4 Cls=ff(vend.) Sub=00 Prot=00 Driver=(none)
E:  Ad=01(O) Atr=02(Bulk) MxPS= 512 Ivl=125us
E:  Ad=81(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=83(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms

```

Even though I've loaded the needed module, lsmod:
```
dvb_usb_dib0700        59432  0 
dib7000p               18408  1 dvb_usb_dib0700
dib7000m               16004  1 dvb_usb_dib0700
dvb_usb                22380  1 dvb_usb_dib0700
dib3000mc              14280  1 dvb_usb_dib0700
dibx000_common          4196  3 dib7000p,dib7000m,dib3000mc
dib0070                 8548  1 dvb_usb_dib0700

```

How can I force it to use the right module?

---

