---
title: "Intrepid, Eee PC and fast boot using finit"
date: 2008-11-05
forum: Hardware
---

### Post by glaze on 2008-11-05
Has anyone had any luck getting finit to work on Eee PC and Intrepid? I'm using Xubuntu 8.10 on Eee PC 701 and compiled finit 0.5 (finit-alt with and without -DDIST_EEEXUBUNTU). Upon boot there's an infinite loop of error messages (sh: Syntax error: "&" unexpected). I also tried smurfy's fork of finit, but it didn't even compile.

Update: I managed to get to X when I changed the username in finit_alt.c. Mouse autodetect didn't work so I added one to X.Org's config file and now it works. Boot process is _very fast_. I haven't had any luck yet getting WiFi to work and the fan is always on (I cannot start powernowd yet, it complains about a missing entry in /sys)

---

### Post by glaze on 2008-11-06
I got my self-modified version of finit-alt to work mostly ok. What doesn't work is usb stick automounting and shutdown is buggy. About the speed: I measure booting speed from power on to the point where I must type my WiFi password. With default init it takes 30 s on my system. With finit it is now 24 s.

---

