---
title: "Lucid, extended desktop, no video"
date: 2010-05-03
forum: Hardware
---

### Post by Anilm3 on 2010-05-03
Hello guys!

I've been setting up my recently installed ubuntu lucid but I've discovered that I can't see any video when I use extended desktop. I've tried different players such as VLC and mplayer, but nothing can be seen on any of the screens.

If I disable the extended desktop everything works just fine, even on mirror mode.

Any ideas?

---

### Post by antiram on 2010-05-04
does this anything for working xv?
xvattr -a XV_CRTC -v 1
or
xvattr -a XV_CRTC -v 0

you could also change video settings with gstreamer-properties to "no xv", but its slower or bad quality without xv.

---

