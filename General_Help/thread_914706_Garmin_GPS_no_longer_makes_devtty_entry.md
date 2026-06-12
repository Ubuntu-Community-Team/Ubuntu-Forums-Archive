---
title: "Garmin GPS no longer makes /dev/tty entry"
date: 2008-09-09
forum: General Help
---

### Post by SSamiK on 2008-09-09
When I connected my Garmin GPS, it used to make a entry to /dev/ttyUSB0, but since a while ago not quite sure when, it dosen't do this anymore. As a result I can't use my mapping software anymore.

It still shows in dmesg and lsusb. 

dmesg sayssomething like this: 
```

3-1 new full speed USB device using uhci_hcd and adress 2
3-1 configuration #1 chosen from 1 choice

```


Anyone knows what to do to get it working again? Sorry for little info, I'm currently at school using a comp running WinXP...:mad:

---

### Post by inselaffe on 2008-09-09
Which model is it? On at most Garmins there is an "interface" option to change the connection type, which may affect how it is seen by the computer. Does your model normally also show as a mass storage device (removable disk)? If so is that still appearing?

---

### Post by SSamiK on 2008-10-18
It's a Garmin Astro 220, and It's not recognized right no matter witch mode I've got it in. But when I connect it to my comp running Debian it connects correctly, so there is something going on in Ubuntu. (it also works correctly under Windows...) 

dmesg in Debian:
```

[61301.947012] garmin_gps 1-3:1.0: Garmin GPS usb/tty converter detected
[61301.947096] usb 1-3: Garmin GPS usb/tty converter now attached to ttyUSB0
[61301.947238] usb 1-3: New USB device found, idVendor=091e, idProduct=0003
[61301.947242] usb 1-3: New USB device strings: Mfr=0, Product=0, SerialNumber=0

```

This is what I used to see in Ubuntu, so can anybody tell me what have happened? And if possible, how to fix it... :)

---

### Post by SSamiK on 2008-10-21
Nobody in the same boat? I'm suspecting this to be related to a kernel update, so maybe there is no easy fix...

---

### Post by SSamiK on 2008-10-25
Just reporting back with latest news... Updating to Ibex haven't solved my problems, so it seems that leaving Ubuntu behind and rather go for debian seems the most likely solution.

---

### Post by SSamiK on 2008-10-27
After digging around a bit more, the solution came crawling towards me.

```
sudo nano /etc/modprobe.d/blacklist
``` 

Put a # in front of (or remove) the entry garmin_gps
Save and exit

```
sudo modprobe garmin_gps
```
To load the correct garmin driver to use with Mapsource. 
Now, to get Mapsource to identify the device all I had to do was
```
ln -s /dev/ttyUSB0 ~/.wine/dosdevices/com1
```

---

### Post by helmut_hed on 2008-11-03
I just went through some of these issues myself and decided to document the results.

The reason the "garmin_gps" module was blacklisted is that it's been fairly unreliable, according to various sources on the net.  This module basically pretends to be a serial interface to a Garmin device connected via usb.

Depending on what applications you use to access your Garmin, you should be able to supply the name "usb:" instead of /dev/ttyUSB0 (or whatever) and the software will search the USB busses for the right device.  If the garmin_gps or usbserial modules are already running the device this will not work.

I was able to transfer my waypoints off my Garmin eTrex Vista CX with this command line:

sudo gpsbabel -i garmin -o kml usb: /tmp/wp.kml

That produces the kml format required by Google Maps.

---

### Post by kript on 2008-12-04
> **helmut_hed said:**
> 

Depending on what applications you use to access your Garmin, you should be able to supply the name "usb:" instead of /dev/ttyUSB0 (or whatever) and the software will search the USB busses for the right device.  If the garmin_gps or usbserial modules are already running the device this will not work.

I was able to transfer my waypoints off my Garmin eTrex Vista CX with this command line:

sudo gpsbabel -i garmin -o kml usb: /tmp/wp.kml


Thanks for this - it was very helpful.. Have you managed to get gpsd or any of the GPS applications such as GPSDrive or Viking working in the same way?  Any hints appreciated!

---

### Post by mathfeel on 2008-12-06
> **helmut_hed said:**
> I just went through some of these issues myself and decided to document the results.

The reason the "garmin_gps" module was blacklisted is that it's been fairly unreliable, according to various sources on the net.  This module basically pretends to be a serial interface to a Garmin device connected via usb.

Depending on what applications you use to access your Garmin, you should be able to supply the name "usb:" instead of /dev/ttyUSB0 (or whatever) and the software will search the USB busses for the right device.  If the garmin_gps or usbserial modules are already running the device this will not work.

I was able to transfer my waypoints off my Garmin eTrex Vista CX with this command line:

