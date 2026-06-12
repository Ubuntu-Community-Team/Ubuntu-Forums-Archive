---
title: "Keyboard issues on FS Amilo Xi 2528: Random letters skipped when typing fast"
date: 2007-12-30
forum: Hardware &amp; Laptops
---

### Post by chriflu on 2007-12-30
Hi all,

some issues posted before sound a bit similar, but I did not find anyone having exactly the same problem as me, therefore, I hope it's okay to open a new thread.

The problem is easy to describe. When typing the title of this post at my usual typing speed, this is what happens:

Amilo Xi 2528: Rando lettersskipped when pinfast

Note that there is no noticeable lag - the missing letters are simply skipped.

In addition, sometimes focus changes while typing.

Some additional information:

- Hardware failure? - No, I dual-boot into Gutsy and Windows Vista, and under Vista, there are no problems whatsoever.
- Slow keys enabled? No, I checked several times, the accessibility settings are turned off.
- Application-specific? no, happens right at login and in any application
- CPU load and memory usage: sometimes even below 10%, never above 20%.
- When did the problem arise? Right after installation (it's a new laptop).

Probably the next things I am going to try are to plug in an external keyboard and see if the problem persists and then to change my xorg.conf so as to disable the touchpad while typing to see if there's any interference from there.

Meanwhile, I thought I might share my problem in case anyone else has already found a solution - many thanks in advance!

Just in case, here is my xorg.conf:

```


Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbVariant"	"deadgraveacute"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8600M GS]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Standardbildschirm"
	Option		"DPMS"
	Horizsync	28-72
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8600M GS]"
	Monitor		"Standardbildschirm"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1440x1440"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection

```

---

### Post by jkrtest on 2007-12-30
I have the same issue on an Acer 5570. I don't type very fast, but I notice it on double letters. So, I turn out leters, tomorow, and folow.
Very anoying. oops

---

### Post by chriflu on 2007-12-31
Hi,

just checked and

a.) disabling the touchpad while typing does not help at all
b.) the problem only arises when using the built-in keyboard. Using an external keyboard, I do not have any issues at all.

Any ideas anyone? Unfortunately, this is a real show-stopper in that it slows down my productivity by a factor of at least two...

Many thanks!

---

### Post by Speedboy on 2008-01-03
I've got the same laptop and that problem also occurs here. :(

---

### Post by chriflu on 2008-01-03
I have "solved" my problem by deciding to sell (or to return) the notebook and get a Thinkpad instead.

However, I would be interested in knowing how the heck this is even possible - I mean, it's **a keyboard**. A KEYBOARD! And so far, my only explanation is that apparently this (otherwise completely standard) keyboard requires some very specific drivers? (since any external keyboard works fine and under Vista it works)? How retarded is that (from the part of Fujitsu-Siemens)? Or did I miss any other potential cause?

I'd be grateful if any hardware specialists out there could explain to me how this is possible. The sheer weirdness of the issue boggles the mind.

---

### Post by petersrin on 2008-01-15
I get the same thing on my MacBook Pro. Pretty wacky. Wish I knew enough to research it, but I'm not knowledgeable about drivers, kernels, etc. yet. I may be in 10 years :)

---

### Post by tea123 on 2008-01-19
Hi

I've noticed this several makes of new laptops. The reason I believe is simply because your palm touches the touchpad while typing fast. If you do not touch it at all, your cursor will not jump.

---

### Post by chriflu on 2008-01-20
Thanks - but as I wrote for, one of my first approaches was temporarily to disable the touchpad specifically to exclude this possibility...

---

### Post by PragueBob on 2008-03-20
I can say with almost 100% certainty that the response by tea123 is the only true and correct one, because I have been experiencing this problem on my my new Amilo for the entire week that I've had it and I've tried practically everything before running across this post. Just keep your palms and fingers away from the mousepad on your Amilo while you type and you will never have this problem again!

---

### Post by tompie29 on 2008-05-04
Hi there

I had a problem with my FujitsuSiemens Amilo Pi 1536 keyboard where one key did not work anymore. By flashing the BIOS this was resolved.

This happens every 1 year.

Regards

Tom

---

