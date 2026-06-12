---
title: "Garmin nuvi 750 recgonized as scsi, should load proper driver"
date: 2009-05-18
forum: Hardware
---

### Post by skippuff54 on 2009-05-18
My Garmin nuvi 750 is connected via USB but shows up as scsi.

How can I get the proper driver to load for this device so that I can transfer maps from Google, Gpsdrive, etc., onto the Garmin?

I can access the data storage on the Garmin and give/take .gpx files, but I need a driver to actually communicate with the GPS that those files I give it are routes. Right now, if I load a gpx file manually, the GPS doesn't recognize it as a route.

For those unfamiliar with the nuvi 750, it lacks NMEA protocol. The GPS stores routes as a series of waypoints, and dumps way/trackpoints into a Current.gpx file before clearing memory on shutdown.

gpsbabel and various other gps programs won't work and again it appears that the issue is the system loads the GPS as a scsi device rather than use the garmin_gps driver.

Any ideas?

---

### Post by skippuff54 on 2009-05-19
Garmin software support just advised me that they do not support Linux. 

He advised me to upload waypoints as.gpx files to the GPX folder, then create routes by hand on the Garmin, using those waypoints. He advised that Mapquest might work, and he also said that updating the Garmin software via Windows could help.

I had asked specifically about Google maps.

That was the scope of our conversation and I have not yet tested either the waypoint method or the Mapquest method.

Comments, anyone?

---

