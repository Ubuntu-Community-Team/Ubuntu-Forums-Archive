---
title: "[SOLVED] Garmin GPS, Google and gpsbabel?"
date: 2008-09-22
forum: Hardware
---

### Post by shane2peru on 2008-09-22
I bought a Garmin 205w GPS, and it connects to Ubuntu fine as a USB mass storage device.  Now I can plot a trip on Google (my GPS doesn't contain Alaska, and I'm going there for a short trip but don't want to pay the $100 for the maps)  soo, I can plot a trip on Google maps and gpsbabel is supposed to then change that file into a Garmin readable file.  I'm very new to this GPS stuff, so if anyone has this figured out and wants to help I would be appreciative!  I did make a gpx file with gpsbabel, and put it on my GPS but not sure how to open it from the GPS now. :)  Perhaps I didn't do it right???  Not sure any help would be appreciated.

Shane

**EDIT:**  Oh here is a link that tells about a plugin for firefox that allows you to send a point from Google maps directly to your GPS, unfortunately it doesn't work with Linux. :(   [http://www8.garmin.com/support/download_details.jsp?id=3608](http://www8.garmin.com/support/download_details.jsp?id=3608)

---

### Post by shane2peru on 2008-09-23
Ok, this works for me!!!  Hoooray.  Let me give a quick guide on getting this to work (I have a Garmin Nuvi 200w)
First on Google earth find the place that you want to mark on your GPS, mark it then save the file as a km**l** not kmz!!  Now in the command line: ```
 gpsbabel -r -i kml -f /path/to/name.kml -x transform,rte=wpt -o gpx -F path/to/where/you/want/name.gpx 
```
After converting the file, you connect your GPS and just copy the gpx file to Garmin/Garmin/GPX/ folder you can name it whatever you want.  When you disconnect your Garmin, and turn it on, it will automatically look through the file, and add the new marker to your Favorites.  I hope this helps someone out.  :)

Shane

---

### Post by SGTF on 2008-11-07
Great! Thank you, just what I needed to convert my downloaded Google Earth placemarks to work with my Garmin Colorado 300.

---

### Post by shane2peru on 2008-11-07
> **SGTF said:**
> Great! Thank you, just what I needed to convert my downloaded Google Earth placemarks to work with my Garmin Colorado 300.

Glad someone got some use out of this!  :)

Shane

---

### Post by YumaJim on 2011-06-01
Another simple way is to 'pin' the location on Google Earth then Right Click on Pin and select Properties and you will see the coordinates of the pinned location. Select "To Where --> Coordinates on your GPS and enter the "pinned" coordinates. My Nivi 205W wants the coordinates in XX.YYYY format and Google Earth gives you the coordinates in DDMMSS. So you must convert the coordinates as follows:

DD + MM/60.0 + SS/3600.0   (don't forget the ".0's)

Round the result to four decimal places and enter into your GPS and save.

PS - Python IDLE is a good app to use for the math.

regards,
YumaJim

---

