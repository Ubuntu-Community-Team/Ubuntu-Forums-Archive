---
title: "A complex situation"
date: 2008-05-04
forum: Hardware
---

### Post by Alessandro Allegri on 2008-05-04
Ok, let me tell you my situation.
Zd7000, P4 3.4GHz, Nvidia GeForce something.
Upgraded from Gutsy to Hardy (Hasty?) a week ago. Everything was working ok until...
Last night I passed to battery power for a while, and in 10 mins Hardy sucked my (already oldish) battery out in Joule effect.
Plugged in power supply again, but the heating wouldn't go off (around 60°C, while Gutsy would dwell in the 40's).
So I looked for a solution: uninstalled powernowd, installed cpufrequtils, modprobed p4_something (as in [http://howtoforge.com/cpu_frequency_scaling_ubuntu](http://howtoforge.com/cpu_frequency_scaling_ubuntu)), added the same module to the modules file, chose a governor (ondemand).
Heating still on, no sign of improving.
I read that the video drivers might be the cause, so I downloaded envyng, uninstalled the former drivers and installed the new ones. Now I am in the fantastic predicament of having Hardy unpredictably cut off my pc (no switching off procedure, just plain and brutal cut off) at leisure. Uninstalled nvidia through envyng, same thing.
Bonus: heating still on.
Then I followed directions in [http://ubuntuforums.org/showthread.php?t=781057](http://ubuntuforums.org/showthread.php?t=781057), reinstalled nvidia-legacy.
Now the temperature thing is much better. But it keeps cutting off unexpectecly. Besides, doing the nvidia-setting thing, it says to use nvidia-xconfig because it appears I am not using nvidia drivers.
What the heck??! 
Now it's either I find a quick and steady solution, or I'll have to say goodbye to Hardy and find a way back to old faithful Gutsy...
Any ideas?
Thanks,
A.

---

### Post by Alessandro Allegri on 2008-05-04
To be more precise, 

```
$ lshw -C video
WARNING: you should run this program as super-user.
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: NV36 [GeForce FX Go5700]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: vga_controller bus_master cap_list
       configuration: latency=40 maxlatency=1 mingnt=5

```

---

