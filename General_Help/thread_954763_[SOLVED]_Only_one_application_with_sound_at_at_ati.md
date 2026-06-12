---
title: "[SOLVED] Only one application with sound at at atime? what is this, windows STARTER e"
date: 2008-10-21
forum: General Help
---

### Post by joey-elijah on 2008-10-21
A query, why has ubuntu suddenly decided that only one application may have sound at a time.

i was listening to a song in RhythmBox while i let a youtube video load, clicked play and no sound. Tried again - nothing. Closed RB and et voila!

Vice versa, after watching the video, i opened up ryhthmbox again and it refuses to play anything - mainly because firefox was still open (youtube wasn't).

Close firefox and... hey presto expectico - RB plays...

Hmm... why is this so? I'm sure it wasn't like this before...

---

### Post by joey-elijah on 2008-10-22
solved 

just type 
> 
sudo apt-get install libflashsupport

and restart firefox etc, should now play sound from more than one source!

---

