---
title: "prevent CPU scaling on battery"
date: 2008-05-30
forum: Hardware
---

### Post by DesiDishoom on 2008-05-30
i recently installed ubuntu 8.04 onto my hp tx2000z laptop. i am a sucker for desktop effects, and have a lot of stuff running with compiz-fusion. however, the laptop runs visibly slower on battery, because the CPU is scaled down to 36% (800 Mhz). Unfortunately, when i try to change it from the 800 Mhz setting, or even the powersaver setting, it does not change...is there some hardware setting that i'm overlooking here? i know for a fact that there are 1.6, 1.8, 2.0 ghz and max 2.2 ghz settings available on the CPU.

i could really use some help in getting my CPU running in the little more respectable 50% range or so...36% is ridiculously low.

thanks a ton.

---

### Post by stchman on 2008-05-30
> **DesiDishoom said:**
> i recently installed ubuntu 8.04 onto my hp tx2000z laptop. i am a sucker for desktop effects, and have a lot of stuff running with compiz-fusion. however, the laptop runs visibly slower on battery, because the CPU is scaled down to 36% (800 Mhz). Unfortunately, when i try to change it from the 800 Mhz setting, or even the powersaver setting, it does not change...is there some hardware setting that i'm overlooking here? i know for a fact that there are 1.6, 1.8, 2.0 ghz and max 2.2 ghz settings available on the CPU.

i could really use some help in getting my CPU running in the little more respectable 50% range or so...36% is ridiculously low.

thanks a ton.

This may help, you may have to backwards use it.

[http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/](http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/)

---

### Post by jocko on 2008-05-30
Have you tried changing the cpu frequency policy in gnome-power-preferences?
System-->Power managment-->Battery power; change the policy from "Maximum power saving" to "based on processor usage" or "always maximum speed"

---

### Post by DesiDishoom on 2008-05-31
> **jocko said:**
> Have you tried changing the cpu frequency policy in gnome-power-preferences?
System-->Power managment-->Battery power; change the policy from "Maximum power saving" to "based on processor usage" or "always maximum speed"
hmm my power management preferences don't have those options.

all it has options for are when to turn off display, what to do when the lid is closed, etc.

do i need to install a package to allow for what you suggested? cause it seems like that's exactly what i need.

---

### Post by NikoC on 2008-05-31
What works for me for constant maximum performance is the following (in a terminal type):
sudo cpufreq-selector -g performance

To set it back to auto use:
sudo cpufreq-selector -g ondemand

To set it to low speed:
sudo cpufreq-selector -g powersave

Cheers, hope it works!

---

