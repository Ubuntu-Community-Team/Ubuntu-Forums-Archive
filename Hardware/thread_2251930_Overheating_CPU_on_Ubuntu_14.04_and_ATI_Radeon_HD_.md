---
title: "Overheating CPU on Ubuntu 14.04 and ATI Radeon HD 3470 graphics card"
date: 2014-11-07
forum: Hardware
---

### Post by Hyrr_Climaxx on 2014-11-07
My CPU is overheating on a fresh install of Ubuntu 14.04 - when idle it is at about 56-60 degrees Celsius. If I open Chrome, that brings it up to 65 degrees and even more if I use unity (80 degrees).
I figured that because I have an unsupported ATI Radeon HD 3470 card, then there is no 3D acceleration detected and part of the graphical processing is done by the CPU - at least that's what I've read.
I tried everything posted [here]("http://askubuntu.com/questions/508802/failed-installed-amd-radeon-hd-3450-driver-on-ubntu-14-04"), but didn't manage to install or compile the proprietary drivers, nor did the opensource lower my CPU temperature. I switched between drivers [here]("https://help.ubuntu.com/community/BinaryDriverHowto/AMD") and [here]("https://help.ubuntu.com/community/RadeonDriver") and none of them solved this issue, mostly it crashed the X server. Now I have:

```
$ /usr/lib/nux/unity_support_test -p[/FONT][/COLOR][/FONT][/COLOR]
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 3.4, 128 bits)
OpenGL version string:  2.1 Mesa 10.1.3

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes
Unity 3D supported:       no
```

I have a medium experience using Ubuntu and am willing to debug and try anything that could solve this. I also looked for ways to combat overheating, but instead of cpufreq didn't find anything that actually lowered the temperature.
Is there anything I can manually do to lower the temperature in /sys/ or recompile a kernel (didn't do one of these in years and I don't know how :) ...)
Thanks a lot in advance!
PS: please hurry, my CPU is melting :)

---

### Post by QIII on 2014-11-07
Hello!

Just to be clear:  you are running a clean install you did *&#8203;after *doing all that with the driver?

---

### Post by Bucky Ball on 2014-11-07
Default font and colour fine thanks. Removed tags. ;)

---

### Post by Hyrr_Climaxx on 2014-11-08
Hi and thanks for the response!

I did a clean install and unity had my cpu at about 75 degrees constantly without doing much.

Then I tried to reinstall the driver in all the ways that I found on the Internet and nothing improved.


> **QIII said:**
> Hello!

Just to be clear:  you are running a clean install you did *&#8203;after *doing all that with the driver?

So I lastly installed Gnome classic so that at least the 3D effects weren't present to overheat the CPU even worse. 
Now it is at a steady 60-65 degrees and I do not know how to force it to be lower.

I'm running Ubuntu on a [MSI EX620  ]("http://www.msi.com/product/nb/EX620.html") 

Thanks.

---

### Post by Mark Phelps on 2014-11-08
> Then I tried to reinstall the driver in all the ways that I found on the Internet and nothing improved.

I admire your persistence in this, but seriously, you are NOT going to be able to get the fglrx drivers to work with your card and any Ubuntu version newer than 12.04.1. It's not a matter of how you do the install; instead, it's a basic incompatibility between the AMD drivers and the X-server versions used in Ubuntu versions newer than 12.04.1.

---

### Post by Hyrr_Climaxx on 2014-11-08
Hi and thanks for your remark. :)

At this moment I am not eager to get the fglrx drivers to work. I am interested in **any **solution that would lower my CPU's temperature, regardless of the driver.
I am unable to downgrade to 12.04.1 as there are other devices that won't be recognized (my wacom tablet for example).

So I would rather do something to fix this CPU overheating on the current 14.04 version.
It is odd to have a CPU temperature of 60 degrees and a processor load of 15%.

I am linking to an image with applets monitoring this: 

[https://www.diigo.com/item/image/4y0ts/3vnd](https://www.diigo.com/item/image/4y0ts/3vnd) 

First icon is a recent cpu usage history -> blue is the occupied portion, you can see it isn't more than 15%
The temperature here is 57 degrees
The last icon is cpufreq in conservative mode.

Is there anything I can do to lower this consumption rate / burn rate of the CPU ?

Is it possible that it's not a problem with the graphics card? How may I investigate this ?


Thanks.

---

### Post by Bucky Ball on 2014-11-08
Your Wacom doesn't work with 12.04? It should. I plugged mine in and there it was, no questions asked. :-k

Pretty much all the models have been supported for quite some time. But back to your issue ...

Have you tried using a can of compressed air on the vents and anywhere else in there that may have dust or other fluffy matter?

---

### Post by Hyrr_Climaxx on 2014-11-09
Hi,


The Wacom is recognized if I force an update of the kernel and of other components - but in time that led to other incompatibilities.
It is not a problem of a dusty cooler. I will try to see in the following days if it's a "conduction" problem from the fan to the CPU.
Also, I will try to install 12.04 on a test hard drive and see what happens. Maybe it is a hardware problem after all.

Any other suggestions ? 

Thanks. :)

---

