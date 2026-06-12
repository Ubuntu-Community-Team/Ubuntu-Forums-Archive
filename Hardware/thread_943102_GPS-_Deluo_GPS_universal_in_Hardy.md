---
title: "GPS- Deluo GPS universal in Hardy"
date: 2008-10-09
forum: Hardware
---

### Post by casaduana on 2008-10-09
I have a Acer 3050 with 2GB that I am trying with no success to use with gpsdrive. The program installs correctly but no GPS functions. The bottom message by the GPS meter says, "no GPS!" I have done a week of research and I think I have installed all the dependencies, including gpsd, and gpsd-client, but the GPS receiver is still _not[U]_[/U] being seen by gpsdrive. I have checked in Terminal gpsd,and it say no socket controler or device detected. I know the little Deluo gps is NMEA 1083 compliant. Does anyone have an idea as to how to fix? 

I have used the same combo of Acer laptop and Deluo Gps usb universal with my former Vista OS before I erased in favor of the much friendlier Ubuntu 8.041. The combo worked fine; This is my first puzzler in Ubuntu that I didn't find somewhere that someone else solved. Please help, much appreciated it will be!:confused:

---

### Post by gnottage on 2008-10-23
The [gpsd website]("http://gpsd.berlios.de/hardware.html") has a hardware compatibility list. gpsd talks to the GPS device and then allows gpsdrive to use the GPS data. The first step is to make sure that gpsd is working with your setup, then everything else will follow. Good luck

---

