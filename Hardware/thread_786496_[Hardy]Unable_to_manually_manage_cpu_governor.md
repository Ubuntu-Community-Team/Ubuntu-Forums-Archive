---
title: "[Hardy]Unable to manually manage cpu governor"
date: 2008-05-08
forum: Hardware
---

### Post by Skumpic on 2008-05-08
Hi, i'm an italian user of Ubuntu Hardy on a Hp nx6110 laptop.
Using the previous release of Ubuntu i was used to configure the scaling feauture of my cpu with the module p4_clockmod (following the indication of this howto: [http://ubuntuforums.org/showthread.php?t=582069&highlight=p4-clockmod+scaling](http://ubuntuforums.org/showthread.php?t=582069&highlight=p4-clockmod+scaling)), and then to manually manage cpu governor thru the gnome-applet cpu freq scaling monitor (setting the right bit with > sudo chmod +s /usr/bin/cpufreq-selector)

The problem is that with the last release of Ubuntu (hardy) i can get the cpu scaling work, but i'm no longer able to manually manage the governor.
Whatever i set i'm not able to change the cpu frequency.

Anyone know how to give me the power back??? :)

Thanks in advance
Skumpic

---

### Post by Skumpic on 2008-05-13
Anyone ????

---

### Post by Tomatz on 2008-05-13
I saw somewhere that cpufreq was broken in hardy. I tried to use it with my athlon X2. Uninstalled powernowd installed cpufrequed but powernowd was still running in services. 

I just turned off cool n quiet in the bios and now my cpu is throttled maximum.

But i guess you cant do that with a p4.

---

### Post by wakady on 2008-05-13
if i remember right this shall do it
> sudo chmod +s /usr/bin/cpu-freq-selector

dont forget to add cpu freq applet  :)
enjoy

---

### Post by sdennie on 2008-05-13
I'm not sure how to fix your problem but, is there a particular reason that the ondemand governor doesn't fit your needs?  It sounds non-intuitive but, it turns out that ondemand is more efficient than conservative and, it scales up quickly enough that it's probably impossible to distinguish it from performance.

---

### Post by Skumpic on 2008-05-14
Hi vor, simply because when my laptop battery is going low the sistem start to reduce the maximum speed of the cpu and this is make the system unusable.
- When my battery is at 80% of charge the maximum speed of the cpu is reduced to 1ghz
- When the battery is at 50% of charge the maximum speed of the cpu is reduced to 825mhz
- When is at 20-25% of charge the maximum speed of the cpu is reduced to 525mhz

This make hard for me to work with programs like gimp or openoffice.
I'm still trying to find a solution :(

---

