---
title: "[SOLVED] Brown colour before GDM Loads..."
date: 2008-07-28
forum: General Help
---

### Post by kamitsukai on 2008-07-28
There's been a couple of little graphical annoyances that have been buggy me with ubuntu one was when i logged in i would get the plain brown colour before the desktop loaded which i managed to banish by using this lovely tutorial Here ([http://ubuntuforums.org/showthread.php?t=753261](http://ubuntuforums.org/showthread.php?t=753261)) but i still have a problem with the brown colour after the Usplash finishes and just before the GDM loads is there maybe a similar tut to turn it to a different colour? or remove it altogether?

Thanks in advance!

---

### Post by sayakb on 2008-07-28
Which version of Ubuntu are you using? If you are using Hardy, then changing the color at System->Administration->Login Window should do it. If it is gutsy, then do:
```
sudo gedit /etc/gdm/PreSession
```

And change the BACKCOLOR="" value at the bottom.

---

### Post by kamitsukai on 2008-07-28
Well that was easier than I expected...:oops:

LOL Thankyou!

---

### Post by sayakb on 2008-07-28
Np :) Glad I could help
Please mark the thread as solved..

---

