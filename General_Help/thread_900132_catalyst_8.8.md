---
title: "catalyst 8.8"
date: 2008-08-25
forum: General Help
---

### Post by Shiskimalii on 2008-08-25
I have been using the ubuntu provided restricted driver for my ATI 2600 but then got the idea that I wanted a newer driver.

I manually installed catalyst 8.8 following the directions here. [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

Everything is good (with fgl_glxgears I got a great fps increas) except now my wine programs do not run (I have them set to run in a virtual desktop but they all take up the entire screen and cause a "torn" looking screen (tested with starcraft and dxdiag both worked before the upgrade)) videos also flicker now.

Here is my xorg

> Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Option	    "AIGLX" "on"
EndSection

Section "Files"
EndSection

Section "Module"
	Load	    "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbVariant" "dvorak"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "XAANoOffscreenPixmaps" "on" 	
	Option	    "TexturedVideo" "on" 		
	Option	    "VideoOverlay" "off"		
	Option	    "OpenGLOverlay" "off"		
	Option	    "Textured2D" "on" 			
	Option	    "TexturedXrender" "off" 		
	Option	    "UseFastTLS" "1" 			
	Option	    "BackingStore" "on"			
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "RENDER" "Enable"
	Option	    "DAMAGE" "Enable"
	Option	    "Composite" "Enable"
EndSection

Reading around I found that FastTLS could cause these problems but disabling it did nothing for me.

btw i did many of those tweaks and switched to aiglx after the problem but nothing has changed

*I would like these problems fixed but rather have them than downgrade.*

---

### Post by TheOrangePeanut on 2008-08-25
As far as Wine goes, there is a bug with fglrx and Wine in general.  It's on Ati's shoulders, and it's been that way for a couple months, but they haven't addressed it yet.

---

### Post by Shiskimalii on 2008-08-25
but about that flickering during videos?

Edit: the flickering only occurs on compiz, though it didn't before. Also Penumbra Overture runs great on compiz and I assume better on meta.

---

### Post by ZDemon on 2008-08-25
Video playback when running Compiz has always flickered. ATI doesnt seem to bother about this fundamental problem. It is because of this I tell my friends to not purchase ATI.

NVidia and Intel are way ahead of ATI's lagging software engineers, Im sad to say. It is a fact they cant deny. How long are we supposed to wait? We waited 13 months for AIGLX (finally), but we need to watch poor quality videos when running AIGLX?

Anyway, open a terminal and run **gstreamer-properties**. Choose your video output as **'No XV'**. The result is your videos are lower in quality, but at least it doesnt flicker. This doesnt happen with NVidia & Intel's drivers.

I wonder if ATI even knows of this issue.

EDIT : Please thank me if my suggestion helped!!! I hunger for thanks!!

---

