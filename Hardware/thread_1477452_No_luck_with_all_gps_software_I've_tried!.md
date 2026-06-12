---
title: "No luck with all gps software I've tried!"
date: 2010-05-08
forum: Hardware
---

### Post by Rocket J Squirrel on 2010-05-08
Ubuntu 9.10

I've got an DeLome Earthmate LT-20 gps receiver connected to a usb port on this little netbook. I've got the GPSd daemon (v2.39) running, and xgps shows several satellites and my present location. So at least the hardware seems to be running. The output of the gps can be seen at 127.0.0.1:2947 -- the default port. 

But I can't find a map program that works for me. I want one that uses and displays USA topographical maps from the hard drive so I use them offline. I don't need route finding, just like to see where I am in relation to the countryside.
[U]
GpsDrive[/U] seems to be a popular program. It loads, and it finds the gps, and it correctly locates me here in Bend, Oregon. But I can't zoom or pan the maps.

_TangoGPS_ is another almost-functional program. It downloads map tiles, and it appears to see the gps -- at least it shows me at 3,690 feet above sea level, which is correct for my location -- but there is no "you are here" icon, and auto-center does nothing, so it's not very useful. 

_RoadNav_ sees the receiver if gpsd is killed (can't see the receiver with gpsd running, and if I tell it to use the gpsd daemon, it says: *"gpsd error: Sorry, Roadnav requires at least gpsd 2.21 or higher (you're running 1.2). - disabling GPS.*" I'm actually running gpsd v2.39. So that's not very helpful.) RoadNav's maps are pretty rudimentary -- they show roads only and I'm more interested in the geography near the roads. RoadNav does not understand destinations that are not on the roads in its database: you can type in latitude/longitude coordinates for a destination, but RoadNav doesn't honor them and substitutes its own coordinates. For example, Pine Mountain Observatory in Oregon is located at 43 47.506' N, -120 56.513' W and can be driven to on a dirt road, but when RoadNav sees those coordinates it changes them to 43 47.506' N, -119 03.487' W, a nearby town. 

So . . . is there any hope to find a gps map program that uses topo maps?

---

### Post by flyfishingphil on 2010-05-09
> **Rocket J Squirrel said:**
> Ubuntu 9.10

I've got an DeLome Earthmate LT-20 gps receiver connected to a usb port on this little netbook. I've got the GPSd daemon (v2.39) running, and xgps shows several satellites and my present location. So at least the hardware seems to be running. The output of the gps can be seen at 127.0.0.1:2947 -- the default port. 

But I can't find a map program that works for me. I want one that uses and displays USA topographical maps from the hard drive so I use them offline. I don't need route finding, just like to see where I am in relation to the countryside.
[U]
GpsDrive[/U] seems to be a popular program. It loads, and it finds the gps, and it correctly locates me here in Bend, Oregon. But I can't zoom or pan the maps.

_TangoGPS_ is another almost-functional program. It downloads map tiles, and it appears to see the gps -- at least it shows me at 3,690 feet above sea level, which is correct for my location -- but there is no "you are here" icon, and auto-center does nothing, so it's not very useful. 

_RoadNav_ sees the receiver if gpsd is killed (can't see the receiver with gpsd running, and if I tell it to use the gpsd daemon, it says: *"gpsd error: Sorry, Roadnav requires at least gpsd 2.21 or higher (you're running 1.2). - disabling GPS.*" I'm actually running gpsd v2.39. So that's not very helpful.) RoadNav's maps are pretty rudimentary -- they show roads only and I'm more interested in the geography near the roads. RoadNav does not understand destinations that are not on the roads in its database: you can type in latitude/longitude coordinates for a destination, but RoadNav doesn't honor them and substitutes its own coordinates. For example, Pine Mountain Observatory in Oregon is located at 43 47.506' N, -120 56.513' W and can be driven to on a dirt road, but when RoadNav sees those coordinates it changes them to 43 47.506' N, -119 03.487' W, a nearby town. 

So . . . is there any hope to find a gps map program that uses topo maps?
Check the programming in Ubuntu Software Center. Just Garmin in the search and it will list several different programming packages available, like QLandkarteGT. Take a look thru those and see if you come up with a solution.

I haven't done much yet with my Magellan Explorist so I can't offer any real help but I noticed it recognized it immediately as a 2GB Filesystem and displayed my POI's in their Lat/Lon as text. Haven't tried to enter any maps in the Laptop yet because I have all the maps I need in my Explorist.

---

### Post by Rocket J Squirrel on 2010-05-09
Thanks, guys!

_LinuxAisle_: DeLorme's Topo USA, a Windows program, has all the functionality I could wish for and plenty of detailed topo maps. It is, however, famous for not running under Wine. From what I read, it will run in a Virtual Machine but I just don't feel like buying a copy of Windows XP. Yet. I may have to if nothing comes up for Linux machines. 

