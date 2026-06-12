---
title: "scrambled images from Bushnell Image View Binoculars digital camera"
date: 2010-11-14
forum: Hardware
---

### Post by meonkeys on 2010-11-14
Anyone tried to view images from the camera on a pair of Bushnell Image View Binoculars? I can, but they look encrypted or obfuscated or something. Here's an example:
[[IMG]http://img688.imageshack.us/img688/7694/sonix002.th.png[/IMG]](http://img688.imageshack.us/i/sonix002.png/)

The bottom of my binoculars/camera says "10x25 FOV 300 @ 1000 yds". [Mine looks exactly like this]("http://www.google.com/products/catalog?q=bushnell+camera+binoculars&hl=en&safe=off&prmd=ivs&resnum=3&biw=1035&bih=706&um=1&ie=UTF-8&cid=4887828654815952229&ei=6lHgTIuJD4GWsgPgx-iCCw&sa=X&oi=product_catalog_result&ct=result&resnum=1&ved=0CFUQ8wIwAA#"). It uses a USB connection.

I'm able to import images using F-Spot. When I click "Import", it shows up as "Mini-Shotz ms-350". lsusb reports a device id of "0c45:8008".

---

### Post by fondle-em on 2011-01-12
You can use [gtkam]("apt:gtkam") to get at the pictures on those binoculars.  It looks like F-Spot does what you pictured, and Shotwell (as of version 0.8.1) doesn't even pretend to support the Bushnell Image View or the [PPM files]("http://en.wikipedia.org/wiki/Netpbm_format") it uses.  Gtkam, GIMP and Eye Of Gnome have no complaints.

---

