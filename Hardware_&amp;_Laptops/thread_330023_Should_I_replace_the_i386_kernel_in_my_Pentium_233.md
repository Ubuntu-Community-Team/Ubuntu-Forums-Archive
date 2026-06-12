---
title: "Should I replace the i386 kernel in my Pentium 233 MMX to an i586?"
date: 2007-01-02
forum: Hardware &amp; Laptops
---

### Post by gtmaneki on 2007-01-02
Hi, all.  I recycled an old ThinkPad 380XD (Pentium 233 MMX, 95 MB ram) into a usable basic system by installing Xubuntu 6.06.  While the system speed is tolerable, it would be nice if it were a little faster.  

Would replacing the i386 kernel with an i586 improve the speed any noticeable amount, or could it cause some problems with the hardware (specifically the D-Link wireless PC card and the CS4237 sound card)?

---

### Post by jpeddicord on 2007-01-02
There is no current kernel in the repository that is for i586 machines. There is one for i686's, however. Even if you did upgrade (by building your own kernel), you would not notice too much of a difference in speed.

FYI if you upgrade to Edgy:
The 386 and 686 kernels were merged into a "generic" kernel because there was no noticeable difference in speed.


Jacob

---

### Post by meng on 2007-01-02
I know I'm just stating the freaking obvious here, but your system would be a little faster with more RAM. Or else look for a lightweight window manager like fluxbox or icewm. Or run Damn Small Linux instead, perhaps Puppy Linux.

---

### Post by gtmaneki on 2007-01-02
Thanks for the info,  I see now that there are some i586-optimized 2.4 kernels, but no i586-optimized 2.6 kernels.  

Also, thanks for the speed boost advice.  I'm at the maximum limit of RAM for a ThinkPad 380XD, though.  Xubuntu is actually the fourth distro I've tested on this computer: Puppy Linux and Damn Small Linux gave me display problems.  VectorLinux worked well, and allowed me to try out FluxBox, IceWM, and XFCE.  The recipient of this particular computer, a 62-year-old grandmother with no previous computer experience, found XFCE the easiest to use and customize (FluxBox was just a little too minimalistic for her, while IceWM required too much effort for her to customize and at the time didn't have a trashcan).  And I found little performance difference between VectorLinux and Xubuntu, but Xubuntu is a whole lot easier for me to set up and maintain.

---

