---
title: "webcam image upside down"
date: 2010-07-22
forum: Hardware
---

### Post by oregonbob on 2010-07-22
I purchased an Asus K50ij laptop, installed Ubuntu 10.04 and got everything working except the image of from the built-in webcam is upside down in all applications. I tried the suggested gtk-v4l tool, but oddly it has no setting to change orienttion. I'm stumped.

I also cannot get Skype to see the camera. Cheese works though.

---

### Post by IcarusR on 2010-07-23
> tried the suggested gtk-v4l tool, but oddly it has no setting to change orienttion

Do you mean you've tried this, it has been tried & works on K50IJ....

[http://ubuntuforums.org/showthread.php?p=8925031#post8925031]("http://ubuntuforums.org/showthread.php?p=8925031#post8925031")

I don't think it is meant to have a setting to invert image. It just does it when you run Skype with the following command...

```
webcamWrapper skype

```

---

### Post by oregonbob on 2010-08-08
I tried the fix you gave link for. It did make it so at least I now see video Skype, but both Skype and Cheese have an upside down image.

Something that doesn't look right is when I do a "lsusb" my results are:

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 13d3:5130 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Shouldn't I see a line that says "video"?

However "usb-devices" command shows a video:
T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=13d3 ProdID=5130 Rev=12.11
S:  Manufacturer=Sonix Technology Co., Ltd.
S:  Product=USB 2.0 Camera
C:  #Ifs= 2 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(video) Sub=01 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(video) Sub=02 Prot=00 Driver=uvcvideo

I even did the suggestion to add the launchpad location to my sources.list but it said I was current.

There is another post that includes downloading source and patching several files, many steps to complete.

---

