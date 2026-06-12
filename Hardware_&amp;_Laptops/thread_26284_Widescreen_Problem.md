---
title: "Widescreen Problem"
date: 2005-04-12
forum: Hardware &amp; Laptops
---

### Post by encho on 2005-04-12
First Hi to all you ubuntu-ers  =;
Ubuntu is the longest surviving distro on my PCs, cause it's fast, easy to use, and so cool. I have it at home & at work and it is my OS of choice.
Few days ago I got a laptop - it is PackardBell EasyNote A, with widescreen display run by Intel 855GM(E) video card. And guess what - installing ubuntu was the first thing to do  :smile: 

Everything is working (and faaast) except for the widescreen - it doesn't display the 1280x768, only 1024x768, so desktop is streched.
I've tryed solutions from this forum, including xorg.conf changes, patches, etc, but nothing helped. So please, don't let me use other OS  :cry:

---

### Post by mendicant on 2005-04-12
What's the contents of /var/log/Xorg.0.log and your /etc/X11/xorg.conf?

---

### Post by NeiL on 2005-04-12
[QUOTE=encho]First Hi to all you ubuntu-ers  =;
Ubuntu is the longest surviving distro on my PCs, cause it's fast, easy to use, and so cool. I have it at home & at work and it is my OS of choice.
Few days ago I got a laptop - it is PackardBell EasyNote A, with widescreen display run by Intel 855GM(E) video card. And guess what - installing ubuntu was the first thing to do  :smile: 

Everything is working (and faaast) except for the widescreen - it doesn't display the 1280x768, only 1024x768, so desktop is streched.
I've tryed solutions from this forum, including xorg.conf changes, patches, etc, but nothing helped. So please, don't let me use other OS  :cry:[/QUOTE]
 My device section looks like this, i'm using EDID maybe you will try it:

    Section “Device”
    Identifier “NVIDIA Corporation NV36 [GeForce FX Go 5700]”
    Driver “nvidia”
    BusID “PCI:1:0:0&#8243;
    Option “NoLogo”
    Option “RenderAccel” “true”
    Option “NvAGP” “1&#8243;
    VideoRam 65536
    Option “UseEdidFreqs” “True”
    EndSection

---

### Post by vnbuddy2002 on 2005-04-12
Can you post the /etc/X11/xorg.conf file?

---

### Post by encho on 2005-04-13
I've tryed HorizSync, VertRefresh, Modeline, IgnoreEDID, DisplaySize - nothing helped... This is my current xorg.conf (default - I removed all the above options).



> ###############################################

[SIZE=1]Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
			# local font server
	# if the local font server has problems, we can fall back on these
        # paths to defoma fonts
	FontPath     "unix/:7100"
	FontPath     "/usr/lib/X11/fonts/misc"
	FontPath     "/usr/lib/X11/fonts/cyrillic"
	FontPath     "/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/lib/X11/fonts/Type1"
	FontPath     "/usr/lib/X11/fonts/CID"
	FontPath     "/usr/lib/X11/fonts/100dpi"
	FontPath     "/usr/lib/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "dbe"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "record"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "keyboard"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "ie"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "Emulate3Buttons" "true"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection


Section "Device"

	Identifier  "Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver      "i810"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x768"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection[/SIZE]

---

### Post by Diego F. on 2005-04-13
[QUOTE=encho]I've tryed HorizSync, VertRefresh, Modeline, IgnoreEDID, DisplaySize - nothing helped... This is my current xorg.conf (default - I removed all the above options).[/QUOTE]
 I had the same problem in Warty and had to install nVidia drivers. Yesterday I did a new installation of Hoary and automatically set it to 1280x800. ¿Are you installing Hoary?

---

### Post by encho on 2005-04-13
Hoary. The latest one.

---

### Post by mendicant on 2005-04-13
What about /var/log/Xorg.0.log after you start X?

---

### Post by goldfish on 2005-04-14
Try running sudo dpkg-reconfigure xserver-xorg

