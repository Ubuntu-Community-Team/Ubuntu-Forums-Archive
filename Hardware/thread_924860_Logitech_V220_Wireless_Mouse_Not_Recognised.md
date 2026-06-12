---
title: "Logitech V220 Wireless Mouse Not Recognised"
date: 2008-09-20
forum: Hardware
---

### Post by Bungtung on 2008-09-20
Hi,

I have a Logitech V220 Wireless USB Mouse and I cannot get Ubuntu Hardy to recognise the mouse on my Compaq nx6120 laptop.  I have Linux Mint 5 installed on another laptop and Mint recognised the mouse "out to the box" without any configuration needed.  There is no mention of the mouse in the xorg.conf file on Mint 5.  It just works.

I have tried the solutions suggested on other threads on ubuntu forums but nothing has worked.  These solutions generally involve changes to xorg.conf.  My ubuntu install is not a recent/clean one as I used dist-upgrade when I moved up to Gutsy and then Hardy and I have made changes trying to get my wireless to survive sleep/resume (it was ok before I upgraded to Hardy).

Any help in getting the wireless mouse going would be much appreciated.

My xorg.conf file is as follows:


Section "Files"
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
	Option		"Device"		"/dev/ttyS0"
	Option		"Protocol"		"Auto"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
        Identifier  "Logitech V220"
        Driver      "evdev"
        Option      "Dev Name" "Logitech USB Receiver"
        Option      "Dev Phys" "usb-0000:00:1d.0-1/input0"
        Option      "SendCoreEvents"
        Option      "evBits" "+1-2"
        Option      "keyBits" "~272-287"
        Option      "relBits" "~0-2 ~6 ~8"
        Option      "Pass" "3"
	Option	    "Device"  "/dev/input/mice"
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
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Logitech V220"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by IntuitiveNipple on 2008-09-22
It might help to attach (compressed) copies of the two log files that report what the system is doing:
```

cd ~
cat /var/log/dmesg | gzip >dmesg.log.gz

cat /var/log/X11/xorg.0.log | gzip >xorg.0.log.gz

```
Someone with a similar configuration can then compare against their own logs and maybe spot a clue.

Does the V220 work outside of X? Try using GPM in a text-console (Ctrl+Alt+F1). Here's the [manual page for GPM](http://manpages.ubuntu.com/manpages/hardy/man8/gpm.html)

```

sudo apt-get install gpm

```
Switch to a text console (Ctrl+Alt+F1) then:
```

sudo gpm

```
Try moving the mouse around and pressing the left button; see if a selection area shows up. If it does that shows the input device is working.

To stop gpm:
```

sudo gpm -k

```

---

### Post by Bungtung on 2008-09-23
Thanks Intu-N,

I am very pressed for time at the moment. I will post the information as soon as I can.

Cheers

---

### Post by Bungtung on 2008-09-23
Hi,

I got not result from the gpm test.  Log files (Xorg.0.log.gz & 
dmesg.log.gz) attached.

Thanks

---

### Post by prashime on 2008-09-25
May be you should Look at this

[www.hidpoint.com](www.hidpoint.com)

---

### Post by Bungtung on 2008-09-26
Thanks.  No progress.  I think the answer to this and the other problems I have with this install is a complete re-install when Intrepid Ibex is released.

---

