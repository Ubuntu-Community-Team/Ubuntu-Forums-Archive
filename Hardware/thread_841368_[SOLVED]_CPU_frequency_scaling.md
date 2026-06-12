---
title: "[SOLVED] CPU frequency scaling"
date: 2008-06-26
forum: Hardware
---

### Post by natirips on 2008-06-26
I'm using emifreq-applet 0.18 to control the CPU frequency when automatic management doesn't have the desired effect.

Story: I use Powersaving mode for playing 3D games to prevent games from getting blocky and having low framerate). But the problem is: I only have Automatic, Powersaving(800Mhz), 1600Mhz, 1800Mhz, 2000Mhz and Performance(aims for 2000Mhz). But when I use any of those, except Powersaving the CPU goes to 91°C (364K), and the CPU speed goes suddenly down to prevent overheating.

Question: Ok, now I'd somehow like to add something like 1200Mhz mode, but I'm not sure how safe would it be to so so, and I don't know how to do it...

My processor is: AMD Turion 64x2 (Mobile), TL-60 (2.0Ghz), in an Acer Aspire 5520G laptop.

---

### Post by ukripper on 2008-06-26
> **natirips said:**
> I'm using emifreq-applet 0.18 to control the CPU frequency when automatic management doesn't have the desired effect.

Story: I use Powersaving mode for playing 3D games to prevent games from getting blocky and having low framerate). But the problem is: I only have Automatic, Powersaving(800Mhz), 1600Mhz, 1800Mhz, 2000Mhz and Performance(aims for 2000Mhz). But when I use any of those, except Powersaving the CPU goes to 91°C (364K), and the CPU speed goes suddenly down to prevent overheating.

Question: Ok, now I'd somehow like to add something like 1200Mhz mode, but I'm not sure how safe would it be to so so, and I don't know how to do it...

My processor is: AMD Turion 64x2 (Mobile), TL-60 (2.0Ghz), in an Acer Aspire 5520G laptop.

EDIT
Sorry didn't see your cpu didn't support scaling to 1200. You can only scale the frequencies your cpu supports.

---

### Post by ukripper on 2008-06-26
Can you do follwoing in termianl and paste output here:

```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequency
```

and 

```
cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_available_frequency
```

---

### Post by natirips on 2008-06-26
> **ukripper said:**
> Can you do follwoing in termianl and paste output here:

```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequency
```

and 

```
cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_available_frequency
```

It said no such file or directory (for both).

---

### Post by ukripper on 2008-06-26
> **natirips said:**
> It said no such file or directory (for both).

my typo sorry,
 it is ```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
```

---

### Post by natirips on 2008-06-27
> **ukripper said:**
> my typo sorry,
 it is ```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
```

OK, here:
```
natirips@natirips-laptop:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
2000000 1800000 1600000 800000 
natirips@natirips-laptop:~$ cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_available_frequencies
2000000 1800000 1600000 800000 
natirips@natirips-laptop:~$ 
```
Does it mean I can't set my own CPU speed? I know it was a simple matter with old 32-bit CPUs I've had (in desktops), either jumpers or the BIOS. However, I don't really think opening up a laptop would be such a grand idea, and I don't have any BIOS options for the CPU...

---

### Post by steevc on 2008-06-27
I have an issue related to CPU scaling. My AMD should be running at 2400, but I see from /proc/cpuinfo that it is running at 1000MHz. I've not intentionally changed anything in this area. I suspect it has been like this for a while, but I had not investigated until now. I only really noticed the difference in the speeds I was getting from the distributed.net software that is always running in the background. This means that both cores are always running flat out.

In another thread I saw a comment about a problem with the scheduler

