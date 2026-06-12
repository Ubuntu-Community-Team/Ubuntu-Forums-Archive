---
title: "Graphic card driver"
date: 2011-12-07
forum: Hardware
---

### Post by Aleksej994 on 2011-12-07
Hi, i am using toshiba satelite c655d-s5120 and i just installed ubuntu 11.10. I have 2 problems: 
1: I dont know how to install/download graphic card driver(ati radeon hd 4200)
2: My headphones don't work( they work fine on my pc)
Any help would be appreciated thanx.

---

### Post by Mark Phelps on 2011-12-07
Since you're probably already seeing a graphical desktop (you would say if you were not), then you're already running the graphics drivers for that card.  The default open-source AMD drivers work very well in Ubuntu 11.10, and unless you really need hardware 3D acceleration (i.e., for Games), you're actually better off leaving them alone -- as there are lots of problems with the restricted drivers.

---

### Post by 2F4U on 2011-12-07
Is the output to the headphones muted?

---

### Post by MoreOrLess on 2011-12-07
Usually, adding this to /etc/modprobe.d/alsa-base.conf fixes satellite 6xx's (after reboot)
```
options snd-hda-intel model=ideapad
```
model=thinkpad is another one that frequently works.

---

