---
title: "[SOLVED] amarok on ubuntu"
date: 2008-08-09
forum: General Help
---

### Post by Elcid247 on 2008-08-09
ok i reaaaaaallly like amarok, despite the fact it cant play videos, its the best music player ive ever seen!

anyway the only problem is tht its for KDE not Gnome...

sometimes, it gets bugged or stuck, but when i try to kill it whether using the system monitor or the xkill command, it buggs the whole pannel and i cant even relog, so im compelled to restart abnormally losing any unsaved data.

ive tried tons of other players, but nothing is like amarok, not even Exaile which is supossed to be the "Gnome amarok"

any ideas?

---

### Post by dexter.deepak on 2008-08-09
in case you are stuck, just switch to ctrl+alt+f1, login and issue 
```
pkill amarok
```
then switch back to ctrl+alt+f7
i think that would save you a restart.

---

### Post by Elcid247 on 2008-08-09
thanks

though i was looking for a solution to get it to work without getting stuck...

---

### Post by mb_webguy on 2008-08-09
Odd...  I use Amarok under Ubuntu without any problems.  Could you run Amarok from the terminal and post the output?

Also, are you using the version of Amarok from the repositories, or did you install it from some other source?

---

### Post by Elcid247 on 2008-08-09
it runs quite good, but sometimes it just gets bugged wierdly..

especially when it trys to bring Knotify, if theres something wrong with the track im trying to play.

yes i downloaded from the add/remove..

---

### Post by Elcid247 on 2008-08-12
ok i just found the reason after installing ubuntu on my friend's new laptop..

the cause of the problem is the "Music Tracker" plug-in of the pidgin messenger, it didnt work properly on my friend's laptop and once we disabled it, everything worked like a charm.

---

