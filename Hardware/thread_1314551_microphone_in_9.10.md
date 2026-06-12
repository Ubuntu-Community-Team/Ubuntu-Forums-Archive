---
title: "microphone in 9.10"
date: 2009-11-04
forum: Hardware
---

### Post by sdlynx on 2009-11-04
Hello,

I have been using Ubuntu for a while now (couple of years), and the microphone refuses to work on my HP dv5 laptop.  It started working randomly at one point when I had 9.04, but for the most part it did not work and still is not working.  Help?

SDLynx

---

### Post by sdlynx on 2009-11-05
bumpity bump

---

### Post by jimmy the saint on 2009-11-05
have you tried the various inputs in alsamixer?

---

### Post by darkshadow on 2009-11-05
Have you specified your model to the module? just add the below line to /etc/modprobe.d/options and reboot then check all your setting in sound preferences

options snd-hda-intel model=hp-dv5

---

