---
title: "How to fix my screen resolution"
date: 2008-09-18
forum: General Help
---

### Post by gamesnepal on 2008-09-18
Hi,

I am a complete newbie in ubuntu. Currently I am not able to change my screen resolution and set it higher than 800x600.

I have the following problem with my display:

[IMG]http://img390.imageshack.us/img390/9739/screenshotez4.png[/IMG]

What other information should I provide along with this? Please tell me how I can know about my display drivers and those stuffs so that I can provide you the details about them.

What can I do to increase my screen resolution to 1024x768

Thanks:)

---

### Post by northern lights on 2008-09-18
First off, you might wanna tick the box next to the driver offered under Hardware Drivers (as is the case in your screenshot).

---

### Post by pro003 on 2008-09-18
> **northern lights said:**
> First off, you might wanna tick the box next to the driver offered under Hardware Drivers (as is the case in your screenshot).

yeah...check that box and you will need to be connected to internet so the driver could be downloaded and installed...

other option is to install driver from nvidia site...

---

### Post by gamesnepal on 2008-09-18
I did not actually notice that the checkbox was off. I ticked it and then the driver got downloaded and my screen resolution is fixed. Thanks a lot.

---

### Post by northern lights on 2008-09-18
Honestly, I'm surprised this actually did it already.

One of the simpler issues...

:wink:

---

### Post by pro003 on 2008-09-19
it was easy just like bunch of things in ubuntu 8.04, they made it so easy "that even a child could fly it"!
```

Lisa: Can I fly it?!
Soldier: Of course you cannot!
```

:lolflag:

---

### Post by michaeljeshurun on 2008-11-23
I installed the nvidia restricted driver, after seeing here that several screens got higher resolutions, restarted my computer, and ***actually ended up with lower resolution options***.  I uninstalled, restarted again, and the maximum 800X600 DIDN'T return until I used a terminal, and typed:

xrandr -s 800x600 

which I found on another thread.  I tried the xrandr command to add a higher resolution, but haven't gotten the --addmode switch to work yet.

I'm going to also try and find drivers for this Sony monitor.  I might need help installing them.

I'll go a couple of directions tomorrow, and post an update.

---

### Post by gamesnepal on 2008-12-03
Ok, now i fixed my resolution and my maximum resolution is 1024x768 which is ok for me.

What if I want to go higher than that? Is it possible?

---

### Post by bodhi.zazen on 2008-12-03
> **gamesnepal said:**
> Ok, now i fixed my resolution and my maximum resolution is 1024x768 which is ok for me.

What if I want to go higher than that? Is it possible?

Either run:

```
gksu nvidia-settings
```

Or

```
sudo nvidia-xonfig
```

---

