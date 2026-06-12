---
title: "VAIO C1XS (NeoMagic) 1024x480 Mode problems"
date: 2006-01-09
forum: Hardware &amp; Laptops
---

### Post by plutonius on 2006-01-09
Hello everyone, I am sure this is old hat to some, but as a Linux newbie I am not having any success at getting my VAIO C1XS display resolution to work correctly.

I have tried editing the xorg.conf file (using nano) and sucessfully added the ModeLine "1024x480" 65.00 etc. etc." to the "Monitor" section of xorg.conf but that does not seem to do anything.
(It IS getting saved properly)

Postings on other websites say to use the "vesa" driver but when I do that X will not load with message "no driver found"

Now, I know there is a NeoMagic driver in 5.04 (Driver "neomagic") but perhaps it does not support 1024x480 ? 

I have looked at the post about changing the resolution and that has not helped me.

I was very impressed that this distro booted thru the PCMCIA CD-ROM BIOS and then installed the PCMCIA support on the fly needed to continue the installation. That is a major accomplishment in my book! 

Now if only I could get the display working properly.....

If you want me to post the contents of my xorg.conf file please give me foolproof instructions for how to export it to a floppy (assuming the Sony USB FDD works.....)

Thanks,
Chris

---

### Post by ranf on 2006-01-10
I have a C1VE (ATI graphics card). So my Modeline won't help you much.
Have a look at some of the links here:
[http://tuxmobil.org/sony.html](http://tuxmobil.org/sony.html)

---

### Post by plutonius on 2006-01-19
Thanks to Kenny from the XFree86 mailing list the following xorg.conf file got the signon screen to work at the proper resolution (more on getting GNOME to work right later in this post)

used Applications>Run Applications>sudo nano /etc/X11/xorg.conf 
(check "run in terminal)
After password for root modify the file to match the following:

------------------------------------------------------------------------
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"NeoMagic Corporation NM2200 [MagicGraph 256AV]"
	Driver		"neomagic"
	BusID		"PCI:1:0:0"
        Option          "override_validate_mode"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
        HorizSync      30-64
        VertRefresh    50-100
        ModeLine        "1024x480" 65 1024 1032 1176 1344 480 491 493 525 -hsync -vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NeoMagic Corporation NM2200 [MagicGraph 256AV]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes	"1024x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes	"1024x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes	"1024x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes	"1024x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes	"1024x480" "1024x768"
                        ViewPort      1024 480
                        Virtual         1024 768
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes        "1024x480" "1024x768"
                         ViewPort        1024 480
                         Virtual            1024 768
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
-----------------------------------------------------------------------

After ediiting and writing (CTRL-O) to
/etc/X11/xorg.conf
also write to
/etc/X11/xorg.conf.save
and
/etc/X11/xorg.conf.custom
in case you need to rewrite xorg.conf after an upgrade.

Reboot and the login screen should now show the lower taskbar.

After login Gnome will still be janky.

Open the Applications>SystemTools>ConfigurationEditor
and navigate to:
desktop>gnome>screen>default>0
edit the resolution key value (1024x768) to 1024x480
close using the top right corner "X" and reboot.

Gnome should now show the lower taskbar!

Now if I could only get all the popup windows to resize to 480.....

Hope this helps someone.
Chris

---

### Post by Tylerdirden on 2007-08-03
Helped me loads, 

THX !

---