sudo gpsbabel -i garmin -o kml usb: /tmp/wp.kml

That produces the kml format required by Google Maps.

gpsd does not work with the usb:, I don't think.

Anyway, getting ttyUSB0 back with garmin_gps doesn't work either:
```
~$ sudo modprobe garmin_gps
~$ sudo gpsd -n -N -D 2 /dev/ttyUSB0 
gpsd: launching (Version 2.37)
gpsd: listening on port gpsd
gpsd: successfully connected to the DBUS system bus
gpsd: running with effective group ID 0
gpsd: running with effective user ID 0
gpsd: opening GPS data source at '/dev/ttyUSB0'
gpsd: speed 9600, 8N1
gpsd: Can't open /proc/bus/usb/devices
gpsd: gpsd_activate(1): opened GPS (5)
```

There is no /proc/bus/usb/devices.

The correct Baud rate should be 4800 (say so on my 60csx's interface setting). I tried to set it with
```
stty -F /dev/ttyUSB0 ispeed 4800 ospeed 4800
``` and it just freezed. Also, I cannot kill the above gpsd with kill -9. Have to reboot to get the ttyUSB0 device unfreeze.

---

### Post by kitplummer on 2008-12-21
I can confirm the same behavior (with Interpid).  I was able to communicate with my 301 using the garmin_gps driver and gpsman.  But, that app is so ugly and didn't get me what I need anyway, which is just the current coordinates.  gpsbabel will probably do this for me - but, gpsd sure would be nice so I can get it from Ruby.

If anyone figures this out...I'd surely be appreciative.

---

### Post by BigBananaMan on 2009-01-05
Well I seem to be having the same exact problem as the original post.  I try to run gpsd and...
```
bananaman@curious-george:~$ sudo gpsd -N -D 6 usb:
gpsd: launching (Version 2.37)
gpsd: listening on port gpsd
gpsd: shmat(0,0,0) succeeded
gpsd: shmat(0,0,0) succeeded
gpsd: shmat(0,0,0) succeeded
gpsd: shmat(0,0,0) succeeded
gpsd: successfully connected to the DBUS system bus
gpsd: running with effective group ID 0
gpsd: running with effective user ID 0
gpsd: opening GPS data source at 'usb:'
gpsd: device open failed: No such file or directory - retrying read-only
gpsd: read-only device open failed: No such file or directory
gpsd: GPS device usb: nonexistent or can't be read

```
As you can see I tried using "usb:" but it also failed like "/dev/ttyUSB0" did.  dmesg and lsusb match what SSamiK had except that mine never worked from the start.  My GPS is a Garmin GPSmap 60CSx.  The GPS is set to NMEA in/out at 4800 baud and displaying that it is "connected".  After trying what SSamiK said in his last post I got...
```
bananaman@curious-george:~$ sudo gpsd -N -D 6 /dev/ttyUSB0
[sudo] password for bananaman: 
gpsd: launching (Version 2.37)
gpsd: listening on port gpsd
gpsd: shmat(0,0,0) succeeded
gpsd: shmat(0,0,0) succeeded
gpsd: shmat(0,0,0) succeeded
gpsd: shmat(0,0,0) succeeded
gpsd: successfully connected to the DBUS system bus
gpsd: running with effective group ID 0
gpsd: running with effective user ID 0
gpsd: opening GPS data source at '/dev/ttyUSB0'
gpsd: speed 9600, 8N1
gpsd: => GPS: $PASHQ,RID*28\x0d

gpsd: Navcom: command dump: 0299661c0800040200001203
gpsd: => GPS: 0299661c0800040200001203
gpsd: Navcom: sent command 0x1c (Test Support Block)
gpsd: Navcom: command 0x1c mode = 02, length = 0
gpsd: Navcom: command dump: 029966200e000001ae02000071000000f203
gpsd: => GPS: 029966200e000001ae02000071000000f203
gpsd: Navcom: sent command 0x20 (Data Request) - data block id = ae at rate 00
gpsd: Navcom: command dump: 029966200e00000186020a0071000000d003
gpsd: => GPS: 029966200e00000186020a0071000000d003
gpsd: Navcom: sent command 0x20 (Data Request) - data block id = 86 at rate 0a
gpsd: Can't open /proc/bus/usb/devices
gpsd: no probe matched...
gpsd: gpsd_activate(0): opened GPS (5)
```
and when I ran xgps in a second window to test it, the following was added in the first terminal:
```
gpsd: client 127.0.0.1 (0) connect on fd 6
gpsd: checking client(0)
gpsd: <= client(0): w+x
gpsd: client(0): assigning channel...
gpsd: User r8-)8-)8-)equires 2, channel type is -1
gpsd: client(0): channel 5 already active.
gpsd: client(0): channel 5 already active.
gpsd: => client(0): GPSD,W=1,X=1231204502.736271
```
It could not open "devices" under /proc/bus/usb because it was not there so I tried to mount it with...
```
sudo mount -t usbfs usbfs /proc/bus/usb
```
and running gpsd again.  This time it returned nothing when I ran gpsd with -N -D 6.  When I try running Gpsdrive it says I have no GPS and xgps just freezes when I try to run it.  This seems to be a long series of problems and not just one.  I've probably fixed it 4 or 5 times from solutions and tutorials in threads spanning across several forums only to find another problem waiting in line.

kitplummer, have you tried to comment out the blacklist and have you had similar results to mine?  Anyone else?
I've been working on this for two days straight and I think my eyes are bleeding now so I'm going to take a really long sleep.

---

### Post by BigBananaMan on 2009-01-10
I haven't made any breakthroughs but I have discovered something kind of obvious.  gpsd works on port 2947 so what happens if you telnet to that?  Well you can telnet to it and if you look in the man page for gpsd you can see all the commands it uses which can be entered through telnet.  
```
bananaman@curious-george:~$ telnet localhost 2947
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
a
GPSD,A=?
b
GPSD,B=9600 8 N 1
x
GPSD,X=1231447275.914733
y
GPSD,Y=?
z
GPSD,Z=1
f
GPSD,F=/dev/ttyUSB0


```
I punched in a few letters and it appears that the GPS really is connected to gpsd and the problem lies somewhere between gpsd and the applications.  Well that's one step closer at least, any ideas where to take this next?  So far I've had no luck with qlandkarte, Gpsdrive, xgps, and kismet.

---

### Post by JohnnySteel on 2009-02-13
Hi there, I would like to buy a outdoor device like garmin extrex H, vista HCX ord legend hcx.

For geocaching, realtime mapping and wardriving :)

