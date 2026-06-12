---
title: "[SOLVED] ubuntu 8.04 incorrect screen display width"
date: 2008-09-25
forum: General Help
---

### Post by Nailhac on 2008-09-25
I am experiencing problems with screen display width. approx 25mm is taken off the right hand side of the screen in maximised window mode. the window will not reduce to unmaximised window mode although it will minimise OK. I have adjusted all in accordance with screen manufacturers instructions but the problem still persists. If I drag the view away from side of screen it is forced into unmaximised mode and I can correct the width by dragging the side of page out. However when I remaximise the screen it reverts to original faulty display. Any suggestions.

---

### Post by cobra741 on 2008-09-25
> **Nailhac said:**
> I am experiencing problems with screen display width. approx 25mm is taken off the right hand side of the screen in maximised window mode. the window will not reduce to unmaximised window mode although it will minimise OK. I have adjusted all in accordance with screen manufacturers instructions but the problem still persists. If I drag the view away from side of screen it is forced into unmaximised mode and I can correct the width by dragging the side of page out. However when I remaximise the screen it reverts to original faulty display. Any suggestions.

you're not running a custom resolution are you? 

what kind of monitor do you have? (brand & size)

---

### Post by Nailhac on 2008-09-25
yes i am running a customised resolution. the monitor is an hp f1723 lcd is there a problem with customised resolutions??

---

### Post by cobra741 on 2008-09-25
not neccesarily but it sounds like your custom resolution is too big for the screen to display

with LCD monitors, they're unable to display anything higher than their native res and depending on drivers etc it'll force the edge of the screen off to the side of the monitor. 

i'm pretty sure the max resolution you can run on that monitor is 1280x1024 so anything higher (or wider) than that will made the edges "appear off screen" 

set your res back to 1280x1024 and you should be sweet! 

hope this help you out mate :)

---

### Post by appropri8 on 2008-09-25
If you have a LCD monitor you should set the resolution to the screens native resolution, if it already is, try messing around with the buttons on the device (if there's an "auto" button press that).  If that doesn't help maybe it's something to do with the refresh rate or vsync or something?

---

### Post by Nailhac on 2008-09-25
I am only using a 1280x960 resolution but tried several lesser resolutions but all show exactly the same amount of screen view. all is ok with windows xp though and i notice that the refresh rate is also a lot higher with windows xp 75 hertz versus only 52hertz with ubuntu. thanks for all the advice received, hoipe i can manage to resolve it though.

---

### Post by Nailhac on 2008-09-25
I resolved the issue which was a Firefox 3.0 upgrade problem which required the dpi file changing to a value 0f 96 and now all works well. Thanks to all comments and proposals.:)

---

