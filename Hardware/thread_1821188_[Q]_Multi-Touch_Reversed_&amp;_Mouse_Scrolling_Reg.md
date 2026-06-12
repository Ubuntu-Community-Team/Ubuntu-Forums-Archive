---
title: "[Q] Multi-Touch Reversed &amp; Mouse Scrolling Regular Combination?"
date: 2011-08-08
forum: Hardware
---

### Post by Paschalis89 on 2011-08-08
Hello. Sorry if i posted in a wrong section.
I m kinda noobie in linux and in this forum.

I was messing up with the scrolling..

What i want, is to have, Reversed(Natural) Scrolling in Two-Fingers Touch in touchpad, and with the Mouse-Wheel, i want the Regular Scroll(Not the reversed).

I use these scripts.

**[SIZE="3"][COLOR="Red"]1st[/COLOR][/SIZE]**
```

#!/bin/sh
#
# Use xinput --list-props "SynPS/2 Synaptics TouchPad" to extract data
#

# Set multi-touch emulation parameters
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Pressure" 32 10
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Width" 32 8
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Two-Finger Scrolling" 8 1
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Two-Finger Scrolling" 8 1 1

# Disable edge scrolling
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Edge Scrolling" 8 0 0 0 

# This will make cursor not to jump if you have two fingers on the touchpad and you list one
# (which you usually do after two-finger scrolling)
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor Threshold" 32 110
```

**[SIZE="3"][COLOR="Red"]2nd[/COLOR][/SIZE]**
and the trick with .Xmodmap with in it:
```
pointer = 1 2 3 5 4 6 7 8 9 10 11 12
```


First, gives me TwoFinger Scrolling, and in combination with Second, it gives me it, reversed! Also the MouseWheel is reversed, which i dont want.
I want only the mouse wheel to be regular!

Any way, to change this?
Thank you! :P

---

### Post by Paschalis89 on 2011-08-09
bumping my thread.. :confused:

any help would be greatly appreciated..

Come on guys, i will give you some pop corn: :popcorn: :D

:popcorn::popcorn::popcorn::popcorn::popcorn:

---

