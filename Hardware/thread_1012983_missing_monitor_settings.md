---
title: "missing monitor settings"
date: 2008-12-16
forum: Hardware
---

### Post by AuronGrande on 2008-12-16
I reinstalled Ubuntu 8.10 and after installing and removing programs to meet my needs, as well as updating some, everything was working fine, for the most part.

fglrx for ATI installed without a problem, I could alter the resolution and refresh rates through System->Preferences->Screen Resolution. The monitor was also detected without that program/settings part.

However, for some reason, that is no longer the case. For some reason the monitor is no longer detected, and the refresh rate is fixed at 60Hz.

Upon looking at the xorg.conf file, the results is this;

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
	Driver	"fglrx"
EndSection

I cannot alter the refresh rate in the Catalyst Control Centre provided by the fglrx drivers.

---

### Post by AuronGrande on 2008-12-17
I am an absolute beginner at Linux and I need the higher refresh rate of 75hz as I keep getting headaches.

---

### Post by rkrash3423 on 2008-12-17
These kind of things are annoying me as well. Apparently they use a new method for detecting displays and resolutions. I have yet to figure out how to get my second monitor set up correctly. It has a native resolution of 1366x768. I am using the root account right now cause toying with resolution settings led to not being able to log into my account. Previously I was able to just add that resolution to gconf. Now I have no idea how to get that res. It won't detect the monitor properly, and all I could find in the forums on this problem were talking about mode lines and entering the monitor specs, etc. What a pain!

Second - In compiz they moved the opacity settings from general settings to brightness and saturation settings. Now none of my desktop is transparent how I want it. I transfered my settings over to the new area but it doesn't work.

Anyone one from ubuntu hear the old term "IF IT AIN'T BROKE...DON'T FIX IT?"

---

### Post by bgerlich on 2008-12-17
You can still use static xorg.conf if you need to. Just type "sudo Xorg -configure". It will create xorg.conf.new with static configuration, that you can edit and when you are happy with results replace your old xorg.conf with it.

---

### Post by rkrash3423 on 2008-12-17
Yeah actually I meant xorg not gconf in my first post. Thanks for the tip.

---

### Post by iponeverything on 2008-12-17
removed

---

### Post by AuronGrande on 2008-12-17
I don't even know how to alter the xorg.conf file. Sure, I can view the darn thing, but I don't know how to make alterations to suit my needs.

---

### Post by bgerlich on 2008-12-17
That's why the forums are here, post your new xorg.conf and say what result you'd like to achieve.

---

### Post by AuronGrande on 2008-12-22
I ended up reinstalling ubuntu because for some odd reason, the screen kept going blank as though the screen has gone into power saving or as though I turned the thing off myself before coming back on about 2 seconds later.

Well, I found something interesting out on the re-installation. The monitor was detected by gnome in the System->Preferences->Screen Resolution settings. I had uninstalled nothing, only installed and updated a few programs. I'll provide a list of what I installed in a moment.

Everything was going fine. The settings were holding for several fresh boot-ups and several restarts without any alterations to settings. Then suddenly, after a restart, the monitor was no longer detected, losing the refresh rate that I need.

The programs that I installed were;
Videolan
MPlayer
ubuntu-restricted-extras
Thunderbird (for some reasons this isn't installed by default like Firefox)
Kate
fglrx
Mirage
Filezilla
GoogleEarth
Knode
Pan
Opera
k3b
Wine

Programs that were updated;
OpenOffice
Firefox
several small features that I cannot remember but to do with networking, plugging a few security holes, etc

Just a thought. Is it possible that fglrx and my Radeon X1950 Pro card are not truly working in Ubuntu, which is causing the problems with missing settings in the Screen Resolution program?

---

