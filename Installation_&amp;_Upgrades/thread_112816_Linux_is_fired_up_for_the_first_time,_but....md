---
title: "Linux is fired up for the first time, but..."
date: 2006-01-05
forum: Installation &amp; Upgrades
---

### Post by Mcjensen on 2006-01-05
Well folks,
     Linux is fired up....wasnt all that hard. :KS :) 
My first Iso download didnt work(only an A: prompt just came up)
My second >ISO download  worked fine and I installed Ubunto 5.10. with no problems...Only my ps2 mouse didnt work...but after I replaced it with a USB mouse, worked fine and I was rolling on.
     I'm using my older HP Compaq Presario 7450 475mhz PC 512 Ram for this dual boot with Windows 2000 installed on my 40GB first hard drive, and now Ubuntu installed on my 8GB 2nd hard drive with a 500MB swap5. I used Grub for dual boot.
     My first impressions were, why havent I tried Linux sooner....Ive heard about it for many years.  Im impressed with the overall many Linux possibilites. One thing struck me being an intermediate PC user is that Linux, even Ubuntu is still geekish with geeky terms...but maybe I need to or want to become more of a geek anyway...:p
      My second impression was this is slower than windows 2000 on my PC, why?
Not enough GBs, or else. Or does the operating motor need more tweaking and how??? Have to check the manuals I guess, duh!  
      Another thought was this dual booting sure is confusing...I thought of using >Partition magic, but decided against it...I still would like to use my windows 2000
bootloader instead of Grub...I mean I have 6 or 7 boot items on the boot menu...can I get rid of some?
       Anyway for day 2, this isnt bad, I like many of the Ubuntu design options.
But Im wondering why its so slow, any suggestions from you Linux masters? And I Thanks, Mcjensen:cool:

D[COLOR="Red"]oes evrything look alright in here???[/COLOR]
[CENTER]
# /etc/X11/xorg.conf (xorg X Window System server configuration file)

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
	Option		"XkbLayout"	"dk"
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

Section "Device"
	Identifier	"Trident Microsystems CyberBlade/i7"
	Driver		"trident"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"HP D8905"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Trident Microsystems CyberBlade/i7"
	Monitor		"HP D8905"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection


[/CENTER]

---

### Post by bjourne on 2006-01-05
Linux in general is *not* slower than Windows. But a GNOME desktop definitely is much slower than a Windows desktop. On the other hand GNOME has much cooler stuff than Windows and looks better. If you can live without GNOME, try another desktop such as xfce4, fluxbox or KDE all of which are faster.

---

