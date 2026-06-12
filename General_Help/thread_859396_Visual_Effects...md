---
title: "Visual Effects.."
date: 2008-07-14
forum: General Help
---

### Post by Jaxite on 2008-07-14
When i try to enable visual effects, i get this error:

[IMG]http://i36.tinypic.com/2ezlmz6.jpg[/IMG]

Im guessing something to do with my Graphics card.
=[

---

### Post by Ryadt on 2008-07-14
Did you enable your graphic card in Hardware Drivers? System> Administration > Hardware Drivers.

---

### Post by Jaxite on 2008-07-14
" No proprietary drivers are in use on this system ".

=/

---

### Post by Darkade on 2008-07-14
could you post the output when you run
```
compiz
```

---

### Post by Jaxite on 2008-07-14
uh when i press alt+F2, put in compiz, nothing happened
terminal:
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity

---

### Post by kk0sse54 on 2008-07-14
Sounds like you don't have the proper driver enabled for 3-D. What exactly is your graphics card?

---

### Post by Ryadt on 2008-07-14
Try this in terminal```
sudo apt-get install xorg-driver-fglrx
```

---

### Post by Jaxite on 2008-07-15
> **C!oud said:**
> Sounds like you don't have the proper driver enabled for 3-D. What exactly is your graphics card?

idk, how do i find it out?

---

### Post by Jaxite on 2008-07-15
bump, yo.
I think my gfx card is SiS

---

