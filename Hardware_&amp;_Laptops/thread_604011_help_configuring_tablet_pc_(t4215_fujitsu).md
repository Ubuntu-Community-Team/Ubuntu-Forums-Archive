---
title: "help configuring tablet pc (t4215 fujitsu)"
date: 2007-11-05
forum: Hardware &amp; Laptops
---

### Post by luckyluca on 2007-11-05
Hello,

I'm fairly new to ubuntu and recently installed ubuntu studio 7.10 to my tablet pc.
I would now like to activate the wacom pen and all automatic rotation screen/buttons stuff.
I've been checking on the forums for some good hours and I've been trying a few things but unfortunately it all seems very fiddly and nothing worked propely:
I've had play with the /etc/X11 conf file removing the wacom commented out lines,

by typing 'wacdump -f tpc /dev/ttyS0' I have a working tablet with working buttons and pressure of course limited to the terminal window. 

WHat should I do now in order to get wacom working normally and to get the extra rotation features (the screen should rotate automatically since the laptop has a built in rotation detection mechanism) plus setting the buttons and additional screen programmable buttons (if possible). Also working pressure.

Thank you
Luca

---

### Post by mgriff2000 on 2008-03-30
I'm running 8.04 hardy heron and I have the exact same problem if someone could please help that would be great.

---

### Post by anasofiapaixao on 2008-04-01
Just had that problem on a Fujitsu T4215 with Hardy beta, and ended up finding out the solution is STUPIDLY simple ](*,):

First, if you haven't done it already, install the wacom drivers by running

```
sudo apt-get install xserver-xorg-input-wacom wacom-tools
```

Now this usually automagically configures your input pen, but apparently it fails to write the appropriate sections on xorg.conf. And now the interesting part comes: when you add the lines

```
Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/ttyS0"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/ttyS0"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/ttyS0"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection
```

(and, for those who don't know, here are the lines that must bee added to the ServerLayout section: )

```
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
```

**Make sure the device is correct!** When I copied the lines I remembered that I've had to correct the device before. You can check which one is it running

```
wacdump -f tpc /dev/ttySX
```

and seeing whether it prints out stuff like position and pressure when you interact with the pen on the screen. **Try replacing X by different numbers and BE PERSISTENT**; in my old Tecra M4 the wacom input device was the ttyS14 (yeah, fourteen Oo).

Well, good luck!

---

