---
title: "Touchscreen problem"
date: 2007-08-02
forum: Hardware &amp; Laptops
---

### Post by i-touchsystems on 2007-08-02
Hi,

I'm trying to install an ETWO Touch USB touchscreen on Ubuntu 7.04 but seem to fail in doing all the steps. The readme file tells me this:

[FONT="Fixedsys"]1. Install touch screen driver, calibration utility, and calibrate it.

  (1.1).After installing the hardware, boot your computer as root.
  (1.2).To install the software, go to console and chang direction to this folder and run ./install(Except FC5) or do the following step a,b,c:
        a).Copy etwousb_drv.o to /usr/X11R6/lib/modules/input  ( /usr/lib/xorg/modules/input  for Fedora Core5 )
            (use "cp etwousb_drv.o /usr/X11R6/lib/modules/input")  ( /usr/lib/xorg/modules/input  for Fedora Core5 )
        b).Copy etwocalusb to /usr/local/bin
            (use "cp etwocalusb /usr/local/bin")
        c).Copy etwocalXusb to /usr/local/bin
            (use "cp etwocalXusb /usr/local/bin")

(1.3).Edit your X Config file which is in /etc/X11/xorg.conf
     <1.3.1>.Before Edit the X Config file,I recommend you backup your config file. 
            cp /etc/X11/xorg.conf /etc/X11/xorg.conf-bk
     <1.3.2>.Add the following line to the Section "ServerLayout" in the X config file
              Inputdevice   "touchscreen1"  "SendCoreEvents"
     <1.3.3>.Find out which event your ETwoTouch Screen is attached to.
            Use "cat /proc/bus/input/devices" in terminal,you will see "Name=... ETWO USB TOUCHSCREEN" and "Handlers=event*"[/FONT]

OOPS! Can't seem to find an event attached to the touchscreen.. The touchscreen isn't even listed...

Can anyone help me a bit on this one, I'm stuck... 

Thank you so much in advance :)

---

### Post by DrAfk on 2007-08-16
i have this problem, producer promises to issue driver update

---

### Post by DrAfk on 2007-08-16
i tested evtouch driver, it work, but iI was not able to calibrate

---

### Post by DrAfk on 2007-08-18
In Fedora Core 6 & Ubuntu 6.10 i dont have trouble

---

