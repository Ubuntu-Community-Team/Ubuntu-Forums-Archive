---
title: "Graphics - Intel® 965GM x86/MMX/SSE2  seems slow"
date: 2012-05-04
forum: Hardware
---

### Post by darkan9el on 2012-05-04
Hi all, I have installed Ubuntu 12.04 on a HP DV2500ea everything looks ok but its a bit slow. Iwas checking system settings etc and I looked at Display and it shows the correct resolution then says Experience: Standard what does this mean? are there other Experience settings and how would I find out if the graphic card is installed correctly.

This laptop has 2.5GB of RAM and a 160GB HDD 5400rpm

It feels like Windows in safemode but with better graphics.

---

### Post by Axxon95 on 2012-05-04
Hey, to see if the graphics drivers are correctly install, run in a Terminal "sudo apt-get install mesa-utils" without quotes. After that is installed run "glxinfo | grep render" in a Terminal without quotes, and respond back with that you receive.

Edit: I recommend you add the Ubuntu-X Team PPA into your software sources and do an update to your system.

---

### Post by Axxon95 on 2012-05-04
Should look something like this(source, my Intel Atom Netbook).

[http://img29.imageshack.us/img29/7077/gpul.png](http://img29.imageshack.us/img29/7077/gpul.png)
[IMG]http://postimage.org/image/xhzoq93jf/[/IMG]

---

### Post by darkan9el on 2012-05-04
Hi thanks for the reply, after typing **glxinfo | grep render** into terminal I get:

```
nikita@nikita-HP-Pavilion-dv2500-Notebook-PC:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 965GM x86/MMX/SSE2
    GL_EXT_vertex_array_bgra, GL_NV_conditional_render, 
nikita@nikita-HP-Pavilion-dv2500-Notebook-PC:~$ 
```

Also added the PPA

---

### Post by darkan9el on 2012-05-04
Ran update, with the PPA included, came back with updates so I installed them, rebooted the system, ran **glxinfo | grep render** and the feedback was the same i.e.

```
nikita@nikita-HP-Pavilion-dv2500-Notebook-PC:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) 965GM x86/MMX/SSE2
    GL_EXT_vertex_array_bgra, GL_NV_conditional_render, 
nikita@nikita-HP-Pavilion-dv2500-Notebook-PC:~$
```

---

### Post by Axxon95 on 2012-05-04
Seems to be in order.  What type of processor do you have?

My Intel Atom N270 and Intel GMA 945GME works near perfect for just being a Netbook(OpenArena is somewhat playable).

---

### Post by darkan9el on 2012-05-05
Hi, 

Intel Core 2 Duo CPU T7100 @ 1.8GHz x2, Linux is the 32Bit version not sure if that makes any difference on performance over 64bit, I also have 2.5GB of RAM.

I may be expecting more from Ubuntu than is reasonable, but one of the reasons I installed it was to enhance performance over the laptops default OS Vista. I think the speeds are comparable so no loss but no gain. I do like Ubuntu over Vista though it's fun to use and once the compiz novelty has worn off it will be a great OS to work on.

---

### Post by Axxon95 on 2012-05-05
> **darkan9el said:**
> I may be expecting more from Ubuntu than is reasonable...

Probably.

And yes, you'll see slight gain performance, Specifically in RAM usage(imo).

I have 2 Acer AOD250s. 1 with Windows 7, and 1 with Ubuntu 12.04. The Ubuntu netbook uses 100-200MB less of ram.

I guess you can mark this thread as Solved. :)

---

### Post by darkan9el on 2012-05-05
I guess so lol always a learning curve just getting used to the command line stuff, its very powerful and actually very easy to understand once you've used it a while.

Maybe I'll get to help other on here if I can get savvy enough. Thanks for the help.

---

### Post by dacoolbg on 2012-05-14
Anyone else affected by this bug: _[Poor performance on Intel® 965GM x86/MMX/SSE2]("http://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/984452")_? If yes, then please go and vote for it as shown here: _[how to vote]("http://goo.gl/wqOjf")_ (*you have to be **logged in***). Thanks in advance, hopefully it will get fixed sooner.

---

### Post by dacoolbg on 2012-05-14
I see that this thread seems to be **solved** but what if **the problem is real**, like this one: _[Poor performance on Intel® 965GM x86/MMX/SSE2](http://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/984452)_. At least in my case the poor graphics performance is because of this bug. If you think that it may be also related to your problem, you could go and vote for it and hopefully it will get fixed sooner.

---

