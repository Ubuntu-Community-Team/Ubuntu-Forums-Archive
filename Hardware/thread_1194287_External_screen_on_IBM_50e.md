---
title: "External screen on IBM 50e"
date: 2009-06-22
forum: Hardware
---

### Post by jsjohnsen on 2009-06-22
Hi all

I am a bit new in the Linux business, and I am having a lot of fun, but I do have a small problem.

I am using an old IBM R50e laptop to run ubuntu 9.04 together with my Samsung Syncmaster 193T.
But I can not get the resolution on my samsung above 1024x768.

When I enable 1280x1024 in System->Preferences->Display I get a view corresponding to 1024x768 pixels, where the picture is all messed up, if I try interacting with the GUI, all the menu's and etc. are positioned corresponding to 1280x1024 but the graphics is not (it is ver strange).

If I use grandr I can get the resolution of 1280x1024 to work but it is only the first 1024x768 that is actually shown on my screen, but the mouse curser is working on the entire screen, but half of the screen is just black ??

Can you please help me, because I really need the extra pixels, when I am doing my homework.

Best Regards
jsjohnsen - Denmark

---

### Post by jsjohnsen on 2009-06-23
Ok here is som news...
I added some lines in xorg.conf, and restarted the PC, then I got a window saying:
ubuntu is running in low-graphics mode ... (EE) No devices detected
I stated that I wanted to start ubuntu in low graphics mode, and quess what, Ubuntu booted in 1280x1024.

If I go to System->preference->display
my display is unknown, and me refresh rate i 0Hz, but it is working.
and this is what is shown in xrandr:
Screen 0: minimum 640 x 480, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024       0.0* 
   1024x768        0.0  
   800x600         0.0  
   640x480         0.0 

My xorg.conf contains the following:

#comments...
Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
#  BoardName    "855 GM"
#  Option       "NoDDC"
#  Screen       0
#  Option       "Rotate" "CW"
#  VendorName   "Intel"
EndSection


Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

(I added Device section)

But it is working, any suggestions on how to make it work in not low-graphics mode?

---

