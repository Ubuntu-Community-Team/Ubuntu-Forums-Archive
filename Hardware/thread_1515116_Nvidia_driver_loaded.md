---
title: "Nvidia driver loaded?"
date: 2010-06-21
forum: Hardware
---

### Post by ackley on 2010-06-21
So after working for about 3 hours on a fresh install of Lucid, I finally managed to get the nvidia drivers working using nvidia-173. Anything else gave me four separate screens on my monitor. It was really wonky. Downloading the driver from the website gave me the same thing.

Now that I have fonts that I can actually read, I tried running glxgears as a test to make sure everything was working properly. When I try to run it, I get the following error:

```
symbol lookup error: /usr/lib/nvidia-173/libGL.so.1: undefined symbol: _nv000131gl
```

Any clue what should be done here?

---

### Post by ackley on 2010-06-22
I feel that 17 hours is sufficient for a bump.

---

### Post by taur on 2010-06-22
glxgears works though
I do get the same error as you when running guildwars through wine
I read something about a lib32/64 confusion could be the culprit

[http://www.nvnews.net/vbulletin/archive/index.php/t-46490.html](http://www.nvnews.net/vbulletin/archive/index.php/t-46490.html)

---

### Post by ackley on 2010-06-22
Ok, so I've gotten closer...I think. I've managed to get libGL.so.1 where it's supposed to be, but now, when I run glxgears, I get this:

```
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
```

I've installed nvidia-glx-173, but it still fails when I try to run glxgears or compiz. Any ideas?

---

### Post by whoopa on 2010-06-22
Howdy!

On my computer, sometimes it forgets that it's supposed to use the NVIDIA drivers.
(This is best checked System > Administration > NVIDIA X Server Settings)

If you have the drivers installed, but aint 'using' them THEN glxgears won't work.
(At least, on my computer)


Anyway, here's what to do:

```
sudo nvidia-xconfig
```
(In a terminal)

Then to actually restart an X server;
either Logout -> Login
OR Restart.

(I restarted, feel as if it has somewhat a more permanent effect, and it only takes 30 seconds on my machine)

Besides glxgears, you can now fiddle with the Nvidia settings & also activate compiz.
Hope this fixes it up for you!

---

### Post by ackley on 2010-06-22
> **whoopa said:**
> Howdy!

On my computer, sometimes it forgets that it's supposed to use the NVIDIA drivers.
(This is best checked System > Administration > NVIDIA X Server Settings)

If you have the drivers installed, but aint 'using' them THEN glxgears won't work.
(At least, on my computer)


Anyway, here's what to do:

```
sudo nvidia-xconfig
```(In a terminal)

Then to actually restart an X server;
either Logout -> Login
OR Restart.

(I restarted, feel as if it has somewhat a more permanent effect, and it only takes 30 seconds on my machine)

Besides glxgears, you can now fiddle with the Nvidia settings & also activate compiz.
Hope this fixes it up for you!

I used nvidia-xconfig first & still got this error. It's a bit annoying. The computer is still usable, but just without features.

---

### Post by whoopa on 2010-06-22
I try not to make any assumptions - did you actually restart after running nvidia-xconfig?

Otherwise, in consolation - I have the features disabled (but I do have a choice).

---

### Post by ackley on 2010-06-23
> **whoopa said:**
> I try not to make any assumptions - did you actually restart after running nvidia-xconfig?

Otherwise, in consolation - I have the features disabled (but I do have a choice).

haha yeah, I've restarted. Numerous times.

---

### Post by ackley on 2010-06-24
Back to the top with you!

---

### Post by taur on 2010-06-29
> **ackley said:**
> Ok, so I've gotten closer...I think. I've managed to get libGL.so.1 where it's supposed to be, [...]

How exactly did you do that ?

---

### Post by kabeza on 2010-10-23
> **ackley said:**
> I feel that 17 hours is sufficient for a bump.

I feel that the thread itself deserves a cron job that bumps it each 5 minutes, until NVidia solves this stuff for us

Having same issue, with 173. Version 260 turns off lcd, etc. and tried EVERYTHING

**Edit: this new driver solved all my problems. Now all is working great, but slower**
[http://www.nvidia.es/object/linux-display-ia32-173.14.28-driver-es.html](http://www.nvidia.es/object/linux-display-ia32-173.14.28-driver-es.html)

---

