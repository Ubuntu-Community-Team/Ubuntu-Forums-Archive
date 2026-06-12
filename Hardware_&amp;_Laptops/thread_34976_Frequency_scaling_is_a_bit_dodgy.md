---
title: "Frequency scaling is a bit dodgy"
date: 2005-05-17
forum: Hardware &amp; Laptops
---

### Post by WakkiTabakki on 2005-05-17
Hi
I've noticed that every ... hmmm... 5th time (maybe) I boot Linux, the frequency won't  change from the minimum of 800 Mhz. And it's not just the applet that gets it wrong, the system is noticably sluggish.
Usually, if I  reboot it gets it going again, but not always...

I've got powernow-k8 module running aswell as powernowd-userspace.

```
:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 4
model name      : AMD Athlon(tm) 64 Processor 3200+
stepping        : 8
cpu MHz         : 802.011
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 pni syscall nx mmxext lm 3dnowext 3dnow
bogomips        : 1585.15
``` 

```

$:cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_min_freq
800000
$:cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq
2000000
$:cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_min_freq
800000
$:cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
800000
$:cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_driver
powernow-k8

``` 

I've tried changing the contents of file scaling-max-freq to 2000000, but it won't stick... Then I've run across the program cpufreq-scaling, but that doesn't seem to to anything  ](*,) 

I did a ```
sudo chmod +s cpufreq-selector
``` and got that nifty menu on the scaling applet, but clicking on 2Ghz doesn't do anything...


This is really annoying! 

Any suggestions?


Cheers N

My system:
Abit KV8-Max3
AMD 3200+
Hoary i386

---

### Post by mirtux on 2005-05-17
Hi, 
   is there any link to cpufreq-set in the /etc/init.d directory?

Regards,
MC

---

### Post by WakkiTabakki on 2005-05-18
[QUOTE=mirtux]Hi, 
   is there any link to cpufreq-set in the /etc/init.d directory?

Regards,
MC[/QUOTE]

Nope, but there is no such thing on my system... I've done searches, but there is no file anywhere called cpufreq-set (nor on Synaptics). Should it be a script? Could you post a copy of it,  at what run-levels should it be run?

I do have an app called cpufreq-selector (in /usr/bin), but that doesn't seem to accomplish anything:
```
$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
userspace
$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
powersave userspace ondemand performance
$ sudo cpufreq-selector -g performance
$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
performance

``` 
But, the frequency is still stuck at minimum...

What bothers me is this one
```
$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
800000
```
When my system is running the way it should, this file contains 2000000... It seems that sometimes this file it initiated wrong (and yes, I've tried writing to it, but to no avail)


Cheers
N

---

### Post by mirtux on 2005-05-18
Hi,
  the package is called **cpufrequtils**

Regards,
MC

---

### Post by WakkiTabakki on 2005-05-18
[QUOTE=mirtux]Hi,
  the package is called **cpufrequtils**

Regards,
MC[/QUOTE]
Hey, thanks for the pointers MC and sorry for being such a noob, but I gather that's a Debian package? Didn't find it in any of the normal Hoary depo:s (including univ and multiverse)... 

But, still... This only happens (just guessing here) once in 4 or 5 times I boot, rest of the time everything is dandy. Thus, all necessary software should be on my system, right? 
Besides, one shouldn't need to drag debian packages into it, really? I mean just to get the cpu working... I may be speaking out of my a*s here, but many of the working Ubuntu systems out there do have cpu:s, right :p

I figured it might be a module that needs to be loaded, like something for the via chipset, or whatever... 

Btw, MC, whats in your /etc/init.d/cpufreq-set?

Thnx
N

---

### Post by mirtux on 2005-05-18
Hi,
>  Hey, thanks for the pointers MC and sorry for being such a noob, but I gather that's a Debian package? Yes it is a Debian package but you can install it with no problems since it does not involve any "core" function: it is just an interface to the sysfs management (id it gives you the ability to change for example the frequency of your CPU without typing echo 2000000 > /sys/.....)
> But, still... This only happens (just guessing here) once in 4 or 5 times I boot, rest of the time everything is dandy. Thus, all necessary software should be on my system, right? Well i think it so.... i don't know...:confused:
>  I figured it might be a module that needs to be loaded, like something for the via chipset, or whatever...  Do you have a scaling driver installed, for example powernowd since you have an AMD CPU, that is working well (id no problems during the boot-up procedure)?
>  Btw, MC, whats in your /etc/init.d/cpufreq-set? Well i have patched my 2.6.10 kernel in order to have the speedstep-centrino scaling driver (as a module) with the ondemand governor.

Hope this helps,
Regards,
MC

---

### Post by mirtux on 2005-05-18
Hi,
  just an update...

 >        The Athlon64 CPU supports frequency scaling with the powernow-k8 kernel module and the powernowd userspace daemon.  **However**, you will need to enable ACPI "p-states" to determine the cpu frequencies (this is what Windows does). This is needed because the frequency tables in the BIOS are broken. 
I've read this from this site [http://cmb.phys.cwru.edu/kisner/linux/compaq-r3000/](http://cmb.phys.cwru.edu/kisner/linux/compaq-r3000/)  
You might want to visit it.... :smile:

Regards,
MC

---

### Post by siennalizard on 2006-04-14
I can second this dodginess. I've got the same problem with a 2.0GHz chip that sometimes never clocks in at over 1.6GHz. Normally it only limits the clock speed to that when the laptop's running off the battery, but sometimes, it happens when I boot up with A/C power as well.

I don't seem to have a scaling_max_freq to play with, either. Using PowerNow and the speedstep-centrino driver on Breezy with a Pentium M.

I'd be glad of any help you could give me, even to make this problem reproducable.

---

