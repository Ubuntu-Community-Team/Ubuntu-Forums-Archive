---
title: "xfce: disable compositing/opacity for certain programs?"
date: 2008-10-09
forum: General Help
---

### Post by pieoncar on 2008-10-09
Is there a way in xfce to disable compositing or opacity only for certain windows or programs?  I'm trying to watch a movie and do some work at the same time, but if the movie (playing in Totem) does not have focus, no video is displayed.  

I can disable compositing altogether, but I'd rather not do that every time I want to watch a movie in the background.

---

### Post by Koori23 on 2008-10-10
I'm assuming you're using XFCE's compositing as opposed to Compiz.

I've been playing with this trying to recreate your problem. Do you have the full effects on? Opacity on "out of focus" windows? 

When I tried to make background programs transparent, the screen turned blue as opposed to playing any video. 

I killed XFCE's compositor and tried it with xcompmgr and I didn't get the same problem. The only flags I had enabled were the basic xcompmgr -cC

I don't believe you can kill compositing for JUST certain programs. The window manager paints the shadows for ALL windows, it's sort of an all or nothing thing.

Disabling transparency for background programs was the only way to correct that problem for me.

---

