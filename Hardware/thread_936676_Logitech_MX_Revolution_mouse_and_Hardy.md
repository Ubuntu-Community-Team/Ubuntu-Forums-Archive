---
title: "Logitech MX Revolution mouse and Hardy"
date: 2008-10-03
forum: Hardware
---

### Post by evolve on 2008-10-03
I'm having some trouble setting up my MX Revolution mouse with Ubuntu Hardy.  I know Logitech is infamous for not playing nice with Linux, but I'm hoping to get at least some functionality out of it.

Currently I'm not getting any reaction from my Thinkpad T43 for ANY input from the mouse.  No movement or button response.  And btnx has not recognized it as an input device either.

I've tried the xorg and btnx solutions on this forum and other sites, but I still can't get my laptop to work with the mouse with any of the solutions.  However, it does show up in my /input/devices list.

I'd really appreciate any help someone could give me.

$ cat /proc/bus/input/devices gives me:

[COLOR="Navy"]I: Bus=0003 Vendor=046d Product=c51a Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.1-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input13
U: Uniq=
H: Handlers=mouse1 event2 
B: EV=17
B: KEY=ffff0000 0 0 0 0 0 0 0 0
B: REL=143
B: MSC=10

I: Bus=0003 Vendor=046d Product=c51a Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.1-1/input1
S: Sysfs=/devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.1/input/input14
U: Uniq=
H: Handlers=kbd event3 
B: EV=1f
B: KEY=37fff ac3027 bf004444 0 0 1 f84 8a37c000 667bfa d9415fed 8e0000 0 0 0
B: REL=40
B: ABS=1 0
B: MSC=10[/COLOR]

And my xorg.conf file is:

[COLOR="Navy"]Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection[/COLOR]

---

### Post by evolve on 2008-10-05
Bump? Can someone please help me?

---

### Post by arius13721 on 2009-01-17
I know I'm a little late to the game here, but I've been experiencing this issue, with 8.10, and 9.04 as well. I haven't figured out how to permanently fix it, but I usually have to pull the usb dongle out and put it back in. That *usually* works. Sometimes it doesn't.

I experience this with both the mouse and the keyboard. It's really irritating.

---

