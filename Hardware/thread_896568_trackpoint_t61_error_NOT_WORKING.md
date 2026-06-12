---
title: "trackpoint t61 error NOT WORKING"
date: 2008-08-21
forum: Hardware
---

### Post by erpan on 2008-08-21
I have just installed ubuntu 8.04 and updated thrue it to the latest kernel.

Now to the problem cannot get middle key in trackpoint to work. 

Have tried do disable it in the bios then  start ubuntu  , restart and enabling trackpoint in the bios but it will not work. Have also tried this site:
[http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint)

Without success modding x11-conf file. as follows:

Section "InputDevice"
	Identifier	"Trackpoint"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
	Option		"EmulateWheel"          "true"
	Option		"EmulateWheelButton"    "2"
EndSection

Nothing happends at all with this mod. i also tried to change from "true" to "on". 

So how can a newbie like me make the middlebutton for scrolling to work? 

Next problem is that i installed the server kernel to have 4gb of ram but then wifi and soundcard disappeared. Strange.
How do i the easiest way to install this 2 , can i download driverpackages ? if so where?


***edit 

As i was looking around in linux i found this 
 Each configuration option enables a list of files. i tried terminal to makefile i was in the right folder but newbi as i am how do i install ibmmouse?

obj-$(CONFIG_MOUSE_AMIGA)	+= amimouse.o
obj-$(CONFIG_MOUSE_APPLETOUCH)	+= appletouch.o
obj-$(CONFIG_MOUSE_ATARI)	+= atarimouse.o
obj-$(CONFIG_MOUSE_RISCPC)	+= rpcmouse.o
obj-$(CONFIG_MOUSE_INPORT)	+= inport.o
obj-$(CONFIG_MOUSE_LOGIBM)	+= logibm.o
obj-$(CONFIG_MOUSE_PC110PAD)	+= pc110pad.o
obj-$(CONFIG_MOUSE_PS2)		+= psmouse.o
obj-$(CONFIG_MOUSE_SERIAL)	+= sermouse.o
obj-$(CONFIG_MOUSE_HIL)		+= hil_ptr.o
obj-$(CONFIG_MOUSE_VSXXXAA)	+= vsxxxaa.o
obj-$(CONFIG_MOUSE_GPIO)	+= gpio_mouse.o

---

