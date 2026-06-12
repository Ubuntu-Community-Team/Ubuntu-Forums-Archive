---
title: "old laptop needs Fbdev help"
date: 2006-06-15
forum: Hardware &amp; Laptops
---

### Post by Uta on 2006-06-15
I have an old Dell Laptop CP M233XT, that has a Neomagic card and after installing Xubuntu I now have a very nice GUI  but only part of the monitor screen is being utilized. There is a 1 and 1/2 inch black border around the screen display. I know this has to do with FBdev being set up correctly in the xorg.conf. I need to ID the driver as "FBdev" and also "VGA 16"

I just can't remember how I set this up before. I'm trying to put some life back into this laptop so I can give it to my elderly next door neighbor to check her email, any help would be appreciated.

---

### Post by Uta on 2006-06-16
I guess I am going to give up on Xubuntu. The only reason I chose this distro was because it was small and more importantly setting up wireless with my DWL-650+ was a snap. I am currently booted with Damn Small Linux which displays perfectly but has no support for my acx100 (DWL-650+) card. I wish there was a way to take the xserver config file from DSL and use it's parameters with Xubuntu? I couldn't find DSL's xorg.conf file, It's setup very differently it appears? Any help would be appreciated.

---

### Post by msofer on 2006-06-16
As far as I remember, DSL does not use Xorg nor Xfree86, but rather the vesa [kdrive]("http://freedesktop.org/wiki/Software_2fXserver") xserver. DSL is indeed very light and fast.

---

### Post by Greg2 on 2006-06-17
[QUOTE=Uta]I have an old Dell Laptop CP M233XT, that has a Neomagic card and after installing Xubuntu I now have a very nice GUI  but only part of the monitor screen is being utilized. There is a 1 and 1/2 inch black border around the screen display. I know this has to do with FBdev being set up correctly in the xorg.conf. I need to ID the driver as "FBdev" and also "VGA 16"[/QUOTE]
I don’t have Xubuntu installed to check this for you. I would however suggest that you open /etc/X11/xorg.conf and edit the Section “Device” with:

Driver    “vga16fb”
or
Driver    “vesafb”

Which ever one works the best?

Make sure that all overlay options are “off”

Make sure your comment out the driver you want to use in /etc/modprbe.d/blacklist-frambuffer

---

### Post by Uta on 2006-06-17
First thank you for your help! I tried both options you stated plus putting a "#" in front of the framebuffer I wanted to use in the blacklist file but upon reboot I got the error that the xserver couldn't start so, I have gone back to my original xorg.conf file (that displayed nicely only not utilizing the full screen) and will ask you (or some kind soul) to help me edit it correctly. I will paste here only the section I am trying to change, Thanks!
Also the parameters that work with DSL(Knoppix) are "fb1024x768" and "Xfbdev" with xserver
________________________________________________________

Section "Device"
	Identifier	"NeoMagic Corporation NM2160 [MagicGraph 128XD]"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NeoMagic Corporation NM2160 [MagicGraph 128XD]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by Greg2 on 2006-06-17
Sorry, that should have been:

Driver    “vesa”

I just did a bit of research on this, and it would appear that the preferred driver for your chip is vesa... at this time, with this kernel.

Here are the boot parameters for screen resolution:
[http://womp.sourceforge.net/documentation/node11.html](http://womp.sourceforge.net/documentation/node11.html)

You will most likely want to add vga=791

vesafb.txt:
[http://www.mat.univie.ac.at/~gerald/laptop/vesafb.txt](http://www.mat.univie.ac.at/~gerald/laptop/vesafb.txt)

You could also edit the

Section "Screen"
Identifier "Default Screen"
Device "NeoMagic Corporation NM2160 [MagicGraph 128XD]"
Monitor "Generic Monitor"
DefaultDepth 24  > (change 24 to 16)

---

### Post by Uta on 2006-06-17
THANK YOU!
O,joy full screen view! I really appreciate the effort you have made to help me solve this issue.
I added the vga=791 to the actual menu.lst, was that right?

Also changing to 24 to 16, why was that necessary?
Again thank you!

---

### Post by Greg2 on 2006-06-17
[QUOTE=Uta]THANK YOU!
O,joy full screen view! I really appreciate the effort you have made to help me solve this issue.[/QUOTE]I’m glad you have it working!> 
I added the vga=791 to the actual menu.lst, was that right?

Also changing to 24 to 16, why was that necessary?
Again thank you!
Yes, add the boot parameter to the menu.1st

changing 24 to 16 was not necessary... but I wasn’t sure :)

---

### Post by dougtheslug on 2007-03-19
will this setup work with desktops
I have been waiting for damnsmalllinux to go the UBUNTU way but I think this is a better aproach
I tried the sugestions in this thread but did not work , went back to my old Xorg.conf
maybe some one could write a more detailed howto 
that a newbee like me can follow
so far I have been able to install icewm with ROX as a file manager for Icons and wallpapers 
that makes it fast . but the Kdrive will be even better.
thanks in advance.

---

