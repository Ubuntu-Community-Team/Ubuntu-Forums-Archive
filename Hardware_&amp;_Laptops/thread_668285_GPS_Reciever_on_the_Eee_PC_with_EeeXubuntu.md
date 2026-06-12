---
title: "GPS Reciever on the Eee PC with EeeXubuntu"
date: 2008-01-15
forum: Hardware &amp; Laptops
---

### Post by matthx on 2008-01-15
Hey guys. I have ordered myself an Eee PC and its bein shipped at the moment. Im planning to get a GPS reciever and i would like to run EeeXbuntu. I have searched a bit about the subject and i have found infos about gpsd (gps deamon) for linux. I visited their website and found multiple other software that uses their program to do some road navigational tracking. My problem is that im in the province of Quebec so most of those road maps are either missing or incomplete. The OpenStreetMap for example only has some major high ways. I would like to know if any of you have infos that could help me get maps for my area. Also is there any of you that have suggestions for a usb reciever that would work well with Xubuntu?
Thx

---

### Post by tgalati4 on 2008-01-15
I've used these in projects with Linux:

[http://www.usglobalsat.com/p-62-bu-353-w.aspx](http://www.usglobalsat.com/p-62-bu-353-w.aspx)

They were about $80 last year, you can probably find them cheaper today.  Waterproof and SirFStar III chipset.  Works well with gpsdrive.  Don't need gpsd, since gpsdrive can query it directly.

Since you have wireless nextworking, try googleearth.  It may rethink your idea of navigation.  Also, car navigation units have come down in price.  For $150 you can get a decent car nav unit with decent maps.

If you want to save money, buy a used copy of Microsoft Streets and Trips (2005-2007 versions) and use the GPS that comes with it.  I've seen them for $20 to $40.

---

### Post by dangoeslinux on 2008-04-08
Hi Matthx,

What did you end up doing? I am in Ontario and have a similar problem....

Take care.

---

### Post by jorgenlidholm on 2008-06-25
Try this: [http://www.tangogps.org/](http://www.tangogps.org/)
I haven't tried it myself.

---

### Post by andcarey on 2008-06-25
I am using a GlobaSat 335 bluetooth data logger.  This can operate as a normal receiver providing NMEA over a bluetooth serial port.  Just add your device to rfconfig (I used [this (http://ubuntuforums.org/showthread.php?p=1497680)]("http://ubuntuforums.org/showthread.php?p=1497680") howto).  I have it working well with gpsdrive.

I have eeeXubuntu installed on a 8GB SDHC card, with gpsdrive running well.  I use the -x startup option which splits the gpsdrive into seperate windows, and the -r and -s to size the map window to fit on the eee PC screen.

I am using gpsdrive version 2.09, but intend to upgrade soon to 2.10pre4.

I live in New Zealand so the openstreetmaps is pretty sparse, so I downloaded bitmap maps from google using [this (http://gtm.tel.uva.es/ztep/maps/dmap.htm)]("http://gtm.tel.uva.es/ztep/maps/dmap.htm") site.  It also creates the entries you need in map_koord.txt for gpsdrive to use them.

Andy.

---

