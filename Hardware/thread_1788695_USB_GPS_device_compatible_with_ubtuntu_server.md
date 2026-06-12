---
title: "USB GPS device compatible with ubtuntu server"
date: 2011-06-23
forum: Hardware
---

### Post by chrisbay90 on 2011-06-23
I have an old laptop with a broken hinge on the screen. I plan to convert it into a trip recorder/wardriving machine to mount somewhere in my car and log where I travel, when i leave, how long im gone for. as well as possibly things like wifi along the way.

The laptop has built in wifi but no gps. I am looking for some suggestions.

What OS should i use. Was considering Ubuntu 10.04 server.
A USB GPS receiver with support for the above OS. Considering both a small USB dongle and an externally mounted arial for the car.
Possibly a secondary USB wifi antena. Considering both dongles and external arials.
Any prepackaged software? I might just pull in the data ever few seconds and dump it in a CSV or XML file.

---

### Post by sanderd17 on 2011-06-23
Normally, any gps software will use the gpsd, here is a list with compatible devices: [http://gpsd.berlios.de/hardware.html](http://gpsd.berlios.de/hardware.html)

I don't know what terminal program you can use to track, and for the OS, any OS that is able to run as a server (so any linux) will do. Ubuntu will be easy because of its easy package management.

---

### Post by chrisbay90 on 2011-06-23
> **sanderd17 said:**
> Normally, any gps software will use the gpsd, here is a list with compatible devices: [http://gpsd.berlios.de/hardware.html](http://gpsd.berlios.de/hardware.html)

I don't know what terminal program you can use to track, and for the OS, any OS that is able to run as a server (so any linux) will do. Ubuntu will be easy because of its easy package management.

Thanks sander. Apreciate it.

Good to know about the standard and that website. looking at GPS receivers now. I think I will go with ubuntu server 10.04.

My only concern is that I would like it to be able to connect to my home wifi whenever in range and upload files. However my experience with CLI machines and wifi has been a nightmare. Furthermore I need it to shutdown once it detects it is on battery power.

Anyone have any suggestions for the wifi?

---

### Post by sanderd17 on 2011-06-23
btw, are you willing to upload your traces to [http://www.openstreetmap.org](http://www.openstreetmap.org) (a free - as in speech and beer - map of the world)?

There are a lot of OpenStreetMap users that are also Linux users, so you'll find a lot of expertise there regarding Linux and gps.

And for the wifi, I can't help a lot. Maybe as a tip, you could look at xbmc. That's a media center that has a live edition build on top of Ubuntu. They offer no gui to connect to wifi, but a lot of users do want to connect to wifi. For normal servers, it's not so normal that they are connected to wifi.

---

### Post by chrisbay90 on 2011-06-24
Yeah, I will.

Thanks for the starting point.

Appreciate the help.

---

