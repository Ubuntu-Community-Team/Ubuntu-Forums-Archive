---
title: "AMD Turion Running constantly in powersave 800mhz"
date: 2007-03-12
forum: Hardware &amp; Laptops
---

### Post by Dj_Extreme_Audiophile on 2007-03-12
Hey guys, 
I have an AMD Turion 1.6ghz on an acer ferrari 4005 WLMi. I have Ubuntu Edgy 6.10 installed on my system and when I checked the CPU speed, its only running at 800mhz ( that is the powersave speed when I am in windows) Is there any way to make it run at 1.6 ghz?! 

Thanks alot!!!

John

---

### Post by bernied on 2007-03-12
Are you sure it doesn't run faster when it's needed - that would be the normal behaviour? This is to save power and keep the machine cool.
To test this you need to do something to make it work hard - image processing, use tar on an entire partition (you can stop it before it finishes with Ctrl-C), compile something big, whatever. Use top in a terminal to make sure the processor is running at near 100%, then measure the speed of the processor. 

CPU frequency scaling is usually controlled by powernowd or cpufreqd (AFAIK). See which one is running:
```
ps -e | grep powernowd
ps -e | grep cpufreqd
```So find out which it is first.
The next step might be to look at the manual, like
```
man powernowd
```
or
```
man cpufreqd
```
I'm not sure whether those man pages actually exist. You can also try the apropos command to see if there are any man pages that mention those applicatons.

You could also just try to install the cpufrequtils package, then run one of the following (this is from memory, so maybe not spot-on, and you may need sudo for these):
```
cpufreq-set -g ondemand   # this is the default I think, only goes into full speed when needed
cpufreq-set -g performance   # I think this one is always at full speed
cpufreq-set -g powersave   # lowest possible speed
```
To find out what the daemon's current policy is:
```
cpufreq-info
```

---

### Post by karhulitos on 2007-03-12
Hope I'm not confusing things but I run 6.10 on Acer 5044 (AMD Turion) and after adding cpufreq-applet on the panel it always showed me 800MHz. Was about to ask the forums until some update came and I noticed the applet showing full 1,8GHz, then 1,6GHz and back to 800MHz. So, in my case I just wasn't using the computer thus cpu speed was low.

---

### Post by Dj_Extreme_Audiophile on 2007-03-18
Thanks, thats what I was looking for!

---

