---
title: "touchscreen calibration"
date: 2007-05-18
forum: Hardware &amp; Laptops
---

### Post by labattazza on 2007-05-18
I've got an 8" touchscreen , an SGDQ "TM-868" that is clone of Innovatek's.

Ubuntu automatically rcognises the device, but.... the  X-Y are inverted and in wrong direction!!! 
Before connecting the monitor i downloaded linux drivers from manufacture's site, but then when i plugged i saw that touching the screen the arrow moved. The problem is that if I move "from  left to right" arrow goes "bottom to up", and if i move "up to bottom" it goes "left to right".
So i decided to install drivers but for some reason i can't compile... So, do you know if there is any possibility to get it working properly? And even if i can make arrow move in the correct directions, how can i calibrate without using those drivers? In apt i didn't find anything useful...
I'd like to understand what driver is sued now, inorder maybe to change a config file..
thanks a lot!

---

### Post by kev000 on 2007-09-08
Try this:
[http://www.nextabyte.com/support/touchscreen/Touchscreen_HowTo.pdf](http://www.nextabyte.com/support/touchscreen/Touchscreen_HowTo.pdf)

or the automatic script:
[http://www.nextabyte.com/nanonymous/LinuxICE/touch.sh](http://www.nextabyte.com/nanonymous/LinuxICE/touch.sh)

-downloads and installs the driver
-downloads and installs the udev rules
-downloads and installs the calibrator

then run the calibrator:
#sudo calibrator

restart X

this is a little late, but I hope it helps... someone

---

### Post by accord on 2007-12-29
Hi, it seems like a real nice tool!

I'm trying to use ubuntu on Asus R2H, which is an UMPC with Touchscreen. I'm also having problems with touchscreen calibration. I've downloaded the calibrator binary and the udev files. When I execute the calibrator program, the calibration screen comes up and a target is blinking in the upper left corner. However, when I click it (with the touchscreen)there is no response. It continues flashing in upper left while the red bar below runs to the end, and the program exits. The touchscreen was not calibrated.

Any ideas?

---

### Post by wellilein on 2008-01-06
@accord: 
I had the same problems here. Running "sudo calibrator" showed up the screen, but touching did not work.

The following helped for me:
1.: cat /proc/bus/input/devices
This prints out a list of devices. One of them is your touch screen.

2.: sudo calibrator /dev/input/event%
Where % is the number of the event for your touchscreen, specified in the "Handler" line of step 1.
With this command line I could successfully touch the blinking points.

---

