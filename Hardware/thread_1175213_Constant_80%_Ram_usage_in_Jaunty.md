---
title: "Constant 80% Ram usage in Jaunty"
date: 2009-05-31
forum: Hardware
---

### Post by Dalif on 2009-05-31
I've had Hardy on my laptop for close to a year, and been pretty satisfied with it. It's the first time I've kept and used a Linux distro for that long, and it made me keener to switch over. 

When Jaunty came out, I was thrilled, and installed it. After a few kinks, things went ahead. I'm dual booting XP SP2 and Jaunty on an Acer Travelmate 7720g

Tweaking and messing around a bit has brought things pretty much up to speed, although I did find a few things were weirdly slow compared to Hardy. When I minized a program to the dock (awn dock), and then alt tabbed it back on the desktop, it took a second or two for it to restore. Also, resizing windows had a wait period of a few seconds from the release of the mouse button, til the action was performed. 

But it wasn't until tonight, when I mounted a DVD Iso, and played it in VLC, that I noticed how the whole system seriously slowed lagged. Especially during the DVD playing. But loads were pretty constant on 80% Ram used. 

I have 2gb, and with 1.6gb in constant use, things do seem a little slow. I looked at the processes, and besides Firefox using 120mb give or take, the rest of the processes only added a couple of hundred mb on top of that. Nowhere near enough to equal 1600. 

I'm thinking perhaps it has something to do with the graphics settings or drivers or whatever. But I'm not adept enough to know exactly what to look for. 

I've prowled the forum, looking for people with a similar predicament, but came up empty. Saw a bug filed on launchpad, but wasn't quite sure it fit.

Any ideas? And if you need additional data, let me know what and how to obtain it, and I'll have it. 

Thanks.

---

### Post by tommcd on 2009-05-31
The 80% RAM usage is probably *cached* RAM. Linux caches RAM for better performance.
 Open a terminal and run:
```
free -m
```
On my desktop with 2GB RAM it reports:
```

bash-3.1$ free -m
             total       used       free     shared    buffers     cached
Mem:          2025       1854        171          0         79       1387
-/+ buffers/cache:        387       1638
Swap:          996          0        996

```
Now, it looks like 1854mb out of 2025mb is being used. But look at the **-/+ buffers/cache:** line. It shows that only 387mb is actually being used by programs, and 1638mb is cached.
The 387 + the 1387 under the cached column + 79 buffers = (approx) the 1854 being used. So the bottom line is I am really only using 387mb RAM right now. Your RAM usage is probably similar.
The slowness you are experiencing is likely a graphics issue. What graphics card does the laptop use? Run:
```
lspci | grep -i vga
```
and report that back if you don't know.
If it is Intel, there are performance issues with Intel gfx drivers in Jaunty. If it's nvidia or ati, do you have the 3D driver enabled properly?

---

### Post by Dalif on 2009-06-01
Hey thanks for replying.

Running free -m, it gives me the following output. What do you make of that?

```
dalif@Ringo:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2012       1847        164          0         19        277
-/+ buffers/cache:       1551        460
Swap:         5890         41       5849
```

And I figured it could be gfx issues, even though I think I got graphics enabled. This laptop uses a ATI Radeon Mobility HD 2600 Series cards. I had problems compositing my screen for a while, but got the drivers working through System->Administrator->Hardware Drivers. Seemed pretty standard.

---

### Post by tommcd on 2009-06-01
> **Dalif said:**
> 
Running free -m, it gives me the following output. What do you make of that?
```
dalif@Ringo:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2012       1847        164          0         19        277
-/+ buffers/cache:       1551        460
Swap:         5890         41       5849
```

Well, it does seem as though you are using a lot of RAM. You are using some swap also. Do you have a lot of programs running? Or a lot of tabs open in firefox? 
How about right after booting up, what is the RAM usage like right when you boot up, before you open any programs?

To find out what is using so much RAM, open a terminal and run **top**. Then hit **shift M** to list the processes according to which are using the most RAM. Hitting **shift P** will return the listing to which processes are using the most CPU, which is the default. Hitting **ctrl s** will pause top so you can see where all the RAM is going. Hitting enter will start it again. 
See if you can figure out what is using so much memory.

If you are using the ATI driver, running:
> fglrxinfo | grep i direct
should tell you if direct rendering is enabled. I have no experience with ATI video cards though.

---

### Post by Dalif on 2009-06-01
Right.

This is the result of fglrxinfo

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 2600
OpenGL version string: 2.1.8575

```

According to top, Firefox and Xorg are the most memory hungry tasks running. I have 5 tabs open at most times in FF, with the occassional surplus, depending on what I'm doing. Nothing out of the ordinary though. 

Right after reboot, running free -m yielded

```
dalif@Ringo:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2012        362       1650          0         16        283
-/+ buffers/cache:        304       1708
Swap:         5890          0       5890
```

Now, 5 minutes later, with a terminal open, and firefox (5 tabs, none sporting flash or java or anything fancy), thos numbers are slightly increased. Again, nothing alarming. But it seems they accumulate over time. Could it be some programs doesn't release their grip on memory? Or something. Wild stabs in the dark.

---

### Post by tommcd on 2009-06-02
> **Dalif said:**
> 
Right after reboot, running free -m yielded
```
dalif@Ringo:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2012        362       1650          0         16        283
-/+ buffers/cache:        304       1708
Swap:         5890          0       5890
```

Now, 5 minutes later, with a terminal open, and firefox (5 tabs, none sporting flash or java or anything fancy), thos numbers are slightly increased. Again, nothing alarming. But it seems they accumulate over time. 
So your memory usage after bootup is about what I would expect. After opening firefox with flash running, memory use should go up some as you said. Still, nothing unusual so far. Do you notice any slowness or performance issues at this point??? I woud expect performance would be ok at this point.

> **Dalif said:**
> 
Could it be some programs doesn't release their grip on memory?

This is possible, but it is not the expected behavior. And you would probably see that in the "top" output if that was the case.
Also, just using RAM should not slow down your system by itself. Only if you are heavily using the swap file would you expect to see a decrease in performance.
I still think any lagging or slowness you may be experiencing would more likely be related to graphics performance, or possibly something hogging your CPU when performance decreases.

---

