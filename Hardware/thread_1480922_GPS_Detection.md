---
title: "GPS Detection"
date: 2010-05-12
forum: Hardware
---

### Post by OOzypal on 2010-05-12
Hello,

I have a GPS that a friend brought to me from China. The splash screen shows: 

iGo Amigo 
[www.naviextars.com](www.naviextars.com)

I want to use for completing my Master's research on Wireless Security. I want to do Wardriving. 

The issue how can I connect it to Ubuntu and read GPS coordinates. How can I know which device it is connected to i.e. /dev/ttyS, etc.

Thx

---

### Post by grege on 2010-05-12
With any GPS you need the gpsd daemon. Open Synaptic and search on gps and you will find a few programs.

Install gpsd and gpsd-clients. gpsd-clients includes xgps a simple program to use to check your GPS is connected and outputting data. xgps is a command line program it will not appear in your menus.

Plug in the gps and run "dmesg" from a terminal and you should see it attached to /dev/ttyUSB0 and gpsd should automatically find it, if it can control it.

I run "sudo dpkg-reconfigure gpsd"  and set it not to autoload or auto configure and then when I want my gps connected I just load it from a terminal with the command "gpsd /dev/ttyUSB0"

I have no idea if your GPS will work in this manner, I use a USB GPS dongle (a Globalsat BU-353) specifically designed for computers. My Globalsat works well, I use it for OpenStreetMap mapping, but it would work for wardriving just as well.

At least this will get you started in your quest.

---

### Post by grege on 2010-05-12
A bit more thought and it is apparent that you will not get a lat/long output from your device. You may be able to save gps tracks and then download them, if that gives you enough info.

---

