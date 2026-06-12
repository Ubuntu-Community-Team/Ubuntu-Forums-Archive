---
title: "Help, Ubuntu cannot mount GPS unit using USB!!"
date: 2008-03-23
forum: Hardware &amp; Laptops
---

### Post by hopestorm on 2008-03-23
Hello everyone:
I got a Mio C320 GPS. It uses a USB to connect to computer. No problem to transfer data in Windows. But Ubuntu cannot recognize the unit. Someone has some ideas about this? 
Thanks..

---

### Post by odin1965 on 2008-04-08
Does your GPS have a setting for the USB connection type? Some GPS's are able to connect as an external GPS to be used thru GPSd for a program like GPSDRIVE. The USB data would usually be NMEA or something similar. 
  You probably want it connected as a mass storage device, so it shows up as a drive. There are a couple different connection option here as well. Ipods and other MP3 players, as well as cameras,  connect as MTP or MSC. If you can configure your GPS device as MSC, it should show up as a drive.

---

### Post by Brian_G_M on 2008-05-04
I have a similar problem with a Garmin 76CSx. I plug it into a USB and nothing happens. What must I do to make UBUNTU recognise it?
Thanks.

---

### Post by chooban on 2008-05-14
[http://ubuntuforums.org/showthread.php?t=773660&highlight=gps](http://ubuntuforums.org/showthread.php?t=773660&highlight=gps)

A quick modprobe might suffice. It worked for me.

---

### Post by Cha0tik on 2008-07-05
I have the same issue.. 

However, I have a Mio C320 GPS and I am not sure how to use modprobe.

I types sudo modprobe mio_gps
and I get FATAL: Module mio_gps not found.

---

