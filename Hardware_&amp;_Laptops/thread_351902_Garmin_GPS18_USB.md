---
title: "Garmin GPS18 USB"
date: 2007-02-02
forum: Hardware &amp; Laptops
---

### Post by Floppyjoe on 2007-02-02
I have a Garmin GPS18 USB device and do not know how to set it up for use with GpsDrive or SWScanner. Does anyone have any experience setting one of these up in Ubuntu Edgy 6.1?

---

### Post by aseneca on 2007-02-06
Those GPS receivers are known to work with gpsdrive:

Magellan 310, 315, 320
Garmin GPS III
Garmin etrex
GPS 45
Crux II GPS PCMCIA card
Holux GM-200 serial version
Holux GM-200 USB (needs USB to serial support in kernel)
Holux GM-210 USB (needs USB to serial support in kernel)
Garmin eMap
Garmin GPSMAP 295
Garmin GNS 530
Garmin GPS 12MAP
EAGLE Expedition II
DeLorme Earthmate
Rayming TripNav, TN-200
Haicom HI-203E
GM-307 USB-Mouse
Magellan Meridian Gold (works only with NMEA V2.1 GSA setting)
NAVILock GPS Receiver ([http://www.navilock.de](http://www.navilock.de))
Haicom GPS HI204e
Magellan Nav 6500 
BendixKing KLX 100
Motorola i58sr Cellular Phone w/built-in NMEA-compatible 

I do not think it will work.  I googled up your receiver and found this.

GPS 18 FAQ
Q: "Can I use the GPS 18 USB with non-Garmin software?"
A: "Not directly. The GPS 18 USB produces data ONLY in the Garmin proprietary format and so is directly compatible ONLY with Garmin mapping products, or other software products that can decipher Garmin protocol such as FUGAWI software. It cannot be used with non-Garmin software which requires NMEA input, UNLESS ancilliary software such as GpsGate is used."

@http://www.gpscentral.ca/products/garmin/18.htm

I can explain how to set up the connection, or, rather, you can set it up by installing the appropiate packages (gpsd, gps-babel) from repositories (eg. synaptics package manager).
I guess its worth a shot at first-hand information that your receiver truthfully will or will not work.

An alternative is to purchase a new receiver like Holux GM-210 which is currently up for grabs on ebay.
[http://search.ebay.com/Holux-GM-210-USB_W0QQfrppZ50QQfsopZ1QQmaxrecordsreturnedZ300QQsatitleZHoluxQ20GMQ2d210Q20USB](http://search.ebay.com/Holux-GM-210-USB_W0QQfrppZ50QQfsopZ1QQmaxrecordsreturnedZ300QQsatitleZHoluxQ20GMQ2d210Q20USB)

I use this receiver.  I have had a few issues with it since I upgraded to edgy, but it works!

---

### Post by Floppyjoe on 2007-02-07
I installed gpsd and ran that before using GPSDrive and I found that it does work in Nmea mode with GPSDrive. Thank you for your reply.

---

### Post by Floppyjoe on 2007-02-09
I can not seem to get it to work with SWScanner. My wireless card on my laptop is not supported by Kismet. Is there another way to go wardriving with this GPS unit?

---

