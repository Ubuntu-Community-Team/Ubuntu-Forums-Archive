---
title: "AMD Dual-Core Is Slow and You Might Not Know It"
date: 2006-04-02
forum: Hardware &amp; Laptops
---

### Post by shadeland on 2006-04-02
Hi All,

I've found an issue that may be causing everyone using Ubuntu (and possibly other distros) with AMD x2 dual core processors (and possibly other dual core systems?) to be running at a slower speed than they should be, and not realize it. I'm posing this here in case anyone has found this issue, as a check to see if anyone else is seeing this on different systems, and a warning that you may want to check it out.    

I was doiing some performance tests by directing web traffic to my workstation, running Ubuntu 5.10 with an AMD 4200+ x2 dual core processor (Gigabyte motherboard).  I did some initial tests, then realized that I should load up an SMP kernel so I can get both processors in use (I just installed this system).  When I did, I found that the performance was slower, significantly so, than when I was in on a single-processor kernel.  

I ran the OpenSSL speed tests, and found that it was about half as fast in SMP mode than in single processor mode. I loaded up the k7-smp kernel, as well as a 686-smp kernel, and found both were half as fast as a single processor kernel for a variety of operations.  OpenSSL speed is single-threaded, so while it shouldn't be faster in a dual-processor system, it shouldn't be slower, even if the kernel did a terrible job scheduling. 

Checking /proc/cpuinfo, I noticed the Bogomips were lower too, as well as the CPU speed.  1 GHz, instead of the 2.2 that it should be running for a 4200+ x2 processor. 

I hit Google up, and found several references to time issues, but then I saw another [post]("http://ubuntuforums.org/showthread.php?t=110093&highlight=speed+frequency+x2+AMD") that basically turned out to be the issue.  It was the speed stepping.  I ran the processor speed applets, but I found it wouldn't let me change the CPU speed, and sure enough, I set up two applets (one for CPU 0 and one for CPU 1), and they both reported 1 GHz. 

I then found a utility called cpufreq-selector.  I hard-set the CPU speed for 2.2 GHz, and that worked for a while, but the processor speed jumped down to 1.0 GHz.  I then found the right command:

```
cpufreq-selector --governor performance
```

This turns off power/heat saving, and just runs them at full speed.  Both processors now show 2.20 GHz.  I setup a simple script to initiate this on reboot, and it seems to be working fine.

The system seemed OK before I started the performance tests, and I probably would never have noticed it had I not done some quantitative measurements for a project, so it's a tricky problem that way.

---

### Post by colo on 2006-04-03
Turning off Cool'n'Quiet in your system's BIOS should take care of having your CPU clock down, too. However, when properly configured, dynamic frequency scaling is a really nice thing to have. It works under GNU/Linux, too, with the in-kernel ondemand-governor, for instance.

---

### Post by Jason_25 on 2006-04-03
I think the powernowd package does this.  It's known to cause lockups too.

---

### Post by shadeland on 2006-04-03
Another item complicating this issue is that the processors only step down when using an SMP kernel.  Every single processor kernel I've tried, including the default, run full-speed without any need to change any settings.  So the issue isn't necessarily a BIOS issue.

Again, I think many more may be having this issue and not realize it.

---

### Post by Absolute on 2006-04-03
You sir, are a genious!

Seriously though, I noticed my CPU was running at 1 GHz but I had assumed it was the second core, and was normally like that.  I ran your command above, and suddenly I'm at 2.2 GHz on my AMD 64 X2 4400+!  It even feels allot faster!

I think you're correct about this being a more serious issue, and not being very well known.  As with the AMD double-clock issue, I never bothered to investigate what was wrong with my system until I read the postings on here.

Thank you for your help, hopefully more X2 users will read this thread and fix their systems.

---

### Post by pixelboy on 2006-12-23
Blody genius.. well done shadeland!!

---

### Post by ~LoKe on 2006-12-24
> loke@x04d:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
stepping        : 6
cpu MHz         : 1596.000
cache size      : 2048 KB
physical id     : 0
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 3590.75

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
stepping        : 6
cpu MHz         : 1596.000
cache size      : 2048 KB
physical id     : 1
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe lm constant_tsc pni monitor ds_cpl vmx est tm2 cx16 xtpr lahf_lm
bogomips        : 3587.74

Fine on my end.

---

### Post by jfrazierjr9@hotmail.com on 2008-05-10
I am new to linux and how this system works. So be patient.
Problem statement:
We have a server using RHE4 this server has cpuspeed installed. The server has 2 dual core processors.
cpuspeed starts 4 processes. 1 for each core. When we run a process that lands on a single core the cpu speed stays at 2000MHz even though the max is 3000MHz. I think that that even though there are 2 cores per cpu there is only one cpu speed for bother coures. It seems that even if one core is loaded 100% while the other core is minimally loaded that cpuspeed continously bounces the cpu speed back to the minumum. I would appreciate any feedback.

Thanks

---

