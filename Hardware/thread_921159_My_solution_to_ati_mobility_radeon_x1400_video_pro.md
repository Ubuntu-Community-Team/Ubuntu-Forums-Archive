---
title: "My solution to ati mobility radeon x1400 video problem in ubuntu 8.04"
date: 2008-09-15
forum: Hardware
---

### Post by spandanj on 2008-09-15
**Problem I had:** (ati radeon mobility x1400 in inspiron 6400)

1) VLC in opengl mode would not work properly with compiz ON
2) VLC in X11 or XV mode would give me pixelated video on fullscreen

**How I solved it:**

1) installed mplayer
2) install smplayer
3) set preferences in smplayer to use "mplayer"; set x11 as the rendering device in smplayer; set audio and other properties in smplayer preferences
4) set preference in mplayer - same as smplayer

--> now, i watch everything in smplayer, in x11. the video is not pixelated in fullcreen (atleast not that i can see, and WAY better than vlc)

Try it out yourself, may be it will work. for me, the problem has disappeared. and SMplayer has more and better options than VLC....

---

