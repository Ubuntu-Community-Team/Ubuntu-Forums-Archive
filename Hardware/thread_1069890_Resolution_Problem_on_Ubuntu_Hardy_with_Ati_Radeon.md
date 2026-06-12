---
title: "Resolution Problem on Ubuntu Hardy with Ati Radeon X600"
date: 2009-02-14
forum: Hardware
---

### Post by hobong on 2009-02-14
Hello all,

I have problem to set resolution higher then 1024x768 
I'm using ATI Radeon X600 ( PCIE ) 

Here's what I got when doing lspci 
01:00.0 VGA compatible controller: ATI Technologies Inc RV380 [Radeon X600 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV380 [Radeon X600]

And I'm using Ati Proprietery Driver ati-driver-installer-9-1-x86.x86_64.run

Here's my xorg.
```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "Dell E773s"
	Option	    "VendorName" "Dell"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc RV380"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen[0]-0"
	Device     "ATI Technologies Inc RV380"
	Monitor    "Dell E773s"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth 24
		Modes "1280x1024" "1280x960" "1280x800" "1152x864" 
	EndSubSection
EndSection

```

Please help me to get higher resolution then 1024x768 

Thanks

---

