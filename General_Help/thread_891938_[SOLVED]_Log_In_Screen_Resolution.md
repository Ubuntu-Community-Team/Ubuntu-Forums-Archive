---
title: "[SOLVED] Log In Screen Resolution"
date: 2008-08-16
forum: General Help
---

### Post by TreeFinger on 2008-08-16
When I hit the log-in screen, it is sort of a blueish tint and not fitting correctly on the screen.

When I first logged into ubuntu my desktop was like this also, until I changed resolutions.

I'm guessing changing the login screen resolution will fix this.

Could someone tell me how to do that?

---

### Post by Too Late on 2008-08-16
You have to edit edit your /etc/X11/xorg.conf file. Post its contents here if you are unsure what to do.

Basically, you must add something like this at the end of the "Screen" section:
```
SubSection "Display"
        Depth           24
        Modes           "1280x960"
EndSubSection

```
Where the values are the values you would like to use.

If that will not help, you must probably manually add a modeline there. 'xvidtune' command will be helpful in that case, but let's see if that earlier method works.

---

### Post by TreeFinger on 2008-08-16
> **Too Late said:**
> You have to edit edit your /etc/X11/xorg.conf file.

Basically, you must add something like this at the end of the "Screen" section:
```
SubSection "Display"
        Depth           24
        Modes           "1280x960"
EndSubSection

```
Where the values are the values you would like to use.

I tried that but nothing changed.

```

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "800x600" "640x480"
	EndSubSection
EndSection

```

My login still has a blueish tint and does not fit correctly on my monitor.

---

### Post by Too Late on 2008-08-16
Ok, I already edited my previous post... Now go to terminal and type xvidtune. After pressing Ok, press the Show button, and then quit.

You'll see a modeline in your terminal. Add this line to "Monitor" section in your xorg.conf file and put the word ModeLine in the beginning of that line.

Remember to take backups of that file just in case...

---

### Post by tad1073 on 2008-08-16
try
```
sudo gedit /boot/grub/menu.lst
```
then add
```
**[color=Red]vga=795[/color]**
```
after 
```
ro quiet splash
```
which will make your boot splash 1280x1024, but I don't know if it will help with your login screen.

---

### Post by TreeFinger on 2008-08-16
> **tad1073 said:**
> try
```
sudo gedit /boot/grub/menu.lst
```
then add
```
**[color=Red]vga=795[/color]**
```
after 
```
ro quiet splash
```
which will make your boot splash 1280x1024, but I don't know if it will help with your login screen.

I'm not using a splash screen.

---

### Post by TreeFinger on 2008-08-16
> **Too Late said:**
> Ok, I already edited my previous post... Now go to terminal and type xvidtune. After pressing Ok, press the Show button, and then quit.

You'll see a modeline in your terminal. Add this line to "Monitor" section in your xorg.conf file and put the word ModeLine in the beginning of that line.

Remember to take backups of that file just in case...

```

Vendor: , Model: 
Num hsync: 1, Num vsync: 1
hsync range 0:  30.00 -  95.00
vsync range 0:  50.00 - 160.00
"1280x1024"   108.00   1280 1328 1440 1688   1024 1025 1028 1066 +hsync +vsync

```

What do you mean by modeline? That last line?

---

### Post by Too Late on 2008-08-16
Yes, the last line is the modeline. But I'm not sure if you need the other lines too, since I'm not having them.

---

### Post by TreeFinger on 2008-08-16
> **Too Late said:**
> Yes, the last line is the modeline. But I'm not sure if you need the other lines too, since I'm not having them.

:confused: So what should I do?

---

### Post by Too Late on 2008-08-16
I don't know... I think it depends on how the monitor is already configured in xorg.conf.

Put its contents (at least Monitor and Screen sections) here so someone can probably help.

---

### Post by TreeFinger on 2008-08-16
> **Too Late said:**
> I don't know... I think it depends on how the monitor is already configured in xorg.conf.

Put its contents (at least Monitor and Screen sections) here so someone can probably help.

```

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
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

```

---

### Post by TreeFinger on 2008-08-16
Hmm, well randomly I decided to install drivers for my video card (nvidia 8800 GT). And that seems to have fixed it!

I'll post my new xorg.conf, i'm guessing it is changed.

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Thu Jul 17 18:39:00 PDT 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

