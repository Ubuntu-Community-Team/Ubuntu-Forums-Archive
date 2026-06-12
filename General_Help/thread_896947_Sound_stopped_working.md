---
title: "Sound stopped working"
date: 2008-08-21
forum: General Help
---

### Post by Quantum Wizard on 2008-08-21
Hello,

I have a problem with Ubuntu and wonder if anyone here could help me. While the sound stopped working even though I don't remember doing anything special. The sound still works in the log-in screen but other than that I get no sound whatsoever. Nothing appears to be muted. I tried reinstalling ALSA and Pulseaudio but that didn't help. What could be the problem?

Thanks in advance.

---

### Post by Spaceman9 on 2008-08-21
Try not using Pulseaudio. It can cause problems with ALSA.

---

### Post by Quantum Wizard on 2008-08-21
Okay, I switched everything in /system/preferences/sound to ALSA. Now the sound seems to work in Totem not in any other program like VLC or MPlayer.

The sound did work just fine couple of weeks ago so it shouldn't be impossible to get it work with Pulseaudio too.

---

### Post by Quantum Wizard on 2008-08-24
I noticed that if I watch a movie file with more than one audio track with Totem and switch the audio track, then the sound also stops working.

---

### Post by Quantum Wizard on 2008-08-30
Okay, now the sound stopped working without Pulseaudio too. It doesn't work with Totem or apparently with any other program either. The only place it works in is the log-in screen. This really annoying. Does anybody have any idea what to do?

---

### Post by smn8600 on 2008-08-31
bump...

this SUCKS!!! I have the same problem!!!  Someone help please D:!!!  Would be greatly appreciated.

---

### Post by Ryadt on 2008-08-31
Try```
killall pulseaudio
```

---

### Post by smn8600 on 2008-08-31
The sound works on and off...  Off more-so than on (after logging in)  It works BEFORE I log in no matter what.  Afterwards, it's intermittent.

---

### Post by nbayiha on 2008-08-31
Follow this thread and you should have all that stuff fixed . I hope :lolflag:
[http://ubuntuforums.org/showthread.php?t=789578&highlight=youtube+sound+problem](http://ubuntuforums.org/showthread.php?t=789578&highlight=youtube+sound+problem)

---

### Post by smn8600 on 2008-08-31
So far so good!  Thanks!

---

### Post by Quantum Wizard on 2008-09-01
> **Ryadt said:**
> Try```
killall pulseaudio
```

That didn't work.

---

### Post by Quantum Wizard on 2008-09-01
> **nbayiha said:**
> Follow this thread and you should have all that stuff fixed . I hope :lolflag:
[http://ubuntuforums.org/showthread.php?t=789578&highlight=youtube+sound+problem](http://ubuntuforums.org/showthread.php?t=789578&highlight=youtube+sound+problem)

I followed the part A, but that didn't help. The other parts didn't seem relevant for my problem.

---

### Post by Quantum Wizard on 2008-12-08
Bump!

I still haven't found a fix to the problem and I'm asking for help again. If no one can still help me, I won't bother you again.

---

