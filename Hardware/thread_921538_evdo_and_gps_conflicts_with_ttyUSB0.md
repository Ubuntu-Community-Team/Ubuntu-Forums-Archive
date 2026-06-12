---
title: "evdo and gps conflicts with ttyUSB0"
date: 2008-09-16
forum: Hardware
---

### Post by memet on 2008-09-16
I'm having a problem with getting an automating the mounting of an EVDO and GPS.

I have a two udev rules set up to mount the two devices.

01-evdo.rules:
```
 SUBSYSTEM=='usb', SYSFS{idProduct}=='2110', SYSFS{idVendor}=='1410', RUN+="/sbin/modprobe usbserial vendor=0x1410 product=0x2110" 
```

25-gps.rules:
```
 BUS=='usb',SYSFS{idProduct}=='2303',SYSFS{idVendor}=='067b', KERNEL=='ttyUSB?', NAME="gps", OPTIONS="last_rule" 
```

About 90% of the time the mount properly with the evdo mounting on /dev/ttyUSB0 and /dev/ttyUSB1 and the gps on /dev/gps.

But the other 10% of the time, the evdo doesn't get recognized properly and while the gps still mounts to /dev/gps and the driver pl2303 (USB-Serial Driver used by usbserial) get attached to ttyUSB0 in /sys/bus/usb-serial/devices (i think).  

```
 
# dmesg | grep usb
# drivers/usb/serial/usb-serial.c: USB Serial support registered for pl2303
# usb 4-1: pl2303 converter now attached to ttyUSB0
# usbcore: registered new interface driver pl2303
# drivers/usb/serial/pl2303.c: Prolific PL2303 USB to serial adaptor driver

```

I know the device is recognized because when I do a lsusb it shows up.

If I remove both the gps and evdo manually and plug the evdo and then the gps in it will work again.  But this is going to be deployed on a moving vehicle so everything needs to be done in software.

As far as I can figure, I need to figure out how to rename the device at /sys/bus/usb-serial/devices level or be able to completely dismount the gps from the system with physically removing the connection.

Any help anyone could give would be great as I have spent several days google searching trying to find a solution. (I don't do forum posting alot so I apologize if its hard to read).

---

### Post by memet on 2008-09-17
never mind, figured out a solution

---

### Post by justcarroll on 2009-04-10
What was the solution?

---

### Post by memet on 2009-04-10
The problem ended up being that the EVDO used a different usb-serial driver than the GPS.  For some reason the EVDO cannot bind usbserial_driver to itself if the GPS driver pl2303 is already bound to ttyUSB0.  

So what I did was edited /etc/modprobe.d/blacklist by adding **blacklist pl2303** to the end of the file.

I was using Centos 5.2 so I added the line **modprobe pl2303** to /etc/rc.d/rc.local.  There isn't an equivalent in Ubuntu by default (as far as I know) but you can create one using the instructinos found **[here]("https://help.ubuntu.com/community/RcLocalHowto")**

Basically, I forced the EVDO to go bind itself to usbserial_driver first.  Then once everything was finished booting, I allowed I loaded usbserial which then attached itself to /dev/gps -- problem solved.

---

