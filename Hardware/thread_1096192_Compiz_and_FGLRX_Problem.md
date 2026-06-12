---
title: "Compiz and FGLRX Problem"
date: 2009-03-14
forum: Hardware
---

### Post by antario91 on 2009-03-14
Hi All!
I have a pretty annoying problem for which I've googled for over a year now... (I feel like only I have this problem...)
I have a Benq Joybook A52 with an **ATI Radeon Xpress 200M** video adapter. I can set its drivers up (**FGLRX**), configure it properly, but I can't run a compositing manager without a pretty annoying error: an OpenGL 3D layer or any other 3D layer kinda floats on the screen. Understand it like this: if I (for example) start glxgears (with compiz running), it starts and runs, but if I move a window over it, the 3D part of the window - the gears - hover over the window I moved over it (attachment: screenshot.png; you can see, that glxgears is actually behind the terminal... well... it should be...). It even flickers sometimes.
Then... when I try to move a window with a 3D part in it, the 3D part (while dragging) just stays where the window originally was, and snaps to the window when I release it.
These happen with video layers as well.
I tried it with many distros, not only Ubuntu, but openSUSE, Debian, Fedora, etc. None worked (obviously).
With Metacity enabled, these annoyances does not happen.
I would like to have Compiz, so please help me.

---

### Post by antario91 on 2009-03-15
Please... Your help would be greatly appreciated. :D

---

### Post by antario91 on 2009-03-16
Anyone?... Sorry for my triple post and my impatience, but I really want to know what I'm doing wrong.
If it can't be done (but I doubt that... in Linux everything is possible... that much I learned), than say that, just say something, please :D

---

### Post by sky5564 on 2009-03-16
yea im having the same problem with mine go to this thread it has more information.

[http://ubuntuforums.org/showthread.php?t=1085733&highlight=radeon+xpress+200m]("http://ubuntuforums.org/showthread.php?t=1085733&highlight=radeon+xpress+200m")

---

### Post by antario91 on 2009-03-17
Thanks, I've checked it out. Didn't find any useful information though...
But this makes me concerned:
> My wife has this same chipset on her Toshiba laptop (running 8.04.1 - 32 bit) and I can say we've never had any problems running the latest driver in the repo's - in both 8.04 and 7.04. **And yes, Compiz is running very smoothly.**

---

### Post by jim_p on 2009-03-17
Can you also try the opensource radeon driver?
I have heard of some people that have roughly the same card as you do and they use it instead of fglrx to have compiz and flicker free video playback.

(please note i dont check the forums very often, so i may delay responding again)

---

### Post by antario91 on 2009-03-19
Thanks for the tip :D
I've tried the opensource drivers, but no use... :(
Compiz would not start... (when I tried, it crashed X).

---

### Post by hampe on 2009-03-22
This comes from a severe bug in the implementation of dri that's been around for years. It has been fixed in dri2. Dri2 has been implemented in xorg-server 1.6. ([http://www.x.org/wiki/Server16Branch](http://www.x.org/wiki/Server16Branch)) So it should work with jaunty once the drivers have been updated. Fill me in if you have the time to test.

---

