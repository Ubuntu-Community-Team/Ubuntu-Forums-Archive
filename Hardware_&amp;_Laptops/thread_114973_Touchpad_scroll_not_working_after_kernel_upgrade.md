---
title: "Touchpad scroll not working after kernel upgrade"
date: 2006-01-09
forum: Hardware &amp; Laptops
---

### Post by firecat53 on 2006-01-09
Hey. I compiled the 2.6.15-cK1 kernel and the vertical scroll on the touchpad no longer works (Inspiron 7000). Everything else seems to be ok. I checked the kernel configuration and all the input devices support, touchpad support, etc are still there.  I tried a sudo dpkg-reconfigure -phigh xserver-xorg and that didn't have any effect.

Here's the output from "cat /var/log/Xorg.0.log|grep synaptics"
```

(II) LoadModule: "synaptics"
(II) Loading /usr/X11R6/lib/modules/input/synaptics_drv.o
(II) Module synaptics: vendor="The XFree86 Project"
Synaptics Touchpad no synaptics event device found (checked 1 nodes)
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(II) UnloadModule: "synaptics"

```

When I do a synclient -l or synclient -h I get a ```
Can't access shared memory area. SHMConfig disabled?
```

Hmmm...so why would the touchpad not be detected but it all works except for one feature??

Any thoughts or guidance? Thanks,

Scott

---

### Post by goombah88 on 2006-01-09
[QUOTE=firecat53]Hey. I compiled the 2.6.15-cK1 kernel and the vertical scroll on the touchpad no longer works (Inspiron 7000). Everything else seems to be ok. I checked the kernel configuration and all the input devices support, touchpad support, etc are still there.  I tried a sudo dpkg-reconfigure -phigh xserver-xorg and that didn't have any effect.

Here's the output from "cat /var/log/Xorg.0.log|grep synaptics"
```

(II) LoadModule: "synaptics"
(II) Loading /usr/X11R6/lib/modules/input/synaptics_drv.o
(II) Module synaptics: vendor="The XFree86 Project"
Synaptics Touchpad no synaptics event device found (checked 1 nodes)
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(II) UnloadModule: "synaptics"

```

When I do a synclient -l or synclient -h I get a ```
Can't access shared memory area. SHMConfig disabled?
```

Hmmm...so why would the touchpad not be detected but it all works except for one feature??

Any thoughts or guidance? Thanks,

Scott[/QUOTE]
i'm having the same problem.  i'm on a gateway m350wvn though.  the vertical scroll on the right side of the touchpad and the up/down scroll buttons don't work anymore.

i tried installing this synaptics driver [http://web.telia.com/~u89404340/touchpad/](http://web.telia.com/~u89404340/touchpad/) but it had no effect.  any help on this would be MUCH appreciated.

here's my output
```
(II) LoadModule: "synaptics"
(II) Loading /usr/X11R6/lib/modules/input/synaptics_drv.o
(II) Module synaptics: vendor="The XFree86 Project"
(II) LoadModule: "synaptics"
(II) Reloading /usr/X11R6/lib/modules/input/synaptics_drv.o
Synaptics Touchpad no synaptics event device found (checked 10 nodes)
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(II) UnloadModule: "synaptics"
```

---

### Post by firecat53 on 2006-01-20
Anyone have any ideas about this? It's driving me crazy!!

Thanks, Scott

---

### Post by firecat53 on 2006-01-20
Solved!  

Add "evdev" to /etc/modules and reboot (or "sudo modprobe evdev" and restart X to test it out first).  For some reason that wasn't loaded anymore....not sure why!

Scott

---

### Post by geearf on 2006-02-11
Thank you so much, I was having the same problem, it was also driving me crazy :)

---

### Post by Heliix on 2006-03-09
[QUOTE=firecat53]Solved!  

Add "evdev" to /etc/modules and reboot (or "sudo modprobe evdev" and restart X to test it out first).  For some reason that wasn't loaded anymore....not sure why!

Scott[/QUOTE]

so you think the "evdev" module is inevitable for touchpad? :-k 
no, it isn't, at least my synaptics touchpad is quite happy without it (everything working right and fully configurable) 
i had the same problems: after kernel upgrade to 2.6.15, the touchpad wasn't working properly. i got exactly the same results as you got when i ran the above mentioned commands..

to be frank, your advice with evdev led me to the impasse, i was looking for this mysterious module.. finally, i gave it up and tried to reinstall synaptics, the newest 0.14.4 version and edited the xorg.conf file accordings to the instructions in synaptics driver INSTALL file. rebooted and.. my touchpad was completely frozen :( 
luckily, i had the old version of xorg.conf (the very old version that i used to have on my old 2.6.10 kernel). i didn't hope it might work but it just do work!! wow..
seems strange to me.. i decided to attach the file.

---

### Post by firecat53 on 2006-03-12
I wish I understood more about the whole xorg.conf thing! The evdev module I found as a suggestion in a different post somewhere, and it worked for me. Unfortunately, I've noticed that very small hardware differences and configuration differences can make a big difference in how problems are solved from system to system. 

At least it works :)

Scott

---

### Post by jemmyw on 2006-03-17
I found I had the same problem, but I noticed that there were two different modules for xorg, one named xserver-xorg-input-synaptics and one named xorg-driver-synaptics, the second of which was installed. The problem fixed itself when i ran ```
apt-get install xserver-xorg-input-synaptics
``` and restarted X

---

### Post by The_Tankengine on 2006-03-22
I am having the same problem with my scroll bar on the touchpad.
Sorry for this easy question, but I am a total n00b as I have been running Ubuntu for only 4 days now.
How do I restart X?
I remember refreshing GNOME at one point when I installed some codecs into FF, but how I did it is beyond me.

---

