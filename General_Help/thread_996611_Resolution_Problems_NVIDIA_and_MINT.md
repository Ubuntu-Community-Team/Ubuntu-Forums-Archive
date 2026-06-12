---
title: "Resolution Problems NVIDIA and MINT"
date: 2008-11-29
forum: General Help
---

### Post by thebrandon on 2008-11-29
I am having trouble getting a decent resolution after installing the nvidia drivers via Envy.  Without the drivers installed I get a resolution of 1024 x 768, which is what I want, but after the install I am stuck at 640 x 480!

I have tried reworking my xorg.conf to force it but I just cant seem to get it right, here is my xorg :

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
	SubSection     "Display"
             Depth       24
       	     Virtual     1024 768 
             Modes      "1024x768,1024x768" "800x600" "640x480" "640x400"
    EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
        Option         "MetaModes" "1024x768,1024x768;800x600,800x600;640x480,640x480"
EndSection

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
	Option		"Emulate3Buttons"	"true"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
        ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync

EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

```

This is my most recent attempt which will allow me to select the 1024 resolution but now it only shows the top portion of my desktop.  I belive that part of this is probably because my monitor kinda sucks, its a sony that from what I read was not very reliable but I know for a fact tha under a previous install of ubuntu I was able to get it and the desktop effects to work but unfortuantely I lost that xorg file in a reinstall!

Thanks!

---

### Post by thebrandon on 2008-11-29
Well I seem to have fixed it, I simply added the Horizsync and Vertrefresh values for my monitor and I was able to fix the resolution!

---

