---
title: "Not able to connect to my Creative Zen Micro"
date: 2007-01-05
forum: Hardware &amp; Laptops
---

### Post by cdysthe on 2007-01-05
Hi,

I am not able to connect my Creative Zen Micro mp3 player. I know others have been able to do this using Gnomad 2, but my problem is that the device seems to be interpreted as a camera when I connect it since a "camera detected" dialog comes up when when I connect it. In /dev/bus/usb/.usbfs/devices I have the following entry:

T:  Bus=01 Lev=01 Prnt=01 Port=01 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=041e ProdID=4130 Rev= 1.00
S:  Manufacturer=Creative Technology Ltd
S:  Product=Creative Zen Micro
S:  SerialNumber=010525513D038FE5
C:* #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=00(>ifc ) Sub=00 Prot=00 Driver=(none)
E:  Ad=02(O) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=82(I) Atr=02(Bulk) MxPS= 512 Ivl=0ms
E:  Ad=83(I) Atr=03(Int.) MxPS=   8 Ivl=1ms

This means the player is detected correctly, doesn't it? So how do I get it to work with Gnomad 2? I have installed everything needed for gnomad 2 to work including MTP support, but no go. 

Ideas anyone?

//C

---

### Post by pay on 2007-01-06
You need to compile gnomad2 with libmtp support. Just installing both packages isn't enough. There are guides on how to do this on the forums.

---

### Post by cdysthe on 2007-01-06
> **pay said:**
> You need to compile gnomad2 with libmtp support. Just installing both packages isn't enough. There are guides on how to do this on the forums.

Thanks, but I've already done that. The player is still not recognized. I will now try to downgrade the firmware to see if that helps.

//C

---

### Post by pay on 2007-01-06
I found that gnomad2 wouldn't work with libmtp 0.1.2 or 0.1.1, but it worked with 0.1.0. Maybe that will help but I don't know.

---

### Post by bsalt on 2007-02-03
Do you have it working now, cdysthe?

---

### Post by cdysthe on 2007-02-03
> **bsalt said:**
> Do you have it working now, cdysthe?

I downgraded the firmware on the Zen, so now it works. Seems to be the latest PlayForSure firmware causing the problems.

//C

---

### Post by bsalt on 2007-02-03
I didn't know you could! Awesome! I just hate seeing people hangin without a solution to their problem.

---

