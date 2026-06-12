---
title: "[SOLVED] Play .m3u .pls in terminal"
date: 2008-10-05
forum: General Help
---

### Post by Woody1987 on 2008-10-05
I wish to be able to play a .m3u or .pls playlist in the terminal. I also want the songs to be shuffled instead of playing one after another. I have tried messing around with sox but cant seem to be able to get it to work. Any help with sox would be appreciated as would any suggestions for other programs i can try.

---

### Post by gausie on 2008-10-05
Mplayer does it nicely from terminal if that's what you need.

mplayer -shuffle -playlist music.m3u

If you want the gui to appear

gmplayer -shuffle -playlist music.m3u

Gausie

---

### Post by Woody1987 on 2008-10-05
awesome, thats exactly what i wanted, thanks alot

---

