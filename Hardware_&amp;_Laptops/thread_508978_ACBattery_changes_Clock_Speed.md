---
title: "AC/Battery changes Clock Speed"
date: 2007-07-24
forum: Hardware &amp; Laptops
---

### Post by marius311 on 2007-07-24
I have an Alienware m5500 laptop, P4 3.2GHz. The problem is basically this: If I reboot plugged into the wall then unplug (and go on battery), the clock slows down. I can tell b/c it looses about 10min per hour, and my music/video stutter when they play back. If I plug back in, it goes right back to normal. Now if I reboot on battery, then plug in, my clock goes fast, again about 10min per hour. 

My processor does not have CPU scaling, however it has always gone way slower when on battery (slower as in my programs go slower, not the clock). I don't have this problem in Windows. 

I tried booting with noapic, nolapic, apci=off, notsc, .... and other stuff as mention in other posts, but same results (or crash on boot). 

Any ideas what could be causing this?

---

### Post by Spartan.II.117 on 2007-07-25
are you shure there's no processor scailing? look for settings in your bios, and check the listed clock speed when starting on ac vs battery.

---

### Post by marius311 on 2007-07-25
I can't directly scale it to what ever I want, but I suppose there must be something there since as I said my computer has always slowed down when on battery power. 

Anyway, some more info. If run hwclock I get the correct time always, but if I run date, I get the screwed up time. For example, say I boot up plugged in. I do a "Synchronize Now" (hwclock and date both are correct and synchronized) then unplug and let it sit on battery for 1hr. hwclock now correctly reports the time as 1hr later, whereas date thinks its been about 50min.

So I guess the problem is that my processor gets scaled down when on battery power, but ubuntu doesn't know about this... however if I boot into AC or battery then its fine... so somewhere in there it must figure out my processor speed and scale accordingly. My question is, whats the command, and how do I add it to some script that runs automatically when I switch power source?

---

### Post by Spartan.II.117 on 2007-07-26
in your bios, you should be able to set the power saving prefrences including, possibly O/S control, you should try looking there, then you should'nt need a comand

---

### Post by marius311 on 2007-07-30
I couldn't find any settings in my BIOS that have anything to do with clock speed. Is there anything else I can do besides hitting F2 at startup?

However, I did find this. A site suggested doing cat /proc/cpuinfo. I did it once after rebooting on battery, and once after rebooting on AC power. Here are the differences:

AC:

[FONT="Arial"]processor       : 0
model name      : Intel(R) Pentium(R) 4 CPU 3.20GHz
cpu MHz         : 3200.361
bogomips        : 6406.07
processor       : 1
model name      : Intel(R) Pentium(R) 4 CPU 3.20GHz
cpu MHz         : 3200.361
bogomips        : 6394.38[/FONT]

Battery:

[FONT="Arial"]processor       : 0
model name      : Intel(R) Pentium(R) 4 CPU 3.20GHz
cpu MHz         : 2752.752
bogomips        : 5512.13
processor       : 1
model name      : Intel(R) Pentium(R) 4 CPU 3.20GHz
cpu MHz         : 2752.752
bogomips        : 5495.72[/FONT]

However, if I plug/unplug while my computer is on, then do cat /proc/cpuinfo, theres no change in those numbers (even though its obvious my processor is getting slower).

So what I think I need is something that "rereads" cpuinfo.. or something like that... any ideas?

---

### Post by marius311 on 2007-07-30
I swear I dreamt about bogomips last night.... 

Anyway.. this is just a glorified bump. I found in the kernel source where bogomips get calculated, in init/calibrate.c (2.6.20). I'm sure thats the problem cause apparently bogomips get used in udelay() which i bet is what linux keeps time with. Past that I have no idea what to do. Barring someone coming to the rescue, I'm probably gonna try to compile the 2.6.22.1 kernel and hope to god it just works...

---

