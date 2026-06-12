---
title: "Cannot Get Synaptics Scrolling to Work"
date: 2009-06-28
forum: Hardware
---

### Post by ve4cib on 2009-06-28
I've been running 9.04 on my (somewhat old) Toshiba Satellite A70 for the last several months.  Everything is great except for one small nagging problem: I cannot scroll with the trackpad anymore.

The trackpad does not have a manufacturer-created "scroll area", but all previous versions of Ubuntu, dating back to 5.04, have always automagically added a scroll area on the right edge of the trackpad for me right out of the box.  9.04 is the only version that does not do this.

I've played around with xorg.conf and gsynaptics to try to enable scrolling, and nothing has worked.  This is a really annoying issue that I'd like to get resolved ASAP.

Here's the relevant section in xorg.conf:

```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/input/event8"
#	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
#	Option		"HorizTwoFingerScroll"	"true"
	Option		"HorizEdgeScroll"	"true"
#	Option		"BottomEdge"		"5"
#	Option		"SpecialScrollAreaBottom"	"true"
#	Option		"VertTwoFingerScroll"	"true"
	Option		"VertEdgeScroll"	"true"
#	Option		"RightEdge"		"5"
#	Option		"SpecialScrollAreaRight"	"true"
#	Option		"UpDownScrolling"	"true"
#	Option		"LeftRightScrolling"	"true"
	Option		"SHMConfig"		"on"
EndSection

```

As you can see I've added/removed lots of options that I thought may or may not solve the problem.  Every commented-out option in there has been tried at least once, with several combinations tried.  I've also tried dpkg-reconfigure -phigh xserver-xorg and starting from a clean config file, but that didn't work either.

I *think* I probably need to edit the BottomEdge and RightEdge properties and set those values to something sensible, but the documentation on Synaptics is lacking somewhat in that regard.  What is the X coordinate of the right edge of the trackpad?  How do I find that out?

I've tried looking on Google, but any bug reports I've found so far are years old (7.10-era), or simply solve a different issue.  My trackpad works as a simple "move the mouse around" device; scrolling is the only thing that isn't working.

Anyone have any advice?  Thanks a lot for the help!

---

### Post by AoSteve on 2009-06-28
I could be wrong, but I believe you have to set the scrolling area dimensions up to a certain size for it to work correctly.  I can't remember how it works.   

I know a friend of mine said it was all done in the xorg file as he had a similar laptop to mine (which my dad has camping right now... or I'd look on it for you).    His laptop wouldn't scroll with 8.04 or 9.04.  I can't remember what exactly he told me though but he said he found it on the xorg website!


I will look tomorrow when my dad brings my laptop back up here.  I never had to mess with it in 9.04!   It worked out of the box and it's a Toshiba L45

---

