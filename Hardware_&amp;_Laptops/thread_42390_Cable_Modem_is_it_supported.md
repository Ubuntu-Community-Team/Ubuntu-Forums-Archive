---
title: "Cable Modem: is it supported?"
date: 2005-06-17
forum: Hardware &amp; Laptops
---

### Post by wadesmart on 2005-06-17
06172005 0944 GMT-5

I have been a windows user but with the problems of late I have decided to make a full move to linux. However, before doing so its best to know if what I have works. 

I have a cable modem and service through my cable company. How can you know if it is going to work? I mean, once you get installing the OS, you wont have access to the net if problems arise. 

Is anyone using a cable modem on their ubuntu system?

Wade

---

### Post by Gary Powers on 2005-06-17
Noithing but cable for my set ups.  I have done several installations of Ubuntu (not to mention other Linux distributions) and all have worked properly.  Enjoy.

Gary

---

### Post by rmjokers on 2005-06-17
You should have no problems using a cable modem with linux.  Linux is not actually aware of the cable modem normally, assuming you have an ethernet card.  It just talks ethernet to the cable modem as if it is on a regular ethernet network.  As long as linux supports the ethernet card, and as long as you set up your network settings properly (if your cable company uses DHCP, this will be done automatically), you will be fine.  If you have a USB connection to the cable modem, there may be some issues (I have never tried this but there is support for some cable modems).

One thing you might want to try is testing a linux live CD like Knoppix or Ubuntu Live to see if all of your hardware works before you actually install anything.  This should give you a good idea of how difficult your upgrade will be.

---

