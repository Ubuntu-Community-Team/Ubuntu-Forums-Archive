---
title: "Sound Card Recognized, Only Plays Static"
date: 2010-07-24
forum: Hardware
---

### Post by Brobdingnag on 2010-07-24
Hello hello,

As the title suggests, the only thing that I hear when I turn the volume up on my computer is pure, white-noise static.  What could the problem be?

---

### Post by lidex on 2010-07-25
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

