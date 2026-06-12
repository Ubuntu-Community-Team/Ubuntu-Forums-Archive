---
title: "Integrated HP Webcam"
date: 2009-03-23
forum: Hardware
---

### Post by anili100 on 2009-03-23
Hi!
Can someone please tell me how can I get my integrated webcam to work in Ubuntu?
Thanks in advance :)

---

### Post by teaker1s on 2009-03-23
what model laptop? 
also Applications>Accessories>Terminal then copy and paste this
```
lsusb
``` will list usb connected devices.
post your output.

---

### Post by anili100 on 2009-03-24
It's HP Compaq 6735s.
Here's my lsusb output:
```
Bus 007 Device 002: ID 04f2:b083 Chicony Electronics Co., Ltd 
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 1241:1166 Belkin MI-2150 Trust Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by teaker1s on 2009-03-24
[COLOR="Red"]Bus 007 Device 002: ID 04f2:b083 Chicony Electronics Co., Ltd [/COLOR]
This is the webcam I can see see on your system, you could use "cheese" to configure it.

We can do this both ways
Graphically by using Applications>Add/Remove
then
in top center box change to "all open source applications" 

then search "cheese"

or terminal

```
sudo apt-get install cheese
```



"cheese" will then be found in Applications>Graphics>cheese webcam booth

you can hit the video tab and hopefully see yourself. If you need to know how cheese has found your webcam hit the Edit>Preferences tabs
mine shows as>  /dev/video0

this information is useful for configuring other applications.

---

### Post by anili100 on 2009-03-25
That worked great for me! I installed cheese and saw myself  :) 
Thanks a lot!!

---

### Post by teaker1s on 2009-03-25
Your Welcome :popcorn:

---

### Post by redenex on 2009-03-25
purrrfect! thank you. But why would my "video" flicker a lot?

---

### Post by teaker1s on 2009-03-25
redenex, have you the same model camera listed in usb devices? if your device isn't exactly the same then it may be that yours isn't completely compatible with cheese.

Secondly what graphics are you using and have you tried checking display refresh rate.

---

### Post by ZeTTi on 2010-08-17
thanks, work for me too !!
you re great maaan :D

---

### Post by l0ssless on 2012-03-25
Hi! I am hoping you're gonna help me.
I have integrated webcam Chicony in my HP 6735s laptop. It works, even in Skype but has strange colors. I look almost like a cartoon guy. I've tried to play with gstreamer and cheese preferences but no luck whatsoever. It's definately not a brightness or contrast issue. 
When I connect some external webcams (logitech obe) it works and shows proper colors etc.
Any ideas? Help much appreciated.

---

