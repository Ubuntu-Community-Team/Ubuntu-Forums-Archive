---
title: "'mknod /dev/gps_fake c 4 64; gpspipe -r -s /dev/gps_fake' wont work"
date: 2008-11-27
forum: General Help
---

### Post by gizmo_the_greater on 2008-11-27
whats the matter with that?

i've tried:

```
sudo mknod /dev/gps_fake c 4 64
sudo gpspipe -r -s /dev/gps_fake
```

Output:
```
gpspipe: error reading serial port settings

```
My permissions of device are set to:
```
crw-rw---- 1 root dialout 4, 64 2008-11-27 12:09 /dev/gps_fake
```

gpsd is running and gpspipe -r output works... 
i'va also fetched setserial and used once on /dev/gps_fake ...

**what am i doing wrong?** i dont find any helpful hints in the net ...

Ive also tried to :
```

setserial -v -z /dev/gps_fake divisor 24
```

but i've never used setserial before

---

### Post by gizmo_the_greater on 2008-11-27
Please help me, i'm still not able to generate a fake device

---

### Post by gizmo_the_greater on 2008-11-27
Please give me any advice or hint why i dont get an answer! am i asking stupid questions or what it is it about?

---

### Post by thomas228 on 2008-11-27
> **gizmo_the_greater said:**
> Please give me any advice or hint why i dont get an answer! am i asking stupid questions or what it is it about?
Hi 
Although I'm a relative newbie I do know that there is no such thing as a stupid question. Be patient and you'll get some help.
Remember that things are quiet during holidays (Thanksgiving here)

Sorry that I can't help you as my knowledge of the program you are trying to run is nill and without a link to the program it is difficult to come up with any suggestions.:(
Good luck
Tom

---

### Post by gizmo_the_greater on 2008-11-28
gpspipe is part of the default gpsd-package

its used when your gpsd-daemon uses your gps-device (serial/usb/bluetooth) and any other program is not capable of using gpsd running on localhost:2947 

instead gpspipe should (not in my case) attach to a selfcreated serial device (mknod) and emulate a physical gps-device (producing standard gps-output [called nmea i thing] output)

in my case i need that becase i need gps-data vor openGTS - a GPS-TrackingServer wich is using the lightweight-protocol dmtp for online position-transmission ... the opendmtp-client is not cappable of talking to gpsd (or that bad documented that i was not able to find the solution)

---

### Post by thomas228 on 2008-11-29
> **gizmo_the_greater said:**
> gpspipe is part of the default gpsd-package

its used when your gpsd-daemon uses your gps-device (serial/usb/bluetooth) and any other program is not capable of using gpsd running on localhost:2947 

instead gpspipe should (not in my case) attach to a selfcreated serial device (mknod) and emulate a physical gps-device (producing standard gps-output [called nmea i thing] output)

in my case i need that becase i need gps-data vor openGTS - a GPS-TrackingServer wich is using the lightweight-protocol dmtp for online position-transmission ... the opendmtp-client is not cappable of talking to gpsd (or that bad documented that i was not able to find the solution)


Hi again
maybe the following will help define the background of your problem a little more
[http://gpsd.berlios.de/]("http://gpsd.berlios.de/")
is the website that can start to shed light on your problem for me however since I don't have a high speed internet connection it might be some time before I can help you with your problem

The website indicates that one can download gpsd packages in ubuntu but my wifi time is limited to vists to a local Hardy's so again it might be awhile
Sorry but maybe someone else who's interested in quote “Applications that presently use gpsd include pyGPS, Kismet, GPSdrive, gpeGPS, position, roadmap, roadnav, navit, viking, and gaia.” may be able to shed some more light on your problem. The above link will provide further links for the quoted applications.

Good luck
Tom

---