Befor buying I want to know if one of these devices work properly with gpsd (ubuntu 8.10 64bit) .

I found a small tutorial...

```
1. edit /etc/modprobe.d/blacklist and add the lines

# stop garmin_gps serial from loading for USB garmin devices

# blacklist garmin_gps

To allow the USB devices to be read and written by a non-privileged user, create a named /etc/udev/rules.d/51-garmin.rules with the following contents:

SYSFS{idVendor}=="091e", SYSFS{idProduct}=="0003", MODE="666" 

source: [http://www.gpsbabel.org/os/Linux_Hotplug.html](http://www.gpsbabel.org/os/Linux_Hotplug.html)

2. When the file /proc/bus/usb/devices is NOT present, it may be because the usbfs is not mounted. One way is to try mounting it, (which may fail if there is no directory /proc/bus/usb) Code:

sudo mount -t usbfs usbfs /proc/bus/usb 

Source: [http://ubuntuforums.org/showthread.php?t=670878](http://ubuntuforums.org/showthread.php?t=670878)

start  "gpsd -nND2 /dev/ttyUSB0"


3. add  

none /proc/bus/usb usbfs deflautls 0 0

to /etc/fstab
```


I am not sure if this works...please let me know.


And whats the output of
```

cat /dev/ttyUSB0

```
?


Cheers

---

### Post by BigBananaMan on 2009-02-26
Hey JohnnySteel, I checked out your guide.  I recently had to reinstall the OS because of hardware failure and after performing every step in your guide I realized I essentially just did everything I did before.  I also got the same results.  Everything worked out fine until I tested it.
```
bananaman@curious-george-2:~$ cat /dev/ttyUSB0
cat: /dev/ttyUSB0: No such file or directory

```
I then telneted into localhost on port 2947 and got the same result as before.
I'll keep searching and messing around with it when I get the time but I'm stumped for now.  Although the Garmin GPSmap60CSx is a great little GPS and one of my best upgrades ever. (previously I used outdated, water damaged maps and a lensatic compass. I kid you not.) Until proven otherwise I have to say it's not Linux compatible.  Other people have had luck with other Garmins so you might want to ask some of the people that have had success.  [Click here for a list of GPSs that the gpsd makers have tested.]("http://gpsd.berlios.de/hardware.html") I suggest you get one that can store data on a micro SD card otherwise you won't be installing any state or large custom maps.

---

### Post by gmaccrim on 2010-01-25
I couldn't get Viking or Qlandkarte to recognize my Garmin GPS  on Ubuntu 9.10 until I ran the programs with sudo, and both then worked.   It appears to be a permissions issue on the device files and I'm still looking for a nice fix to get around having to run this stuff as superuser.

Update:  Aha!  I editted my user id's properties and gave it all privileges, logged out, logged back in and Viking was able to download from my GPSmap60 without sudo.  I'm not sure which privilege did the trick as there was nothing specific for USB.

---

