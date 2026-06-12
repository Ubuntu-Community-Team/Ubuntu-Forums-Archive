---
title: "Require Help :Ubuntu Freezes: Nothing responds"
date: 2008-09-06
forum: General Help
---

### Post by deepaksubu on 2008-09-06
Hi ,
I am very recent convert to Ubuntu. Removed all windows and running only on Ubuntu.
I am facing this issue that when I am using any application like Mplayer or any music player or any apps for that matter, my entire Ubuntu freezes.

Trying CTRL+ALT+BKSPC

Have tried everything from enabling CTRL+ALT+DEL and then pressing them when the freeze occurs.

Mine is an AMD Turion processor.
2 GB Ram.
NVIDIA GE Force 6150 graphics card.

Please help.
Regards,
Deepak

---

### Post by deepaksubu on 2008-09-06
Oops forgot to mention:
Using Ubuntu version Hardy Heron 8.04

---

### Post by OutOfReach on 2008-09-06
Do you by any chance have Compiz fusion enabled (all the effects and such)?

---

### Post by deepaksubu on 2008-09-06
Thanks a ton for your quick reply. 
I had enabled them by going to the Desktop effects. But I also disabled them but to no effect.

---

### Post by OutOfReach on 2008-09-06
Odd this usually happens to me when I have compiz fusion enabled.
Try typing:
```
metacity --replace
```
then try to play something and see if it works or not.

---

### Post by deepaksubu on 2008-09-06
The command is still running and I have got the error 

Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x12000de (VLC media )
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

Also,
Now I am not hearing any sound in the players.

---

### Post by deepaksubu on 2008-09-06
I am still stuck. I watched a movie and the same thing happened in the middle of that. 
ran the metacity replace command to no effect.

Please help me. I am not able to do anything useful as a result of this.

---

### Post by deepaksubu on 2008-12-02
solved this by getting out...Xp rules

---

