---
title: "dual monitor video ram problem?"
date: 2007-10-18
forum: Hardware &amp; Laptops
---

### Post by asdf29 on 2007-10-18
:-k:mad:

I have a really weird problem and I have spent an evening searching for the solution, but to be honest I don't really know where to start.  

I have:-
HP nx6325
ATI Express 1150 (128M shared memory)
NEC MultiSync 20WGX2 monitor
Kubuntu Gutsy 7.10

```
asdf29@thestation:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.0.6473 (8.37.6)
```


When I have both screens running as a big desktop then I get these two stripes at the bottom right of each screen.  (see the photos).  This doesn't occur with windoze or when I switch to single screen.

[[IMG]http://img132.imageshack.us/img132/9282/p1000771jp4.th.jpg[/IMG]](http://img132.imageshack.us/my.php?image=p1000771jp4.jpg)[[IMG]http://img98.imageshack.us/img98/5937/p1000772yn8.th.jpg[/IMG]](http://img98.imageshack.us/my.php?image=p1000772yn8.jpg)

From my very limited experience of writing graphics libraries it feels like a memory overlap issue or something...


Here is my xorg.conf file.

```
<snip/>
Section "Device"
	Identifier	"ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"
	Driver		"fglrx"
	Busid		"PCI:1:5:0"
    Option "DesktopSetup"  "horizontal,reverse" #Enable Big Desktop
    Option "Mode2"         "1680x1050" #Resolution for second monitor
    Option "DesktopSetup" "LVDS,AUTO" #the types of monitors that is connected LVDS = LCD, CR
    Option "EnablePrivateBackZ" "yes" #Enable 3d support <= May Not Work
    Option "HSync2" "65" #This sets the horizontal sync for the secondary display.
    Option "VRefresh2" "60" #This sets the refresh rate of the secondary display.
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
    Option  "Composite" "Disable"
EndSection
```

---

### Post by asdf29 on 2007-10-19
shameless bump

---

### Post by hessiess on 2007-10-19
try difarent driver?

---

### Post by asdf29 on 2007-10-23
such as?

---

