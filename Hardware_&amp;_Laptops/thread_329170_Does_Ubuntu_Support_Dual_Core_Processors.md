---
title: "Does Ubuntu Support Dual Core Processors?"
date: 2007-01-01
forum: Hardware &amp; Laptops
---

### Post by geo_bio on 2007-01-01
I have an Intel Core Duo (T2300) processor in my very new laptop.

I was wondering if Ubuntu (Drapper) supports both cores, or if only one of the two cores are used. I have installed the packages that Ubuntu prompts me to install, and did not install extra drivers/programs.

Please give me info or any details you have regarding the use of Intel dual core processors.

---

### Post by an.echte.trilingue on 2007-01-01
Yup, it supports it like a dream.  You need to install the smp kernel.

---

### Post by geo_bio on 2007-01-02
Can someone tell me how to get support for my Intel Core Duo (T2300) processor? I notice that just by moving a window around the screen quickly, the area of the screen that is uncovered (once covered when I dragged a window over that rea) starts to flash as the computer tries to generate the image/stuff. 

In Windows XP, the processor does not max out at 100%, and runs a lot smoother when doing simple functions like that. I'm not sure if all of the processor's potential is used, or if only one of the two cores are used. Please give detailed info on what you know.

---

### Post by maxamillion on 2007-01-02
Sounds like you just need some video drivers. Your processor is supported.

---

### Post by tommcd on 2007-01-02
See this thread:
[http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)
It is a bit old, but the info on which kernel is right for you , and how to install it, is still relevant for Dapper. For Edgy wou would just install linux-generic.
Hope this helps.

---

### Post by starfire1983 on 2007-01-19
Would the SMP kernel apply to a Turion64 X2 since it's dual core or what? I'm not 100% on this since it isn't a k7 processor, but a k8 soooo...yeah. Anyone have a definite answer? I want to get the best out of my laptop on Linux.

---

### Post by tommcd on 2007-01-20
If you are on Edgy then the generic kernel would be for you. Type <uname -r> in terminal to see if you are on the generic or 386 kernel. The 686 and k7 kernels have been made obsolete by the generic kernel. If you search for linux-686 or linux-k7 in synaptic it will tell you that.
You can install the generic kernel from synaptic, or do <sudo apt-get install linux-generic> in terminal. Personally I don't see any performance difference from 386 or generic kernel, but if you have a dual core CPU then you might. Are bot cores listed from the command <cat /proc/cpuinfo>? Also, AFAIK the system monitor GUI should list both cores.

---

### Post by chlopez on 2007-01-22
Along the lines of this thread... Do any of the Ubuntu flavors support not dual-_core_ processors, but dual processors? I've got an older dual processor desktop that I'd like to bring back to usefulness.

---

### Post by RandomJoe on 2007-01-22
A dual-proc system is going to look more or less the same to Ubuntu as a dual-core system.  All a dual-core is really doing is putting two processors on one die, instead of having two separate dies.

So as with the dual-core, just be sure you select the SMP-capable kernel and you're good to go.

---

