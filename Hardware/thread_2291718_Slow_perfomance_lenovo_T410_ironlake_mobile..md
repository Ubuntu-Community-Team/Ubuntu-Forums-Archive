---
title: "Slow perfomance lenovo T410 ironlake mobile."
date: 2015-08-22
forum: Hardware
---

### Post by jean_rivire on 2015-08-22
Hello everyone,

I have recently buy a lenovo t410 and have install ubuntu 14.04 without problems. My issue begins as the computer slows down as I ask it to mutlitask. Now I am thinking this might be an hardware issue, and there might be no way to get around it apart from installing another linux OS that asks for less. But the computer has i5 and seemed to word just fine with windows 7 so I was kind of expecting it to be even faster with ubuntu.

It might has to do with the graphics as there are no drivers which are detected.

Thank you in advance for your help with this, it woul be great to use my computer without having a freeze when several tabs are opened!

Jean

---

### Post by Doug S on 2015-08-22
Hi And welcome to Ubutnu forums,

> **jean_rivire said:**
> My issue begins as the computer slows down as I ask it to mutlitask. 
Do you mean heavy load on the CPUs, which might indicate thermal related throttling?
How much does it slow down, a little or a lot?
> **jean_rivire said:**
> it would be great to use my computer without having a freeze when several tabs are opened!Is the freeze in addition to the slow down?

when your computer is in this slowed down state, what do you get for "grep MHz /proc/cpuinfo"?

---

### Post by tgalati4 on 2015-08-22
Open a terminal and install *htop*.  

```
sudo apt-get install htop
htop
```

Keep it running and watch the CPU load and what processes are running when the computer slows down.  What graphics card do you have?

```
lspci | grep VGA
```

---

### Post by jean_rivire on 2015-08-22
First of all, thanks for the quick answers!! 

Ok, a overloaded CPU is something I though of, by tipping grep MHz /proc/cpuinfo Ia couple of times  got:
jean@jean-ThinkPad-T410:~$ grep MHz /proc/cpuinfo
cpu MHz		: 1199.000
cpu MHz		: 1199.000
cpu MHz		: 2400.000
cpu MHz		: 2400.000
jean@jean-ThinkPad-T410:~$ grep MHz /proc/cpuinfo
cpu MHz		: 2400.000
cpu MHz		: 1199.000
cpu MHz		: 1199.000
cpu MHz		: 1199.000
jean@jean-ThinkPad-T410:~$ grep MHz /proc/cpuinfo
cpu MHz		: 2400.000
cpu MHz		: 1199.000
cpu MHz		: 2400.000
cpu MHz		: 2400.000
jean@jean-ThinkPad-T410:~$ grep MHz /proc/cpuinfo
cpu MHz		: 2400.000
cpu MHz		: 2400.000
cpu MHz		: 2400.000
cpu MHz		: 2400.000


 

Now the last time was a real "freeze". Actually I should better use crash than freeze, since what happens is unresponsive windows darkening, this stuff. 
Now this happens quite often and the slowing down is sometimes not long sometimes longer, hard to say, most of the times though it has  difficulty with opening the dash when I have several tab or opening a window when a programm is downloading (difficulty to  show the interaction of the icon that is added to the menu hwen downloading) sometimes even text selecting makes it slow down. Having generally no other probelm, I first hesitated to report, but I have ubuntu before on an older machine and it was really extremely better.

With htop, looks like compiz is slowing down the machine the most as far , I think.

for the graphic card: 00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

Thanks for your help!!!!!

---

### Post by tgalati4 on 2015-08-22
So, you have a 4-core Intel CPU that throttles between 2.4 GHz and 1.2 GHz.  Compiz is the 3D graphics rendering engine.  Intel Graphics tend to be slow with Unity.  Some have better performance with a lighter weight window manager such as MATE.

If your machine is truly locking up such that you have to hit the power button, then you have a hardware problem.  Could be a bad battery, or a clogged heatsink, or a weak power brick.

It could also be hitting swap.  When you run out of RAM, memory pages are swapped to the hard disk in a swap partition and that can cause very slow response.  

Keep a terminal open and when you get slow behavior:

```
free
```

---

### Post by jean_rivire on 2015-08-26
all right thanks!

---

### Post by jean_rivire on 2015-09-02
Soory I must have misunderstood, I did what you asked and I got this:
Mem:       1907680    1833568      74112     171800        380     269548
-/+ buffers/cache:    1563640     344040
Swap:      1951740     796792    1154948
jean@jean-ThinkPad-T410:~$ free
             total       used       free     shared    buffers     cached
Mem:       1907680    1836572      71108     161072        448     262476
-/+ buffers/cache:    1573648     334032
Swap:      1951740     807420    1144320
jean@jean-ThinkPad-T410:~$ free
             total       used       free     shared    buffers     cached
Mem:       1907680    1843096      64584     130904       1344     267672
-/+ buffers/cache:    1574080     333600
Swap:      1951740     853684    1098056


For information I recude swappiness from 60 to 10 already, I think it is slightly better since then

best,

---

### Post by jean_rivire on 2015-09-06
Anyway, after having instaled a 32 bit version things were better, I also use midori instead of chromium and avoid having all these bugs. SO it&#347; now ok, not ideal but I &#7743; happys with it, thanks for your answers and your help, have a great day!

---

### Post by J_Me on 2015-09-06
You've only got 2GB of memory and that's causing a bottle neck, you need at least 4GB. Fortunately for the T410 to do that type of upgrade is straight forward, to get to the primary memory slot you only need to remove one screw.

---

### Post by tgalati4 on 2015-09-06
Yes, both google-chrome and firefox are memory hogs.  By jailing each tab, when you have several tabs open, the RAM gets eaten up quickly.  With add-ons and plug-ins, the browser has become a complete operating system--sort of a virtual machine in the cloud.  2 GB is now no longer enough for decent performance.

---

### Post by michael337 on 2016-01-22
Yeah, I agree, I have 8gb in RAM or 4gbX2 and chromium & Firefox work great on the 64-bit version of Ubuntu :D so compiz crashes not much, but since minecraft is the biggest memory hog, of course it's going to go at 15-20 fps because integrated cards suck

---

