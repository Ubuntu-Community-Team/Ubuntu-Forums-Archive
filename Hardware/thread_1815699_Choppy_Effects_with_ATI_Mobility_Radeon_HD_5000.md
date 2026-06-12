---
title: "Choppy Effects with ATI Mobility Radeon HD 5000"
date: 2011-07-31
forum: Hardware
---

### Post by dgcruiser on 2011-07-31
Ever since I installed 11.04, anything involving a change in the desktop is extremely choppy. When the login screen loads, it choppily fades from black to Natty's purple. I also have a slideshow running as my wallpaper, but it's transitions are also very choppy, not smooth at all. I've tried messing with the Sync to VBlank setting in OpenGL, but it didn't make any difference either way. Is anyone having a similar problem?

Is there anything I can do, or is it just a problem with the ATI drivers? It says that I'm using the ATI/AMD proprietary FGLRX graphics driver...

---

### Post by kshep92 on 2011-09-03
I can confirm this problem as well. I, too am using the proprietary drivers because the default open source ones wreaked all sorts of havoc with my display.

Anyone got a fix?

---

### Post by dinkstopejaw on 2011-09-25
Same problem here. My unity is running simply because of the 4 gigs of ram and the quad core i have. 

running glxgears gives me the most choppy animation ever.

---

### Post by dinkstopejaw on 2011-09-25
Wow. So that was an easy fix. Remove your previous ati driver, and use "additional driver" app to download the most recent ATI catalyst control center. 

After that just tweak the video card settings administratively. My problem was that they were all set to "performance" instead of "quality" Hope that helps.

---

