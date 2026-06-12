---
title: "Screen Resolution on a new install"
date: 2009-05-23
forum: Installation &amp; Upgrades
---

### Post by jhl on 2009-05-23
[FONT=Comic Sans MS][SIZE=3]Hello, First I'm a newbie to Ubuntu.  I just installed 8.04 LTS without windows.  The screen resolution that Ubuntu defaulted to was 800 x 600.  I wanted something else (1280x768 or 1280x1024), but I'm unable to figure out how to do that.

My mobo is a EVGA e-7050/610i with nvidia on board video.  I obtained the proprietary driver[/SIZE][/FONT] [SIZE=3][FONT=Comic Sans MS]and installed it.  However, the screen shows it's enabled, but the message next to it says "not in use[/FONT][/SIZE]."

[FONT=Comic Sans MS][SIZE=3]Need help getting a better resolution[/SIZE][/FONT].  [FONT=Comic Sans MS][SIZE=3]THANKS[/SIZE][/FONT][SIZE=3]
[/SIZE]

---

### Post by taurus on 2009-05-23
Which nvidia graphic card do you have and which driver did you install?

The best (or easy) way to install an nvidia driver for your graphic card is from System -> Administration -> Hardware Drivers (if it's on the list).

---

### Post by jhl on 2009-05-23
I have the video that came with the motherboard.
I used driver that Ubuntu installed when I selected Nvidia.  However, the only two screen resolutions offered are 800x600 and 640x480.

Those were the only two offerings before the upgrade as well.

---

### Post by taurus on 2009-05-23
```
lspci | grep VGA
```
Will tell you which onboard graphic card do you have.

---

### Post by doomsword2001 on 2009-05-23
hello i had screen resolutions too, i found a post in forums helped me.

sudo gedit /etc/X11/xorg.conf
**After changing xorg.conf**

Section "Device"
    Identifier    "Intel Corporation Mobile Integrated Graphics Controller"
    Driver        "intel"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Intel Corporation Mobile Integrated Graphics Controller"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        24
        Modes        "1024x768"
        EndSubSection
EndSection

**before changing xorg.conf**

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

i guess if your **xorg.conf **is like mine was you have to do something similar, according to your hardware.

---

### Post by artsci2 on 2009-05-27
Thanks Doomsword, with your hints I was able to get my misbehaving install to start up and use a 1680x1050 screen that it wasnt able to properly detect during install.

[
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Subsection	"Display"
	Depth		24
	Modes		"1680x1050"
	EndSubSection
	Device		"Configured Video Device"
	Subsection	"Display"
	Depth		24
	Modes		"1680x1050"
	EndSubSection
EndSection
]

---

### Post by artsci2 on 2009-05-27
OK so now does anyone know where the file is that ATI Catalyst Control Center uses to get the screen resolution and refresh rates at?

I just want to go to the file and permanently set the resolution to 1680x1050 and 60Hz refresh for both screens.

---

