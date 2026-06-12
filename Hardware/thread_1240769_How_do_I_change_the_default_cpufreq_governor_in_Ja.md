---
title: "How do I change the default cpufreq governor in Jaunty?"
date: 2009-08-15
forum: Hardware
---

### Post by AmyRose on 2009-08-15
I used to be able to change the default speed governor in Intrepid by going to /apps/gnome-power-manager/cpufreq and changing the defaults.

This feature seems to be removed from Jaunty.

Is there a way to change the default governors in Jaunty? I do not need or want my desktop to run the "ondemand" governor because it's too jerky (and I don't need to save battery power on a desktop), and with my laptop, I want "performance" when it's plugged in and "powersave" when it's on battery power, though just getting it to run in performance mode by default is fine since I use the cpufreq panel applet anyway. Changing it manually every time I log in is a bit annoying...

I have tried using the laptop-mode config files and they have no effect.

---

### Post by sdennie on 2009-08-15
> **AmyRose said:**
> 
Is there a way to change the default governors in Jaunty? I do not need or want my desktop to run the "ondemand" governor because it's too jerky (and I don't need to save battery power on a desktop)


What CPU is your desktop running?  For almost all CPUs that support ondemand, the time it takes to switch from highest to lowest frequencies is measured in microseconds and literally impossible for humans to notice.  The only way you should really notice the difference between ondemand and performance is if you are running poorly written benchmarks where the slightly amount of "noise" introduced by changing CPU frequencies is significant to the timings.

> 
, and with my laptop, I want "performance" when it's plugged in and "powersave" when it's on battery power, though just getting it to run in performance mode by default is fine since I use the cpufreq panel applet anyway.

Same thing applies here for "performance" but, also, "powersave" is a bit of misnomer as well.  For very old CPU's powersave was just that.  However, with the introduction of very deep sleep states to modern CPUs, under normal desktop loads, you save more power by having your CPU burst to maximum speed and then quickly return to the deeper sleep states (which is what ondemand does) rather than having the CPU slowly speed up and then speed back down.  This idea is called Race to Idle and you can find more information about it [from Intel]("http://www.lesswatts.org/projects/applications-power-management/race-to-idle.php") or via google.

Having said all that, if you still want to change your CPU frequency governors create a file named, 99-cpu and add the following to it:

```

#!/bin/sh

if on_ac_power ; then
    cpufreq-selector -g performance
else
    cpufreq-selector -g powersave
fi

```

Then install it with:

```

sudo install 99-cpu /etc/pm/power.d

```

That should handle both your laptop and desktop the way you described.

---

### Post by AlexanderDGreat on 2009-08-15
Hi, I'm using a laptop HP Pavilion dv2000 Series. I read a little bit about Ubuntu's CPU Frequency Settings.

1. Did you configure it already? Say Yes when asked to use ROOT when making changes to your Cpu Scaling Applet.

    sudo dpkg-reconfigure gnome-applets

2. My settings are stored here, change cpu0 to cpu1 - If you have 2 Cores because they have different settings.

    /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

3. To set it automatically to preferred setting on startup, these lines should be added in /etc/rc.local

    echo powersave > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

4. To stop it from changing to other modes after 1 minute has passed. Backup then delete afterwards, then reboot:

    /etc/init.d/ondemand

I gathered these info from these:
[http://www.pantz.org/software/cpufre...eqonlinux.html](http://www.pantz.org/software/cpufre...eqonlinux.html)
[http://ubuntuforums.org/showthread.php?t=1143506](http://ubuntuforums.org/showthread.php?t=1143506)

Hope to help.

---

### Post by AmyRose on 2009-08-15
> **sdennie said:**
> What CPU is your desktop running?  For almost all CPUs that support ondemand, the time it takes to switch from highest to lowest frequencies is measured in microseconds and literally impossible for humans to notice.  The only way you should really notice the difference between ondemand and performance is if you are running poorly written benchmarks where the slightly amount of "noise" introduced by changing CPU frequencies is significant to the timings.AMD Athlon 64 X2 Dual Core Processor 4200+ at 2.2 GHz

The problem is that it likes to stay with the lower clock speeds most of the time and only burst into the highest when I have a LOT going on, which seems to cause games to get jerky on it.

> **sdennie said:**
> Same thing applies here for "performance" but, also, "powersave" is a bit of misnomer as well.  For very old CPU's powersave was just that.  However, with the introduction of very deep sleep states to modern CPUs, under normal desktop loads, you save more power by having your CPU burst to maximum speed and then quickly return to the deeper sleep states (which is what ondemand does) rather than having the CPU slowly speed up and then speed back down.  This idea is called Race to Idle and you can find more information about it [from Intel]("http://www.lesswatts.org/projects/applications-power-management/race-to-idle.php") or via google.

Having said all that, if you still want to change your CPU frequency governors create a file named, 99-cpu and add the following to it:

```

#!/bin/sh

if on_ac_power ; then
    cpufreq-selector -g performance
else
    cpufreq-selector -g powersave
fi

```

Then install it with:

```

sudo install 99-cpu /etc/pm/power.d

```

That should handle both your laptop and desktop the way you described.Thanks.

---

