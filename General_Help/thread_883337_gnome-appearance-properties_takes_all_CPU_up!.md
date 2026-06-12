---
title: "gnome-appearance-properties takes all CPU up!"
date: 2008-08-07
forum: General Help
---

### Post by dkeceh on 2008-08-07
Hi there,

I found that gnome-appearance-properties use CPU more than 60%, and never come down. I saw it on the System Monitor. I have to log out and login again to terminate the gnome-appearance-properties and make some space for other application to use the CPU.

The questions are, is it normal? Is there any ways to limit gnome-appearance-properties use too many of CPU resource?

Thank you.

PS: I'm new in Ubuntu.

---

### Post by djxcon on 2008-08-07
Have you installed all of the updates?  There was a bug in Hardy where the appearance dialog caused the CPU usage to spike but it has since been resolved.

---

### Post by tuxxy on 2008-08-07
try and kill the app from terminal and could save you logging out

```
killall <appname>
```

---

### Post by kk0sse54 on 2008-08-07
I don't know if you have a small amount of RAM but gnome can be very resource heavy so instead you might want to check out one of the lighter wm's (xfce, openbox, fluxbox, etc etc)

---

### Post by tuxxy on 2008-08-07
My GNOME at bootup is running with 300MB RAM, this is with many custom desktop items and compiz effects

---

### Post by dkeceh on 2008-08-07
Hi .. thank you. I can suspend the application.

I've regulary updated as the patch arrived. Hence, my Hardy sould be the newest.

Is there any clue about what had happened? Did I do something wrong and make it happened?

Thank you for your help and information


PS: I use Laptop Toshiba Portege (M300), with Pentium (M) processor 1.1OGHz, and 500MB memory.

---

### Post by tuxxy on 2008-08-07
Could it be you were running a lot of memory intensive apps

---

### Post by jkid on 2008-08-07
you need a lot more  memory

---

### Post by dabugas on 2008-09-22
The same thing happened to me a few days ago: gnome-appearance-properties sucks up all my CPU and I need to kill it manually; this didn't use to be the case. I am on an HP 530 and running Gutsy, so presumably I am caught by the aforementioned bug; it is *not* however a memory problem, as I have a gig of RAM.

---

### Post by skintythe1andonly on 2008-09-23
I am having the same problem, all of my CPU1 is being used up by gnome-appearance-properties. I am using a HP dv2000. I have 1Gb of RAM so i dont think this is an issue. I used to run kde4.1 with compiz with no problems before. I am not running intensive programs either. Any ideas?

---

### Post by skintythe1andonly on 2008-09-23
ok do not kill gnome-appearance-properties, i tried to kill it, everything seemed fine until i rebooted. I couldnt log into gnome at all. I logged into the failsafe terminal and started it again. When i logged back in with gnome....the 1st CPU is being all taken up by it again, and its getting very hot.

---

