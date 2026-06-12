---
title: "CPU, or RAM?"
date: 2015-08-17
forum: Hardware
---

### Post by CorneliusSneed on 2015-08-17
MoBo:  ASRockM3A770DE 
CPU: AMD Athlon II X2 250
GPU:  MSI GTX 750 Tl
RAM: 4 GB

Which to do first? A better CPU, or more RAM? For details see below:

On an extremely limited budget, I am upgrading my machine, a little at a time. I recently purchased an MSI GTX 750 Tl, and while I have seen an obvious improvement in performance, (over my old 9800 GT) it is apparent this new card is being throttled by a lack of processing speed, a lack of RAM, or both. This is a low mid-range machine, and is not intended to be much more than that. However, I would like to get all the performance I can out of the GPU with my current, admittedly old mobo. I can get a socket AM3 quad core CPU that will far outperform the current CPU for about sixty bucks, and I can get 8 gigs of RAM for about the same amount. However, it is unlikely I will be able to purchase both at the same time. So for the quickest performance increase, which would you do first?

---

### Post by dino99 on 2015-08-18
actually the cpu is the limited hardware; but in a couple months we should get kernels (and drm) that will enable the gpu units instead of of only the cpu to run the OS.
of course ram usage is enough for courant usage, but if you have the needs for heavy apps (games, compiling, art work, design, simulation, .... then 16 gb is recommended, and ssd too

---

### Post by oldfred on 2015-08-18
I do not know AMD, but is current RAM compatible with new motherboard/chip?

I have a older system now, that was part 2006, part 2009 (new video card 9600GT, power supply, motherboard) as 7600GT video card blew up (capacitors) and in late 2011 thought about building new system. But Microcenter had a house brand 60GB SSD for under $100. That sped up system enough that I only built new system last fall, I just could not justify new system as old on was running so well.

I did make the mistake of assuming I could reuse power supply as it was standard. But very new motherboard & Intel chip needed new power supply also. And I reused old case from 2006, but now have no USB3 ports on front. :(

---

### Post by Yellow Pasque on 2015-08-18
RAM would be a waste of money unless you run VM's or do something else that would require a large amount of RAM. As for CPU upgrade, I guess a Phenon II X4 would help with multi-threaded tasks.
Personally, I'd rather save up for a new mobo instead of upgrading an older AM3 system (other than the GPU which was a good buy).

> but in a couple months we should get kernels (and drm) that will enable the gpu units instead of of only the cpu to run the OS.
I'm going to guess the OP is running the nvidia proprietary driver rather than nouveau.

---

### Post by CorneliusSneed on 2015-08-19
[QUOTE=[COLOR=#000000]I'm going to guess the OP is running the nvidia proprietary driver rather than nouveau.[/QUOTE]

Yes, I am. 


[QUOTE=[COLOR=#000000]RAM would be a waste of money unless you run VM's or do something else that would require a large amount of RAM[/COLOR][/QUOTE]

Well, as to that, I don't really know. The one program I run that is the most graphics-intensive is Second Life. (And before people decide to give me a hard time about this, I made enough money in it to buy my new GPU, and a better PSU to go along with it in a couple of months.) I have been doing Second life for about nine years, and one of the most significant things I did regarding performance in it back in the old days was to double my RAM. (from 512K)  However, I'm thinking with the onboard RAM on the GPU, the CPU would be the next logical step, but I thought I would ask here and see what perhaps wiser minds thought about it.

---

### Post by Yellow Pasque on 2015-08-19
> and one of the most significant things I did regarding performance in it back in the old days was to double my RAM. (from 512K) 
It's not the old days. RAM upgrades don't help nearly as much as they used to. 

Check free command when doing intensive tasks you normally do, like running SL, playing video, having browser tabs open, etc.
```
free -m
```
See here for how to read it: [http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)
If you have more than ~500M free while doing the most memory-intensive tasks you do, then you probably won't get much benefit from adding more RAM.

BTW, you are running 64-bit version, correct?
```
uname -a
```

---

### Post by CorneliusSneed on 2015-08-25
> **Temüjin said:**
> BTW, you are running 64-bit version, correct?


Yes

---

### Post by CorneliusSneed on 2015-09-01
> **Temüjin said:**
> RAM would be a waste of money unless you run VM's or do something else that would require a large amount of RAM. As for CPU upgrade, I guess a Phenon II X4 would help with multi-threaded tasks.

I installed a conky that monitors RAM and CPU usage, among other things, and have noticed that sometimes the "bottleneck" is the CPU, and at other times it is RAM. When my SL viewer is downloading new textures, the CPU gets a big hit, but when my machine is communicating with the SL servers in other ways, it is RAM that is nearly maxed out.

The good news, I suppose, is that all this is fixable with a better CPU and more RAM

---

### Post by Yellow Pasque on 2015-09-02
> But when my machine is communicating with the SL servers in other ways, it is RAM that is nearly maxed out.

Do you have conky set up to read the actual amount of used RAM or is it including the cached RAM that could be made available if needed? [http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

