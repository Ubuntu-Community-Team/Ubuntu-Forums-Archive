---
title: "help"
date: 2009-05-19
forum: Hardware
---

### Post by orrloff on 2009-05-19
i don't know what i am doing and am about to smash my computer i am trying to find
 a driver for a jayton 3dforce g-32  video card it works like garbage under linux and works fine in windows with the driver what do i do?

---

### Post by Joeb454 on 2009-05-19
What graphics package do you currently have installed (if any)?

There seems to be 2 different packages for Nvidia drivers, one for newer cards one for older cards.

---

### Post by orrloff on 2009-05-19
i don't have any installed  but it is an older card

---

### Post by Joeb454 on 2009-05-19
It may be worth searching synaptic for the nvidia drivers that are available in the repo's.

A quick search gave me the following:

```
nvidia-common - Find obsolete NVIDIA drivers

nvidia-glx-173 - NVIDIA binary Xorg driver

nvidia-glx-180 - NVIDIA binary Xorg driver

nvidia-glx-71 - NVIDIA binary Xorg driver

nvidia-glx-96 - NVIDIA binary Xorg driver
```

Though I can't guarantee that any of these will work, as I don't have much experience with the older nvidia cards. It may also be worth checking out Nvidia's website (they do Linux drivers)

---

### Post by Zimmer on 2009-05-19
I do not think it is an Nvidia card...  an old Trident, by the looks of it. 

Not mentioned on the appendix of supported cards.

[http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/appendix-a.html)

---

