---
title: "My ryzen 7 1700 is hitting only 1200Mhz"
date: 2019-02-13
forum: Hardware
---

### Post by Dedalo on 2019-02-13
Hi there. Just a moment ago I wanted to check the clock speed of my processor, and my surprise is that my ryzen 7 1700, which should be hitting the 3Ghz clock speed, only register roughly 1200Mhz. This is a multicore processor with eight core, so I'm not sure if there is something wrong, or ubuntu is just printting one of the cores which is not being used. I'll attach a picture with the terminal reading of the cpu clock.

I am currently running some programs with heavy calculations, and the clock speed is actually very important to me, because I need to know the time it takes to my code to run this calculations for benchmarks, and there is a huge difference between running at half speed. But I don't know if the cores that are running and doing this calculations are working at 1200Mhz, or 3000Mhz, as it should be.

[img]https://ubuntuforums.org/attachment.php?attachmentid=282503&d=1550094074[/img]

---

### Post by QIII on 2019-02-13
Are you running lscpu when the CPU is running under load?

Are you running a stock cooler?  What is the temperature?  Is your CPU freq set to "On Demand"?

```
cat /proc/cpuinfo | grep MHz

```

should capture the speed of all of your processors at that instant.

---

### Post by Doug S on 2019-02-14
My expertise is with Intel processors, not AMD processors, so this reply might be garbage.

Notice how your listed actual CPU frequency is less than the listed minimum CPU frequency. Typically this means some sort of throttling has been activated, perhaps due to a high temperature event. Also some computers makers force throttling if the AC adapter was not made by them (Dell) or when they are on battery power. Clock modulation is one way to throttle that can result in CPU frequencies below the listed minimum.

---

### Post by Dedalo on 2019-02-14
> **QIII said:**
> Are you running lscpu when the CPU is running under load?
Three of them. But I don't know which processor I was looking at.

> Are you running a stock cooler?  

Yes.

> What is the temperature?  Is your CPU freq set to "On Demand"?
I don't know the temperature, neither how the cpu frequency is set. How can I check that?

> 
```
cat /proc/cpuinfo | grep MHz

```

should capture the speed of all of your processors at that instant.

Ok. Now it looks better, it shows all threads, and there are two at maximum speed. I still running one application, so maybe that one is working properly. Can the i.d. of each processor be printed too in order to identify which ones are working at the maximum speed?

Thanks!

---

### Post by Doug S on 2019-02-14
> **Dedalo said:**
> I don't know the temperature, neither how the cpu frequency is set. How can I check that?Do this:
```
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor

```Example:
```
doug@s15:~/temp$ [COLOR="#FF0000"]cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver[/COLOR]
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
intel_pstate
doug@s15:~/temp$ [COLOR="#FF0000"]cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor[/COLOR]
powersave
powersave
powersave
powersave
powersave
powersave
powersave
powersave

```


> **Dedalo said:**
> Ok. Now it looks better, it shows all threads, and there are two at maximum speed. I still running one application, so maybe that one is working properly. Can the i.d. of each processor be printed too in order to identify which ones are working at the maximum speed?Well, they will be in order from CPU 0 to the max CPU. Example (with 100% load on CPU 7):

```
doug@s15:~/temp$ [COLOR="#FF0000"]grep MHz /proc/cpuinfo[/COLOR]
cpu MHz         : 3638.727    [COLOR="#FF0000"]<<< CPU 0[/COLOR]
cpu MHz         : 3647.271
cpu MHz         : 3612.834
cpu MHz         : 3639.526
cpu MHz         : 3611.977
cpu MHz         : 3656.281
cpu MHz         : 3610.798
cpu MHz         : 3741.850   [COLOR="#FF0000"]<<< CPU 7[/COLOR]

```Myself, I prefer this method:
```
doug@s15:~/temp$ [COLOR="#FF0000"]cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_cur_freq[/COLOR]
3589984
3711531
3678665
3650661
3611350
3704713
3674066
3779090

```My guess is that for what you are trying to do, you might want to use the "performance" scaling governor:```
doug@s15:~/temp$ [COLOR="#FF0000"]sudo su[/COLOR]
[sudo] password for doug:
root@s15:/home/doug/temp# [COLOR="#FF0000"]for file in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor; do echo "performance" > $file; done[/COLOR]
root@s15:/home/doug/temp# exit
exit
doug@s15:~/temp$ [COLOR="#FF0000"]cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor[/COLOR]
performance
performance
performance
performance
performance
performance
performance
performance

```And if you are wondering what governors are available:
```
doug@s15:~/temp$ [COLOR="#FF0000"]cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_available_governors[/COLOR]
performance powersave
performance powersave
performance powersave
performance powersave
performance powersave
performance powersave
performance powersave
performance powersave

```

---

