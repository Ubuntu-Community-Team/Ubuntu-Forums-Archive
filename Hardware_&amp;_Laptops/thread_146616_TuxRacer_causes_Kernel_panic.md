---
title: "TuxRacer causes Kernel panic"
date: 2006-03-18
forum: Hardware &amp; Laptops
---

### Post by Banshee256 on 2006-03-18
Greetings.

I have a small problem, which you might have guessed from the title. 

I've just installed the newest ATI drivers (ver. 2.0.5695 (8.23.7)) and they work fine. I think. I use a ATI 9800 Pro, no overclocking or anything fancy like that. I installed TuxRacer to test the drivers, actually and, well, they failed, obviously.

If someone could give me a command to display the log-file (or just tell me where such a file might be found) I could give you some more info.

---

### Post by nrwilk on 2006-03-18
Are you sure you're using TuxRacer?

From what I've gathered, TuxRacer has been abandoned and has problems such as what you're having.  There is a spur which is actively being developed.  You won't see a difference between them, and it works much better.  It's called PlanetPenguin-Racer.

Remove TuxRacer, and do the following:
```
sudo apt-get install planetpenguin-racer planetpenguin-racer-extras
```
then run the game, and let us know if that still doesn't work.  Though, it should work.

---

### Post by Banshee256 on 2006-03-18
Erm, sorry... should have clarified that. I have installed planetpenguin-racer... I'm just used to calling it TuxRacer. 

From Synaptic:
```
package             Installed Version    Latest Version
planetpenguin-racer 0.3.1-2build1        0.3.1-2build1
```

---

### Post by nrwilk on 2006-03-18
Sorry, gave it my best shot. :D 

I hope you find the problem, good luck!

---

