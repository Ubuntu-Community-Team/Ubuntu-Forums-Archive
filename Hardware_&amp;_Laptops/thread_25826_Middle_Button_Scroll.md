---
title: "Middle Button Scroll"
date: 2005-04-11
forum: Hardware &amp; Laptops
---

### Post by benplaut on 2005-04-11
the title says it all (mostly)...

i have a Thinkpad T40, and want to be able to use the middle trackpoint button as a scroll button. any suggestions? :-|

---

### Post by Pierre T on 2005-04-11
I have a thinkpad t41p with middle trackpoint button as a scroll button. I have patch my kernel (2.6.11.7) to do this. This patch work perfectly ([http://people.clarkson.edu/~evanchsa/software/kernel/patches/trackpoint-2.6.11-rc3.patch-1)](http://people.clarkson.edu/~evanchsa/software/kernel/patches/trackpoint-2.6.11-rc3.patch-1)).

   $ cp trackpoint-2.6.11-rc3.patch-1 /usr/src/linux/
   $ cd /usr/src/linux/
   $ patch -p1 <trackpoint-2.6.11-rc3.patch-1

... and rebuild the kernel

---

### Post by jmcvey on 2005-04-11
I have a R50p (1832-22U) and had the same issue. I saw a posting somewhere (can't remember the link at the moment), but basically you needed to add the last two lines under the mouse section of the xorg.conf file. Here's the snippet of that file that I run. Once you do that and restart X the middle scroll works fine and no kernel patching is needed.

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
	Option		"EmulateWheel"		"true"   <== add this line
	Option		"EmulateWheelButton"	"2"   <== add this line
EndSection

Jer

---

### Post by benplaut on 2005-04-12
[QUOTE=jmcvey]I have a R50p (1832-22U) and had the same issue. I saw a posting somewhere (can't remember the link at the moment), but basically you needed to add the last two lines under the mouse section of the xorg.conf file. Here's the snippet of that file that I run. Once you do that and restart X the middle scroll works fine and no kernel patching is needed.

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "Emulate3Buttons"    "true"
    Option        "ZAxisMapping"        "4 5"
    Option        "EmulateWheel"        "true" <== add this line
    Option        "EmulateWheelButton"    "2" <== add this line
EndSection

Jer[/QUOTE]

thanks! works like a charm \\:D/

---

### Post by ernestoongaro on 2005-04-26
Works really good for me too on a Thinkpad 600x  - Thanks for the post, probably would of tried to recompile kernel : ( if u had not!

---

### Post by bpilgrim1979 on 2005-07-09
This worked for me too, although I don't see the pretty scroll cursor icon that I do in Windows.  It stays an arrow.

HOWEVER, the xorg.conf file says the following

```

# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg


``` 


Be VERY careful if you follow this advice.  I did and I was taken through Linux hardware configuration nightmare.  This is exactly what I want to avoid with Ubuntu.  :)

I accepted all the defaults and then finally just copied the original xorg.conf file back (plus the two additional lines) and rebooted.  I got some conflict message and a backed up xorg.conf and just restored my own backup.  I think everything's the same.  

Don't run dpkg-reconfigure xserver-xorg unless you really know what you're doing!!!   ](*,)

---

### Post by shizow on 2005-07-22
[QUOTE=jmcvey]I have a R50p (1832-22U) and had the same issue. I saw a posting somewhere (can't remember the link at the moment), but basically you needed to add the last two lines under the mouse section of the xorg.conf file. Here's the snippet of that file that I run. Once you do that and restart X the middle scroll works fine and no kernel patching is needed.

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
	Option		"EmulateWheel"		"true"   <== add this line
	Option		"EmulateWheelButton"	"2"   <== add this line
EndSection

Jer[/QUOTE]


this works but then the middle button is not working as PASTE anymore
any suggestions

---

### Post by mlambie on 2005-08-12
The paste functionality has been removed for me also, and whilst I love scrolling, I can't live without paste. Can they both play together?

---

### Post by transactionlogfiller on 2005-08-14
It seems you can get the middle button paste effect by pressing buttons 1 and 3 simultaneously. 

I'm still looking into making the middle button click and scroll.

---

### Post by shizow on 2005-08-25
[QUOTE=jmcvey]I have a R50p (1832-22U) and had the same issue. I saw a posting somewhere (can't remember the link at the moment), but basically you needed to add the last two lines under the mouse section of the xorg.conf file. Here's the snippet of that file that I run. Once you do that and restart X the middle scroll works fine and no kernel patching is needed.

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
	Option		"EmulateWheel"		"true"   <== add this line
	Option		"EmulateWheelButton"	"2"   <== add this line
EndSection

Jer[/QUOTE]


if you do this you get the scrolling, but the same time the paste functionality is removed!!

---

### Post by wabble on 2005-08-25
[QUOTE=transactionlogfiller]It seems you can get the middle button paste effect by pressing buttons 1 and 3 simultaneously. 

I'm still looking into making the middle button click and scroll.[/QUOTE]

Ctrl+V not working in linux? On my work computer now and i can't check it, but i have not noticed this on my thinkpad so i think that would work...

---

### Post by shizow on 2005-08-25
[QUOTE=wabble]Ctrl+V not working in linux? On my work computer now and i can't check it, but i have not noticed this on my thinkpad so i think that would work...[/QUOTE]

no we are talking about the paste functionality of the middle button!

---

