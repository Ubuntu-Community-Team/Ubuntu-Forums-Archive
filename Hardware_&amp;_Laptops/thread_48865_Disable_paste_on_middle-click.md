---
title: "Disable paste on middle-click"
date: 2005-07-14
forum: Hardware &amp; Laptops
---

### Post by j0e on 2005-07-14
Hi folks,

Just joined the forum having installed Ubuntu on my new laptop - painlessly I must add!

Anyway, I'm using the touchpad (Synaptic) and whenever I 'tap' the pad, I get a middle-click - I'm not sure it's supposed to be doing this though, as I've heard there can be some issues with the touchpad on this laptop (HP dv1265ea).

I don't have a problem with the middle-clicking really, but it's really annoying when I accidentally middle click and have masses of text pasted into whatever I'm working on!

Is there a way to turn off this feature? I can see the obvious advantages when using a mouse, but not with the touchpad.

Thanks for any help and congratulations to the Ubuntu team/community. :-)

---

### Post by badrinarayan on 2005-07-14
Try disabling tapping altogether with [FONT=Courier New]MaxTapTime=0[/FONT] if you so wish.

I guess the problem could be with the configuration of left edge, right edge etc.,
If you tap in the top right corner, synaptics could middle click in certain configurations. With wrong dimensions, this could happen everywhere. Or may be you have an ALPS touchpad.

Anyway, you may try this:

```
  Identifier  	"Synaptics Mouse"
  Driver  	"synaptics"
  Option 	"Device"  	"/dev/psaux"
  Option	"Protocol"	"auto-dev"
  Option	"LeftEdge"      "1700"
  Option	"RightEdge"     "5300"
  Option	"TopEdge"       "1700"
  Option	"BottomEdge"    "4200"
  Option	"FingerLow"	"25"
  Option	"FingerHigh"	"30"
  Option	"MaxTapTime"	"180"
  Option	"MaxTapMove"	"220"
  Option	"VertScrollDelta" "100"
  Option	"MinSpeed"	"0.09"
  Option	"MaxSpeed"	"0.18"
  Option	"AccelFactor"	"0.0015"
  Option	"SHMConfig"	"on"
#  Option	"Repeater"	"/dev/ps2mouse"
```

which I got from [http://www.codexinteractive.com/cwt/dv1000/xorg.conf.cwt](http://www.codexinteractive.com/cwt/dv1000/xorg.conf.cwt)
I don't have access to dv1265ea and can't be sure!

Regards
Badri

---

### Post by j0e on 2005-07-15
[QUOTE=badrinarayan]Try disabling tapping altogether with [FONT=Courier New]MaxTapTime=0[/FONT] if you so wish.

I guess the problem could be with the configuration of left edge, right edge etc.,
If you tap in the top right corner, synaptics could middle click in certain configurations. With wrong dimensions, this could happen everywhere. Or may be you have an ALPS touchpad.

Anyway, you may try this:

```
  Identifier  	"Synaptics Mouse"
  Driver  	"synaptics"
  Option 	"Device"  	"/dev/psaux"
  Option	"Protocol"	"auto-dev"
  Option	"LeftEdge"      "1700"
  Option	"RightEdge"     "5300"
  Option	"TopEdge"       "1700"
  Option	"BottomEdge"    "4200"
  Option	"FingerLow"	"25"
  Option	"FingerHigh"	"30"
  Option	"MaxTapTime"	"180"
  Option	"MaxTapMove"	"220"
  Option	"VertScrollDelta" "100"
  Option	"MinSpeed"	"0.09"
  Option	"MaxSpeed"	"0.18"
  Option	"AccelFactor"	"0.0015"
  Option	"SHMConfig"	"on"
#  Option	"Repeater"	"/dev/ps2mouse"
```

which I got from [http://www.codexinteractive.com/cwt/dv1000/xorg.conf.cwt](http://www.codexinteractive.com/cwt/dv1000/xorg.conf.cwt)
I don't have access to dv1265ea and can't be sure!

Regards
Badri[/QUOTE]
 Cheers Badri.

It doesn't seem to have disabled tap-to-click but it now seems to associate it with left-click rather than middle-click, so that's fine for me. :-)

---

### Post by badrinarayan on 2005-07-15
Joe, 

The code snippet does not disable tapping. It only provides right values for your touchpad. If you do want to disable tapping too, it is possible. Just change MaxTapTime from 180 to 0.

Regards
Badri

---

