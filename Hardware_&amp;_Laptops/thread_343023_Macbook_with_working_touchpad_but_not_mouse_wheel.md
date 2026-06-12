---
title: "Macbook with working touchpad but not mouse wheel"
date: 2007-01-20
forum: Hardware &amp; Laptops
---

### Post by widemos on 2007-01-20
I'm using Ubuntu 6.10 with a custom compiled 2.6.19.2 kernel. I did the configuration of the touchpad in synaptics mode and everything went fine, but I've lost the mouse wheel and the forward/backward buttons of my mouse. With the kernel 2.6.17 it used to work. Any suggestions of what I have to check?

Some of the xorg.conf I'm using:

```

Section "InputDevice"
	Identifier	"Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
	Option		"Buttons"		"7"
	Option		"ButtonMapping"		"1 2 3 6 7"
EndSection

Section "InputDevice"
	Identifier	"Touchpad"
	Driver		"synaptics"
	Option		"Device"		"/dev/input/event7"  
	Option		"SendCoreEvents"	"true"
	Option		"Protocol"		"auto-dev"
	Option  	"LeftEdge"      	"100"
	Option  	"RightEdge"     	"1120"
	Option  	"TopEdge"       	"50"
	Option  	"BottomEdge"    	"310"
	Option  	"FingerLow"     	"25"
	Option  	"FingerHigh"    	"30"
	Option  	"MaxTapTime"    	"180"
	Option  	"MaxTapMove"    	"220"
	Option  	"MaxDoubleTapTime"      "180"
	Option  	"VertScrollDelta"       "20"
	Option  	"HorizScrollDelta"      "50"
	Option  	"MinSpeed"      	"0.79"
	Option  	"MaxSpeed"      	"0.88"
	Option  	"AccelFactor"   	"0.0015"
	Option  	"SHMConfig"     	"on"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Teclado"
	InputDevice	"Mouse"
	InputDevice	"Touchpad"
EndSection

```

Thanks.

---

### Post by tweedledee on 2007-01-21
> **widemos said:**
> I'm using Ubuntu 6.10 with a custom compiled 2.6.19.2 kernel. I did the configuration of the touchpad in synaptics mode and everything went fine, but I've lost the mouse wheel and the forward/backward buttons of my mouse. With the kernel 2.6.17 it used to work. Any suggestions of what I have to check?



I've no idea why it stopped working, but this thread may help you restore the functions manually: [http://www.ubuntuforums.org/showthread.php?t=316441](http://www.ubuntuforums.org/showthread.php?t=316441).

---

### Post by widemos on 2007-02-21
I've posted to bluez.org mailing list and seems that my problem is with bluetooth and the need for patching the kernel with 2.6.20-mh1 patch found there. Does somebody know how to do it or how to ask upstream?

Oh, I forgot it. I'm using Feisty Herd 4 now.

---

