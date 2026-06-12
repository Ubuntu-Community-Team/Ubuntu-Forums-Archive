---
title: "Power managment on a Dell XPS 14z with ubuntu 11.10"
date: 2012-03-27
forum: Hardware
---

### Post by maunz on 2012-03-27
Hi, I just bought a Dell XPS 14z and installed ubuntu 11.10 on it. It seem to work pretty good except that the batteeries drains a lot faster when using ubuntu. I have 7 hours battery time on w7 at low activity and only about 3 on  ubuntu. So far I've installed Bumblebee to keep my graphic card from being active all the time but the power consumtion is still pretty high. It's about 20 W in idle mode according to powertop.

I have read a lot about other options but can't really put the peaces together. I've read about powersave at this link:

[https://help.ubuntu.com/community/PowerManagement/ReducedPower](https://help.ubuntu.com/community/PowerManagement/ReducedPower)

and also a bit at lesswatts.com but I don't really feel experienced enough to create my own tweak files and how i should do it. Has anyone done any similar thing or have any usefuls tips? I'm pretty new to ubuntu so please try to explain it simple. 

some specs:
Intel(R) Core(TM) i7-2640M CPU @ 2.80GHz (with 3.5 GHz boost that by the way doesn't seem to be working)
8 GB RAM
SSD disc: xD/SD/M.S.

I don't really know what specs are necessary.
does anyone know a good guide or have any tips I would really appreciate it.

Thanks!
//maunz

---

### Post by ashindeed on 2012-03-27
Try the tips from the  following link  [https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks]("https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks")

By far, the biggest powersaving comes by doing this at terminal

 1. sudo gedit /etc/default/grub 
 2. change: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
       to:
     GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **i915.i915_enable_rc6=1**"

 3. sudo update-grub

---

### Post by 2F4U on 2012-03-27
I would like to point you to a set of scripts with some more advanced power management settings. They were originally developed for ThinkPad laptops running Ubuntu, but from my own experience I can say that most of those settings also work on other brands (except the battery threshold settings).

[https://github.com/linrunner/TLP/wiki/TLP-Linux-Advanced-Power-Management](https://github.com/linrunner/TLP/wiki/TLP-Linux-Advanced-Power-Management)

---

### Post by maunz on 2012-03-27
> **ashindeed said:**
> Try the tips from the  following link  [https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks](https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks)

By far, the biggest powersaving comes by doing this at terminal

 1. sudo gedit /etc/default/grub 
 2. change: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
       to:
     GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **i915.i915_enable_rc6=1**"

 3. sudo update-grub

Thanks a lot, this works beautifully!

---

### Post by maunz on 2012-03-27
> **2F4U said:**
> I would like to point you to a set of scripts with some more advanced power management settings. They were originally developed for ThinkPad laptops running Ubuntu, but from my own experience I can say that most of those settings also work on other brands (except the battery threshold settings).

[https://github.com/linrunner/TLP/wiki/TLP-Linux-Advanced-Power-Management](https://github.com/linrunner/TLP/wiki/TLP-Linux-Advanced-Power-Management)

I installed this and I think its running as it should, is there anyway to make sure it works properly?

I used the default settings altough I enabled
 CPU_SCALING_GOVERNOR_ON_AC=ondemand  CPU_SCALING_GOVERNOR_ON_BAT=ondemand

by removing the '#' in front of them in the tlp file, do you have any more 
tips on configurations? Everything on my laptop seem to be working so far and 
I've gotten the discharge rate down to about 15 W (while writing this) which 
is great! Ill make sure to post any updates if something goes wrong or I find 
some more configurations.

---

