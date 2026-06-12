---
title: "touchpad problems"
date: 2006-06-20
forum: Hardware &amp; Laptops
---

### Post by halitus87 on 2006-06-20
Hello all

i have been having very stange problems with the touch pad on my toshiba satellite 2400 with ubuntu   as a mouse pointer it works fine on the top of a page if no scrolling is required
but if i scroll down at all the mouse pad scrolls me up automaticaly when i move the cursor at all

this is bad if i want to see anything but the first bit of a web page or want to change anything on tabs which arnt defualt

any ideas?  i would very much like to get this working properly

oh and its not the mouse pad becuase it still works fine in windows which i have set up to dual boot](*,) 

thank you

---

### Post by spier on 2006-06-21
Not sure I understood your problem, but it could be your touchpad settings. It would help if you'd tell us how it is configured, i.e. posting the "Synaptics Touchpad" InputDevice section in /etc/xorg.conf file.

---

### Post by halitus87 on 2006-06-22
im sorry this will be an anoying question  but how do i do that i cant find an xorg.conf that is in the place u said

thank you for helping

---

### Post by ewinslow on 2006-06-22
[QUOTE=halitus87]im sorry this will be an anoying question  but how do i do that i cant find an xorg.conf that is in the place u said

thank you for helping[/QUOTE]

Should be /etc/X11/xorg.conf

---

### Post by spier on 2006-06-22
[QUOTE=ewinslow]Should be /etc/X11/xorg.conf[/QUOTE]

:oops:

---

### Post by Xamusk on 2006-06-22
I'm having similar problems with my Synaptics (non-Alps) Touchpad.
The xorg.conf entry is almost the same as the one above (it only has SHMConfig of the two custom entries). However, these are the symptoms:

When I click with the separate button (no tapping), usually only the button pressing event is sent. The release event is only sent when I move the cursor.
Sometimes I try to simply move the cursor and the touchpad enables click-and-drag just as if I did a double-tap-and-move, but without doing the double-tapping.
If I use tapping with two or three fingers, then the above symptom is done with middle-button-drag and right-button-drag.
Some times the single-click tap does not work.

This problem drives me nuts ](*,) , as the touchpad keeps clicking when I only want to move the cursor. Most of the time I have to use an USB mouse just to do normal work. The external mouse works perfectly.

---

### Post by Xamusk on 2006-06-22
After a LOT of research, I have managed to get the stuff working right here.
The catch? Change the package. Looks like even though Ubuntu has a "seriouslythistime" string in the version of the xserver-xorg-input-synaptics, they didn't really made it right.

I just downloaded a newer package from the debian testing repositories (found through [http://packages.debian.org]("http://packages.debian.org")) and installed it with **dpkg -i <filename>**

As the driver was already "up" before (synclient did work), now those strange things stopped happening.

---

### Post by halitus87 on 2006-06-23
wow fantastic

although as i am new to linux i am not sure which package to install

also i found this info in the file sugested
but am unsure of what some of it means

**
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection
**

thank you very much everybody

---

### Post by halitus87 on 2006-06-23
oh and i downloaded a what i think is a touchpad package  it was for i386 is that the correct acritecture to use??
when i tried to install it it said i needed to be a superuser ,
why am i not? 

thanks

---

### Post by halitus87 on 2006-06-23
[QUOTE=halitus87]oh and i downloaded a what i think is a touchpad package  it was for i386 is that the correct acritecture to use??
when i tried to install it it said i needed to be a superuser ,
why am i not? 

thanks[/QUOTE]


alrighty i got dpkg to work by puting sudo infront of it but it said that the xfree driver i was trying to install conflicted with the xorg driver  what does this all mean??

thank you all very much for putting up with my problems

---

### Post by Xamusk on 2006-06-23
[QUOTE=halitus87]alrighty i got dpkg to work by puting sudo infront of it but it said that the xfree driver i was trying to install conflicted with the xorg driver  what does this all mean??

thank you all very much for putting up with my problems[/QUOTE]

You probably are installing the wrong package... the right one is xserver-xorg-input-synaptics... you probably got xfree86-driver-synaptics, which is for xfree86 (Ubuntu uses X.org)

[QUOTE=halitus87]oh and i downloaded a what i think is a touchpad package  it was for i386 is that the correct acritecture to use??
when i tried to install it it said i needed to be a superuser ,
why am i not? 

thanks[/QUOTE]

The right architecture depends on what Ubuntu version you have installed. If you have the i386 Ubuntu installed, then you use a package for the i386 arch. If your computer is 64-bits and you installed the amd64 version of ubuntu, then you have to get the package for the amd64 arch.

---

