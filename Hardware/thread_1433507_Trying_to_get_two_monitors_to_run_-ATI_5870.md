---
title: "Trying to get two monitors to run -ATI 5870"
date: 2010-03-19
forum: Hardware
---

### Post by houseonfire on 2010-03-19
I have been trying to get dual monitors running for about 2 days now, with no success.
I have Ubuntu Desktop 64bit, 9.10.

Here is my xorg

```
Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen      0  "amdcccle-Screen[1]-0" 0 0
	Screen         "amdcccle-Screen[1]-1" 1920 12
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "dri"
	Load  "GLcore"
	Load  "glx"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier   "0-CRT2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1280x1024"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "1-DFP4"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1920x1200"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "Default Device"
	Driver      "vesa"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	Option	    "Monitor-DFP4" "0-DFP4"
	Option	    "Capabilities" "0x00000800"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-1"
	Driver      "fglrx"
	Option	    "Monitor-CRT2" "0-CRT2"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   3200 3200
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-1"
	Device     "amdcccle-Device[1]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```


I tried to follow this guide here, 
[http://ubuntuforums.org/showthread.php?p=1773544](http://ubuntuforums.org/showthread.php?p=1773544)

This is my progress when following the instructions on there.

Step one is to back up the xorg file.

Step two:
```
tim@tim-desktop:~$ sudo aticonfig --initial --overlay-type=Xv
Found fglrx primary device section
Error: invalid string value for --ovt option. 
Please check aticonfig help info for supported overlay type.
aticonfig: parsing the command-line failed.

```

Considering that wont work, I'm guessing that's why the rest of the commands don't work.

Step four says to
```
sudo aticonfig --query-monitor
```

But I get:
```
tim@tim-desktop:~$ sudo aticonfig --query-monitor
Error: option --query-monitor is not supported when RandR 1.2 is enabled!

```

I really would like to get this working. If anyone could help me, that would be so great.

I have searched, I have googled, I have tried everything I can think of and just can't seem to get it working.
Something else... My other monitor. Sometimes my desktop appears on it but then the screen starts to fade away in a weird pixilated way. 

Here's a picture of it halfway through.

[http://i41.tinypic.com/1j58gi.jpg](http://i41.tinypic.com/1j58gi.jpg)
[http://i40.tinypic.com/k3qhxs.jpg](http://i40.tinypic.com/k3qhxs.jpg)

And no, those aren't glares. It's the lightest part of my desktop.

---

### Post by I8NY on 2010-03-20
did you try setting up the dual monitors in ati driver or in System>Preferences>Display?  In the Display both monitors *_have_* to be detected for the settings to stay.

---

