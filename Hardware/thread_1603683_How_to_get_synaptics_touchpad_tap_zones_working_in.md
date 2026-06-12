---
title: "How to get synaptics touchpad tap zones working in 10.04 LTS Lucid"
date: 2010-10-23
forum: Hardware
---

### Post by Gary_inNYC on 2010-10-23
Honestly, setting this up is tedious compared to other OSes, and it's an example of how Ubuntu can be further improved.  But enough of the rant.  Here's how to get tap zones working in Lucid LTS.

Some assumptions:  
1) you're using Lucid LTS 10.04
2) you're not using an xorg.conf file
3) you've read through the synclient manual and are still confused

I don't use the old xorg.conf file because I don't like shooting myself in the foot.  Instead, I use configuration snippets located in:
/usr/lib/X11/xorg.conf.d

There, you can add your own custom configurations without affecting other things in your system, like what can happen if you somehow mess up xorg.conf.  Sure, you can back up xorg.conf (and it is essential if you do use this, and are tweaking it), but it's better people don't put themselves in a position where they have to use this back up to begin with.  My system HAS NO xorg.conf and I'd like to keep it that way.  I wish Ubuntu would just provide GUI configuration tools that has all configurable options, which sadly, the built in Mouse Config tool in System/Preferences/Mouse does not.  This is why you're here reading about tap zones.  

While tweaking config files in the xorg.conf.d directory in Lucid, particularly the 10-synaptics.conf file, look for this part:

Section "InputClass"
	Identifier "touchpad catchall"
	MatchIsTouchpad "on"
	MatchDevicePath "/dev/input/event*"
	Driver "synaptics"
EndSection

====================

There, you can add your own synclient instructions, structured in the form of "Options" and their corresponding number assignments which tells the driver how to interpret your actions.

Since we're configuring Tap Zones, we're only interested in a few Options.  Particularly, they are the zones themselves, and their number assignments.

The zones are:

RTCornerButton is the (R)ight (T)op corner
RBCornerButton the (r)ight (b)ottom
LTCornerButton the left top
LBCornerButton the left bottom

The number assignments for those options are defined as follows:

1=leftclick
2=middleclick
3=rightclick
4=scrolldown
5=scrollup
6&7=horizontal scrolling (not needed when using two finger scrolling), 8=navback
9=navforward

========================

Editing the 10-synaptics.conf file, you merely "Options" and assign your desired number for that option.  So for our tap zones we can do something like:

Section "InputClass"
	Identifier "touchpad catchall"
	MatchIsTouchpad "on"
	MatchDevicePath "/dev/input/event*"
	Driver "synaptics"
	Option "RTCornerButton" "3"
	Option "RBCornerButton" "9"
	Option "LBCornerButton" "8"
	Option "LTCornerButton" "2"
EndSection

============================

The added options I added says that right top is now my right-click action.  Left top will be my middle click.  Left Bottom will navigate back, while Right Bottom will navigate forward.  

Read the synclient manual for more available options.

Save your changes, and either restart X or reboot.

===========================

To check your current synclient settings, to go terminal and:

synclient -l

which will list all current assigned options.

---

