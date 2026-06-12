---
title: "Toshiba Satellite Pro 4600- How do I disable Trackpoint?"
date: 2008-10-03
forum: Hardware
---

### Post by Gohansan on 2008-10-03
And Bear in mind I am a absolute beginner at this whole Linux thing :D

Okay, so the trackpoint on my toshiba has been on the fritz for a few months now, and was driving me nuts until I decided to install a synaptics driver that allowed me to disable it. Now I installed Ubuntu the driver is unuseable, and I can't get the Ubuntu equivalent to boot up (set 'SHMConfig' to 'true', still nothing) so that I can disable it. 

Any Method of fixing this problem is perfectly welcome, as long as it does not involve opening up the machine and cutting any wires. :p

---

### Post by rustybronco on 2008-10-03
Is it because the accu-point mouse tracks on its own?
try disabling dual pointing in bios.

only thing I can offer...

***EDIT***

have a look in /etc/X11/xorg.conf (open terminal>type in... sudo gedit /etc/X11/xorg.conf > then your password) and see if you can disable the accupoint mouse


***MORE*** [http://ftp.x.org/pub/X11R7.0/doc/html/mouse.4.html](http://ftp.x.org/pub/X11R7.0/doc/html/mouse.4.html)

try removing the section "option" that deals with the "CorePointer" save and restart.

---

### Post by Gohansan on 2008-10-04
Unfortunately, none of this advice seem to work for me.Here is my xorg.conf as it is now-
> Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
	Option          "SHMConfig"             "true"
EndSection


---

### Post by Gohansan on 2008-10-04
Okay, For a unrelated reason, I have  had to reconfigure the X server. 
I have reached the point where the mouse must be reconfigured.
If done correctly (ie wrong) I can kill this thing. but what do I choose?

also, bump.

---

### Post by rustybronco on 2008-10-04
You won't kill it. but you may have to type in at a command line...

sudo dpkg-reconfigure -phigh-xserver-xorg

and undo what you changed.

then restart x by hitting ctrl+alt+backspace and then type 'startx' to start it again at a command line if you miffed it up.

***edit*** > If done correctly (ie wrong) I can kill this thing. but what do I choose? I'm not at home right now to look at the options.

***EDIT*** did you try to removing the complete mouse section from the config file?

---

### Post by rustybronco on 2008-10-04
How about a nice working keyboard...

if it's the same as a pro4300 I should have a spare one.

---

### Post by stupidfrog on 2008-11-17
hi!

i have the same "crazy mouse jumping all over that drives me crazy" problem.
i understand how to disable the trackpoint, and i ve done it, but when i restart the computer (toshiba too), it detects "a new device" (that trackpoint mouse) and...reinstalls it automatically..!!
any way how to disable automatic reinstallation? it s under windows XP.

thanks a lot!

---

### Post by SamNSane on 2008-11-18
You have looked in the BIOS setup to see if the trackpoint can be disabled there, haven't you? I had to ask, because I didn't see this possibility mentioned anywhere.

I've been using laptops for as long as they've existed. Most I've used had this option in the BIOS.

---

