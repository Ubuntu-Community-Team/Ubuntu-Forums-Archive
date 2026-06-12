---
title: "Frequency Scaling Problem"
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by hormati on 2007-04-23
Hi all,
I just updated from Edgy to Feisty. I had cpu frequency scaling all set up in Edgy. I had added 
echo -n "conservative" > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
in my bootmisc.sh. So, after boot "conservative" was my scaling governor. In Fiesty, my problem is that whatever I do my scaling governor reverts to "ondemand". I can change it by hand to "conservative" but after reboot, or after I unplug or plug the AC, it just goes back to "ondemand". 

I do not have powernow or cpudyn installed. I have laptop mode(it is enabled in acpi-support), and I changed the following lines:
CONTROL_CPU_FREQUENCY=1

BATT_CPU_MAXFREQ=fastest
BATT_CPU_MINFREQ=slowest
BATT_CPU_GOVERNOR=conservative
LM_AC_CPU_MAXFREQ=fastest
LM_AC_CPU_MINFREQ=slowest
LM_AC_CPU_GOVERNOR=conservative
NOLM_AC_CPU_MAXFREQ=fastest
NOLM_AC_CPU_MINFREQ=slowest
NOLM_AC_CPU_GOVERNOR=conservative

So, there is nothing in there about ondemand. I am completely clueless. I do not know what is changing my scaling governor to ondemand. Any ideas?

one more thing, my laptop-mode status says that my laptop-mode is started and running.
Thanks,
Amir

---

### Post by Angry penguin on 2007-05-05
Try adding the command you use to fix it, to the sessions dialog and restarting.

---

