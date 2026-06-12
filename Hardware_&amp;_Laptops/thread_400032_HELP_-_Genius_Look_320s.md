---
title: "HELP - Genius Look 320s"
date: 2007-04-03
forum: Hardware &amp; Laptops
---

### Post by eyad on 2007-04-03
Dear All,

i buy a webcam (Genius look 320s), but i couldnt get it working with ubuntu, how to make it work?

by the way:
- i have ubuntu 7.04
- i dont have linux driver for this webcam, it came with windows and mac drivers only

regards

---

### Post by teaker1s on 2007-04-04
In terminal please type
```
lsusb
```
Please post output, I will try to see if your cam is supported

---

### Post by eyad on 2007-04-07
Dear teaker1s,

this is the output of the lsusb command:

Bus 004 Device 003: ID 0458:7029 KYE Systems Corp. (Mouse Systems) 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 15d9:0a33  
Bus 001 Device 001: ID 0000:0000  


regards

---

### Post by teaker1s on 2007-04-07
> 0458:7029 KYE Systems Corp. (Mouse Systems) 

provided you have no other genius products connected then the above is your webcam vendor and product id 0458:7029 

While I have not managed to find specific documentation for your model, can I recommend these
[https://help.ubuntu.com/community/Webcam?highlight=%28webcam%29]("https://help.ubuntu.com/community/Webcam?highlight=%28webcam%29")

[http://ubuntuforums.org/showthread.php?t=97382&highlight=genius+webcam]("http://ubuntuforums.org/showthread.php?t=97382&highlight=genius+webcam")

---

### Post by eyad on 2007-04-08
still no luck :(
i have try to use easycam but it cannot recognize my cam
even the videocam look its different than what i have 
mine is genius look 320s
here is the link to the vendor

_***[GeniusLook320s]("http://www.geniusnet.com/geniusOnline/online.portal?_nfpb=true&_pageLabel=productPage&productPortlet_actionOverride=%2Fportlets%2FproductArea%2Fproduct%2FqueryProduct&productPortletproductId=114011&test=default")***_

and the driver they provide is windows and mac only is there any way to have the linux driver from these driver ?

regards

---

### Post by eyad on 2007-04-08
by the way i just installed gspcav1 and with no luck

this is the lsmod output

#lsmod | grep gspca
gspca                 607824  0 
videodev               28160  1 gspca
usbcore               134280  5 gspca,usbhid,ehci_hcd,uhci_hcd


any idea ??? 

regards

---

### Post by teaker1s on 2007-04-08
I'm sorry I have no more suggestions, maybe someone else will suggest which driver if any is avaliable, your 0458:7029 is the key to finding a driver

---

### Post by eyad on 2007-04-22
thanks for you help, i really need help guys :(

---

### Post by eyad on 2007-04-23
guys i still couldnt make my web cam working this is my /proc/bus/usb/devices
i dont wrote all the file i only wrote the section that is related to my web cam


```

 T:  Bus=04 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  6 Spd=480 MxCh= 0
 D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
 P:  Vendor=0458 ProdID=7029 Rev= 1.00
 S:  Product=USB20 Camera    
 C:* #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
 I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
 E:  Ad=81(I) Atr=01(Isoc) MxPS=   0 Ivl=125us
 E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
 E:  Ad=83(I) Atr=03(Int.) MxPS=   1 Ivl=64ms
 I:  If#= 0 Alt= 1 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
 E:  Ad=81(I) Atr=01(Isoc) MxPS= 128 Ivl=125us
 E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
 E:  Ad=83(I) Atr=03(Int.) MxPS=   1 Ivl=64ms
 I:  If#= 0 Alt= 2 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
 E:  Ad=81(I) Atr=01(Isoc) MxPS= 256 Ivl=125us
 E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
 E:  Ad=83(I) Atr=03(Int.) MxPS=   1 Ivl=64ms
 I:  If#= 0 Alt= 3 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
 E:  Ad=81(I) Atr=01(Isoc) MxPS= 384 Ivl=125us
 E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
 E:  Ad=83(I) Atr=03(Int.) MxPS=   1 Ivl=64ms
 I:  If#= 0 Alt= 4 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
 E:  Ad=81(I) Atr=01(Isoc) MxPS= 512 Ivl=125us
 E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
 E:  Ad=83(I) Atr=03(Int.) MxPS=   1 Ivl=64ms
 I:  If#= 0 Alt= 5 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
 E:  Ad=81(I) Atr=01(Isoc) MxPS= 680 Ivl=125us
 E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
 E:  Ad=83(I) Atr=03(Int.) MxPS=   1 Ivl=64ms
 I:  If#= 0 Alt= 6 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
 E:  Ad=81(I) Atr=01(Isoc) MxPS= 800 Ivl=125us
 E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
 E:  Ad=83(I) Atr=03(Int.) MxPS=   1 Ivl=64ms
 I:  If#= 0 Alt= 7 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
 E:  Ad=81(I) Atr=01(Isoc) MxPS=1800 Ivl=125us
 E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
 E:  Ad=83(I) Atr=03(Int.) MxPS=   1 Ivl=64ms
 I:  If#= 0 Alt= 8 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
 E:  Ad=81(I) Atr=01(Isoc) MxPS=3072 Ivl=125us
 E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
 E:  Ad=83(I) Atr=03(Int.) MxPS=   1 Ivl=64ms

```

---

### Post by teolemon on 2007-09-29
Same problem here. Bringing it back to the store for refund, and buying another one. I've sent a mail to Genius asking for a driver or a release as open-source of the specs.

---

### Post by LuVeS on 2008-02-03
I have the same webcam (look 320S) and I find Linux drivers only for webcam Look 316 but I can`t install it... 
Content of arhive is: 
$ ls
mview  usbvm305.ko  vm305.sh

What should I do with that?? (I am new in Linux)
(sorry for my english)
Any help would be great

---

