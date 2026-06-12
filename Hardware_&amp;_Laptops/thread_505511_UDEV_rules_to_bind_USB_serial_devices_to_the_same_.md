---
title: "UDEV rules to bind USB serial devices to the same path"
date: 2007-07-20
forum: Hardware &amp; Laptops
---

### Post by hotspoons on 2007-07-20
Here's what is happening. I have a somewhat unique set up (in-car computer w/7" VGA touchscreen, running Feisty), and I have 2 USB serial devices always hooked up to the car. One is a garmin GPS receiver, and one is a future data systems USB to serial device ([Openport calbe for data logging and ECU flashing in Subaru's]("http://www.tactrix.com/product_info.php?products_id=31&osCsid=135512009ae2c60fb78bdd0fc7bfcec5")). I have GPSD and roadnav for GPS, and [Enginuity]("http://www.enginuity.org/") for data logging.

The problem is that every time I boot the car, the devices will randomly switch spots at /dev/ttyUSB0 and /dev/ttyUSB1. This makes it a pain to launch the ECU logger, because I do not know (without opening a terminal, which isn't practical with a touchscreen and no keyboard) which device is assigned to which node.

I had to use UDEV rules for the touchscreen so it shows up at the same symlink so I could use it reliably with X, but they came with the EVTOUCH Xorg driver, so I didn't have to customize them, and I am at a bit of a loss how to write my own. I do know that making symlinks for the devices in the rules won't work because of the way GPSD and Enginuity enumerate serial devices, so they will have to show up at default tty locations. Any help is appreciated. Thanks!

---

### Post by hotspoons on 2007-07-27
?Anybody? Thanks,

-Rich

---

### Post by detarmstrong on 2007-09-14
I wish I could help. Unfortunately I can't even get as far as you ...

When I plug my garmin gps 18 USB in dmesg says:

usb 3-2: Garmin GPS usb/tty converter now attached to ttyUSB0

Good.
But when I run:

stty -F /dev/ttyUSB0  && cat < /dev/ttyUSB0

expecting to see output I see nothing :(

Did you experience a similar problem? Thanks for any help.

---

### Post by psusi on 2007-09-14
Have you read the udev man page?

---

