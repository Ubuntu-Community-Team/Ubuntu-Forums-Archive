---
title: "Jumping Cursor problem, Breezy, Dell SmartPC 250n"
date: 2005-11-15
forum: Hardware &amp; Laptops
---

### Post by Ranulf on 2005-11-15
Hi all,

Firstly apologies if they is a better place to post this message; I can never work out exactly where they should go.

My problem is that I experience random mouse movements and button clicks at random intervals of around 20 minutes whilst using my machine.  I first had this problem with Hoary and it was quickly fixed with the removal of the battery monitor.  Having just installed Breezy I am experiencing the same problem but without as much luck in solving it.  I have come across several over people with this problem but am yet to find a solution that works.

I have tried,
* Removing the battery monitor from the tray thingy.
* Updating my synaptic drivers to the latest version.
* Editing the Xorg.conf file to comment out the touch pad.
from this

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

to this

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

#Section "InputDevice"
#	Identifier	"Synaptics Touchpad"
#	Driver		"synaptics"
#	Option		"SendCoreEvents"	"true"
#	Option		"Device"		"/dev/psaux"
#	Option		"Protocol"		"auto-dev"
#	Option		"HorizScrollDelta"	"0"
#EndSection

this however caused a horrible X failure so I had to put it back.

* as well as `sudo /etc/init.d/powernowd stop'

Any ideas from anyone would be appreciated.
I have the lastest version of breezy as of today as I did a netinstall, my hardware is a Dell smartpc 250n with a synaptic touch pad.

Thanks in advance.

Ranulf

---

### Post by xtacocorex on 2005-11-23
I have a Dell Smartstep 250N and the only odd behavior I get is the keyboard will keep typing a letter if I do something wierd (haven't pinpointed exactly what causes it). I think that could be a problem with the 3 month interval heat sink clean schedule I'm on and the fact that the computer is old.

My touchpad works fine now since I got rid of the xserver-xorg-dbg package. No random clicks. I do know that if I hold the shift and/or control key while clicking with my external mouse, I can get it to spaz out, but I deem that my fault and not the hardware.

I don't use powernowd as it seemed really slow. I use cpufreqd instead. I can't really comment on battery life difference between the two daemons since my battery is shot anyway and doesn't last longer than 45 minutes.

I've never tried the netinstall, so I don't know how well that works, but I have everything working with a clean install from the cd. 

I hope this helps some, sorry for not having any solutions.

---

