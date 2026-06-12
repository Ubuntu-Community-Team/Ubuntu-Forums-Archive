---
title: "two-finger scroll gesture after screen rotation."
date: 2010-10-23
forum: Hardware
---

### Post by luisito on 2010-10-23
Today I discover to my surprise that some two finger gestures were working on my Thinkpad X201 with ubuntu 10.10 when I accidentally triggered a right click with my fingers.

The zoom and scroll gestures also work, although they are not too smooth yet. One thing that is not perfect is that after I rotate the screen, the scroll gesture does not adjust well and scrolls sideways.

I use the following script to rotate the screen, that I found somewhere online.
```

#!/bin/sh 

# Find the line in "xrandr -q --verbose" output that contains current screen orientation and "strip" out current orientation. 

rotation="$(xrandr -q --verbose | grep 'connected' | egrep -o  '\) (normal|left|inverted|right) \(' | egrep -o '(normal|left|inverted|right)')" 

# Using current screen orientation proceed to rotate screen and input tools. 

case "$rotation" in 
    normal) 
#    -rotate to the right 
    xrandr -o right 
    xsetwacom set "Serial Wacom Tablet"  Rotate  CW 
    xsetwacom set "Serial Wacom Tablet touch" Rotate CW 
    xsetwacom set "Serial Wacom Tablet eraser" Rotate CW  
    ;; 
    right) 
#    -rotate to normal 
    xrandr -o normal 
    xsetwacom set "Serial Wacom Tablet" Rotate NONE 
    xsetwacom set "Serial Wacom Tablet touch" Rotate NONE 
    xsetwacom set "Serial Wacom Tablet eraser" Rotate NONE 
    ;; 
esac

```

The clicks with the touchscreen are correctly mapped by the Rotate command with xsetwacom, but the scroll gesture is not. Does anyone know if there is any way to solve it?

The sad fact is that the scroll gesture would be really useful only when the screen is folded and rotated.

---

### Post by Favux on 2010-10-23
Hi luisito,

If you are using the default Lucid xf86-input-wacom 0.10.5 most likely you want to update it to 0.10.8+.  See step II. at the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").

Also if you still have the default then touch probably isn't on the wacom driver.  I don't believe 0.10.5 supported gestures yet.  So your touch is probably on the Synaptic touchpad driver or evdev driver, which is why it isn't rotating.  Does single finger touch rotate?  You seem to be saying it does.

---

### Post by luisito on 2010-10-23
No. I am using 10.10, not Lucid. My wacom driver is indeed 0.10.8 and I'm pretty sure the gestures come from the wacom driver because if I run the command xsetwacom list param "Serial Wacom Tablet touch TOUCH" |grep gesture I get
```

Gesture          - Turns on/off multi-touch gesture events (default is enable/on). 
ZoomDistance     - Minimum distance for a zoom gesture (default is 50). 
ScrollDistance   - Minimum motion before sending a scroll gesture (default is 20).

```

---

### Post by Favux on 2010-10-23
OK, then with 0.10.8 in Maverick you do have gestures.

I suppose it is possible you've uncovered a bug.  Most folks with wacom 2FG touch/gestures in Maverick are using the Bamboo Pen & Touch, not a tablet pc.

Is your video chipset Intel with an Xorg driver?

---

### Post by luisito on 2010-10-23
Of course I do have gestures. More precisely I have the following three: zoom, scroll and right click. It is possible that it may be a bug. The feature is fairly recent. In that case, I hope it gets resolved in future versions of the wacom driver.

My video is Intel with Xorg driver, yes.

---

### Post by Favux on 2010-10-23
> My video is Intel with Xorg driver, yes. 
I haven't heard of a problem with rotation with the Intel driver.  It is sounding like a bug.  It may explain some problems that lefties were having rotating their Bamboo tablet.  Stylus and eraser are good, correct?  Only touch is off?  I don't know if having touch in Absolute or Relative mode makes a difference.  Can you check which you have set?  See 'man xsetwacom'.

---

### Post by luisito on 2010-10-24
The mode of my touch is absolute.

In case I didn't make it completely clear already, after the rotation, the clicks with the touch, pen or eraser are all positioned perfectly well. The right click gesture (of the touch) also works perfectly well rotated. It is the scroll gesture ONLY that gets messed up.

---

### Post by Favux on 2010-10-24
OK, Absolute is standard or default for tablet pc touch.  The Bamboo has touch on Relative mode.  Again don't know if it makes a difference.

Gotcha.  Just wanted to remove any ambiguity.

Saw your bug report.  Nice job.

---

