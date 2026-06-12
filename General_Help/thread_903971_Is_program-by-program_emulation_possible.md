---
title: "Is program-by-program emulation possible?"
date: 2008-08-28
forum: General Help
---

### Post by PhaeZee5 on 2008-08-28
I am curious as to the existence of a program-by-program emulator for windows apps. Since wine doesn't work, and qemu is too slow, I was curious as to the existence of a middle ground.

---

### Post by Sephoroth on 2008-08-28
As far as I know it isn't possible currently.  One can either attempt to create a compatibility layer so that the program will run alone on the host OS (WINE) or one can emulate the entire OS (aka VM).  What exactly are you trying to run?

---

### Post by mssever on 2008-08-28
Last time I tried Qemu, it was really slow. But I just installed VirtualBox and found its speed to be quite acceptable.

---

### Post by PhaeZee5 on 2008-08-28
> Last time I tried Qemu, it was really slow. But I just installed VirtualBox and found its speed to be quite acceptable

I do like virtualbox, and have used for awhile, but it currently does not have working kernel modules for the intrepid developement branch.

> What exactly are you trying to run? 

iTunes...I know 'bout Amarok, Rhythmbox, etc.

---

### Post by y@w on 2008-08-28
I used [Wine-Doors]("http://www.wine-doors.org/wordpress/") to install iTunes on Ubuntu at one point. You can't sync an iPod, but iTunes runs and the radio works.

---

### Post by PhaeZee5 on 2008-09-15
It appears wine doors is just a "package" manager for wine, which we all know is not an emulator, anything else?

---

### Post by mssever on 2008-09-15
> **tsudrummer24 said:**
> It appears wine doors is just a "package" manager for wine, which we all know is not an emulator, anything else?
Your choices are wine and its derivatives (Crossover, Cedega, etc.) and virtualization (I like VirtualBox). There are no other alternatives.

---

