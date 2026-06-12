---
title: "[SOLVED] mp3 playback after hibernating"
date: 2008-11-02
forum: General Help
---

### Post by bryncoles on 2008-11-02
hi people. dunno if this has already been reported elsewhere, but having upgraded my dell inspiron 1525n from hardy to intrepid, i noticed this morning that after waking up from hibernate, it wont play MP3s (stored on the hard-disk or on data cd'dvds). 

rebooting resolves the issue - i have mp3 playback again, but if i have to reboot everytime i hibernate then i might as well not hibernate!

anyway, any one hot any idea what the issue is? and anyone know how to solve it, or where to report it more formally?

beyond this issue, (and ignoring that the screensaver wont quit when i move the mouse, only when i touch a key), im finding intrepid a nice sheen of polish for my ubuntu!

---

### Post by bryncoles on 2008-11-03
oh well, must have been a fluke as ive not managed to recreate the issue despite hibernating and trying mp3's again a few times...

good times!

---

### Post by bryncoles on 2008-11-05
bad times! now ive managed to recreate the problem. no-one else suffering this? got some crazy message about initialising audio drivers - i dont recall what exactly though. 

:(

---

### Post by bryncoles on 2008-11-06
bump! anybody know why i cant play mp3s after i hibernate anymore? why i have to restart my computer each time?

---

### Post by bryncoles on 2008-11-07
bumpy bump bump!

its any sound after hibernating that wont play, if thats any help...

---

### Post by bryncoles on 2008-11-09
bump!

---

### Post by bryncoles on 2008-11-10
ker-bump!

---

### Post by bryncoles on 2008-11-20
bump again! im still having the same issue...

---

### Post by rudy.elgato on 2008-11-20
Don't know what causes the problem, but I know I can get sound back after suspend/hibernate by running:

sudo /sbin/alsa force-reload

At least it alot quicker then rebooting your system.

Good Luck...

---

### Post by bryncoles on 2008-11-20
excellent! thats a work-around, is much faster than rebooting and will do for now... ill keep this thread alive until either problem is solved, or it becomes apparent that no-one knows what the issue is!

---

### Post by bryncoles on 2008-12-05
*touch wood* it seems to be solved by the recent kernel update...

---

