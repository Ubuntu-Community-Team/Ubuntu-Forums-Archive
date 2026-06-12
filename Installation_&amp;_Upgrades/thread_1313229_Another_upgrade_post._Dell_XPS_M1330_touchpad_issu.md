---
title: "Another upgrade post. Dell XPS M1330 touchpad issues (scroll) after upgrading to 9.10"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by youngerpants on 2009-11-03
Hi,

Sorry if this is a little long, but I have quite a bit of information already gathered...

n.b. I'm running kernel 2.6.31-14-generic, but have tested everything below with a few previous versions, back to 2.6.27-12

I recently (yesterday) upgraded from 9.04 to 9.10. Everything seems to have gone well except for my touchpad; after the upgrade I've lost its vertical scroll on the right side.

I've done a lot of digging around and have come up with a few inconsistencies as to why this may be;
1) In System> Preferences> Mouse, I'm missing the 3rd tab to configure the touchpad

So, I'm thinking, maybe the touchpad didn't get correctly recognised during the upgrade...
Lets see what dmesg says

2) dmesg | grep synaptics gives nothing, 

dmesg | grep mouse gives

[    0.951901] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.004781] mice: PS/2 mouse device common for all mice

OK, its not getting recognised as a trackpad at all (but still working, which is nice!)
Lets install gsynaptics, wonder if that sees it

3) gsynaptics
euw, error window

GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

Good idea! let me have a look at my xorg.conf in /etc/X11

4) xorg.conf
now this is a bit strange, my xorg.conf is a little... odd...

```

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
	BusID		"PCI:1:0:0"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection

```

I have no input devices mentioned at all???

I would imagine at this stage I should reinstall my touchpad altogether, so I reinstall xserver-org-input-synaptic, and for good measure xserver-org-input-mouse AND xserver-org-input-vmmouse (because I thought, why the hell not), rebooted, and... no change

Running out of ideas here, so if anyone has any ideas they'd be greatly appreciated

---

