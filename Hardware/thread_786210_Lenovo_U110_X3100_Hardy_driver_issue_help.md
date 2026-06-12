---
title: "Lenovo U110 X3100 Hardy driver issue help"
date: 2008-05-07
forum: Hardware
---

### Post by dmunk on 2008-05-07
Trying to install Hardy on my new Lenovo.  The Live CD would hang and the screen black out, similar to other experiences with the chipset.  I started in safe graphics mode, and installed - which worked fine.

I've tried some suggestions for switching the driver to "intel" or "i810", but haven't had any luck - always a black screen.  Any guidance would be greatly appreciated.

Wireless, sound and bluetooth all work fine.

---

### Post by garyau on 2008-06-16
have you try to plug the external VGA ?

I can see normal display in external VGA.... 

It seem that -
1. it can just output to external VGA for 'intel' driver
2. Notebook LCD just for work for 'vesa' module ...

---

### Post by stchman on 2008-06-16
> **dmunk said:**
> Trying to install Hardy on my new Lenovo.  The Live CD would hang and the screen black out, similar to other experiences with the chipset.  I started in safe graphics mode, and installed - which worked fine.

I've tried some suggestions for switching the driver to "intel" or "i810", but haven't had any luck - always a black screen.  Any guidance would be greatly appreciated.

Wireless, sound and bluetooth all work fine.

The X3100 works OOB with Hardy.  3D acceleration and Compiz are also enabled even when using the LiveCD.

---

### Post by garyau on 2008-06-18
> **stchman said:**
> The X3100 works OOB with Hardy.  3D acceleration and Compiz are also enabled even when using the LiveCD.


Are you use Lenovo u110 ? I worry it is problem of U110 ...

---

### Post by stchman on 2008-06-18
> **garyau said:**
> Are you use Lenovo u110 ? I worry it is problem of U110 ...

No I have a Toshiba with the 965 chipset.  One would think that the chipset is the controlling factor not the laptop maker.

---

### Post by nwputra on 2008-06-19
Hi all.

I have U110 and it seems that the issue is on the chipset that used on the u110.
If you look at the lspci, it says GMA965 rev 03.
My other notebook, using x3100 GMA965 rev 0c (which has no problem).

Worked OOB :

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)


U110 :
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)


The startx output says :

(WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found

xorg.conf :

Section "Device"
  Identifier "Intel Corporation Mobile GMA965/GL960 Integrated Graphics Controller"
  Driver "intel"
  BusID "PCI:0:2:0"

---

### Post by nwputra on 2008-06-19
One other thing...

I also found that there is an error when trying X -configure
It says :

Module ABI major version (1) doesn't match the server version(2) ..

---

### Post by nwputra on 2008-06-25
Finally it worked !!
\\:D/

Eventhough I was not sure what did that, but now I can get full 1366x768
graphics resolution on my u110.

I tought that u110 needs intel driver since it uses x3100 as graphics controller. But when I tried to use vesa with some additional config in xorg.conf, I got the screen resolution worked well.

Here is the needed config :

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:0:2:0"
	Driver		"vesa"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1280x768@60"	"1280x720@60"	"800x600@60"	"800x600@56"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:0:2:0"
	Driver		"vesa"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"1280x768@60"	"1280x720@60"	"800x600@60"	"800x600@56"
	EndSubSection
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1360x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
	Gamma	1.0
EndSection
Section "device" # 
	Identifier	"device2"
	Boardname	"VESA driver (generic)"
	Busid		"PCI:0:2:1"
	Driver		"vesa"
	Screen	0
EndSection
Section "screen" # 
	Identifier	"screen2"
	Device		"device2"
	Defaultdepth	24
	Monitor		"monitor2"
EndSection
Section "monitor" # 
	Identifier	"monitor2"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection



So, where is 1368x768 defined ? Perhaps it was configured by the 915resolution as I played with the utility before I changed the xorg.conf

# 915resolution 3b 1368 768

---

### Post by garyau on 2008-06-26
> **nwputra said:**
> Finally it worked !!
Section "device" # 
	Identifier	"device2"
	Boardname	"VESA driver (generic)"
	Busid		"PCI:0:2:1"
	Driver		"vesa"
	Screen	0
EndSection
Section "screen" # 
	Identifier	"screen2"
	Device		"device2"
	Defaultdepth	24
	Monitor		"monitor2"
EndSection
Section "monitor" # 
	Identifier	"monitor2"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection



So, where is 1368x768 defined ? Perhaps it was configured by the 915resolution as I played with the utility before I changed the xorg.conf

# 915resolution 3b 1368 768

I don't think VESA is a acceptable solution ..... I have already work for VESA resolution ... 

I would like to make the intel driver work , for acceleration.

---

### Post by chacon on 2008-06-29
I have a similar machine with the x3100 card.  But mine works out of the box, but I assume it works fine because the resolution is a standard one.  But I too am using the VESA driver and I have acceleration(at least enough to use compiz).

---

### Post by nwputra on 2008-06-29
> **chacon said:**
> I have a similar machine with the x3100 card.  But mine works out of the box, but I assume it works fine because the resolution is a standard one.  But I too am using the VESA driver and I have acceleration(at least enough to use compiz).

Hi, I understand that VESA solution is not our goal here. But at least the
Ubuntu 8.04 can be used with higher resolution instead of "Save" 800x600 mode. So, Chacon, is that work out of the box standard resolution is 800x600 ?

We still need to pursue Intel to provide solution, there are so many x3100 problem out there.

Regards

---

### Post by Omar777 on 2008-07-03
> **nwputra said:**
> Finally it worked !!
\\:D/

Eventhough I was not sure what did that, but now I can get full 1366x768
graphics resolution on my u110.

I tought that u110 needs intel driver since it uses x3100 as graphics controller. But when I tried to use vesa with some additional config in xorg.conf, I got the screen resolution worked well.

Here is the needed config :

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:0:2:0"
	Driver		"vesa"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
	Gamma	1.0


So, where is 1368x768 defined ? Perhaps it was configured by the 915resolution as I played with the utility before I changed the xorg.conf

# 915resolution 3b 1368 768

Hi there, I have the same machine, Although i havent acheieved that resolution. I have however reached 1024x768. If you could post what your setting are in the Screen Res. Application. I'm just not sure how you are getting the desired res. with those modelines. I have tried using the 915resolution, and mode #62 is the 1366 res. but all attempts to patching that fails after reboot. As if it never changed anything.
However I have entered this modeline into Xorg:
"1366x768@60" 84.50 1360 1392 1712 1744 768 783 791 807 -vsync -hsync 
But doesnt seem to do anything.

---

### Post by nwputra on 2008-07-03
Hi, I played with the config since I was curious about what makes it worked.
So I remove the 915resolution (apt-get remove 915resolution, remove it also
from /etc/init.d/915resolution).

I change the xorg.conf file, delete all modelines except the one that
Omar777 mention.

Using this new xorg.conf, I still get the 1366x768 resolution working.

So,Omar777: If you can try my xorg.conf file in your u110. Let us know
does it work ?

Here is my xorg.conf :




# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:0:2:0"
	Driver		"vesa"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
	modeline  	"1366x768@60" 84.50 1360 1392 1712 1744 768 783 791 807 -hsync -vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth		24
		Modes		"1366x768@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	screen 0	"Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"

EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection

Section "device" # 
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:0:2:0"
	Driver		"vesa"
	Screen	1
EndSection

Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth		24
		Modes		"1366x768@60"
	EndSubSection
EndSection

Section "monitor" # 
	Identifier	"monitor1"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1360x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
	modeline  	"1366x768@60" 84.50 1360 1392 1712 1744 768 783 791 807 -hsync -vsync
	Gamma		1.0
EndSection

Section "device" # 
	Identifier	"device2"
	Boardname	"VESA driver (generic)"
	Busid		"PCI:0:2:1"
	Driver		"vesa"
	Screen		0
EndSection

Section "screen" # 
	Identifier	"screen2"
	Device		"device2"
	Defaultdepth	24
	Monitor		"monitor2"
EndSection

Section "monitor" # 
	Identifier	"monitor2"
	Gamma		1.0
EndSection

Section "ServerFlags"
EndSection

---

### Post by daroots on 2008-07-06
Hello,
I used your xorg.conf on my u110,
thx....1366x768 resolution works great:))) 
but i am still looking for a way to get acceleration
got an idea ??


