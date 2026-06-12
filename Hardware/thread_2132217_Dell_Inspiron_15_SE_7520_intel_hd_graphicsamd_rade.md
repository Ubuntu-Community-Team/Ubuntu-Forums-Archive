---
title: "Dell Inspiron 15 SE 7520 intel hd graphics/amd radeon muxless switching."
date: 2013-04-04
forum: Hardware
---

### Post by xfcewithmutter on 2013-04-04
inspiron 7520:  bios a09   intel i7 3612qm  1920x1080 samsung panel 8gb ram  amd radeon 7730m ( muxless switching px 5 enduro )

Im tried Ubuntu 12.04 and 12.10 .  I can disable radeon from vgaswitcheroo ( good for battery consumption) .  I cant use radeon with switcheroo ( echo DDIS > ....... ). **When i select radeon and logout and try login again ( restart X ) vga switheroo client refused**. Bu its not my real problem.

Best fglrx drivers lastest beta offical amd fglrx drivers. When i installed fglrx  (sudo sh .......................run ) its working. i can get 3800 score from glxgears and offical amd fglrx can run over intel/amd muxless switching. nvidia cant do this only over bumbleebee and performance more broken. 

problem is **when i select intel internal gpu from amd control center its not working. i select it and doing restart. system locking at start x.** i cant go command prompt from there. i starting from other linux with usb. i'm deleting xorg.conf file and ubuntu start with normal hd graphics. if i install amdconfig --initial -f fglrx start normally.

extra not:  fglrx cant do opengl vsync.

what is the solutions ? using legacy driver from switheero.    and using hd graphics from amd fglrx control panel setting.

---

