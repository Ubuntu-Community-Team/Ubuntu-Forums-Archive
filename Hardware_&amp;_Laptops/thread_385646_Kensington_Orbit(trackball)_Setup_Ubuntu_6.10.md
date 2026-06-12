---
title: "Kensington Orbit(trackball) Setup Ubuntu 6.10"
date: 2007-03-15
forum: Hardware &amp; Laptops
---

### Post by eagletistic on 2007-03-15
Very new to Ubuntu and Linux for that matter but also enjoying the experience.

I have a Kensington Orbit mouse that I would like to use in KXMAME.  I was using is somewhat but was choppy.  I have been installing tons of stuff so before I posted I decided to put a fresh image of Ubuntu 6.10.  The trackball mouse is not recognize at all  at this point in time, even after reboots.

I am not part of the pre Gui era so commands are somewhat difficult.  Been just pasteing in terminal when I found tutorials.  I have been unable to see anything on mouse settings for this device.  

Would like to use the trackball feature for games that use that feature.  

Any help would be appreciated

Mouse settings

"InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"

---

### Post by Bernie_K on 2007-07-25
I ran into a similar problem after installing Ubuntu 7.04. The following simple exercise solved the problem on my system:

1. Changed the following lines in the mouse-related InputDevice section of /etc/X11/xorg.conf:

     from
          Option "Device" "/dev/input/mice"
          Option "Protocol" "ExplorerPS/2"
     to
          Option "Device" "/etc/X11/mouse"
          Option "Protocol" "microsoft"

     (shell command: "sudo vi /etc/X11/xorg.conf")

2. Created a soft-link in /etc/X11 relating "mouse" to /dev/ttyS0 (first serial port).

     (shell command: "sudo ln -s /dev/ttyS0 /etc/X11/mouse")

3. Removed the 9-pin RS-232 to PS/2 adapter from the Kensington Orbit mouse,  and plugged the mouse's 9-pin RS-232 directly into my computers first serial port (COM1 in the Windows world, /dev/ttyS0 in the Linux world).

Now, if I could only get audio output from my Soundblaster Live! card...

Good luck!

---

