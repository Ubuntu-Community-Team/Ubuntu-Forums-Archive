---
title: "Went from 250+ FPS to 39FPS"
date: 2011-02-06
forum: Hardware
---

### Post by DAC1138 on 2011-02-06
I moved from Mint Linux to Ubuntu just this afternoon and on Mint it wasn't fully detecting and using my graphics card. It was using a generic VGA driver and it was giving me 270+ FPS ith GLXGears. After my ubuntu install, everything is working out of the box and I'm only getting 59 FPS. What gives?

Here's some hardware info:

~$ glxinfo |grep rendering
direct rendering: Yes

$lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller


I'm using an asus EEEPC 1210p

---

