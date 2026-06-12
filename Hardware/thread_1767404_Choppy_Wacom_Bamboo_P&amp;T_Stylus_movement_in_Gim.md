---
title: "Choppy Wacom Bamboo P&amp;T Stylus movement in Gimp"
date: 2011-05-25
forum: Hardware
---

### Post by eyedeal on 2011-05-25
Hi,

sorry if this issue has been discussed before here, I wasn't able to find it. 

I'm running Ubuntu 11.04 (AMD64) with the default Wacom driver that comes with it.

I own a Wacom Bamboo P&T CTH-460 (056a:00d6). 

xinput list says:

```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 ALPS GlidePoint                  	id=19	[slave  pointer  (2)]
&#9116;   &#8627; Gaming Mouse                            	id=16	[slave  pointer  (2)]
&#9116;   &#8627; Gaming Mouse                            	id=17	[slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooPT 2FG 4x5 Pen eraser       	id=12	[slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooPT 2FG 4x5 Pen stylus       	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooPT 2FG 4x5 Finger pad       	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Wacom BambooPT 2FG 4x5 Finger touch     	id=15	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=8	[slave  keyboard (3)]
    &#8627; Power Button                            	id=9	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=10	[slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_HD             	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=18	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys
```

There are also two pointing devices, as you can see: the ALPS touchpad, and a Prestigio mouse.

I've got one pressing issue (err... pun intended). The tablet is recognized, and it seems to work for most part. The touch doesn't work correctly which is unimportant to me. However, when I press with my stylus quickly multiple times to draw parallel lines in Gimp, the tablet only draws the lines every second stroke, and ever other stroke is ignored, so to speak.

Here's a video that shows the problem (sorry for bad compression at the beginning, I'm not very experienced with video stuff): [http://www.youtube.com/watch?v=zjrMVu4FwjQ](http://www.youtube.com/watch?v=zjrMVu4FwjQ)

You can see that on every other stroke the pointer hangs at the top of the stroke. If I do it slowly, it works, but then again, the utility is hugely diminished...

Incidentally, the xsetwacom list shows:

```

Wacom BambooPT 2FG 4x5 Pen eraser	id: 12	type: ERASER    
Wacom BambooPT 2FG 4x5 Pen stylus	id: 13	type: STYLUS    
Wacom BambooPT 2FG 4x5 Finger pad	id: 14	type: PAD       
Wacom BambooPT 2FG 4x5 Finger touch	id: 15	type: TOUCH
```

I used to disable the touch functionality in 10.10, and it worked fine, but this problem happens regardless of whether the touch is disabled or not. Here's the script that I use to disable the touch:

```

#!/bin/bash

TOUCH="Wacom BambooPT 2FG 4x5 Finger touch"
xsetwacom set "${TOUCH}" Touch off
```

Other than this script, I haven't done anything in the way of configuring the tablet (no xorg.conf manipulation, etc).

---

### Post by eyedeal on 2011-05-25
Updated to 0.11 from IRIE ppa, and it's same. Could it be some configuraiton option?

EDIT: It occurred to me. I set the double-click timing to shorter in the **mouse** settings, and the problem disappeared. I'm not sure how the mouse settings can influence the tablet like this, but it seems to work.

---

### Post by xube on 2011-06-22
The same problem here. Any solution? I really want use the GIMP as image editor and drawing app. With another applications there is no any problem (Inkscape, MyPait). But i really want GIMP...

Pressure doesn't work at DrawPile. Just wondering if some one know why.

EDIT: OK, I found out that **problem could be with Compiz or Unity**. *With Ubuntu Classic (no effects) there is no problem* with chopy drawing. There is no need turn off touch pad. I will do more testing tomorow.

---

### Post by xube on 2011-06-22
Allright, for me solution is **disable synchronize with Vblank** in *CompizConfig > OpenGL*

I hope it helps someone.

---

### Post by Pete Mander on 2011-07-10
Yes, it did help me, thanks you.

How did you discover that it was Compiz and VBLANK that was the problem?

Pete.

---

### Post by messie on 2011-07-27
Hey there, sync to Vblank reduced the problem for me too.  It still does it, less often tho. Any more info would be nice to have.

---

### Post by cldx on 2011-08-24
I can confirm this weird bug too for a Bamboo (no Touch) Model CTL-460.

Disabling VBlank seems to help a little, but the Bug persists.

Anyone know if there is some official Bug Report for this?

---

### Post by otaconisme on 2011-09-17
I found out this on another thread. [http://ubuntuforums.org/showthread.php?t=1795819](http://ubuntuforums.org/showthread.php?t=1795819)
It turn out to be unity 3d bug. One method is to disable unity 3d and use other shell, or go to Edit>Preferences>Windows Management in GIMP, and setting both the "Hint for toolbox" and "Hint for other docks" to "Normal window". With this you can turn on VBlank again if you want. I guess this is solved. Now I can happily use wacom bamboo on my ubuntu.:p

---

