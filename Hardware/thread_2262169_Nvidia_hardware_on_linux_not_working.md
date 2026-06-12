---
title: "Nvidia hardware on linux not working"
date: 2015-01-23
forum: Hardware
---

### Post by greg69 on 2015-01-23
I've been using Nvidia happily since November last year and it was all fine. Binary drivers worked a charm. However, One day they just stopped working. (Computer said "OpenGL is not using direct rendering" when it was. Couldn't run any games.)
 I was confused and reinstalled to try and fix it. Nouveau drivers worked fine and I could do everything but as you know they're slower and I play a lot of games. So I reinstalled the latest binary drivers.
Now, It said nothing but blocked my keyboard and mouse input at startup. It got to the screen OK but for the ticking password box it may as well have been frozen.
I'm currently on my 3rd install after the second time, I tried using Nvidia-331 with sudo apt-get install from the repos but that didn't work either. I also tried deleting my old drivers before I installed these and it didn't show them. Sudo apt-get remove nvidia-* and all of them were uninstalled.

Help :(

---

### Post by tokyobadger on 2015-01-23
More info please:
Ubuntu version
Kernel (uname -r)
Hardware

---

### Post by greg69 on 2015-01-23
Ubuntu version, 14.04
Kernel, 3.13.0-32-generic
Hardware: EVGA GTX 760.

---

### Post by tokyobadger on 2015-01-23
ok so when was one day and what updates/changs did you make around that time?

---

### Post by greg69 on 2015-01-23
I was playing 7 days to die earlier that day. I don't recall doing updates at any point that day. I believe it was wednesday or thursday. No changes to key sys structures. Even if I did, I reinstalled and tried it all again.

---

### Post by tokyobadger on 2015-01-23
please show us the output of ```
dkms status
```

---