_FlyFishingPhil_: Thanks for pointing me to the Ubuntu Software Center. I had previously searched for "gps" there. However, it only gave me QLandKarte when did a "garmin" search -- you said there were several apps that came up for you? I installed QLandKarte and it seems to be very focused on Garmin maps and devices. It does not appear to support USB ports, which is where I have my DeLorme gps receiver connected. 
Added to the list of gps/map programs that don't work here: _Viking_. It only wants to see Garmin or Magellen receivers, does not work with the DeLorme LT-20.

---

### Post by him610 on 2010-05-09
Hello,

> TangoGPS is another almost-functional program.

Actually, TangoGPS is a pretty good program. I have configured it and used it with my GlobalSat BU-353 on several computers using various flavors of Linux.
You may want to read this article...
[http://www.linux.com/archive/feature/152468]("http://www.linux.com/archive/feature/152468") which I found to be very helpful.

Good luck, have fun, and find your own way.

---

### Post by Rocket J Squirrel on 2010-05-09
Thanks, hgh9mrp! I did try TangoGPS and it does look like a very nice program. But even though I've got gpsd running fine, TangoGPS does not show where I am (no "you are here" icon) and auto-center doesn't.

---

### Post by him610 on 2010-05-11
Did you start the gpsd daemon with this...
```
gpsd -n /dev/ttyUSB0
```

---

### Post by Rocket J Squirrel on 2010-05-11
Thanks, hgh9mrp.

TangoGPS does see the receiver but never puts down a "you are here" icon. I've tried gpsd with and without -n and -B, but it makes no difference. There are also screen redraw problems I'm experiencing w/ TangoGPS. Sometimes the + and - buttons vanish until the cursor is waved over them. Autocenter doesn't do anything at all. 

I'm hoping I can get some results with gpsdrive. It seems to be generally working, although it also sort of just doesn't bother to draw a map. 

Of equal importance to me is that there doesn't seem to be any Linux map/gps programs that can read DeLorme TopoUSA topo files, nor any repository of USGS maps that I can find that are readable by any of apps, either. Some very advanced GIS guys have managed to stitch together and tile usgs maps, and they blithely toss about mentions of scripts that can do that but none of the links to scripts they've used are live, and a lot of the information is out of date or too incomplete for a bozo like me to do anything with.

---

### Post by him610 on 2010-05-12
I don't if this has anything to do with it or not, but a week or so ago I read an article about one of the GPS satellites that had been sending the WAAS signal(?) malfunctioned. On another note, I connected my own GPS BU-353 device with gpsd and tangogps both running, and sure enough there was nothing showing where the location of my GPS device was receiving its signal. I could see the locations of "friends" though. In the past I could always see where my GPS unit was on the map.
I take that all back; my signal just popped up - I guess it takes awhile; the autocenter is working as it should. Xgps shows three satellites, the minimum necessary for geolocation; I get weak signals because I am in my basement.
I'll see if I can attach a photo so you can see what it looks like.
[IMG]/home/hughm/Desktop/Screenshot-tangoGPS.png[/IMG]
Looks like the image did not attach. By the way, I use OSM maps; you can see your coordinates by clicking the Trip tab.

---

### Post by him610 on 2010-05-12
> From what I read, it will run in a Virtual Machine but I just don't feel like buying a copy of Windows XP.

If you are interested in running with a virtual machine, you might want to look into Sun VirtualBox.

Good luck

---

### Post by Rocket J Squirrel on 2010-05-12
Thanks hgh9mrp,

I'm not seeing the image.

xgps is routinely reporting five or more satellites, the receiver has a good view of the sky. gpsdrive says it's getting enough for a 3D fix. So signal strength isn't the issue. TangoGPS is having, as I mentioned, a screen drawing problem here, so maybe the missing "here-o-glyph" is part of that. I have not tried driving around to see if TangoGPS keeps track of me, but without getting a fix for the screen thing, it's not very valuable information. 

Don't you need a Windows XP disk to set up a Windows XP environment in any kind of a virtual box?

---

### Post by him610 on 2010-05-13
Don't give up just yet. It took a bit of doing to get everything working on my AAO ZG5 which originally came with Linpus Linux and did not have the capability to recognize the PL-2303 through the USB port.

I remembered something last night that I had forgotten since I had completed my installation so long ago. On the tangoGPS website, located at this link
 [http://www.tangogps.org/gps/articles/7-Installation.html#extended]("http://www.tangogps.org/gps/articles/7-Installation.html#extended") 

The instructions also advise installing packages curl and sqlite3. Have you installed those packages yet?

> Desktop: Debian, Ubuntu, eeePC

Install the .deb package with:

    dpkg -i tangogps-XXX.deb (XXX being the version number)

Additionally you need: gpsd, curl and sqlite3

In case you get an error message "libcurl.so.3 not found" install the curl package and if it still fails then do as root "ln -s /usr/lib/libcurl.so.4 /usr/lib/libcurl.so.3".

Another note on virtual machines: you are right about needing a WinXP disk if you want to use that as a guest OS.

I think I figured how to attach some screenshots.

Keep trying.

---

