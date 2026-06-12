---
title: "high CPU usage when moving mouse"
date: 2012-05-14
forum: Hardware
---

### Post by ldcdc on 2012-05-14
Hello guys,

I just noticed a relatively high CPU usage when just moving the mouse around. It goes from basically none (2% on 4 cores) to about 10%. The culprits seem to be Xorg, and the particular application over which I hover the mouse. 

Xorg goes to 20-25%, and say gnome-terminal which I use to run "top" goes to ~30%. Is this such an increase normal? I'm using Unity 3d, but I got similar behavior in Unity 2d as well.

---

### Post by davegeetbf on 2012-06-13
Hi folks, I'm experiencing the same problem after an update last week. Ubuntu 12.04 using gnome shell

---

### Post by davegeetbf on 2012-06-14
The last ubuntu update (kernel 3.2.0-25 x64) seems to fix the problem :lolflag:

---

