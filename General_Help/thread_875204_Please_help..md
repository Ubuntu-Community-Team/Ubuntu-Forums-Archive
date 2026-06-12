---
title: "Please help."
date: 2008-07-30
forum: General Help
---

### Post by Alchemists_Kitten on 2008-07-30
Im having trouble with my volume. At random points when I'm surfing the web or even just talking to my friends on pidgin, the volume will turn off but the volume button on the screen says that it is still on. Also, when this happens, I become unable to click on the applications, places, and system menu along with the power button at the top of the screen.  The only way to restore the volume or turn the computer off is to use the reset button on the actual computer.
Please, if you have anything that might help, tell me.
Thank you, 
Alchemists_Kitten

---

### Post by Ataris on 2008-07-30
My volume shuts off randomly too, but I've never had serious crash issues like that. Are your drivers up to date? What version of Ubuntu and what are your hardware specs?

---

### Post by hessiess on 2008-07-30
Try:

system->preferances->sound->change everything to ALSA

also open a terminal and run

```
alsamixer
```

check if anything is muted

---

### Post by JohnWesleyHarding on 2008-07-30
Hey,

I had the exact same problem, which the system log said was from pulseaudio, but really was flash player interacting with pulseaudio. 

try to download flash support.

*sudo apt-get install libflashsupport*

I hope this works.

---

### Post by Alchemists_Kitten on 2008-08-01
Thank you all for helping me out. I'm going to try eachof the methods tomorrow.

---

