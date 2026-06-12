---
title: "Old games slow with Radeon Xpress 1250?"
date: 2009-02-01
forum: Hardware
---

### Post by Diskdoc on 2009-02-01
I bought a low-end (but still packed with nice features, IMO) LG E300 laptop a few months ago. It came with the ATI Radeon Xpress 1250 IGP. I figured it would be enough for the older games I want to play..but I was a bit dissapointed.

Two old 3D FPS I've been playing around with are Untreal Tournament (99) and Soldier of Fortune II. I've tried UT with both OpenGL and SDL 3D @ 1280x800 but even if I drop the quality settings a lot it seems certain things on the screen slow down the frames per second count a LOT. In playing Capture the flag, for example, when the flag (wobbling texture?) comes into view the fps slows enough to get me killed since I can't react to enemy players. There are other intense situations that slows down the game too.

I've been trying out SoF II in Wine but that too seems oddly slow when you look at certain things or directions, even though I've tried setting moderate settings at 800x600.

I get the feeling there's some kind of graphics situation this chipset + driver (Intrepid, fglrx) isn't handling very well. Just a gut feeling of course, but I would love some input from other Ati users on this.

fgl_glxgears gives me about 840 fps, glxgears 2450 fps.

---

### Post by nixscripter on 2009-02-03
Do you have native rendering? Run: ```
 glxinfo | grep rendering
``` in a terminal.

---

