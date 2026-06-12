---
title: "Accessing USB GPS device"
date: 2009-07-14
forum: Hardware
---

### Post by chriskot on 2009-07-14
I have just installed Ubuntu 9.0.4, it's my first ubuntu installation.

I want to be able to plug in my Garmin GPSmap 76Cx.

I have run dpkg-reconfigure gpsd and set it to start on boot and use auto.
The daemon seems to fire up just fine.

However, the user.log shows:
Jul 13 12:29:55 lapper gpsd[11182]: gpsd: GPS device /dev/ttyUSB0 nonexistent or can't be read

Indeed there is no ttyUSB0 device. I copied /lib/udev/rules.d/40-gpsd.rules to /etc/udev/rules.d which from what I can gather is supposed to create /dev/ttyUSB0 when the device gets plugged in and remove it when it gets unplugged. When it gets plugged in I can see in /var/log/messages that the kernel seems to recognize it:

Jul 13 15:51:48 lapper kernel: [ 1896.348062] usb 3-1: new full speed USB device using ohci_hcd and address 3
Jul 13 15:51:49 lapper kernel: [ 1896.550527] usb 3-1: configuration #1 chosen from 1 choice

But, I never get the ttyUSB0 device made.

My understanding is that when the device gets plugged in /lib/udev/gpsd.hotplug.wrapper gets run which runs /lib/udev/gpsd.hotplug. These should create the /dev/ttyUSB0 device and then send the device name to the gpsd daemon's control socket to tell the daemon what device name to use to access the GPS. It does this by passing the name to the gpsd daemon through a socket. It seems gpsd.hotplug expects that socket to be at /var/run/gpsd.sock so I set an option of -F /var/run/gpsd.sock when I run dpkg-reconfigure. I see the socket exists and that gspd is running.

It just seems I can't get udev to create the /dev/ttyUSB0 device.

I used lsusb and can see that the device does report the expected vendor ID and product ID in 40-gpsd.rules:
# Garmin International GPSmap, various models (tested with Garmin GPS 18 USB)
SYSFS{idVendor}=="091e", SYSFS{idProduct}=="0003", SYMLINK="gps%n", RUN+="/lib/udev/gpsd.hotplug.wrapper"

$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 091e:0003 Garmin International GPSmap (various models)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)


So, it should be running the script.

What am I missing ?

Thanks

Chriskot

---

### Post by gerkin on 2009-07-14
Hi chriskot

I found that on my eTrex that GPSD wouldn't see the device on "Garmin" output (for live tracking) I had to set the device to "NMEA" output 

there is quite alot of GPSD & GPSBabel stuff you can google but here are a couple of links  