regards,

---

### Post by Omar777 on 2008-07-09
OK, so i used it and it works great. Although I lose the ability to shut down my system when i close the lid. Another problem i noticed is that when i shut down and start it back up again, somehow my system tries to repair xorg.conf. Im taken back into 800x600 and have options for 1024x768 in screen/res utility.
The latter gives me full control without any problems to the system. The xorg.conf that im posting is completely different since my system "fixed" it. Anyone have this problem?  
> 

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
# sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection


Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:0:2:0"
	Driver		"vesa"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"
	
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection

Section "device" #       
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:0:2:0"
	Driver		"vesa"
	Screen	1
EndSection

Section "screen" #       
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"800x600@56"	"800x600@60"	"640x480@60"	"1024x768@60"
	EndSubSection
EndSection

Section "monitor" #       
	Identifier	"monitor1"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1360x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

Section "device" #       
	Identifier	"device2"
	Boardname	"VESA driver (generic)"
	Busid		"PCI:0:2:1"
	Driver		"vesa"
	Screen	0
EndSection

Section "screen" #       
	Identifier	"screen2"
	Device		"device2"
	Defaultdepth	24
	Monitor		"monitor2"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
EndSection

Section "monitor" #       
	Identifier	"monitor2"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "ServerFlags"
EndSection

---

### Post by garyau on 2008-08-13
> **chacon said:**
> I have a similar machine with the x3100 card.  But mine works out of the box, but I assume it works fine because the resolution is a standard one.  But I too am using the VESA driver and I have acceleration(at least enough to use compiz).

I cannot use dual head .... 

I have update the intel driver from intel linux web site. The 'TV output' is disappear. However, I cannot output on LCD with intel driver ...

---

### Post by Omar777 on 2008-08-26
OK. After weeks of messing with my Xorg.conf file. I finally gave up and decided to reinstall Hardy. Incredibly after updating the 256 or so packages my system has been looking up. I currently have 1024x768 bootable. Take a look at my xorg.conf. I know its still vesa and not 1366x768. but its better than what it was before and having to manually change it every time I booted.

> # xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:0:2:0"
	Driver		"vesa"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1360x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"vesa"
	Busid		"PCI:0:2:0"
	Driver		"vesa"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "device" # 
	Identifier	"device2"
	Boardname	"VESA driver (generic)"
	Busid		"PCI:0:2:1"
	Driver		"vesa"
	Screen	0
EndSection
Section "screen" # 
	Identifier	"screen2"
	Device		"device2"
	Defaultdepth	24
	Monitor		"monitor2"
EndSection
Section "monitor" # 
	Identifier	"monitor2"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

---

### Post by soccerush10 on 2008-09-29
Pardon. But what does VESA mean in this context, and how does this have any effect on the resolution?  

I researched VESA online, and what I could assurmize is that it is an accronym for the Video Electronics Standard Association, which is like an FDA for PC screen resolutions.  So, please try to explain how this VESA resolution plays into this issue as I am trying to help my gf configure her new Lenovo U110 to use Hardy.

Thanks, in advance.

---

### Post by soccerush10 on 2008-10-27
Omar777, I am going through the same issues with my girlfriend's Lenovo U110.  In my experience when installing Ubuntu on my HP Tx1320us, I had better luck in making permanent changes to the video driver if I updated my system completely, enabling universal repositories as well, BEFORE doing anything to the video drivers.  This is likely a compatibility issue, or something of the sort.  In any case, I feel your pain, but let's continue to pressure Intel for a REAL solution so that we can use the full capabilities of this chipset's 3D acceleration (as limited as it may be).

---

### Post by garyau on 2009-01-09
The other way: 

Boot with option :

vga=0x361

In X window , use 'frame buffer' as driver

The resolution become 1366x768 ...

---

### Post by langmarp on 2010-07-09
[http://ubuntuforums.org/showthread.php?t=1125192&highlight=u110](http://ubuntuforums.org/showthread.php?t=1125192&highlight=u110)

any idea to solve the problem?
thanks!

---

