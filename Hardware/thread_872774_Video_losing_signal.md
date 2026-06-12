---
title: "Video losing signal"
date: 2008-07-28
forum: Hardware
---

### Post by Aenima99x on 2008-07-28
Uggh need some help, been fighting with this for a couple days. I've got an HTPC setup running Hardy 8.04 that I use strictly for XBMC. I have an ATI Radeon HD 3450 PCIe card that connects directly to my plasma via HDMI. Any time I change input on the tv and then come back to the HDMI input, I get "No Input Signal" on the plasma. Keyboard/mouse input, powering off/on the plasma, or reseating the HDMI cable will not bring the display  back. I have to terminal or VNC in to the active session and reboot the box. I've swapped out the cable and all screensaver/power mgmt. functions are disabled. I've run out of ideas at this point. Here's my Xorg.conf
```

Section "Files"
EndSection

Section "Module"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "off"
	Option      "BlankTime" "0"
	Option      "StandbyTime" "0"
	Option      "SuspendTime" "0"
	Option	    "OffTime" "0"
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
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "false"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "XaaNoOffscreenPixmaps" "true"
	Option	    "vs" "on"
	Option	    "DPMS" "false"
	Option	    "TexturedVideo" "off"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

```

---

### Post by Aenima99x on 2008-07-28
bump

---

### Post by markbuntu on 2008-07-28
The driver is hanging up x because it has lost one of its displays and does not know what to do. Since you are using the ati restricted driver, fglrx, then you should be turning off the display with Catalyst Control Center before you switch the tv inputs. You can then use CCC to turn the display back on when you switch back. That way, the driver should not get so confused.

---

### Post by Aenima99x on 2008-07-28
I just ended up switching my TiVo to use the component inputs on the TV and the HTPC only using the HDMI....all is good now. I'm pretty sure it all comes down to the EDID not getting sent from the TV to the ATI card correctly.

---

### Post by markbuntu on 2008-07-29
Yes, that will cause problems.

---

