---
title: "desktop effects stopped working after todays update"
date: 2008-08-05
forum: General Help
---

### Post by Joey-G on 2008-08-05
i am a new linux user been running now for about 2 weeks

everything been brilliant and i had everything working fine. like videos, music, compiz, wireless 8187b etc etc so i have learnt a fair bit quickly, maybe because i am a young student studying IT at college.

today i was just browsing the net and i noticed an update was due and being abit lazy i didnt really check what was being installed and everything was ok. until i closed the lid of my laptop. hibernate or sleep does not work properly in ubuntu as far as i know of and it froze my system so i had to manually shutdown. i rebooted and i had problems with videos which started to annoy me. i re-installed gnash and re-booted and videos are ok again. and now i have noticed my desktop enhancements are not working.

i have tried to just enable them again but it displays "can not enable desktop effects". This is really annoying because i had everything working fine until this afternoon,

i run ubuntu hardy (i know its not great) and i need some help with this because i dont understand why i having all these problems after an update.


thanks in advance 

joey-G

---

### Post by PmDematagoda on 2008-08-05
Did the problems start to occur after a reboot or just after the updates were installed? Also what are the specifications of your PC?

---

### Post by tuxxy on 2008-08-05
Have you tried re-eanbling the video drivers ?

---

### Post by KenDiPietro on 2008-08-05
I can confirm that the upgrade wiped out my Desktop effects as well as my dock.

After the upgrade I had "issues" but when I rebooted, everything was gone.

I did check prior to posting and my restricted NVidia driver is enabled.

---

### Post by Squonk07 on 2008-08-05
> **KenDiPietro said:**
> I can confirm that the upgrade wiped out my Desktop effects as well as my dock.

After the upgrade I had "issues" but when I rebooted, everything was gone.

I did check prior to posting and my restricted NVidia driver is enabled.

Same here.  The upgrade yesterday made keyboard input impossible on my login screen.  After installing today's updates, this issue went away but left my previously-detected graphics card (Intel 945GM), well, undetected.  However, for me the Hardware Drivers window shows no proprietary drivers in use, though according to Synaptic these drivers appear to be installed.

At this point I think I'll sit tight and wait another week for Alpha 4 and just do a clean install from there.

UPDATE: Scratch all that.  A little fiddling with the X.org file solved my trouble.  It seems a workaround I used to try to get around the text input issue was throwing everything off.  Plus, come to think of it, I'm not sure the Intel drivers are restricted.  Everything is working fine now and they still don't show up in the Hardware Drivers list.

---

### Post by Joey-G on 2008-08-05
yo man

what did you do to fix the problem?

i just checking for the NVidia restricted driver from the other guy's post hopefully it will solve it...

update: i unabled NVidia and i still cant get the desktop effects working...what was in that update to screw this all up anyway?

any help would be appreciated....

---

### Post by Squonk07 on 2008-08-05
> **Joey-G said:**
> yo man

what did you do to fix the problem?

i just checking for the NVidia restricted driver from the other guy's post hopefully it will solve it...

update: i unabled NVidia and i still cant get the desktop effects working...what was in that update to screw this all up anyway?

any help would be appreciated....

I'm not sure what finally fixed it, except that I think those extra lines I appended to my Xorg file were what were causing the trouble.  I just put it back to the way it was before the updates, and everything was good.  After the latest updates, there was a new Xorg file there in place of the original one.  There were also several others, and one of those was my original one.  I just swapped out the "new" one for my original one, and this fixed everything.

Check your X11 folder (/etc/X11) for multiple versions of Xorg (they should have a dot and a number after them).  Try making each one of them the default by renaming all the others and leaving the one you want to test as xorg.conf.  You'll have to use the gksudo hack to open Nautilus (open a Terminal and type gksudo nautilus--it will ask you for your password), otherwise you can read entries but not save any changes.

Keep in mind that I'm pretty new to Linux, and maybe somebody with a lot more experience will be able to help you better or else point out serious flaws with what I've said here.  Also, I'm using the Intrepid Ibex alpha, which might make my issue different.  Proceed at your own risk.

---

### Post by Joey-G on 2008-08-05
right i have a toshiba satiellite equium A200-1VO laptop and its perfect for what i need it for. 

1.46Ghz intel pentium dual core
2gb Ram
120GB hardrive
INTEL GMA X3100 graphics card


had the desktop enhancements working fine up until after i rebooted after the update and now it wont enable the desktop enhancements which is annoying me. its like going through <snip> vista all over again. everything works and an update screws the system. running ubuntu hardy(awful) if you didnt know.

any help?

---

### Post by SpenceMakesSense on 2008-08-05
> **Joey-G said:**
>  its like going through F***ing vista all over again. everything works and an update screws the system. running ubuntu hardy(awful) if you didnt know.

any help?

Wow comparing ubuntu to vista AND saying hardy is awful. Well..anyway. One thing that helped me was completely redoing my xorg file. Being a not so experienced linux user I cant exactly say how to do this or if this will even help. But thats what forums are for ;)

---

### Post by Joey-G on 2008-08-06
right.... i tried compiz check and compiz into the terminal and here is what i have got:

```
 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

```

then i did "compiz" into the terminal and i got this:

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2a02 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 


```

i have Xgl installed and Nvidia could be installed aswell but nothing seems to be working according to compiz check. here is the Xorg.config file aswell..........really need some help now it is greatly appreciated..

```
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
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection
```

thanks in advance..

---

