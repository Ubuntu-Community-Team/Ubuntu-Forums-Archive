---
title: "DW700 GPS min card on Dell Mini 1010"
date: 2010-03-27
forum: Hardware
---

### Post by pwolfamv on 2010-03-27
I've been looking into how to get this up and running on 9.10.  lsusb shows the device is being detected (Bus 004 Device 002: ID 413c:9500 Dell Computer Corp.) but I don't think a driver is installed...  I'm relatively new to linux troubleshooting so i'm learning as i go.  would like some direction from anyone willing to help.  let me know if you need more information.

---

### Post by pwolfamv on 2010-03-27
So, i have a general hardware driver question to throw out there... How do I know if a device has a driver installed? 

I looked at my devices via the gnome device manager and it shows the DW700 GPS Card mounted on /dev/ttyUSB0.  tried to use gpsbabel to get some info off of it but it seems like it's just not doing anything so no output.  not getting anything off of gpsd/xgps.  Any suggestions as to what to try next would be appreciated, thanks.

---

### Post by montgoj on 2010-03-28
I just got mine in the mail today.  After I image the harddrive I'll be blasting it and loading ubuntu.  GPS is one of my first projects on this so I'll let you know what I find on mine.

---

### Post by pwolfamv on 2010-03-29
> **montgoj said:**
> I just got mine in the mail today.  After I image the harddrive I'll be blasting it and loading ubuntu.  GPS is one of my first projects on this so I'll let you know what I find on mine.

Awesome, let me know what you come up with or if there's anything I can do to help.

---

### Post by SLamontagne on 2010-03-29
Hi, I also got mine saturday and I would like to have the GPS/WPS working. It came with XP pre-installed so I kept it and put UNR 9.10 beside it. I had to use the poulsbo video driver instruction to get decent video and now everything seems to work except the GPS.

In windows I've openned it with hyperterminal and was able to get the NMEA string. I'm wondering if the cp210x chip is sending it directly through the serial port or if a driver is really needed.

In the first case I believe that configuring the baud rate should work directly, as it does for me with the GPS Locator that came with a Streets & Trips and that was seen as a pl2303 usb-to-serial.
With this pl2303 thing I was using gtkterm on ttyUSB0 at 4800baud and it was working perfectly. But for the DW700 seen as cp210x it doesn't... I tried with all the baud rate accessible in gtkterm without success.

I think that the DW700 is using a driver to do the GPS analyze before sending it to the serial adapter. Anyway, I can help on providing information if required. I would also like to have it working.

Sly

PS: Sry I'm in a hurry right now so I write this post quickly

---

### Post by viking415 on 2010-05-13
I have attempted to talk to my GPS on my Dell Mini 10 (Inspiron 1010) without success.  I do know that Ubuntu recognizes it as a tty device.  However, out of the box, gpsd can't talk to it.  Admittedly, I haven't spent all that much time on it.

Maybe there's a way to figure out the COM communication by running it on Windows.

According to the Dell GPS utility, the GPS chip is BCM4750 A1.  The iPhone GPS chip appears to be the same (BCM4750).  There is a post in the French ubuntu forum about this here:

[http://forum.ubuntu-fr.org/viewtopic.php?id=345391](http://forum.ubuntu-fr.org/viewtopic.php?id=345391)

---

