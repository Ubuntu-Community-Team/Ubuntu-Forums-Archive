---
title: "Desktop effects could not be enabled"
date: 2009-10-22
forum: Hardware
---

### Post by Zach1188 on 2009-10-22
I'm not sure what happened, desktop effects was working after a fresh install of Jaunty (fading windows, etc). All I did before it quit working, is switch to proprietary nVidia drivers (by System > Administration > Hardware Drivers), then attempt to enable "Extra" desktop effects, too see if it was really worthwhile (I don't like eye candy to be real bloated, but figured I may as well check it out). So it said "Desktop effects could not be enabled". So, fine, I thought, as I went to put normal desktop effects back on. Now they will not turn on either, giving the same error. I do have direct rendering, AWN and Docky work great, and glxgears returns >2000fps.

My video card is an nVida EVGA geForce 9400 GT 1GB VRAM, and I am using driver version 180.

Here is my xorg.conf
> 
# <--Some comments I erased

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection



---

### Post by Zach1188 on 2009-10-22
This fixed my problem. Just figured I would post for anyone else who has the same issue.

Edit: Oh, and interestingly enough, now I'm getting about 4700fps on glxgears.

> 
zach@zach-desktop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation D9M-20 [GeForce 9400 GT] (rev a1)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Another compositing manager in use. 

Would you like to know more? (Y/n) y

 The default window manager of GNOME has its own compositing manager to
 provide basic desktop effects.
 If this one is in use, Compiz will not be able to run. 

Do you want to disable GNOME's compositing manager? (Y/n) y


---

