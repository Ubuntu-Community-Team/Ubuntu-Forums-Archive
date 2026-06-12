---
title: "High CPU activity on first login."
date: 2017-07-16
forum: Hardware
---

### Post by luca-dgh on 2017-07-16
I have Ubuntu Mate 16.04 with kernel 4.4.0-83, on AMD 64 Athlon X2, gpu is nVidia GeForce 210 controlled by Nouveau driver.

When I boot the system, the first time I log in any of the 3 account I have, I can see that the cpu frequency and usage go to maximum and never rest. In "top" I can see that Xorg occupies the cpu in rates between 12 and 20 %. Obviously the cpu temp increases over 60º C in a short time.
The workaround I found is to log out and log in again, in that way the cpu rests immediately to the minimum frequency and usage is around 2 or 3 % (Xorg almost disappears from "top"). Any other account that logs in after that can see the cpu always quiet, until next reboot.

I had the same problem with all the previous kernel versions I installed since the installation of the 16.04 .
If I remember well I found the same behaviour (often but not always) with the 14.04, but there I was using nVidia driver.

What I can do to fix that problem?
 Thx a lot for your help.

---

### Post by luca-dgh on 2017-07-31
The new linux kernel 4.4.0-87 looks like to fix the problem.
I hope that the next kernel versions maintain this ability.

---

