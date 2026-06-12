---
title: "ubuntu alternate install partitioner"
date: 2009-01-07
forum: Hardware
---

### Post by theRightNee on 2009-01-07
so i am using the alternate install method as outlined here 

[https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

and i managed to boot (needed to use noacpi  acpi=off apm=off) and got the installer running..everything is normal until i reach the partition manager, at which point a box with ??? ??? pops up. sometimes i have gotten the partition manager to run, but the installation will hang...

i have a really low spec machine (600 mhz P3 and 64 mb of PC100 RAM)..could it be that i need to beef up the system?

---

### Post by 2hot6ft2 on 2009-01-07
Most definitely. 64MB of RAM is not enough. Even xubuntu calls for more than that.

---

### Post by blackened on 2009-01-07
> **2hot6ft2 said:**
> Most definitely. 64MB of RAM is not enough. Even xubuntu calls for more than that.

Considering that xfce is by no means the lightest WM (or pseudo-DE if it pleases) out there, then that isn't a very useful suggestion. I've run ubuntu alternate installer on much slower and leaner than the mentioned machine (given that upon reaching gnome I decided better of it).

All that said, I would suggest that you use the server install cd to get a usable command line interface, then install a window manager that suits your hardware better than standard gnome (trust me, gnome will be murder).

If this idea doesn't suit you, then I would suggest checking the installation media integrity. Sounds like you may have gotten a bad burn or that the language settings may be amiss.

---

### Post by theRightNee on 2009-01-09
thank you for your replies.

problem is this machine was built to be ultra portable, and as a result has no cd drive. there is no ethernet cable, and i am not going to do a server install from a 56kb dial up modem..therefore i used the iso to install, 

i will redownload and see what happens.

---

### Post by blackened on 2009-01-09
> **theRightNee said:**
> thank you for your replies.

problem is this machine was built to be ultra portable, and as a result has no cd drive. there is no ethernet cable, and i am not going to do a server install from a 56kb dial up modem..therefore i used the iso to install, 

i will redownload and see what happens.

In your shoes then, I would do one of two things: install, at most, xubuntu, though I still think it would be excrutiatingly slow, or install a distro that comes with fluxbox or some other light WM as the default.

This will probably save you some headache in the long run as you don't have the ability to easily change the setup once its installed on that machine (because it lacks a network connection).

---

