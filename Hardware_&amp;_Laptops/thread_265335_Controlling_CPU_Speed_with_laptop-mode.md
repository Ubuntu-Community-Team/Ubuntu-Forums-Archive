---
title: "Controlling CPU Speed with laptop-mode"
date: 2006-09-25
forum: Hardware &amp; Laptops
---

### Post by illfingaz on 2006-09-25
I'm hoping someone can help me out here. I am very new to Linux and recently installed Ubuntu 6.06 on my Toshiba 2410 laptop. 

I would like for my laptop to run at its max cpu speed (1.9GHz) when plugged in to AC and drop down to its min cpu speed (1.2GHz) when on battery. I've read some posts already describing how to manually change the speed using the CPU Freq monitor applet in gnome but I would like for this to happen automatically. I've tried doing this with laptop-mode by editing the conf file but it doesn't seem to work, infact, if I remove the file completely I'm still able to start and stop laptop-mode.

I've also read about powernowd and cpufreqd, so now I'm really confused about what it is I should be using. Is there a preference? Does powernowd and cpufreqd conflict with what laptop-mode is trying to do? Can someone please shed some light on this topic? Thanks

---

### Post by Melcar on 2006-09-25
I use emifreq-applet which lets you change CPU speeds, but since you say you want it to be automatic you may want to try kpowermanager which is the power manager in Kubuntu (KDE) which lets you set up profiles for different power states.

---

### Post by illfingaz on 2006-09-25
> **Melcar said:**
> I use emifreq-applet which lets you change CPU speeds, but since you say you want it to be automatic you may want to try kpowermanager which is the power manager in Kubuntu (KDE) which lets you set up profiles for different power states.

Thanks for the reply and the tips but I'd like to stick with gnome if I can. Is there an equivalent method of doing this in gnome?

---

### Post by Melcar on 2006-09-26
You can simply run kpowermanager while still running Gnome; just download it and install it with Synaptic.  It works rather well too.  As far as I know (and I know very little when it comes to Linux) there is no direct Gnome counterpart to kpower.

---

### Post by m83 on 2006-09-26
It took me a while to find out how I could control the CPU Speed using laptop-mode, but I succedeed. I'll try to explain what I did as simple as posible.

The file that you need to modify is [FONT="Courier New"]/etc/laptop-mode/laptop-mode.conf[/FONT]. In that file search for the section [FONT="Courier New"]CPU frequency scaling and throttling[/FONT]. In that section you need to modify the values for BATT_CPU_MAXFREQ and BATT_CPU_MINFREQ so that they are equal to "slowest". My configuration is as follows:
```
BATT_CPU_MAXFREQ=slowest
BATT_CPU_MINFREQ=slowest
BATT_CPU_GOVERNOR=userspace
LM_AC_CPU_MAXFREQ=fastest
LM_AC_CPU_MINFREQ=slowest
LM_AC_CPU_GOVERNOR=userspace
NOLM_AC_CPU_MAXFREQ=fastest
NOLM_AC_CPU_MINFREQ=fastest
NOLM_AC_CPU_GOVERNOR=userspace
```

What I did there was forcing the frequency for the CPU to be the slowest possible when the laptop is running on battery power; exactly what you wanted. I also forced the frequency of the CPU to be the fastest possible when the laptop is not running on battery (see the NOLM_AC_CPU_MAXFREQ and NOLM_AC_CPU_MINFREQ options).

This setup works perfectly for my IBM Thinkpad T23. I hope it will work for you too.

---

### Post by zgornel on 2006-09-26
I simply removed powernowd from startup and run it manally when on batteries. Memory economy reasons ;)

---

### Post by m83 on 2006-09-26
> **zgornel said:**
> I simply removed powernowd from startup and run it manally when on batteries. Memory economy reasons ;)

How much memory do you have, zgornel? powernowd doesn't use much at all. I  see no reason to turn it off. On my machine powernowd uses 250 kB of memory.

---

### Post by illfingaz on 2006-09-27
> **m83 said:**
> It took me a while to find out how I could control the CPU Speed using laptop-mode, but I succedeed. I'll try to explain what I did as simple as posible.

The file that you need to modify is [FONT="Courier New"]/etc/laptop-mode/laptop-mode.conf[/FONT]. In that file search for the section [FONT="Courier New"]CPU frequency scaling and throttling[/FONT]. In that section you need to modify the values for BATT_CPU_MAXFREQ and BATT_CPU_MINFREQ so that they are equal to "slowest". My configuration is as follows:
```
BATT_CPU_MAXFREQ=slowest
BATT_CPU_MINFREQ=slowest
BATT_CPU_GOVERNOR=userspace
LM_AC_CPU_MAXFREQ=fastest
LM_AC_CPU_MINFREQ=slowest
LM_AC_CPU_GOVERNOR=userspace
NOLM_AC_CPU_MAXFREQ=fastest
NOLM_AC_CPU_MINFREQ=fastest
NOLM_AC_CPU_GOVERNOR=userspace
```

What I did there was forcing the frequency for the CPU to be the slowest possible when the laptop is running on battery power; exactly what you wanted. I also forced the frequency of the CPU to be the fastest possible when the laptop is not running on battery (see the NOLM_AC_CPU_MAXFREQ and NOLM_AC_CPU_MINFREQ options).

This setup works perfectly for my IBM Thinkpad T23. I hope it will work for you too.

Well I did as indicated in your post and at first I didn't have any luck, the laptop wouldn't switch when I unplugged/plugged the AC cord. I then removed the laptop-mode tools package and another package called laptop-mode, I re-installed the laptop-mode tools package from the package website, made the necessary changes in the conf file as per your post and viola, it works perfectly.

I'm assuming there was a conflict between the two packages (laptop-mode and laptop-mode tools). Thanks for your and everyone's help. Peace :D

---

### Post by m83 on 2006-09-27
Great. I'm glad you made it work.

---

### Post by EDzior on 2006-11-11
> **m83 said:**
> It took me a while to find out how I could control the CPU Speed using laptop-mode, but I succedeed. I'll try to explain what I did as simple as posible.

The file that you need to modify is [FONT="Courier New"]/etc/laptop-mode/laptop-mode.conf[/FONT]. In that file search for the section [FONT="Courier New"]CPU frequency scaling and throttling[/FONT]. In that section you need to modify the values for BATT_CPU_MAXFREQ and BATT_CPU_MINFREQ so that they are equal to "slowest". My configuration is as follows:
```
BATT_CPU_MAXFREQ=slowest
BATT_CPU_MINFREQ=slowest
BATT_CPU_GOVERNOR=userspace
LM_AC_CPU_MAXFREQ=fastest
LM_AC_CPU_MINFREQ=slowest
LM_AC_CPU_GOVERNOR=userspace
NOLM_AC_CPU_MAXFREQ=fastest
NOLM_AC_CPU_MINFREQ=fastest
NOLM_AC_CPU_GOVERNOR=userspace
```

What I did there was forcing the frequency for the CPU to be the slowest possible when the laptop is running on battery power; exactly what you wanted. I also forced the frequency of the CPU to be the fastest possible when the laptop is not running on battery (see the NOLM_AC_CPU_MAXFREQ and NOLM_AC_CPU_MINFREQ options).

This setup works perfectly for my IBM Thinkpad T23. I hope it will work for you too.

Did you setup this with working powernowd or cpufreqd? Or did you disable both of them and use only laptop-mode-tools?
P.S. Sorry for my english.
Regards.

---

