---
title: "Ubuntu on 686 Hardware"
date: 2006-04-13
forum: Hardware &amp; Laptops
---

### Post by s_baramov on 2006-04-13
Is there any chance to see Ubuntu compiled for 686 instruction set?

I believe Ubuntu should be compiled for 686 instead of 386. After all, who is using 386, 486 or even Pentium based PC? It is not even possible to install Ubuntu on any of these platform. So what is the point compiling for 386, obsolete old platform.

Thanks
Stefan

---

### Post by zerhacke on 2006-04-13
It is already.  The 386 kernel is installed by default because the makers of Ubuntu don't know if you have a 686 processer, a K7 processer, or otherwise.  The 386 kernel is installed by default so you can still boot without segfaults everywhere. It's designed to be a placeholder untill you can get the right kernel installed for your machine.

To install the 686 kernel, at a terminal enter ```
sudo apt-get install linux-686
``` and press enter.

---

### Post by az on 2006-04-13
[QUOTE=s_baramov]Is there any chance to see Ubuntu compiled for 686 instruction set?

I believe Ubuntu should be compiled for 686 instead of 386. After all, who is using 386, 486 or even Pentium based PC? [/QUOTE]

A Via C3 processor is a 386.  So is a Cyrix.  As well, a pentium I or an amd k6-II.

Anyway, optimising the userspace code will not provide you with any noticeable improvement.

---

### Post by s_baramov on 2006-04-14
> A Via C3 processor is a 386. So is a Cyrix. As well, a pentium I or an amd k6-II.

I don't know about Via C3 but Cyrix and K6-II will probably run on a quite old (like 5-6 years) hardware. Which probably means their video controller will not run on XFree86 4.x. To get it running you would have to download and install XFree86 3.3.6. Or you would really have to get a modern video controller to get Ubuntu running. Besides, what is the RAM on these systems: 32MB or may be 64MB? I still remember my first PC with 486 with 16MB of RAM. Oh boy. But can Gnome run on 16MB or 32 or 64 I doubt it. I have a PIII machine at home with 128MB and Gnome is crowling. 

```
Anyway, optimising the userspace code will not provide you with any noticeable improvement.
```

I don't think so. What is the point of adding new instruction sets to CPU core, then ? Just marketing hype? I doubt it. Why Adobe Premier comes compiled with SSE instuction set, so I can't run it on my old PIII machine? The Via C3 does come with SSE instruction set (an instruction set introduced with the latest P4). However, C3 is designed for consumer electronic devices and I would not be surprise to support only the 386 instruction set. 

Next, Gentoo does not exist becuase the instruction set does not matter. The Gentoo fans do believe that compiling the OS and the application for the right instruction set does make a differentce. 

I guess all I am trying to say is that it may be a good idea to have Ubuntu optimized for modern architecture (it is great we have a kernel compiled for 686). After all, if we have Ubuntu for AMD64, why don't we have Ubuntu for 686 architecture.

---

### Post by anoopjohn on 2006-07-05
I installed ubuntu 5.10 on my system which came with 
mercury pvcle266-ml motherboard
via c3 samuals processor
266 MB DDR400 RAM
The system is usable and works fine but once in a while hangs completely - keyboard and mouse stops responding. 
Can somebody help me here

---

### Post by jerinjoy on 2006-07-12
first thing you should get Dapper Drake (Ubuntu 6.06) instead of the 5.10.
I'm not sure how new your machine is but I suggest you download 
Xubuntu 386 version if 6.06 which uses the lightweight XFCE desktop. if you find that your machine can take more load, install ubuntu-desktop from synaptic.

---

### Post by anoopjohn on 2006-07-12
Hi Jerin,
Thanks For the tip - i will try that out and post results.
Cheers
Anoop

Edit: I upgraded to ubuntu 6.10 and everything works like a charm

---

