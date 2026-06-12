---
title: "nv/nvidia driver problems w/ HP laptop"
date: 2008-11-05
forum: Hardware
---

### Post by dgavenda on 2008-11-05
Laptop: HP dv2500t
Video card: nVidia Corporation GeForce 8400M GS (rev a1) 

Problem: whenever I use the 'nvidia' driver instead of the 'nv' driver, it's almost as if it ignore xorg.conf.   Resolutions are really big (eg 640x480) and next to useless.  


I would like to kick video to an Acer 1916w flatpanel thru VGA and eventually kick video thru the HDMI out to a Sony HD tv.  

The problem is if I use the nv driver, it works but as far as I understand it's not the better driver.  I have seen some lag and I can't get the proper resolution on the Sony tv.  

So, I have been experimenting w/ the nvidia driver.  This is where the problems start and aggravation kicks in.   

Can someone explain the difference between the two drivers and how I can use the nvidia driver?

---

### Post by Tamlynmac on 2008-11-05
If your using 8.1 you might read this:
Hope it helps.

[http://albertomilone.com/wordpress/?p=294](http://albertomilone.com/wordpress/?p=294)

---

### Post by dgavenda on 2008-11-06
Tamlynmac,

Ok...I'll play with the different driver but just to be clear....I should be using the nvidia driver and NOT the nv driver right?  

For example, in my xorg.conf it should read:

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"GeForce 8400M GS "
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
	Option		"NoLogo"	"True"
EndSection

and not:

Section "Device"
	Identifier	"Failsafe Device"
	Boardname	"GeForce 8400M GS "
	Busid		"PCI:1:0:0"
	Driver		"nv"
	Screen	0
	Option		"NoLogo"	"True"
EndSection


Correct?  How do I confirm which driver I am using?  Thru which one is installed thru synaptic/apt-get?

---

### Post by dgavenda on 2008-11-07
Also, whenever I run Nvidia X Server Settings, it states: 

You do not appear to be using the NVIDIA X Driver.  Please edit your X Configuration file (just run 'nvidia-config' as root), and restart the X server.

This does nothing.  I was able to use this on a laptop at work (Dell 620) which uses the nvidia driver in the xorg.conf.

---

### Post by Tamlynmac on 2008-11-07
Think you'll find more answers here:

[http://ubuntuforums.org/showthread.php?t=968405](http://ubuntuforums.org/showthread.php?t=968405)

---

