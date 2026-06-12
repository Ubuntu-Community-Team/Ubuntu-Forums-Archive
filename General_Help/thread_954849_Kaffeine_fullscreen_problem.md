---
title: "Kaffeine fullscreen problem"
date: 2008-10-21
forum: General Help
---

### Post by Morientes on 2008-10-21
After one of the latest updates, I don't know which one unfortunately, kaffeine can't play fullscreen videos at the proper size on my TV.

I have my normal monitor on 1600x1200 and my TV on 1024x768. What seems to happen is that on my TV kaffeine displays the videos in 1600x1200 when I go to fullscreen, causing them to not fit the TV at all of course.
Has anyone else experienced this and do anyone know what I can do? It used to work fine...

---

### Post by SpiritFleur on 2008-10-21
I use to use Kaffeine and still do for the TV Guide.

Unfortunately it had a habit of crashing, so I now use gmplayer.

Eg.

gmplayer "dvb://Virgin1"

you may need to setup up channels.conf in ~/.tzap

Kaffeine is under constant development, I imagine the problem you describe has something to do with aspect ratio.

You could have a hunt in the dvb config section for words like that as well.

---

