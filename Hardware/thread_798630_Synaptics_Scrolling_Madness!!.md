---
title: "Synaptics Scrolling Madness!!"
date: 2008-05-18
forum: Hardware
---

### Post by eOgas on 2008-05-18
So I just upgraded to Hardy and for some reason the scrolling on my touchpad is all messed up.  Vertical scroll is recognized, as in the mouse pointer doesn't go anywhere when I try to scroll, but nothing happens as far as scrolling.  When I try to scroll horizontally, it scrolls vertically.  I installed gsynaptics to no avail.  It seems like no matter what I do, horizontal scroll *always*scrolls vertically.  Here is the relevant part of my xorg.conf file:

```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection
```

This is just what gsynaptics gave me by default.  I messed around with the different options to my heart's content, but nothing seemed to do the trick.  Any ideas?

---

### Post by nicedude on 2008-05-18
Try installing gsynaptic touchpad manager and see if it works to control your touchpad better. You will need to add a line to your synaptic section in xorg.conf file but you seem to know how to do that so you should have no problems. The first time you run gsynaptic it will tell you the line to add in an error message :-)

Good luck

nicedude

---

### Post by prshah on 2008-05-18
> **eOgas said:**
> 
```

	Option		"HorizEdgeScroll"	"0"

```


Looks like that option needs to be "1" (0=false; 1=true).

---

### Post by eOgas on 2008-05-19
Thanks for the help guys but nothing seems to be working.  In fact, changed it to a one and nothing happened.  I installed gsynaptics, again, added the line, and nothing happened.  It's as if it's totally ignoring everything I do.  The weird thing is that when I go into gsynaptics and disable the horizontal and vertical scroll, it stops scrolling.  When I reenable them, the horizontal scroll scrolls vertically and the vertical scroll seems to capture the mouse, but doesn't scroll anything.  Pfft.  What's up with this man?

This sucks.  It worked fine on Gutsy, I don't see why it shouldn't work on Hardy.  My brightness keys don't work correctly now either, but I can make a separate post for that.  Any more ideas are gladly welcomed.

---

### Post by prshah on 2008-05-19
> **prshah said:**
> Looks like that option needs to be "1" (0=false; 1=true).

OK, try:```

Option		"HorizEdgeScroll"	"true"
```

---

### Post by eOgas on 2008-05-19
> **prshah said:**
> OK, try:```

Option		"HorizEdgeScroll"	"true"
```

Nope, same story.  Actually, the story changed a little bit.  It turns out that the whole time, scrolling vertically actually did a horizontal scroll.  In essence, it's backwards.  Which sucks.  Any ideas to fix this?

---

### Post by prshah on 2008-05-19
> **eOgas said:**
> Nope, same story.  Actually, the story changed a little bit.  It turns out that the whole time, scrolling vertically actually did a horizontal scroll.  In essence, it's backwards.  Which sucks.  Any ideas to fix this?

Suggestion only: Not tried by me, so can't comment on it's usefulness. It's for wacom, but...
Install wacom-tools, then use the xsetwacom command:```
sudo apt-get install wacom-tools
xsetwacom set stylus rotate x
```

Where "x" is 0,1,2,3: as suitable for you.

Hope it helps.

---

### Post by eOgas on 2008-05-20
Yeah, it doesn't look like that's gonna work.  It's telling be that I don't have a device named 'stylus', probably because I don't have a wacom tablet.

If anyone has any other ideas it would be greatly appreciated.  I have found another thread on the same problem, but didn't seem to have anything useful in it.

---

### Post by eOgas on 2008-05-21
bump

---

