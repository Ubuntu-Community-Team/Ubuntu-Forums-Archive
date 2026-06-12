---
title: "Avermedia MR800 usb radio Ubuntu 7.04"
date: 2007-05-23
forum: Hardware &amp; Laptops
---

### Post by nioakeim on 2007-05-23
Hi to all!!!

Although i am not a new linux, i have a thing with configuring devices that dont work...
My problem is with a Avermedia MR800 usb radio. Let me give you some info:

user@desktop:~$ uname -r
2.6.20-15-generic

user@desktop:~$ lsusb | grep AV
Bus 003 Device 002: ID 07ca:b800 AVerMedia Technologies, Inc. 



user@desktop:~$ cat /proc/bus/usb/devices

T:  Bus=03 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=07ca ProdID=b800 Rev= 0.03
S:  Manufacturer=AVerMedia Technologies
S:  Product=AVerMedia USB Radio
C:* #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=200mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=03(HID  ) Sub=00 Prot=00 Driver=usbhid
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=255ms
E:  Ad=02(O) Atr=03(Int.) MxPS=   8 Ivl=120ms

Could You Pleaseeeeeeeee tell me what i need to do to make it work? I want to use gnomeradio for it but i says "could not open device /dev/radio0" which is quite right since no radio0 is registered with this device. You will fill my life with music....Thanks in advance

---

### Post by nioakeim on 2007-05-23
None? Hmmm I see...I suppose it's a lot to ask for some guidance. Thanks anyway

---

