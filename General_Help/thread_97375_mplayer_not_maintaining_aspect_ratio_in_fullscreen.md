---
title: "mplayer not maintaining aspect ratio in fullscreen mode"
date: 2005-11-30
forum: General Help
---

### Post by michael_salcher on 2005-11-30
When I watch videos in window mode in mplayer, the aspect ratio is correct, but when I go into fullscreen mode, the image is stretched. I think this happens because the aspect ratio is not being maintained when the window get's resized.
does anyone know how to tell mplayer to maintain the aspect ratio or maybe there's some other way to fix it?

---

### Post by Bachstelze on 2005-11-30
I had the same issue and the only way I found to fix it is using another playr. Both VLC and Totem keep the ratio.

---

### Post by sup on 2005-12-06
[http://www.ubuntuforums.org/showthread.php?t=49980](http://www.ubuntuforums.org/showthread.php?t=49980)

opengl worked for me

---

### Post by finni on 2006-11-06
> **michael_salcher said:**
> When I watch videos in window mode in mplayer, the aspect ratio is correct, but when I go into fullscreen mode, the image is stretched. I think this happens because the aspect ratio is not being maintained when the window get's resized.
does anyone know how to tell mplayer to maintain the aspect ratio or maybe there's some other way to fix it?

You need to edit the /etc/mplayer/mplayer.conf -config file and particularly enable zoom by uncommenting #zoom=yes and add your monitors aspect ratio to monitoraspect={ASPECT_RATIO_HERE}, for example mine is monitoraspect=16:10.

Hope this helps

---

