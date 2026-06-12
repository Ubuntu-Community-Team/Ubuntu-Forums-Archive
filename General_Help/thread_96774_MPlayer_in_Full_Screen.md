---
title: "MPlayer in Full Screen?"
date: 2005-11-29
forum: General Help
---

### Post by Mr. Electric Wizard on 2005-11-29
I have been digging about this all day and have come up short...
Has anyone gotten MPlayer to play in full screen mode?
I can get full screen to supposedly work, but the movie is small, and the large black border is full screen.:confused: 
So far, I am not sure if this is even possible.

---

### Post by Robgould on 2005-11-29
You have to change settings.  In Mplayer select options and try different video settings.  You will have to restart Mplayer to test each setting.  I woud try X11/XV first.  I am going off memory so if that is wrong, choose the closest one.  Worst case, try them all.  One should work for you.

---

### Post by Mr. Electric Wizard on 2005-11-29
I shall try tonight.  Thnx:p

---

### Post by Dr. Nick on 2005-11-29
X11/Xv I believe is correct as Robgould stated, Thats what mine is. Open mplayer right click in video screen, hit prefrences, then video tab and change it their

---

### Post by bored2k on 2005-11-29
Note: for those running mplayer from a terminal, it's
```
mplayer -vo xv movie.avi
```

---

### Post by Mr. Electric Wizard on 2005-11-30
bored, that didn't work for me.
I had to use the gl vo driver...

---