GPSD: (I use this for live tracking)
[http://gpsd.berlios.de/](http://gpsd.berlios.de/)

GPSBabel: (I use this to upload/download tracks/waypoints/routes
Heres the script I use:

[http://ubuntuforums.org/showthread.php?t=875478](http://ubuntuforums.org/showthread.php?t=875478)

cheers........gerkin

---

### Post by chriskot on 2009-07-14
Thanks for those pointers, I will definitely use them once I get over thi hurdle.

But, I think I am not quite to protocol worries yet. I think this is strictly a udev issue for me. The gpsd daemon needs for a /dev to get created before it can try and talk to the device and that doesn't seem to be happening.

The system does recognize the product ID and vendor ID, lsusb shows that, which is in the 40-gpsd.rules list which should be enough to get the gpsd.hotplug.wrapper script started to get a  /dev entry created.

I have switched the GPS to use NMEA though and gpsd still can't seem to find the device.

I was hoping to avoid having to do this, but I may need to add some debug statements to some of the scripts to see how far I am getting.

Thanks

Chriskot

---

### Post by chriskot on 2009-07-15
I put udevd into debug mode and also added an echo statement in gpsd.hotplug.wrapper to print a message to /tmp/gpsd.out. I turned the gps on and off and I never got the file generated so the wrapper script wasn't getting called.

I noticed in udevd output this:

[20143] event_fork: seq 1750 forked, pid [22591], 'add' 'usb_endpoint', 1 seconds old

I also noticed that in udev/rules.d/40-gpsd.rules it has this line:

SUBSYSTEM!="tty", GOTO="gpsd_rules_end"

SInce it didn't seem to pass tty as a parameter I commented this line out and then turned on the device and I got the /tmp/gpsd.out file. I also looked in /dev and found some /dev/gps* files. I turned it off and they went away.

In looking at the comments about the various GPS devices a lot of them mention "Serial" so I assume this file is really only for serial connection GPS. But, mine is through USB. So, I changed the gps rule to set the SUBSYSTEM comparison to usb_endpoint and removed all of the other devices except the Garmin device.

Now when I turn on the GPS I get /dev/gps* files like this:
# ls -l /dev/gps*
lrwxrwxrwx 1 root root 15 2009-07-14 15:10 /dev/gps00 -> usbdev3.14_ep00
lrwxrwxrwx 1 root root 15 2009-07-14 15:10 /dev/gps03 -> usbdev3.14_ep03
lrwxrwxrwx 1 root root 15 2009-07-14 15:10 /dev/gps1 -> bus/usb/003/014
lrwxrwxrwx 1 root root 15 2009-07-14 15:10 /dev/gps81 -> usbdev3.14_ep81
lrwxrwxrwx 1 root root 15 2009-07-14 15:10 /dev/gps82 -> usbdev3.14_ep82

and when I turn off the GPS they go away.

So, I reran dpkg-reconfigure gpsd and set the device to /dev/gps1. Unfortunately, gpsd is still complaining abiout no device:

Jul 14 15:21:02 lapper gpsd[22515]: gpsd: device open failed: No such device or address - retrying read-only 
Jul 14 15:21:02 lapper gpsd[22515]: gpsd: read-only device open failed: No such device or address 
Jul 14 15:21:02 lapper gpsd[22515]: gpsd: GPS device /dev/gps1 nonexistent or can't be read 

But there is a /dev/gps1 if I do an ls  . So, I tried some of the other /dev/gps* symlinks to no avail.

Seems I have udev configured OK now since I am getting the /dev/gps* files. Even though in the last few iterations I don't seem to get the gps1 devices:

# ls -l /dev/gps*
lrwxrwxrwx 1 root root 15 2009-07-14 15:20 /dev/gps00 -> usbdev3.15_ep00
lrwxrwxrwx 1 root root 15 2009-07-14 15:20 /dev/gps03 -> usbdev3.15_ep03
lrwxrwxrwx 1 root root 15 2009-07-14 15:20 /dev/gps81 -> usbdev3.15_ep81
lrwxrwxrwx 1 root root 15 2009-07-14 15:20 /dev/gps82 -> usbdev3.15_ep82

which seems kind of weird. I don't really know what the difference is between the various gps* but I assumed since gps1 was different then the others that is the one I should use.

Anyway, I guess the next step is to put gpsd into debug mode and see if it can tell me anything more about what the issue might be.

Thanks
Chriskot

---

### Post by FAo10rK on 2011-10-23
Try to remove brltty.

I've this problem in my new 11.10 

dmesg said :
```
[ 1440.276086] usb 3-1: new full speed USB device number 8 using ohci_hcd
[ 1440.448688] cp210x 3-1:1.0: cp210x converter detected
[ 1440.588092] usb 3-1: reset full speed USB device number 8 using ohci_hcd
[ 1440.750824] usb 3-1: cp210x converter now attached to ttyUSB0
[ 1443.892226] usb 3-1: usbfs: interface 0 claimed by cp210x while 'brltty' sets config #1
[ 1443.893774] cp210x ttyUSB0: cp210x converter now disconnected from ttyUSB0
[ 1443.893807] cp210x 3-1:1.0: device disconnected

```

I remove brltty and /dev/ttyUSB was alive and was ready with mtkbabel.

```
sudo apt-get remove brltty
```

I use this with My Holux M241. It worked fine in my 11.04, but not on the 11.10. brltty was the problem, remove it was the solution.

---

