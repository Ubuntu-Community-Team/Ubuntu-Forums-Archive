---
title: "Fujitsu Stylistic LT C-500 and the touchscreen, again"
date: 2008-09-07
forum: Hardware
---

### Post by zhamm on 2008-09-07
Fujitsu Stylistic LT C-500 and the touchscreen, again

Has anybody been able to get Xubuntu 8.04 to run properly on the Fujitsu Stylistic C-500?  I am surprised that an updated fpit driver hasn't been relased in any of the updates.

I'm still struggling with it, and have yet to be able to get the driver to either NOT crash my system, or give me a reliable mouse cursor.

I've read the other threads here, which were helpful to at least diagnose the problem, but none of the solutions listed seems to work properly for me.

A working xorf.conf and autoserial.conf file for the C-500 would be much appreciated, as well as an fpit driver that works with the latest kernel.

Also, anyone know how to get the xvkbd to work on the gdm login screen?  Is it possible?

Thanks

---

### Post by robert1968 on 2008-12-29
Hi,

Fujitsu Stylistic LT C-500 touchscreen ( fpit ) works fine with Ubuntu 8.10 Intrepid.

Kernel:   2.6.27-9-generic
Xorg:     X.Org X server 1.5.2

Steps taken:
1. Install fpit.
apt-get install xserver-org-input-fpit 

2. setserial configuration.

```
dpkg-reconfigure setserial 
```
and set the configuration to manual.

Then comment out all the lines -except bellow- in /var/lib/setserial/autoserial.conf :

```
/dev/ttyS1 uart 16450 port 0xfd68 irq 5 
```

3. xorg.conf configuration:
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"hu"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
#	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"TOUCHSCREEN"
	Driver		"fpit"
	Option		"Device"		"/dev/ttyS1"
	Option		"Passive"		"true"
	Option		"SendCoreEvents"	"true"
	Option		"AlwaysCore"		"on"
#	Option		"DebugLevel"		"3"
	Option "Baudrate" "9600"
	Option "MaximumXPosition" "4096"
	Option "MaximumYPosition" "4096"
	Option "MinimumXPosition" "0"
	Option "MinimumYPosition" "0"
	Option "TrackRandR" "true"
EndSection

Section "Device"
	Identifier	"Cyber 9525"
	Driver		"trident"
	BusID		"0:20:0"
EndSection

Section "Monitor"
	Identifier	"L70S"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Cyber 9525"
	Monitor		"L70S"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse" "CorePointer"
	InputDevice	"TOUCHSCREEN" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection



```

4. Install xvkbd, the useful virtual keyboard.
apt-get install xvkbd

5. Restart system to use new (serial) configuration.

After having intstalled Ubuntu, most fight were with the fpit, 
but now suspend, hibernate, touchscreen, wlan, is all right.

C-500 and Ubuntu 8.10 is very good solution for skype, SIP voip, pdf reading, and browse net with firefox 3, at a low price.

Any question is welcomed.
Robert

---

### Post by Wirelesspirate on 2009-04-27
Thanks a lot for posting those steps!  :)

---

### Post by zhamm on 2009-07-12
Trying this on Jaunty doesn't seem to work. Although it ALMOST works.  I know the xorg.conf stuff is all handled by hal now, but hal doesn't seem to recognize the touchscreen for some reason (as far as I can tell).

Manually putting the xorg.conf example you have *does* do something, but it appears a calibration step for the touchscreen is needed.  At least now the screen actually responds to the stylus though.

Is there a way to calibrate the touchscreen, or am I missing something else?

---

