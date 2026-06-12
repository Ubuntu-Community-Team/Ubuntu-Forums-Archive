---
title: "How to configure TouchScreen in Linaro on IGEPv2"
date: 2011-08-17
forum: Hardware
---

### Post by pratikshinde on 2011-08-17
Dear All,
I am using Linaro (Ubuntu 10.10 Netbook) on ARM platform [IGEPv2]("http://shop.igep.es/index.php?main_page=product_info&products_id=40"). 

I have 4.3" LCD with touchscreen interface, The touchscreen driver is ADS7846 Touchscreen which has SPI interface, I could find this information by command** cat /proc/bus/input/devices**,

on booting up I can see GUI on LCD and touch works well, but no calibration:(, I tried methods in some forums but no luck,
I found some forum threads and [**this webpage**]("http://setupguides.blogspot.com/2010/10/calibrating-touchscreen-in-ubuntu-1010.html").

my touch screen is working I can find some garbage data on command** cat /dev/input/event0**.

I have installed xinput,
but on giving command **"#xinput list"**  I get 
> root@localhost:~# xinput list
Unable to connect to X server
So I cant follow next instructions.
Any suggestions?

---

### Post by pratikshinde on 2011-08-19
I am somewhat successful to make use of touch screen.
I followed the following steps:
**1. In my case I had 5 files listed in /usr/share/X11/xorg.conf.d/**

10-evdev.conf
50-wacom.conf
60-magictrackpad.conf
50-synaptics.conf
51-synaptics-quirks.conf
but only the **10-evdev was useful. I deleted other files.**

2. I added the following line in touchscreen section of 10-evdev file and It worked!

Section "InputClass"
        Identifier "evdev touchscreen catchall"
        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event0"
        Driver "evdev"
    **Option "InvertY" "true"**
EndSection


However still have calibration issue with corners,and some part of top and bottom. 

Thanks

---