[http://ubuntuforums.org/showpost.php?p=5048122&postcount=4](http://ubuntuforums.org/showpost.php?p=5048122&postcount=4)

After one reboot I did briefly see it running at full speed, but then it dropped back to 1000 again.

So is there anything I can do to get my PC back up to full speed?

---

### Post by ukripper on 2008-06-27
> **natirips said:**
> OK, here:
```
natirips@natirips-laptop:~$ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
2000000 1800000 1600000 800000 
natirips@natirips-laptop:~$ cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_available_frequencies
2000000 1800000 1600000 800000 
natirips@natirips-laptop:~$ 
```
Does it mean I can't set my own CPU speed? I know it was a simple matter with old 32-bit CPUs I've had (in desktops), either jumpers or the BIOS. However, I don't really think opening up a laptop would be such a grand idea, and I don't have any BIOS options for the CPU...

Well i am afraid your cpu doesn't support your expected 1200Mhz frequency setting. It is very much cpu specific. If your processor doensn't support scaling to that frequency then you won't be able to scale there unless you find a way to underclock your specific processor to 1200Mhz then it won't go any further to the specified.

---

### Post by natirips on 2008-06-27
> **steevc said:**
> I have an issue related to CPU scaling. My AMD should be running at 2400, but I see from /proc/cpuinfo that it is running at 1000MHz. I've not intentionally changed anything in this area. I suspect it has been like this for a while, but I had not investigated until now. I only really noticed the difference in the speeds I was getting from the distributed.net software that is always running in the background. This means that both cores are always running flat out.

In another thread I saw a comment about a problem with the scheduler

[http://ubuntuforums.org/showpost.php?p=5048122&postcount=4](http://ubuntuforums.org/showpost.php?p=5048122&postcount=4)

After one reboot I did briefly see it running at full speed, but then it dropped back to 1000 again.

So is there anything I can do to get my PC back up to full speed?
Try loading it with something, like open any web-site with loads of flash content on it in firefox, and then check it's speed. It may be simply reducing the speed to reduce heating when the speed ain't needed. My proc (Turion 64 2.0GHz) normally runs at 800Mhz, to save power and to produce less heat.

---

### Post by natirips on 2008-06-27
> **ukripper said:**
> Well i am afraid your cpu doesn't support your expected 1200Mhz frequency setting. It is very much cpu specific. If your processor doensn't support scaling to that frequency then you won't be able to scale there unless you find a way to underclock your specific processor to 1200Mhz then it won't go any further to the specified.

I see, too bad...

---

### Post by natirips on 2008-06-27
<I'll be marking the thread as "solved" as soon as this other guy/gal's problem is closed.>

---

### Post by ukripper on 2008-06-27
> **steevc said:**
> I have an issue related to CPU scaling. My AMD should be running at 2400, but I see from /proc/cpuinfo that it is running at 1000MHz. I've not intentionally changed anything in this area. I suspect it has been like this for a while, but I had not investigated until now. I only really noticed the difference in the speeds I was getting from the distributed.net software that is always running in the background. This means that both cores are always running flat out.

In another thread I saw a comment about a problem with the scheduler

[http://ubuntuforums.org/showpost.php?p=5048122&postcount=4](http://ubuntuforums.org/showpost.php?p=5048122&postcount=4)

After one reboot I did briefly see it running at full speed, but then it dropped back to 1000 again.

So is there anything I can do to get my PC back up to full speed?

If you right click on panel and add cpu scaling from there then you would be able to set your desired frequency depending upon your processor supporting scaling.

alternatively post output of the commands i posted earlier starting with cat... then i can have a go through it and help you set your desired freq.

---

### Post by ukripper on 2008-06-27
Here is a good thread if you want at some stage consider to under- volt your cpu if it is generating a lot of heat.

[http://ph.ubuntuforums.com/showthread.php?t=786402](http://ph.ubuntuforums.com/showthread.php?t=786402)

---

### Post by steevc on 2008-06-27
> **ukripper said:**
> If you right click on panel and add cpu scaling from there then you would be able to set your desired frequency depending upon your processor supporting scaling.

alternatively post output of the commands i posted earlier starting with cat... then i can have a go through it and help you set your desired freq.

I'm on KDE, so installed KPowersave and set the scaling policy to Performance. That looks like it has fixed it.

Thanks for your help.

---

### Post by ukripper on 2008-06-27
> **steevc said:**
> I'm on KDE, so installed KPowersave and set the scaling policy to Performance. That looks like it has fixed it.

Thanks for your help.

nice one! i think this thread can be marked solved now.

Cheers

---

### Post by steevc on 2008-07-16
I was not totally happy with using the applet to control my scaling policy as that had to be done for all users. I've now worked out that the issue is with the settings for powernowd. By default that ignores nice'd processes and uses the ondemand governor. You can change this by adding the -n option to /etc/default/powernowd as in

```
#default file for powernowd, see man 1 powernowd
# 
# Options
OPTIONS="-q -n"
```

I hope this helps others.

---

