---
title: "Dual-head support with ati driver"
date: 2009-04-25
forum: Hardware
---

### Post by [TCK] on 2009-04-25
Seeing as Jaunty no longer supports the proprietary fglrx driver for my ATI X1600 I have been forced to use the open-source ATI drivers.  And it has really proved to be a headache.  I'm trying to set them up so that I can use a dual-head setup where the desktop spans both monitors.  Of note, I'm using a single card with two outputs, with one monitor being 1680x1050 and the other 1280x1024 (which I understand means that Xinerama isn't a good option).  I've never been good with the xorg.conf file in the past, but I thought that with the help of [a couple]("http://ubuntuforums.org/showthread.php?t=221174&page=2") [of guides]("http://ubuntuforums.org/showthread.php?t=301961") I could work this out.

How wrong I was.

My xorg.conf file as it stands.  I'm sure I'm missing something fundamental, and hope someone here can show that to me.

```
Section "Device"
	Identifier	""
	Boardname	"ATI Radeon"
	Busid		"PCI:1:0:0"
	Driver		"radeon"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"true"
	Option "MonitorLayout" "LVDS (TMDS), CRT" # LVDS = Laptop Screen, TMDS = DVI Port, CRT = VGA Port NOT MONITOR TYPE!
 	 Option "CRT2Hsync" "30-65" #Horizontal Sync of the Monitor (check your monitor's manual for correct values)
  	Option "CRT2VRefresh" "50-75" #Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
  	Option "OverlayOnCRTC2" "true"
  	Option "CRT2Position" "RightOf" #Physical location of your secondary monitor in relationship to your primary monitor. Values can be: LeftOf, RightOf, Above, Below, and Clone.
  	Option "MetaModes" "1280x1024-1280x1024" #Monitor Resolutions for Primary-Secondary monitors 
	#Option "MergedXineramaCRT2IsScreen0" "true" #determines which screen is going to be the primary screen; value can be "true" or "false"
EndSection


Section "Monitor"
	Identifier	"Configured Monitor"
	modeline  "1280x102460" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
	Horizsync    	28-64 #You may wish to change the values to fit your specific monitor
	Vertrefresh   	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

---

### Post by linuxuser21 on 2009-04-25
A while back, I looked into getting two different resolutions for my dual-monitors because one of my monitors couldn't handle the resolution my card was putting out.  To my knowledge, it is possible.  If it is, getting there would probably require some serious modifications to some files.

---

### Post by brendanpiater on 2009-04-26
I'm in a similar position with a X700, laptop and 19" LCD. I cannot for the life of me figure out how to get my 19" to be the primary display... 12 hrs and counting... Just loving Jaunty...

The LCD is just dead, (is working, tested) was 100% with propriety driver under 8.10.

Here's hoping someone has a good idea for both of us...

Cheers
B

---

### Post by [TCK] on 2009-04-26
Okay, I seem to have got a lot further with this since stumbling on [this guide (and the accompanying link).]("http://ubuntuforums.org/showthread.php?p=6946925")  Mostly it works now, I now have two separate screens that span a whole desktop.  It's not perfect though, I'm having an issue getting the widescreen monitor to output the correct resolution, as it stands it's outputting to 1280x1024 like my second monitor is.  There's also quite a few flickering issues that I think may be related to the resolution issue but I'm not quite sure.  If anyone knows how to solve that problem I'd be much appreciative. 

For those who want to see if they can see what's wrong, or that could use with a rough template for what xorg.conf should look like, here's my xorg.conf as it stands.

EDIT: Solved the resolution problem, still flickering though.

```
Section "Device"
Identifier "X1600"
Driver "ati"
BusID "PCI:1:0:0"
Option "Monitor-VGA-0" "Samsung SyncMaster 172v"
Option "Monitor-DVI-0" "Samsung SyncMaster 205BW"
EndSection

Section "Monitor"
Identifier "Samsung SyncMaster 172v"
Option "PreferredMode" "1280x1024x60.0"
EndSection

Section "Monitor"
Identifier "Samsung SyncMaster 205BW"
Option "LeftOf" "Samsung SyncMaster 172v"
Modeline "1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync
Option "PreferredMode" "1680x1050_60.00"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Samsung SyncMaster 172v"
Device "X1600"
DefaultDepth 24
SubSection "Display"
Depth 24
Virtual 2960 1050
EndSubSection
EndSection

```

---

