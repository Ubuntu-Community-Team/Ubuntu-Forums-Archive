---
title: "Problems with Nvidia Quadro FX 1700"
date: 2009-02-16
forum: Hardware
---

### Post by inhibitor on 2009-02-16
Hello. I tried to install ubuntu 8.10 on Sun Ultra 24, but I get some problems with videocard( Nvidia Quadro FX 1700 ). Recommended resolution for my monitor is 1680x1050, but now I have 640x480 and no more. I tried to install nvidia drivers from repository( vers. 173, 177 ) and from nvidia site( vers. 180 ), but nothing changed. Also I edited xorg.conf and added sections Modes, ModeLine, result was the same. Sorry for my bad english, and please help me.

---

### Post by inhibitor on 2009-02-18
Sorry, It was not problem with videocard, it was problem with monitor( ViewSonic VG2030wm). If add     Option "ExactModeTimingsDVI" "True" in xorg.conf, the problem would be solved.

---

