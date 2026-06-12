---
title: "Serial USB Device - cant load usbserial"
date: 2008-04-04
forum: Hardware &amp; Laptops
---

### Post by n3utrino on 2008-04-04
Hi all.

I have a problem to load the usbserial module.
if i ```
 sudo modprobe usbserial vendor=0x0471 product=0x082d
```

my dmesg states 

```

[ 1062.416238] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: USB Serial support registered for generic
[ 1062.416276] /build/buildd/linux-2.6.24/drivers/usb/serial/usb-serial.c: static descriptor matches
[ 1062.416282] usbserial_generic 7-6:1.0: Generic device with no bulk out, not allowed.
[ 1062.416302] usbserial_generic: probe of 7-6:1.0 failed with error -5

```

but if i check /proc/bus/usb/devices
it has bulk out but not on the active config (i'm assuming the line with the star is the active config)

```
T:  Bus=07 Lev=01 Prnt=01 Port=05 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=ff Prot=ff MxPS=64 #Cfgs=  1
P:  Vendor=0471 ProdID=082d Rev= 0.03
C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 0 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none) <--- Active Config
I:  If#= 0 Alt= 1 #EPs= 6 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none) <--- Config with Bulk I/O
E:  Ad=01(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=81(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=04(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=86(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=88(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
I:  If#= 0 Alt= 2 #EPs= 6 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=01(O) Atr=03(Int.) MxPS=  64 Ivl=125us
E:  Ad=81(I) Atr=03(Int.) MxPS=  64 Ivl=125us
E:  Ad=02(O) Atr=03(Int.) MxPS= 512 Ivl=125us
E:  Ad=04(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=86(I) Atr=03(Int.) MxPS= 512 Ivl=125us
E:  Ad=88(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
I:  If#= 0 Alt= 3 #EPs= 6 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=01(O) Atr=03(Int.) MxPS=  64 Ivl=125us
E:  Ad=81(I) Atr=03(Int.) MxPS=  64 Ivl=125us
E:  Ad=02(O) Atr=01(Isoc) MxPS= 512 Ivl=125us
E:  Ad=04(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=86(I) Atr=01(Isoc) MxPS= 512 Ivl=125us
E:  Ad=88(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms

```

Now my question is how can i activate the second one?

greez
n3utrino

---

### Post by n3utrino on 2008-04-22
bump...

---

