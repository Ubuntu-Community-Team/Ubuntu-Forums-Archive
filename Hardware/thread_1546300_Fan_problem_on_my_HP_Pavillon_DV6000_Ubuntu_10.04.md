---
title: "Fan problem on my HP Pavillon DV6000 Ubuntu 10.04"
date: 2010-08-05
forum: Hardware
---

### Post by lucacerone on 2010-08-05
Dear all,
I recently installed Ubuntu 10.04 (32 bit) on my laptop.
Everything works fine except that the fan never stops 
(it doesn't always go at full speed but is quite annoying though :))
I've tried to google and search in the forum,
but the solutions seem to be very hardware-dependant and
there are several different solutions proposed.
I don't like to mess up with my laptop,
so I'd like to know if any of you could give me some help
in figuring out what is exactly the issue before of changing
anything.
Cheers, -Luca

---

### Post by lidex on 2010-08-07
There may be a setting in the bios for that. I recently changed a setting in mine and now the fan scales to the load. Sorry I can't remember the actual name of it though.

---

### Post by lucacerone on 2010-08-09
Thanks.
I've checked but there is nothing about temperatures or fan in my bios.
I really think it might be something I can set through Ubuntu because I didn't
have this problem with the 64bit version!
Cheers, -luca

---

### Post by Peter09 on 2010-08-09
install powertop to see what may be keeping your laptop busy (and hot)
 
```
sudo apt-get install powertop
```
 
also there is a set of tools that help set your system to laptop mode
 
[http://packages.ubuntu.com/lucid/laptop-mode-tools](http://packages.ubuntu.com/lucid/laptop-mode-tools)
 
These 'may' help'.
 
Finally - it may be that the fan inlets/outlets are blocked with dust.

---

### Post by fercactus on 2010-09-07
lucacerone - has your problem been solved?  I'm running Kubuntu 64bit and my dv6700z fans are always running.  I'm trying Peter09 suggestion as well.

---

