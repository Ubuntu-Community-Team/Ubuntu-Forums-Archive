---
title: "No sound"
date: 2008-11-23
forum: General Help
---

### Post by L1GTN1NG on 2008-11-23
I have no sound for flash videos such as youtube. I hear sound when ubuntu boots up though.

Edit: I also hear sound when I play videos through vlc.

---

### Post by swoody on 2008-11-24
Try installing this, and see if it helps with flash support:
```
aptitude install libflashsupport
```

Do you have a 64bit computer? You may want to try installing the 32bit Firefox. I've heard the 32bit FF addons work much better:
[http://ubuntuforums.org/showthread.php?p=1174435](http://ubuntuforums.org/showthread.php?p=1174435)

Restart your comp after any changes you make, but try these out, and please let me know if they work or not! :D

---

### Post by blazemore on 2008-11-24
Change to ALSA:
System -> Preferences -> Sound (or similar)
Change everything to ALSA, not Pulse. I think this is a problem with Pulse Audio.

---

### Post by L1GTN1NG on 2008-11-24
I installed libflashsupport, restarted and it didnt work. No, I have a 32bit computer.

My sound was already at ALSA.

---

