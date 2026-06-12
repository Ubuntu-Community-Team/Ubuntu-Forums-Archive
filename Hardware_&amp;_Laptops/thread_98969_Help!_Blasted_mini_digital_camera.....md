---
title: "Help! Blasted mini digital camera...."
date: 2005-12-04
forum: Hardware &amp; Laptops
---

### Post by Shifty Powers on 2005-12-04
My sis has bought a digital camera for her daughter based on:

[http://www.jeilin.com.tw/English/jl2005a.htm](http://www.jeilin.com.tw/English/jl2005a.htm)

When i plug it in i get this:

[[IMG]http://img206.imageshack.us/img206/5097/screenshot7ht.th.png[/IMG]](http://img206.imageshack.us/my.php?image=screenshot7ht.png)

```
T:  Bus=02 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#= 10 Spd=12  MxCh= 0
D:  Ver= 1.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0979 ProdID=0224 Rev= 1.00
S:  Manufacturer=
S:  Product=PC CAMERA
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=300mA
I:  If#= 0 Alt= 0 #EPs= 5 Cls=00(>ifc ) Sub=00 Prot=00 Driver=(none)
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=03(O) Atr=02(Bulk) MxPS=   8 Ivl=0ms
E:  Ad=84(I) Atr=02(Bulk) MxPS=   8 Ivl=0ms
E:  Ad=85(I) Atr=01(Isoc) MxPS=   0 Ivl=1ms
I:  If#= 0 Alt= 1 #EPs= 5 Cls=00(>ifc ) Sub=00 Prot=00 Driver=(none)
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=03(O) Atr=02(Bulk) MxPS=   8 Ivl=0ms
E:  Ad=84(I) Atr=02(Bulk) MxPS=   8 Ivl=0ms
E:  Ad=85(I) Atr=01(Isoc) MxPS=1023 Ivl=1ms
I:  If#= 0 Alt= 2 #EPs= 5 Cls=00(>ifc ) Sub=00 Prot=00 Driver=(none)
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=03(O) Atr=02(Bulk) MxPS=   8 Ivl=0ms
E:  Ad=84(I) Atr=02(Bulk) MxPS=   8 Ivl=0ms
E:  Ad=85(I) Atr=01(Isoc) MxPS= 760 Ivl=1ms
I:  If#= 0 Alt= 3 #EPs= 5 Cls=00(>ifc ) Sub=00 Prot=00 Driver=(none)
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=03(O) Atr=02(Bulk) MxPS=   8 Ivl=0ms
E:  Ad=84(I) Atr=02(Bulk) MxPS=   8 Ivl=0ms
E:  Ad=85(I) Atr=01(Isoc) MxPS= 512 Ivl=1ms
I:  If#= 0 Alt= 4 #EPs= 5 Cls=00(>ifc ) Sub=00 Prot=00 Driver=(none)
E:  Ad=81(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=02(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=03(O) Atr=02(Bulk) MxPS=   8 Ivl=0ms
E:  Ad=84(I) Atr=02(Bulk) MxPS=   8 Ivl=0ms
E:  Ad=85(I) Atr=01(Isoc) MxPS= 256 Ivl=1ms

```

shows up in my cat /proc/bus/usb/devices

and using usbview gives me:

[[IMG]http://img204.imageshack.us/img204/534/screenshot13xc.th.png[/IMG]](http://img204.imageshack.us/my.php?image=screenshot13xc.png)

BUT, it isn't mounted and i can't find anyway to do it.... The jeilin website says, (it seems), that it should work on linux but the cd only has windows drivers on it.... I.m really stumped.
I'm really hoping someone can help. If you need any more infro please let me know and i'll post it.

---

### Post by Colly on 2007-06-12
I have the same exact problem.  I have the VuPoint DC-10B2-M Mini Digital Camera that's also based on the JL2005a chips and I can't get pictures from it either. Ubuntu Edgy EFT shows it in the hardware manager, but doesn't mount it and I can't find any software that handles it.  Automatix2 had some driver that was supposed to handle 352 types of web cams, but Vupoint and Jeilin are not listed and neither is JL2005a or DC-10B2-M. 
The camera works fine on my XP machine with the software that came with it.
By the way, that's a letter 'b' not a digit 'eight' in the model # DC-10B2-M.   ( one-zero-bee-two)
I was typing it wrong in Google searches until I looked again at the tiny label under the camera with a magnifying glass and discovered my error.

---

