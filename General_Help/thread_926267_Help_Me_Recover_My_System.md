---
title: "Help Me Recover My System"
date: 2008-09-21
forum: General Help
---

### Post by kiisu on 2008-09-21
I majorly f-ed my Ubuntu up ... ran what I thought was a regular update earlier, nothing special though I did feel like it was taking longer than normal.

Well, it seems to have upgraded (only partially?) to Intrepid and nothing is currently working.

When I boot, it takes waaayyy longer than usual, getting stuck for a long time on 'configuring network interfaces'. When it does load, I have a desktop background and that's it. There seems to be something wrong with the gui too, because anything i try to open up has only a blank white box.

Basically, I can't run anything, not even the terminal.

I tried booting into recovery too but that resulted in the same.

Can it either be fixed, or is there a way for me to roll it back to Hardy as I had it before? I'd really prefer not needing to do a fresh install and losing everything I had on there.

---

### Post by Yannick Le Saint kyncani on 2008-09-21
> **kiisu said:**
> Well, it seems to have upgraded (only partially?) to Intrepid and nothing is currently working.

Hi Kiisu,

Ubuntu won't silently upgrade to Intrepid so that's not what has happened here.

I would :

- First, try a previous kernel : at startup, you should have a list of kernels you can choose. A kernel upgrade may not work for your particular hardware configuration.

- You may have hardware problems. So boot your current ubuntu installation, switch to a console (ctrl+alt+f1), login and look at kernel messages (with "dmesg"). Look at the end of dmesg for hardware-related error messages.

- You could also boot ubuntu livecds, either hardy or gutsy. If they do not work either, I'd double-check for hardware failures.

---

### Post by cariboo on 2008-09-21
You could also boot into recovery mode and run:

```
apt-get install -f
```

This will finish downloading the missing packages that are needed to update your system.

Jim

---

### Post by kiisu on 2008-09-21
Doesn't make any sense to me either but that's what happened, however I was able to go into recovery and finish downloading the packages and cleaned up a few broken ones, which is probably what was stopping from fully booting before.

So... guess I'm running Intrepid now! We'll see how this goes.

I am still left with the long boot process though. It hangs for approx. 3-4 minutes on 'configuring network interfaces' ... then says 'stopping ntf server', then 'starting ntf server' (I think- going by memory here but it's something like that).

Anyone know what thats about, and/or how to resolve?

---

### Post by kiisu on 2008-09-21
this thread seems to have helped so far:
[http://ubuntuforums.org/showthread.php?t=401673](http://ubuntuforums.org/showthread.php?t=401673)
but only time will tell....

---

### Post by tuxxy on 2008-09-21
Are you sure that your running intrepid, its still alpha 6 stage

Run this command to be  certain

```
lsb_release -a
```

---

### Post by kiisu on 2008-09-22
> $ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu intrepid (development branch)
Release:	8.10
Codename:	intrepid


No major issues thus far. Firefox has crashed a few times, thats it.
I had just woken up today when I updated but I'm certain I didn't do anything special, just opened update manager and hit Install Updates.

---

