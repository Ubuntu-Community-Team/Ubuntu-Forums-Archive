---
title: "resolution problem with nvidia driver 185"
date: 2009-12-15
forum: Hardware
---

### Post by cailamaia on 2009-12-15
Hi everyone,

I'm still a relative newb, so please excuse any stupidities I might utter in this post. ^^;

I just installed 9.10, 64-bit Karmic, about two weeks ago. Updated with the manager, and then today I decided I was tired of having the computer lag trying to render my favourite screensaver, so I installed the restricted drivers for my nvidia GEForce8600M. The recommended version (185) installed just fine, with no errors, but on reboot, my screen resolution was all weird. My background is all stretched, out and there's a nice big black section off to the right of my desktop. I can open the nvidia xserver config GUI and set a number of different resolutions (all 4:3, and below my monitor's native 1440x900 resolution), but when I try to set the 1440x900 resolution, all I get is a black screen. I can get to the tty, but I don't know enough command line to do anything useful once I get there.

I've done a little googling to see if anyone else had the same problem, but have not found anything that helped me resolve this. Included is a screenshot, and a copy of my xorg.conf file. Any help would be much appreciated!!

(I don't know how to add the little text box in my post, either. Sorry if this gets a little long.)


my xorg.conf file:

Section "Screen"
	Identifier	"Configured Screen Device"
	Device	"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Virtual	2565 900
	EndSubSection
EndSection

Section "Module"
	Load	"glx"
	Disable	"dri2"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
EndSection

---

### Post by mikewhatever on 2009-12-16
You could try changing the resolution with nvidia-settings tool, but since you get a black screen, take a look at the following line in xorg.conf:
```
Virtual 2565 900
```

Perhaps changing it to 1440 900 will make things work. On the other hand, I am not quite sure you need xorg.conf at all, so try renaming it, then log out and login.

---

