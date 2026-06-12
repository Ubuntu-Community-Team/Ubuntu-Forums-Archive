---
title: "Sound Gone..."
date: 2009-05-26
forum: Hardware
---

### Post by dmillard10 on 2009-05-26
While trying to disable the horrendously horrendous system beep that Jaunty so kindly shocks me out of my shoes with on a power state change, I managed to totally disable all sounds EXCEPT the system beep.  The only thing that I remember doing was putting 'blacklist pcspkr' in /etc/modprobe.d/blacklist.conf, but I have removed it and lsmod shows pcspkr (if that even means anything).  Possibly of note is the fact that I am running Ubuntu on a Thinkpad R60, for which Jaunty separated the system and software volumes.  This is in documented in [https://bugs.launchpad.net/bugs/364127](https://bugs.launchpad.net/bugs/364127), but as a quick explanation, Thinkpad hotkeys were 'double stepping' the volume, so they unlinked the software volume from the hardware volume and the hotkeys control the hardware volume while the volume slider controls the software volume.  Both volumes are all they way up (although there is no gauge for the system volume now, and I just hit the 'Volume Up' button until my hand got tired), and my computer still makes the beep when changing power states, but there is no sound from rhythmbox or youtube.  Sorry for the extensive post, but does anyone know of a way to help me?  Thank you.

---

### Post by dmillard10 on 2009-05-27
Sorry to bump, but can anybody help with this please?  If you could, that would be great.  Thanks.

---

