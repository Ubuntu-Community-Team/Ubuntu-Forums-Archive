---
title: "(PALM-OS) Sony Clie sync problems"
date: 2004-10-31
forum: Hardware &amp; Laptops
---

### Post by jdusablon on 2004-10-31
According to dmesg, the device has been found by Ubuntu

```

drivers/usb/serial/usb-serial.c: USB Serial support registered for Generic
usbcore: registered new driver usbserial_generic
usbcore: registered new driver usbserial
drivers/usb/serial/usb-serial.c: USB Serial Driver core v2.0
drivers/usb/serial/usb-serial.c: USB Serial support registered for Handspring Visor / Palm OS
drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 3.5drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 5.0usbcore: registered new driver visor
drivers/usb/serial/visor.c: USB HandSpring Visor / Palm OS driver v2.1

```

I can't, however, sync by using Gnome Pilot (by USB cable, obviously.) The settings stage never detects the device.

I've tried using pilot-link, but I'm not sure if this is a front-end or command.

Any insights?

---

### Post by nocturn on 2004-12-23
[QUOTE=jdusablon]According to dmesg, the device has been found by Ubuntu

```

drivers/usb/serial/usb-serial.c: USB Serial support registered for Generic
usbcore: registered new driver usbserial_generic
usbcore: registered new driver usbserial
drivers/usb/serial/usb-serial.c: USB Serial Driver core v2.0
drivers/usb/serial/usb-serial.c: USB Serial support registered for Handspring Visor / Palm OS
drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 3.5drivers/usb/serial/usb-serial.c: USB Serial support registered for Sony Clie 5.0usbcore: registered new driver visor
drivers/usb/serial/visor.c: USB HandSpring Visor / Palm OS driver v2.1

```

I can't, however, sync by using Gnome Pilot (by USB cable, obviously.) The settings stage never detects the device.

I've tried using pilot-link, but I'm not sure if this is a front-end or command.

Any insights?[/QUOTE]


Good news and bad news.
I know what is wrong, and how fix it... in the source code of gnome-pilot.
The patch I created (on Gentoo) is here:
[http://bugs.gentoo.org/show_bug.cgi?id=52550](http://bugs.gentoo.org/show_bug.cgi?id=52550)

---

### Post by nocturn on 2004-12-23
[QUOTE=nocturn]Good news and bad news.
I know what is wrong, and how fix it... in the source code of gnome-pilot.
The patch I created (on Gentoo) is here:
[http://bugs.gentoo.org/show_bug.cgi?id=52550](http://bugs.gentoo.org/show_bug.cgi?id=52550)[/QUOTE]

Better news.
gnome-pilot 2.0.11 and higher have a seperate file to store vendor/product ID in.
If you locate that, enter the info from /var/log messages to it and try again.

---

### Post by nocturn on 2004-12-23
[QUOTE=nocturn]Better news.
gnome-pilot 2.0.11 and higher have a seperate file to store vendor/product ID in.
If you locate that, enter the info from /var/log messages to it and try again.[/QUOTE]
 I think the file is called devices.xml  (found it on google)

---

### Post by Cloudchaser on 2004-12-25
Hello:

I'm having the same problem with my Treo 90. I looked in the devices.xml and my the product ID and vendor ID are already there, but I can't get past the settings setup, I hit the sync button and it just kinda hangs there and does nothing. Output from dmesg:

usb 1-1: new full speed USB device using address 10
visor 1-1:1.0: Handspring Visor / Palm OS converter detected
usb 1-1: Handspring Visor / Palm OS converter now attached to ttyUSB0
usb 1-1: Handspring Visor / Palm OS converter now attached to ttyUSB1
usb 1-1: USB disconnect, address 10
visor ttyUSB0: Handspring Visor / Palm OS converter now disconnected from ttyUSB0
visor ttyUSB1: Handspring Visor / Palm OS converter now disconnected from ttyUSB1
visor 1-1:1.0: device disconnected

usbview shows the device:

visor
Speed: 12Mb/s (full)
USB Version:  1.00
Device Class: 00(>ifc )
Device Subclass: 00
Device Protocol: 00
Maximum Default Endpoint Size: 8
Number of Configurations: 1
Vendor Id: 082d
Product Id: 0200
Revision Number:  1.00

Any help or suggestions would be appreciated. I've already lost all my data once because my Treo's battery died and I hadn't sync'd since I installed Ubuntu. Being able to sync is critical. I don't want to have to go back to Redhat 9 to be able to sync ;(

Thanks for any suggestions.

---

### Post by Cloudchaser on 2004-12-25
Ok after fussing for hours, I got my Handspring Treo 90 to sync with Jpilot!

It uses the visor modules.

I think the major trick was...I had to hit the hotsync button on the Treo first, then open jpilot and hit the "Sync" button within the program. Then it worked just fine!

It also seemed to work in gnome-pilot when I did it that way. Before that it was just hanging.


I also read somewhere to make a symlink:  $ sudo ln -s /dev/ttyUSB1 /dev/pilot

and in another googled post it said to make one also for /visor and /palm so I did both of those, although I'm not sure it was necessary.

Hope this helps!

Update: Well I'm back to square one again. After it sync'd once, I tried to install an appication to the visor via jpilot. I couldn't get that to work. I told jpilot what to install, then tried to sync it. When I hit the sync button within jpilot it keeps opening up the install window but doesn't install the selected apps. I remove the apps from the list and then tried to sync again. No luck there...haven't been able to get it sync'd again.

---

