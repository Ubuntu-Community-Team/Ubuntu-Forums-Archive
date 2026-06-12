---
title: "Re-enable CPU Frequency scaling on my laptop"
date: 2007-11-09
forum: Hardware &amp; Laptops
---

### Post by popophobia on 2007-11-09
I had my CPUfreq managed by powernowd before. Then, in the search to find out what freezes my system, I tried to replace powernowd with cpufreqd with this guide.
[http://ubuntuforums.org/showthread.php?t=394911](http://ubuntuforums.org/showthread.php?t=394911)


Thing is, I restarted the computer after removing powernowd. Now, even after installing cpufreqd, it does not seems that I can manage my CPU freq anymore (the folder /sys/devices/system/cpu/cpu0/cpufreq does not exist anymore :( )

Now, how can I re-enable CPU scaling again? Thanks very much for any pointer or help

edit: link edited

---

### Post by dedalos on 2007-11-10
I will try to help from what i did.

1. U dont need deamons running for CPU scaling (powernowd and cpufreqd)
2. U need to load modules in /etc/modules file for governors and CPU scaling to work direct with kernel, [http://ubuntuforums.org/showthread.php?t=248867](http://ubuntuforums.org/showthread.php?t=248867)) at step 6 
3. From my experience run gconf-editor and in apps>gnome-power-manager>cpufreq
in policy_ac make it (nothing)and policy_battery again (nothing)should both be ondemand.
somehow gnome-power-manager dont work very well with cpufreq or sysfs ,with this your CPU scaling should be faster.
install the (cpufrequtils) and (sysfsutills) if u dont have them

read carefully the above link and i hope u make it

---

### Post by cubeist on 2007-11-10
do you have an intel or amd processor... if amd, your best bet is powernowd... you could reinstall it via synaptic...

---

