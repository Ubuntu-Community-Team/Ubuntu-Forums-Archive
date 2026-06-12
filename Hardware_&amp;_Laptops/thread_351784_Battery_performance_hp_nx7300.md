---
title: "Battery performance hp nx7300"
date: 2007-02-02
forum: Hardware &amp; Laptops
---

### Post by mlakilud on 2007-02-02
Hi everyone,
I am having some problems on my brand new laptop HP nx7300. It is a C2D T5500,2gb ram, GMA950.
When I am running on AC everything is ok. However, when I unplug the power the sound in Amarok, and whole machine simply freezes for a sec or two every 2 min. 
Also, I cannot start Ubuntu when I am on battery, the startup process freezes every time on the first third of the startup bar.

I am using Ubuntu 6.10 32bit.

Thanks in advance,
Mladen

---

### Post by capdog on 2007-02-07
Hi Mladen

Did you solve any of your problems? I'm also trying to get Ubuntu to work on my NX7300, problems with speedstep and "bad state", as well as suspend.

Thanks
capdog

---

### Post by mlakilud on 2007-02-13
I solved "bad state" problem.
You must unload psmouse module in halt and reboot scripts

Cpu frequency scaling works, but I must set max frequency manually on every boot.
 sudo -s
echo 1667000 > /sys/devices/system/cpu/cpu0/cpufreq/scaling_max_freq
echo 1667000 > /sys/devices/system/cpu/cpu1/cpufreq/scaling_max_freq

Suspend to ram doesn't work yet and probably never will on 2.6.17 kernel. I have managed to suspend to disk, but I have problems with resolution when computer wakes up. This will work eventually. 

I use kpowersave for changing between cpu modes and it works flawlessly.
added the following to /etc/modules 
cpufreq_conservative
cpufreq_ondemand
cpufreq_powersave
cpufreq_stats
cpufreq_userspace

to enable frequency scaling

I will not give up :)

---

