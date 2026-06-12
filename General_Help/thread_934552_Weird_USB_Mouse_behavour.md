---
title: "Weird USB Mouse behavour"
date: 2008-09-30
forum: General Help
---

### Post by raiXer on 2008-09-30
Hello everyone,

I got a laptop and I use a USB mouse and it works BUT only if I boot with it attached to the laptop. 
If I boot without it and then connect the USB mouse it doesn't work properly. The mouse turns crazy.


I took a look at /proc/bus/input/devices on both situations and I found they are quite different and probably thats why it is not working correctly.

Here I show the working devices info when I boot my laptop with the mouse attached:
> I: Bus=0003 Vendor=046d Product=c513 Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.1-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input12
U: Uniq=
H: Handlers=kbd event2 evbug 
B: EV=120013
B: KEY=10000 7 ff800000 7ff febeffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=1f

I: Bus=0003 Vendor=046d Product=c513 Version=0111
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.1-1/input1
S: Sysfs=/devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.1/input/input13
U: Uniq=
H: Handlers=kbd mouse1 event3 evbug 
B: EV=1f
B: KEY=37fff 4ac332f bf084444 0 0 ff0001 1f84 8a37cc00 667bfa dd71dfed 9e0000 0 0 0
B: REL=1c3
B: ABS=1 0
B: MSC=10



And here is the one when I boot the laptop without the mouse attached and then connect it afterwards:
> I: Bus=0003 Vendor=046d Product=c513 Version=3200
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:1d.1-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.1/input/input10
U: Uniq=
H: Handlers=mouse2 event10 evbug 
B: EV=7
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0003 Vendor=046d Product=c513 Version=3200
N: Name="Logitech USB Receiver"
P: Phys=/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input11
U: Uniq=
H: Handlers=kbd event11 evbug 
B: EV=120003
B: KEY=7 ff87207a c14057ff febeffdf ffefffff ffffffff fffffffe
B: LED=1f




If someone knows how to fix it manually from terminal it would be so helpful.  Far better than having to restart  :)

Thanks

---

### Post by phidia on 2008-09-30
You could enter (from a terminal) "sudo dpkg-reconfigure xserver-xorg" but probably creating an entry in /etc/X11/xorg.conf for your usb mouse permanently is the easiest way.

---

### Post by raiXer on 2008-09-30
How do I configure the xorg.conf for my mouse?

Here is my xorg.conf:
> Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Option		"NoLogo"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	SubSection "Display"
		Depth	24
		Modes		"nvidia-auto-select"
	EndSubSection
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
EndSection

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
  screen "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"	"CoreKeyboard"
	Inputdevice	"Configured Mouse"
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
EndSection


---

### Post by raiXer on 2008-09-30
Notice my xorg.conf never changes so I didn't think xorg.conf was the problem

---

### Post by Crafty Kisses on 2008-09-30
Post the results of this command:
```
lsusb
```

---

### Post by raiXer on 2008-09-30
this is the result of lsusb

> Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 046d:c513 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


---

### Post by raiXer on 2008-09-30
once I boot with the mouse attached I can unplug it and plug it back on without problems. but I don't wanna boot with the mouse plugged in all the time.

---

### Post by raiXer on 2008-10-01
Anyone?

---

### Post by raiXer on 2008-10-01
bump

---

### Post by raiXer on 2008-10-01
bump

---

### Post by raiXer on 2008-10-01
bump

---

### Post by raiXer on 2008-10-01
k

---

