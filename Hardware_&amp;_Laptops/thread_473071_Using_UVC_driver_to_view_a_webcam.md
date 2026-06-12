---
title: "Using UVC driver to view a webcam"
date: 2007-06-13
forum: Hardware &amp; Laptops
---

### Post by stealth86 on 2007-06-13
I'm trying to setup a webcam on Kubuntu 7.04. The cam is USB video class compatible, it works in windows just  fine without an explicit driver. I've installed the latest version of the linux uvc driver, and the camera is using this as the driver. (See below)

When I try to view the camera however, results vary from crashing (xawtv) to failing with an error. Camorama fails with the error message "could not connect to video device (/dev/video0). Please check the connection."

So does anyone have any ideas?


From /proc/bus/usb/devices

Bus=01 Lev=01 Prnt=01 Port=03 Cnt=02 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(unk. ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=0c45 ProdID=62c0 Rev= 1.00
S:  Manufacturer=Sonix Technology Co., Ltd.
S:  Product=USB 2.0 Camera
S:  SerialNumber=SN0001
I:  If#= 0 Alt= 0 #EPs= 1 Cls=0e(unk. ) Sub=01 Prot=00 Driver=uvcvideo
E:  Ad=83(I) Atr=03(Int.) MxPS=  16 Ivl=4ms
I:  If#= 1 Alt= 0 #EPs= 0 Cls=0e(unk. ) Sub=02 Prot=00 Driver=uvcvideo
I:  If#= 1 Alt= 1 #EPs= 1 Cls=0e(unk. ) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS= 128 Ivl=125us
I:  If#= 1 Alt= 2 #EPs= 1 Cls=0e(unk. ) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS= 256 Ivl=125us
I:  If#= 1 Alt= 3 #EPs= 1 Cls=0e(unk. ) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS= 800 Ivl=125us
I:  If#= 1 Alt= 4 #EPs= 1 Cls=0e(unk. ) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS=1600 Ivl=125us
I:  If#= 1 Alt= 5 #EPs= 1 Cls=0e(unk. ) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS=2400 Ivl=125us
I:  If#= 1 Alt= 6 #EPs= 1 Cls=0e(unk. ) Sub=02 Prot=00 Driver=uvcvideo
E:  Ad=81(I) Atr=05(Isoc) MxPS=3000 Ivl=125us

---

### Post by stealth86 on 2007-06-13
So i did some more testing with MPlayer, and I got a little bit farther.

From the terminal i ran mplayer tv:// -tv driver=v4l2:width=640:height=480:device=/dev/video0 -fps 30   .

This actually brought up movie window, but there was no output, it was all green. The following error was reported (in the console):

v4l2: ioctl dequeue buffer failed: Invalid argument, idx = 0

So I'm still stuck, but hopefully going in the right direction....

---

### Post by silverglade00 on 2007-06-13
I have the same camera. It only work in apps that support v4l 2. AFAIK, ekiga is the only one that will fire it up so far.

---

### Post by dmit10 on 2007-09-25
threy say that mplayer works with patch 

[http://www.mail-archive.com/linux-uvc-devel%40lists.berlios.de/msg01147.html](http://www.mail-archive.com/linux-uvc-devel%40lists.berlios.de/msg01147.html)

patch here: 

[http://svn.mplayerhq.hu/mplayer/trunk/stream/tvi_v4l2.c?r1=20662&r2=21603&view=patch](http://svn.mplayerhq.hu/mplayer/trunk/stream/tvi_v4l2.c?r1=20662&r2=21603&view=patch)

---

