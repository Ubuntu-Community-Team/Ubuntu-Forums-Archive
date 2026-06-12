---
title: "[SOLVED] Problem with Amd 3500+ Cpu"
date: 2008-11-05
forum: Hardware
---

### Post by ricpat51 on 2008-11-05
Hi everybody,
I looked into the /proc/cpuinfo file in my system and it is showing a wrong information about my cpu. I've got a Amd Sempron 3500+ in my pc and it's a 1.8GHz. The /proc/cpuinfo file is showing a 800.000MHz Cpu though. So, my Cpu is being used under its capacity? If so, how can I fix it? I'm gonna write my /proc/cpuinfo file below so you can take a look on it. Thank you all in advance.

Best regards

```
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 76
model name	: Mobile AMD Sempron(tm) Processor 3500+
stepping	: 2
cpu MHz		: 800.000
cache size	: 512 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow up pni cx16 lahf_lm extapic cr8_legacy
bogomips	: 1600.04
clflush size	: 64
power management: ts fid vid ttp tm stc

```

---

### Post by ricpat51 on 2008-11-08
Well, nonetheless no one has answered my thread, I've gotten the solution. Anyway I wanna thank you all.

best regards

---

### Post by srt4play on 2008-11-08
Please tell everyone how you solved it.

---

### Post by ricpat51 on 2008-11-08
No budy, I simply figured out that there's nothing to be solved since there isn't any problem at all. It's something called Cpu Frequency Scaling. That is an Ubuntu feature that manages the Cpu power for energy economy and reduce the heat producing. If you wanna know more about, just install the cpufreq package doing:

```
sudo apt-get install cpufrequtils
```

Then you will have two new applications installed in you system: cpufreq-info and cpufreq-set. Reading its manuals you're gonna find some interesting things about.
To read the manual just do: 
```
man cpufreq-info
```
```
man cpufreq-set
```

I hope it helps. Sorry for my English.

best regards

---

### Post by srt4play on 2008-11-09
Thank you for sharing the "solution" to your problem for others to benefit from.

---

### Post by costre on 2008-11-13
I just found this little application when I played around with the panel.

The best thing was, when I boosted both CPU's to the max (3.2 GHz each) I finally managed to sit through some 1080p-movies that previously had continously and repeatedly had frame skips at certain scenes! Yay! 

Seems like the CPU isn't automatically scaling up fast enough to compensate for the added weight of sudden changes in hi-res movies, resulting in frame drops. Running them at max all the time solved this!

(Or am I suffering from the wonderful delusions of placebo?) :lolflag:

*EDIT*
I just realized something else. When I was running lo-res episodes from my software RAID array, the player sometimes "lost track", and got mpeg-compression blobs for a few seconds.Very very annoying. This NEVER happened when watching hi-res material! This makes it even more probable that when the CPU is running at it's highest performance, it's easier for it to take sudden bursts of load, like heavy scenes in hi-res movies, or arranging bursts of data on a software raid array?

*EDIT AGAIN*

Call me crazy, but my computer as a whole is running like a friggin dream! This was the cheapest way to boost your computer's performance yet! Perhaps I'll regret it when the power bill arrives? :D

---

### Post by ricpat51 on 2008-11-13
> **costre said:**
> I just found this little application when I played around with the panel.

The best thing was, when I boosted both CPU's to the max (3.2 GHz each) I finally managed to sit through some 1080p-movies that previously had continously and repeatedly had frame skips at certain scenes! Yay! 

Seems like the CPU isn't automatically scaling up fast enough to compensate for the added weight of sudden changes in hi-res movies, resulting in frame drops. Running them at max all the time solved this!

(Or am I suffering from the wonderful delusions of placebo?) :lolflag:

*EDIT*
I just realized something else. When I was running lo-res episodes from my software RAID array, the player sometimes "lost track", and got mpeg-compression blobs for a few seconds.Very very annoying. This NEVER happened when watching hi-res material! This makes it even more probable that when the CPU is running at it's highest performance, it's easier for it to take sudden bursts of load, like heavy scenes in hi-res movies, or arranging bursts of data on a software raid array?

*EDIT AGAIN*

Call me crazy, but my computer as a whole is running like a friggin dream! This was the cheapest way to boost your computer's performance yet! Perhaps I'll regret it when the power bill arrives? :D

Wow! By the way I've been facing the same problem when watching movies in my pc. I'm wondering if it's the same case, although I've got the max cpu speed on cpufreq-info when I play a movie. I'm gonna try it out and see if there is a difference. Thanks for your reply.

best regards

---

