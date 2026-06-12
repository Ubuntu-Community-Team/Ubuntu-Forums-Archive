---
title: "X Server Fails on Startup Without My G5 Mouse"
date: 2008-01-28
forum: Hardware &amp; Laptops
---

### Post by flintmecha on 2008-01-28
Hello, I'm still pretty new to Linux (started with Ubuntu back in November)

I've got a Dell Inspiron Laptop, and I use Feisty. My mouse is a Logitech G5 Gaming Mouse.

Shortly after I got Ubuntu installed, I decided I wanted to try to configure it to work best with my mouse. I found and followed the tutorial [here]("http://adterrasperaspera.com/blog/2006/06/20/logitech-g5-review-under-linux"). Well everything was going great until school started up again and I decided to take my laptop to campus with me a few weeks back. I didn't bring my mouse, because I rarely do when I bring my laptop on the go. I went to start it up into Linux (my machine is dual-booted) I was greeted with a really nasty error screen telling me the X Server failed to start. After scanning through all of the (confusing) text, I discovered the problem was simply that my mouse wasn't detected.

I think this is a real problem. It's a laptop, after all, and I should be able to boot my computer without a mouse attached. How do I get around this problem in Feisty? There has to be something.

Thanks!

---

### Post by flintmecha on 2008-02-03
I really hate to bump my own forum threads, and I apologize if this is against the rules.. but I really would like a solution. Anybody? :(

---

### Post by Yellow Pasque on 2008-02-03
Post your /etc/X11/xorg.conf file. You probably have the mouse declared as a "core pointer" and that makes X cry when it's not there.

---

### Post by flintmecha on 2008-02-04
> **Temüjin said:**
> Post your /etc/X11/xorg.conf file. You probably have the mouse declared as a "core pointer" and that makes X cry when it's not there.

Seems so..

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option		"Name"  		"Logitech USB Gaming Mouse"
	Option          "Device"                "/dev/input/event2"
	Option		"ZAxisMapping"		"1 2 3 4 5 6 7"
	Option		"Emulate3Buttons"	"true"
EndSection

---

### Post by Yellow Pasque on 2008-02-04
Ok, well don't declare that mouse as a Core pointer if you're going to boot without it

---

### Post by flintmecha on 2008-02-06
Hm.. thanks! Figures it's such a simple fix and right there in my face the whole time.

HOWEVER

I now have another problem, which is almost just as annoying. I can now start up Ubuntu without my mouse attached just fine. But if I start up Ubuntu WITH the mouse connected, the mouse won't work. Ubuntu loads without a problem, but it's like it doesn't detect my mouse. In order for me to use the mouse, I have to start Ubuntu WITHOUT the mouse connected, and then plug it in after Ubuntu is finished loading.

All I did to my xorg.conf was delete the "CorePointer" line. Is this correct, or should I have replaced it with something else?

```
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
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load    "dre"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
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
	Driver		"evdev"
	Option		"Name"  		"Logitech USB Gaming Mouse"
	Option          "Device"                "/dev/input/event2"
	Option		"ZAxisMapping"		"1 2 3 4 5 6 7"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option          "CorePointer"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-72
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by flintmecha on 2008-02-06
Anyone? Maybe?

---

### Post by flintmecha on 2008-02-10
Bump.

--Edit--

Never mind, I figured it out.

The problem lay with the "SendCoreEvents" option line. In order for X to start correctly without my mouse plugged in, yet at the same time properly recognize it at start up, I needed to configure my xorg.conf as such:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option		"Name"  		"Logitech USB Gaming Mouse"
        **Option          "SendCoreEvents"        "true"**
	Option          "Device"                "/dev/input/event2"
	Option		"ZAxisMapping"		"1 2 3 4 5 6 7"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	**Option          "CorePointer"**
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection
```

Notice how the Touchpad must be set as a CorePointer. By default, it is not. Also, by default, the Touchpad is set to send core events. But this option needs to be moved to the Mouse.

---

