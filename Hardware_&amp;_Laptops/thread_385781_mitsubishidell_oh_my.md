---
title: "mitsubishi/dell oh my"
date: 2007-03-16
forum: Hardware &amp; Laptops
---

### Post by joynasjay on 2007-03-16
Dell Inspiron 6000 (Ubuntu works fine in the built in lcd display). The problem is, I don't know how to output the display to Mitsubishi Diamond pro 2040u monitor. This monitor is like 6 years old already and Mitsubishi doesn't have a driver or support page anymore. So do I need a driver or is there another way to output it to this monitor?

---

### Post by teaker1s on 2007-03-16
you need to find the technical spec's of the monitor, then
```
sudo dpkg-reconfigure xserver-xorg
```
here you will need to tell xserver the horizontal and vertical specs and display resolutions the monitor can handle

---

