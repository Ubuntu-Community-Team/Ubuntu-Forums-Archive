---
title: "Help setting up my graphics card"
date: 2006-12-10
forum: Hardware &amp; Laptops
---

### Post by championchap on 2006-12-10
Well, i thought that my card was all set up fine, id installed the drivers following ubuntuguide, and even had xgl/compiz working nicely enough.
But checking my config file, it seems that the device being used is still my horrible intel intergrated graphics chip rather than my Geforce FX 5200 PCI card.

Can anyone offer any help?
Would just changing the entry in the config file to point to my pci card do the trick?

I want to use my monitor at its intended resolution!! haha

Oh, im running a fully updated Dapper by the way.

---

### Post by daou on 2006-12-10
You can check what gfx cards Ubuntu has detected by running

```
lspci
```

in your terminal. Then you need to find your gfx card in the list. For example, I have a 6600 GT and the following shows up in the bunch of text that lspci gives:

```
05:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)

```

This means it's located at PCI 05:00.0
Now check your xorg.conf (make a backup first)

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo gedit /etc/X11/xorg.conf
```

Under Section "Device" there might be a line with

```
BusID       "PCI:X:X:X"
```

Make sure the X's are the same as the PCI location given from lspci. If it's not, your xserver is using the integrated card. So for my card, I would change the line to

```
BusID       "PCI:5:0:0"
```

Then you can restart your xserver (CTRL+ALT+BACKSPACE). If it doesn't boot,  restore the old xorg.conf file from your terminal and restart gdm:

```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart
```

---

### Post by daou on 2006-12-10
Also, make sure that xserver is configured to use the right driver. So under the Section "Device", make sure there is a line

*If you have installed new nvidia drivers*
```
Driver "nvidia"
```

or

*If you haven't installed new nvidia drivers or the above doesn't work*
```
Driver "nv"
```

---

### Post by championchap on 2006-12-10
Hey thanks for the help.. but im a little confused
This is what i got when i checked for my graphics card

```
0000:01:06.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200 ] (rev a1)
```

And this is what i get in my config file, notice it references the intel chip in the monitors section too.. should i do something about that??

```
Section "Device"
    Identifier     "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
    Driver         "nvidia"
   Option		"NoLogo"
	Option		"RenderAccel"		"true"
	Option		"AllowGLXWithComposite" "true"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
    Monitor        "DELL E773p"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

---

### Post by daou on 2006-12-10
Actually, if your Xserver works with those settings, I believe it's using your NVIDIA gfx card. Your integrated Intel card would not work with the "nvidia" driver specified in the Device section.

The identifier, "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device", doesn't mean anything. It is probably a remnant from when your system was using the Intel chipset. In fact, the identifier can be anything. You could name it "My Card" and it would still work, granted you also change the device field in the Section "Screen" to "My Card" as well. It is only an identifier used internally in the xorg.conf file.

---

### Post by jonatelo on 2008-06-27
helloo my name is jonathann well i really really like relly need help from u guys i have a lcd tv monitorr which in windows xp i used intel extreme graphic properties to set a custom resolution of 1152x864 and now im a newbi in linux and im really tried every thing to fix the resolutionn look at my xorg.conf file 

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"v4l"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	VideoRam	65535
EndSection

Section "Monitor"
	Identifier	"VTEK"
	Option		"DPMS"
	HorizSync	30-100
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"VTEK"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

what can u recomendd me guyss i have a 19 inch haier screen with intel 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device  pliixxx helppp meee

---

### Post by ethanklein on 2008-06-27
Yeah the experiences I've had with i810 are horrible. I'm sorry dude I had that same problem so I switched to Nvidia 6200 :).

---

### Post by ethanklein on 2008-06-27
run sudo dpkg-reconfigure -phigh xserver-xorg your xconfig is really messy.

---

### Post by jonatelo on 2008-06-27
soo whatt do u gguys recomend me to the plixx i just love linux so much but this resolution is bs

---

### Post by jonatelo on 2008-06-28
plizzz helpp mee i just want a 1152x864 resolutionnn i still cant manage to get it

---

