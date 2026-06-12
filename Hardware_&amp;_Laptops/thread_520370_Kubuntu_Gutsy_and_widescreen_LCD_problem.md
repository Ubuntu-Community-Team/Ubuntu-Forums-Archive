---
title: "Kubuntu Gutsy and widescreen LCD problem"
date: 2007-08-08
forum: Hardware &amp; Laptops
---

### Post by master_b on 2007-08-08
I have an LG Flatron Wide Screen LCD which runs "straight out of the Box" as a Plug 'n Play monitor with Kubuntu Gutsy at 1680 x 1050.

Problem is that even after playing with manual control on monitor the Desktop still needs to move about 1/8 th inch to the left on the screen as the Desktop is cut-off about 1/2 way through the Garbage Bin and therefore when using applications at full-screen, especially Browsers, I lose the scroll-bar (which is on the far-right and therefore off the screen).

Is there any application or file to edit that will allow me to move the desktop permanently to the left on the screen.

Once upon a time there was such a utility if I remember correctly.

Anybody else have this problem and , hopefully, a solution?
Thanks.

---

### Post by lucy_liu_lover on 2007-08-08
Are you sure that you are running the correct resolution for your monitor ?

---

### Post by master_b on 2007-08-08
Yep - 1680x1050 is monitors native resolution - it is WIDESCREEN

I forgot to mention that the PC is runninhg an ATI card - forget which.

---

### Post by EXCiD3 on 2007-08-08
Sure the driver is installed correctly? Have you tried modifying xorg.conf?

---

### Post by master_b on 2007-08-10
Below is the appropriate xorg.conf section:-

Section "Device"
	Identifier	"ATI Technologies Inc RV280 [Radeon 9200 PRO]"
	Driver		"ati"
	BusID		"PCI:2:0:0"
EndSection

Section "Monitor"
	Identifier	"L206WTQ"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV280 [Radeon 9200 PRO]"
	Monitor		"L206WTQ"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050" "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050" "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050" "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1440x1440" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection


-------------------------------------

Which part, if any, should I edit to move Desktop to the left?

thanks

---

### Post by master_b on 2007-08-10
In additiion to above post I've tried the Kubuntu Gutsy Tribe 4 Live CD, Mepis 6.5 Live CD, Linux Mint Cassandra Live CD and I get the same problem.

All distros see the ATI Radeon card and use the ati driver.

All have the desktop about 1 1/2 inches to the right ( black column on left) until I use the monitors controls to move the image horizontally to the left as far as the controls will allow, still ending up between 1/8 and 1/4 inch too far to the right.

Tried to use vesa driver without any luck.


Monitor works fine on other PC with NVidia card and Kubuntu 6.06 so problem must be combination of ati driver and widescreen monitor, both of which are detected correctly with correct default resolution of 1680 x 1050 by all above distros. Possibly ATI driver not written to handle my LG widescreen LCD 

May have to try to find an NVidia  PCI video card somewhere.

------------------------------------------

Anotherr PC - one with onboard video (via s3 unichrome) , also fails to work in widescreen res. Defaults fot Monitor - LG L206WTQ 20 inch - 1680 x 1050, 60hz, 30-83 and 56-75 h and v sync..

---

### Post by Nphyx on 2007-12-12
Hi,

Sorry to necro this thread, but it's the first that comes up on a Google search for LG Flatron Kubuntu.  After long hours of searching, I've discovered that this is a bug in the current version of the xorg-server.  There is a fix but it hasn't been released for Ubuntu yet.  One can find the updated .deb packages here:

[http://people.ubuntu.com/~bryce/Testing/xorg-server/Good/](http://people.ubuntu.com/~bryce/Testing/xorg-server/Good/)
 
I was able to fix the bug by installing the two xorg-core packages.  I'm a bit of a noob with Linux and with Ubuntu in particular (last time I used linux was... oh, 1997 or so, until last month).  So while I hope that's helpful to some people out there, I cannot provide any further useful information or help :)

---