---

### Post by encho on 2005-04-14
I'll give you the log as soon as I can. Reconfigure didn't work for some reason - after it was finished I was unable to logon (X server error), guess log would explain the reasons. Thank you all for your effort, I'll have the log tomorrow.

---

### Post by WAL on 2005-04-14
I have a similar problem (Acer Aspire 1410 with 15.4" 1280x800 res.)

config file include, log is large so if needed I'll need to remove some stuff (so tell me what things you need)

please help!

---

### Post by mendicant on 2005-04-14
It's difficult to say what would be useful.  Just attach it as you did with xorg.conf.txt and those who choose to, can download it and look at it.

---

### Post by encho on 2005-04-15
Here is my log

---

### Post by yusufk on 2005-04-15
I've got a Dell D800 with widescreen and Nvidia 5200. After much tweaking I've got the   settings perfect, including 2 monitor mode. So I've attached my xorg.conf file for you to try. Also, You may need to disable the twinview option which you can do by changing the twinview option  from "on" to "off".

Good luck, hope it helps

p.s., u need to have installed the nvidia-glx drivers!

---

### Post by mendicant on 2005-04-15
encho, that's perfect.  The information you're looking for is here:
(II) I810(0): Manufacturer's mask: 0 (II) I810(0): Supported additional Video Mode:
(II) I810(0): clock: 68.2 MHz   Image Size:  284 x 171 mm
(II) I810(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) I810(0): v_active: 768  v_sync: 770  v_sync_end 777 v_blanking: 790 v_border: 0
...
(II) I810(0): Not using mode "1280x768" (no mode of this name)

What this all means is that you need to modify your Section "Monitor":

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
Modeline "1280x768" 68.2 1280 1328 1360 1440 768 770 777 790
EndSection

Let me know if that works.  For others having problems, check for similar lines ("Supported additional Video Mode" in particular).

---

### Post by jkbys on 2005-04-15
I have Dell 700m which has 1280x800 screen. It parfectly works with 855resolution ( [http://perso.wanadoo.fr/apoirier/](http://perso.wanadoo.fr/apoirier/) ).
I found 855resolution debian package at [http://www.debian.or.jp/~kmuto/855resolution/](http://www.debian.or.jp/~kmuto/855resolution/).
I think we need 855resolution program to set wide resolution with intel 855 chipset.

---

### Post by encho on 2005-04-19
[QUOTE=mendicant]
Let me know if that works.  For others having problems, check for similar lines ("Supported additional Video Mode" in particular).[/QUOTE]
Sorry, I was away for few days. I'm not one of those people who, when they have their problem fixed, never even say 'thanks'.  ;-) I've tryed modeline, but no luck there. So, desperate, tryed this 855resolution package, run the command, restarted X and, amazed, found out that it is WORKING. Later I only had to change /etc/default/855resolution file and set mode to my 1280x768.
Thank you all guys for trying and for all your hard work. This is the best distro - pardon - OS in the history of PCs.
I guess there must be other way than installing this patch (just modifying the xorg.conf) but I'll rest my case. It IS working and it is fast.  \\:D/

---

### Post by WAL on 2005-04-21
my problem was solved via 855resolution

---

### Post by applejesse on 2005-09-11
I will try this patch on my Sony Vaio PCG-TR3AP3! 

Ubuntu fun great on my work Vaio VGN-S360P (Best distro for Notebooks!!!)

---

### Post by jfarschman on 2007-10-29
I think someone got clever because I did an

apt-get install 855resolution 

and on reboot it solved everything for my Sony Vaio VGN-T340P.  Anyone else solving Sony VGN T-series problems would be wise to go here"

[http://statistic.gunadarma.ac.id/pub/driver/T350P/UbuntuOnSonyVaioTRSeries.htm](http://statistic.gunadarma.ac.id/pub/driver/T350P/UbuntuOnSonyVaioTRSeries.htm)

I'm solving problems I didn't even know I had yet :)

---

