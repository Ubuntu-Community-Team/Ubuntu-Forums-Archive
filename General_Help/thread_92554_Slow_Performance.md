---
title: "Slow Performance"
date: 2005-11-19
forum: General Help
---

### Post by Sebby on 2005-11-19
I have a Sony VAIO FS215S, which has a 1.87GHz Intel Centrino CPU, 512MB RAM, and 100GB hard drive. I have recently installed Ubuntu, and really like it. But something is stopping me from switching from Windows XP entirely. It's not compatibility like I originally thought - I've got everything working - my iPod, PVR, and the list goes on. What is stopping me making the switch is the performance of Ubuntu. Firstly, the boot is quite slow compared to XP, but I can live with this. However, the actual performance once everything has loaded is great either. Applications are fairly slow to start, and minimising windows is very jerky, for example.

So, is Ubuntu just slow, or is there something I can do? I've had a search, but can't really find a definitive answer. I really would like to make the switch once and for all... :D 

Many thanks in advance.

---

### Post by Efwis on 2005-11-19
Hi and welcome to ubuntu.

Just got a couple of questions for ya to see what we can do to help.

what Kernel are you using?

and what kind of graphics card is in the comp?

---

### Post by kruz on 2005-11-19
[http://ubuntuforums.org/archive/index.php/t-80423.html](http://ubuntuforums.org/archive/index.php/t-80423.html) 

[http://ubuntuforums.org/archive/index.php/t-89491.html](http://ubuntuforums.org/archive/index.php/t-89491.html)

check the whole ubuntu forums > tips tricks and custs.

---

### Post by Sebby on 2005-11-20
[QUOTE=Efwis]Hi and welcome to ubuntu.

Just got a couple of questions for ya to see what we can do to help.

what Kernel are you using?

and what kind of graphics card is in the comp?[/QUOTE]
It's kernel 2.6.12-9-386 and the graphics card is an NVIDIA GeForce Go 6200 with TurboCache. I have installed the NVIDIA drivers and have edited xorg.conf accordingly.

---

### Post by Efwis on 2005-11-20
[QUOTE=Sebby]It's kernel 2.6.12-9-386 and the graphics card is an NVIDIA GeForce Go 6200 with TurboCache. I have installed the NVIDIA drivers and have edited xorg.conf accordingly.[/QUOTE]
download and install from synaptic the 686 kernel.

start synaptic and click on search. then enter the following into the search box
linux-image-2.6.12-9-686 and hit enter or click on ok.

mark for installation, and hit apply.
After it is done reboot the computer. on the bootloader make sure you choose the 686 version of the kernel.

if this is a dual processor computer you will need to get this image instead of the one listed above.

linux-image-2.6.12-9-686-smp

let me know if that helps with things. Also try the links that were mentioned.

---

### Post by pneumonia on 2005-11-20
I have similar problem, but maybe more complicated. In my computer even GRUB is loading 10 seconds (normally 1), and the whole boot now takes about 10x more time then usually and I don't have so much patience to run it all the times. Sometimes I'm doing a tea, but after that I can see only the Desktop running, but I have never waited until the end. GRUB is on my Linux partition. What is strange, my partition with W98 (FAT) is running properly. Can you see any solution?

Ubuntu 5.04 for Intel 86x
Duron 850 Mhz
384 MB RAM
ReiserFS on Linux partition
Kernel 2.6.10
GeForce 2 MX 32MB

---

### Post by Sebby on 2005-11-20
Thanks for the replies everyone. I've tried installing the i686 kernel, which went fine, but I don't think it makes very much difference. It's not painfully slow, but just very sluggish compared with XP.

---

### Post by yaztromo on 2005-11-20
I remember reading a thread once on gentoo forums discussing this. It was said that its a design flaw of the X server that makes it not quite as snappy as another well known OS.

I think X was just never designed to cope with the demands placed on it today.

For linux on the desktop I would recommend at least a 1.5ghz CPU. At 2ghz thats sluggishness dissapears for me.

EDIT: Firefox 1.5 will makes things feel better too.

---

### Post by Sebby on 2005-11-20
I'm not far off 2GHz at 1.86GHz. I can live with it, it's just that it doesn't feel as nice to use as Windows and I really want it to! ;)

---

### Post by oskude on 2005-11-20
[QUOTE=Sebby]I'm not far off 2GHz at 1.86GHz. I can live with it, it's just that it doesn't feel as nice to use as Windows and I really want it to! ;)[/QUOTE]well, go complain gfx card makers to open their hardware for others, then linux could get atleas good as ms-windows... (its not "linux" to blame that theres so few real hardware support for it)

---

### Post by 23meg on 2005-11-20
You're probably experiencing low 2D graphics performance, which unfortunately is the case for just about everyone, due to graphics card drivers not allowing X to truly utilize the GPU. Maybe there's still room for improvement in your config, however; post your xorg.conf file for a start.

---

### Post by Sebby on 2005-11-20
[QUOTE=oskude]well, go complain gfx card makers to open their hardware for others, then linux could get atleas good as ms-windows... (its not "linux" to blame that theres so few real hardware support for it)[/QUOTE]
Ah, I see, fair enough.

---

### Post by Sebby on 2005-11-20
[QUOTE=23meg]You're probably experiencing low 2D graphics performance, which unfortunately is the case for just about everyone, due to graphics card drivers not allowing X to truly utilize the GPU. Maybe there's still room for improvement in your config, however; post your xorg.conf file for a start.[/QUOTE]
Here you go:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	#Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	#Load	"dri"
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
	Identifier	"NVIDIA Corporation NV40M? [GeForce Go 6200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"NoLogo"
EndSection

Section "Monitor"
	Identifier 	"Generic Monitor"
	HorizSync 	28.0 - 110.0
	VertRefresh 	43.0 - 90.0
	Modeline 	"1280x800" 80.58 1280 1344 1480 1680 800 801 804 827
	Option 		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV40M? [GeForce Go 6200]"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
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

```

---

### Post by RAOF on 2005-11-20
You can speed X up by adding 
```
        Option          "RenderAccel"           "true"

``` to your Device section, just under Option "NoLogo".

---

### Post by 23meg on 2005-11-20
Be aware that RenderAccel is an experimental feature though, and remove it if it seems to cause problems. Also, what exactly is the model of your video adapter? If it's a non-AGP one, add this line to your "Device" section:```
	Option		"NvAGP" "0"
```

---

### Post by Sebby on 2005-11-21
[QUOTE=23meg]Be aware that RenderAccel is an experimental feature though, and remove it if it seems to cause problems. Also, what exactly is the model of your video adapter? If it's a non-AGP one, add this line to your "Device" section:```
	Option		"NvAGP" "0"
```[/QUOTE]
It's a GeForce Go 6200 with TurboCache.

---

### Post by 23meg on 2005-11-21
I use the same chip and you should definitely put "NVAGP" "0" there. 

I'm actually having some major 2D problems at the moment myself. Desktop icons take a long time to get repainted when switching workspaces (which also happens with some lag) and 2D performance suddenly went down; all this happened after reinstalling the Nvidia drivers. It's like all 2D acceleration suddenly went away. Did you ever experience this?

---

### Post by Sebby on 2005-11-22
This is possibly what I'm experiencing, but I'm not certain. It seems to be okay, but not perfect.

---

### Post by Efwis on 2005-11-22
[QUOTE=oskude]well, go complain gfx card makers to open their hardware for others, then linux could get atleas good as ms-windows... (its not "linux" to blame that theres so few real hardware support for it)[/QUOTE]
you know it's comments like that, that make people not want to ask for help. FYI he has one of the best gfx cards supported on Linux. Nvidia naturally supports linux unlike Radeon.

your attitude is the same as those idiots that spew out that "read the f*ing man pages" crap.

---

### Post by Sebby on 2005-11-23
[QUOTE=Efwis]you know it's comments like that, that make people not want to ask for help. FYI he has one of the best gfx cards supported on Linux. Nvidia naturally supports linux unlike Radeon.

your attitude is the same as those idiots that spew out that "read the f*ing man pages" crap.[/QUOTE]
Thanks for your comments. I think it was a bit of a misunderstanding. I wasn't complaining about Linux itself... :???:

---

### Post by kairu0 on 2005-11-23
[QUOTE=Efwis]your attitude is the same as those idiots that spew out that "read the f*ing man pages" crap.[/QUOTE]

I think we are getting better here. Before Ubuntu, wiki forums, ubuntuforums *wink*, etc. "read the man page" was almost all you could get on a lot of channels.

---

### Post by Efwis on 2005-11-23
[QUOTE=kairu0]I think we are getting better here. Before Ubuntu, wiki forums, ubuntuforums *wink*, etc. "read the man page" was almost all you could get on a lot of channels.[/QUOTE]
we are a lot better then that. although it seems there is a still a lot of that going on. mostly by the diehard Linux zealots. I run into a lot of them on other boards I frequent.

---

### Post by oskude on 2005-11-23
[QUOTE=Efwis]you know it's comments like that, that make people not want to ask for help. FYI he has one of the best gfx cards supported on Linux. Nvidia naturally supports linux unlike Radeon.

your attitude is the same as those idiots that spew out that "read the f*ing man pages" crap.[/QUOTE]you know it's comments like that, that make people who read those man pages to wonder why they even help "you"...

and yeah, i know i should not have reacted to that: "...it's just that it doesn't feel as nice to use as Windows and I really want it to!".
so i apologize for that.

and i know i should not say this: go install zeta and complain MS about windows-xp being slower than zeta... :-\"

---

### Post by Sebby on 2005-11-23
All I was trying to say is I really like Ubuntu, but Windows is faster, and I was asking if I could speak Ubuntu up because I want to keep on using it. There was no hidden agenda or anything like that!

---

### Post by Efwis on 2005-11-23
[QUOTE=Sebby]All I was trying to say is I really like Ubuntu, but Windows is faster, and I was asking if I could speak Ubuntu up because I want to keep on using it. There was no hidden agenda or anything like that![/QUOTE]
I dont' think anyone was insinuating you were. I've found on some computers Ubuntu runs really slow while others it rocks. only thing I can think of that would slow ubuntu down would be a hardware specific item, (ie CPU, HDD, Mobo etc etc)
part of the problem today with computers is most manufacturers gear them towards Windows. Hopefully someday soon they will realize that not everyone wants to use windows.

anyway, back to your issue, how is the machine working? you've mentioned its slower before so I'm curios. does it seem that yoru HDD is working a lot when your using it? or maybe your memory is running at 100% there are a lot of factors that can cause this issue, lets see if we can remove some possiblities.

---

### Post by Sebby on 2005-11-24
[QUOTE=Efwis]anyway, back to your issue, how is the machine working? you've mentioned its slower before so I'm curios. does it seem that yoru HDD is working a lot when your using it? or maybe your memory is running at 100% there are a lot of factors that can cause this issue, lets see if we can remove some possiblities.[/QUOTE]
With the 686 kernel and those few graphics card tweaks, it feels a bit better. To be honest, once it's booted, it's not too bad at all... In fact it's feels quite nippy now. I'm really enjoying using Ubuntu, and of course, if there are anymore tweaks, I'll gladly try them. :D

---

