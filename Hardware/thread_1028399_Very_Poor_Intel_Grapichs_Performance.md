---
title: "Very Poor Intel Grapichs Performance?"
date: 2009-01-02
forum: Hardware
---

### Post by Dolfhin01 on 2009-01-02
Hi Guys,

GLXgears gives me around 200 FPS, scrolling in Firefox stops music from playing and freezes the system. Overall the GUI feel ¨slow¨.

(possible) useful info from glxinfo :

¨[I]name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2[/I]
¨

¨[I]OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.2
OpenGL shading language version string: 1.10[/I]
¨

I have also found : [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/252094](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/252094)

But no workaround seems to be available?

My Xorg.Conf :

¨[I]Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2960 1082
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection[/I]¨


Any one else encountering this problem? If so how do you cope, any fix available?

Thanks in advance!

---

### Post by igknighted on 2009-01-02
You are not making use of the Mesa 3d libraries, you are using the software rasterizer (very slow).  I notice you are probably using dual screens... which intel card do you have?  Some do not support dual monitors at high res...

Run 'lspci | grep VGA' if unsure.

---

### Post by Dolfhin01 on 2009-01-02
I´m using a GM945. 

I´m aware that I can´t use compiz in dual monitor configuration with 2 monitors but surely I should be able to browse the internet and listen to music with this card?

Output from : lspci | grep VGA
¨> ¨

But this should work ;)

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

---

### Post by salemboot on 2009-03-04
Interesting nobody has any more insight into this problem.

I just got a new LCD to play xbox and laptop on.  No kidding it's nice they now include HDMI inputs.

The behavior I've noticed is that when cloning the display, *Ctrl/Alt/BackSpace*, or setting up an extended display.  The *glxgears* frame-rates reduce exponentially, 800fps - 190fps.  That's approximately 23% of my graphics potential out the door as to say.

What I noticed was that adding the Option *"AutoAddDevices" = "False"*
Allows me to correctly configure the proper resolutions for the displays.

VGA or the external LCD is a 1680 x 1050  display.
Laptop is a 1280x800 display.  I can use *xrandr* scripts to enable and disable each display.

It seems like it's a bug in the agpgart stuff.  When I reboot with the LCD unplugged it goes back to working.   

But I'll accept this rather than the alternative.  .-_

---

