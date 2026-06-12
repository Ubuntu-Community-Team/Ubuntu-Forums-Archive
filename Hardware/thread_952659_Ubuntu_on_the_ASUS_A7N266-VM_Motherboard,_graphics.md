---
title: "Ubuntu on the ASUS A7N266-VM Motherboard, graphics messed up and will not shutdown"
date: 2008-10-19
forum: Hardware
---

### Post by kev717 on 2008-10-19
I have an old ASUS A7n266-VM Motherboard with a GeForce2-MX Integrated Graphics Card that I've had for a while (Since the days when I used Microsoft XP), but now I'm trying to convert it to Ubuntu like the rest of my machines... I intended it to be my gaming computer because it's got my best GPU in there and one gigabyte of RAM... Anyway, when I booted to live CD, the screen resolution was 800x640 and there were no desktop effects... I decided to install figuring that it would work afterwords... so I installed Ubuntu 8.04 and installed the updates, and it was still like that.  I told it to use the restricted driver and when I restarted, there were white boxes after login and everything was fuzzy and mixed up so I turned the restricted driver off.  I also tried EnvyNG but that just causes my system not to boot up all the way, and now restricted drivers won't even boot either.  What can I do to get this to work properly? It's really only the Geforce2-MX Integrated Graphics card that is giving me trouble... that and the fact that the system says it's shut down while the computer is still running...

Sorry for the long post and Thank-You in advance for your help
-Kev :confused:

---

### Post by nicksim_f on 2009-02-01
I have exactly the same problem. Did you find a way to make it work? I am new to linux, I'd really like to make this work, but I just can't operate on a system with a resolution of only 800x600. Anyone have any ideas?

---

### Post by nischg on 2009-02-24
Any news on this issue? I've tried with hardy and interpid to no avail

---

### Post by bluelightav on 2009-05-05
Same problem in Jaunty.

---

### Post by lanerobe on 2009-05-05
I also have these problems. Adding the following to the "Monitor" section of /etc/X11/xorg.conf fixed the resolutions:

    HorizSync    30-80
    VertRefresh    56-75

Still looking for an answer to the screen corruptions, missed redraws, occasional log outs (wtf??) and complete reboots... The NVidia splash screen is very pretty though.

---

