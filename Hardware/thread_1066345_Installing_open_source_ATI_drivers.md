---
title: "Installing open source ATI drivers?"
date: 2009-02-10
forum: Hardware
---

### Post by Zach1188 on 2009-02-10
**EDIT: Can a mod lock this? I apologise, I posted in the wrong board.**

I am using Ubuntu 8.10 with the fglrx drivers, and I am having a problem with any openGL application, where the screen flickers. I have read that disabling compiz can solve this problem, but I don't want to do that. A few sources have said that switching from fglrx to the open source ATI drivers can also solve the problem, which is no problem for me. However, using this xorg.conf, the "ati" drivers do not work. X starts, but I do not get any hardware acceleration:

```


Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Option "AIGLX" "on"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "ati"
	BusID       "PCI:1:0:0"
	Option "XAANoOffscreenPixmaps" "on"
	Option "TexturedVideo" "on"
	Option "VideoOverlay" "off"
	Option "OpenGLOverlay" "off"
	Option "Textured2D" "on"
	Option "TexturedXrender" "off"
	Option "UseFastTLS" "1"
	Option "BackingStore" "on"
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
	Mode 0666
EndSection

Section "Extensions"
	Option  "RENDER" "Enable"
	Option "DAMAGE" "Enable"
	Option "Composite" "Enable"
EndSection

```
(I know I still have some things named aticonfig-*, but that shouldn't matter)

Again, X starts and I am able to reach my desktop, however when running glxgears or glxinfo, I get the following error:
```

zach@zComp:~$ glxgears
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10

```

Now, using the fglrx drivers, everything works fine, and I get direct rendering, but the flickering is unbearable. Can anyone help?

---

