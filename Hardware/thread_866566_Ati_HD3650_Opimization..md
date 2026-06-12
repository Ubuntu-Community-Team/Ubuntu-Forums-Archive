---
title: "Ati HD3650 Opimization."
date: 2008-07-21
forum: Hardware
---

### Post by tjwallis on 2008-07-21
I have been really enjoying my HD 3650 card. But I have a few issue that I want to try to resolve. Fist the HD 3650 is advertised as being able to play HD videos at 1080p I still have yet to play Big Buck Bunny at that resolution, at best I get about 3-4 seconds of good video then the video starts to jump are there any options or suggestions that you guys have to optimize the xorg file so i can watch HD videos at 1080p quality?

the second thing is I have two xorg processes running in the background and they are both taking up about 60 MB of memory their are also two GMD processes running and I would like to be able to cut it down to one. So if you have any suggesting pleas let me know.

Here is my xorg so you guys can see my current configuration.
```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	Option	    "AIGLX" "on"
EndSection

Section "Files"
	RgbPath      "/usr/X11R6/lib/X11/rgb"
	FontPath     "unix/:7100"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
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
	Option	    "Protocol" "IMPS/2"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	Option	    "XAANoOffscreenPixmaps" "on"
	Option	    "AccelMethod" "EXA"
	Option	    "MigrationHeuristic" "greedy"
	Option	    "DRI" "true"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "TexturedVideo" "on"
	Option	    "Textured2D" "on"
	Option	    "TexturedVideoSync" "on"
	Option	    "UseFastTLS" "1"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Group        0
	Mode         0666
EndSection

Section "Extensions"
	Option	    "RENDER" "Enable"
	Option	    "DAMAGE" "Enable"
	Option	    "Composite" "Enable"
EndSection

```

---

### Post by tjwallis on 2008-07-23
Bump! Anyone have a suggestions?

---

### Post by markbuntu on 2008-07-24
Try VideoOverlay "off". And turn off the desktop visual effects. 

I have no problems playing 1080p fullscreen video with my HD3650 card on my 24" monitor with 1920x1200 resolution in big desktop with my 19" 1280x 1024 second monitor. The only problem I have is when they are downloading and playing at the same time, like from HULU, which is not even 1080p I think but 1080i or 720p. My little single core cpu can't handle that.

My xorg.conf 

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	Option	    "AIGLX" "on"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "XAANoOffscreenPixmaps" "on"
	Option	    "TexturedVideo" "on"
	Option	    "VideoOverlay" "off"
	Option	    "OpenGLOverlay" "off"
	Option	    "Textured2D" "on"
	Option	    "UseFastTLS" "1"
	Option	    "BackingStore" "on"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "DRI"
        Group       "Video"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "RENDER" "Enable"
	Option	    "DAMAGE" "Enable"
	Option	    "Composite" "Enable"
EndSection

The xorg and gdm processes actually take up a lot less ram since they are sharing almost everything. You can always kill the one that is not being used if you can figure out which one that is.

---

### Post by tjwallis on 2008-07-25
It's weird I can play Big Buck Bunny in 1080p when its encoded in .mov but not .ogg and then only in mplayer or movie player and not in vlc.  but thanks adding Option "VideoOverlay" "off" Option "BackingStore" "on" looks made it so I can play full quality HD :grin:

---

