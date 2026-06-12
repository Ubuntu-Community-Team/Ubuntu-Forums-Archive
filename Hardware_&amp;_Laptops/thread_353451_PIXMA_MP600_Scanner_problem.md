---
title: "PIXMA MP600 Scanner problem"
date: 2007-02-04
forum: Hardware &amp; Laptops
---

### Post by aaronfulton on 2007-02-04
First of thanks for any assistance! :) 

I have already edited my sane PIXMA backend to use the MP 600 and it works kind of. SANE sees my scanner and every little option it has and everything looks good but when I click Scan in xSANE it connects to my scanner and it does scan but when it tries retreiving the image it errors stating *Error during read: Error during device I/O* . 
I also have had probs with Dapper properly mounting drives which I think could be the issue. 
It original didn't see my utility partition and thought my Windows partition was a removable drive. Now it sees my MP 600 as a USB Storage device:

T:  Bus=05 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#=  4 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=04a9 ProdID=1718 Rev= 1.03
S:  Manufacturer=Canon
S:  Product=MP600
S:  SerialNumber=11137A
C:* #Ifs= 3 Cfg#= 1 Atr=c0 MxPwr=  2mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=00 Prot=ff Driver=usbfs
E:  Ad=07(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=88(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=89(I) Atr=03(Int.) MxPS=  64 Ivl=128ms
I:  If#= 1 Alt= 0 #EPs= 2 Cls=07(print) Sub=01 Prot=02 Driver=usblp
E:  Ad=01(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
I:  If#= 2 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 **Driver=usb-storage**
E:  Ad=84(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=05(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms

I tried modprobe but the scanner module is not longer available. Does anyone know how I get Dapper to recognize my scanner as a scanner?

---

