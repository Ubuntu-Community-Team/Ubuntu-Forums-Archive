---
title: "[SOLVED] watching video while using compiz"
date: 2008-08-01
forum: General Help
---

### Post by brokenhachi on 2008-08-01
hi everyone, i'm having trouble with compiz and watching videos..

while i am running compiz, it is impossible for me to watch any kind of video file or dvd EXCEPT in my web browser. when watching videos on a web browser (any kind) it works, but if i try to open a video file with VLC or mplayer or any other video player, it tells me that there is insufficient resources and it just closes.. 

is there a way around this? maybe a command to tell mplayer to ignore that (or vlc or whatever) i remember there was a command for compiz that told compiz to ignore the insufficient resources error, maybe there is the same thing for video players? anyone know?


Thanks!

p.s. im using ubuntu hardy now

---

### Post by overdrank on 2008-08-01
moved :)

---

### Post by brokenhachi on 2008-08-01
oh ok that works.. anyways, anyone out there know what to do?

---

### Post by brokenhachi on 2008-08-07
nobody out there?

---

### Post by sayakb on 2008-08-07
Open VLC. Goto Settings->Preferences
**Check** the *Advanced Options* checkbox (bottom right)
Expand Video -> Output Modules and change the *Video Output Module *from default to X11 output.
Save it and restart VLC.

---

### Post by brokenhachi on 2008-08-07
thanks! that works perfect :)

---

