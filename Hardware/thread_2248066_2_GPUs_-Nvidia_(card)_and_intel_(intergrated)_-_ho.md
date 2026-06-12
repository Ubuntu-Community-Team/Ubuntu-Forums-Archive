---
title: "2 GPUs -Nvidia (card) and intel (intergrated) - how to use 2nd GPU?"
date: 2014-10-12
forum: Hardware
---

### Post by interzoneuk on 2014-10-12
Hi.

I have a desktop with an Nvidia 450 card and also an intergrated intel card.

When I boot up I the desktop is on the Nvidia one (which is what I want) - my 2nd monitor (plugged into the intel gpu) just displays the Ubuntu (or Kubuntu) logo.

How do I use the 2nd GPU - i.e can I start an X session in it ?

nvidia-settings only sees my nvidia card.

xrandr can see the intel one though

i.e

xrandr --listproviders
Providers: number : 2
Provider 0: id: 0x2b5 cap: 0x1, Source Output crtcs: 2 outputs: 4 associated providers: 0 name:NVIDIA-0
Provider 1: id: 0x49 cap: 0x2, Sink Output crtcs: 4 outputs: 6 associated providers: 0 name:Intel

Any help would be welcomed

---

### Post by grahammechanical on 2014-10-12
What version fo Ubuntu do you have? For this situation it is better to have Ubuntu 14.04.

[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

[http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html](http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html)

[http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html](http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html)

Regards.

---

### Post by Vladlenin5000 on 2014-10-12
Desktop usually don't work as notebooks with hybrid graphics. Most of the times you shouldn't be using the integrated chip when you have an add-on card. As a matter of fact most traditional BIOS just disable the integrated if they sense there's a discrete.

---

