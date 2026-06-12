---
title: "acer laptop: suspend, battery usage, touchpad sensitivity, fan"
date: 2006-01-11
forum: Hardware &amp; Laptops
---

### Post by jimmyp on 2006-01-11
I have an acer travelmate 4650 with breezy installed. I can hibernate the machine by going System->Log Out->Hibernate but hitting fn+f4 doesn't have any effect on the machine's state.  I don't get anything in dmesg or anything when I run acpi_listen and hit fn+f4. If I go to System->Preferences->Keyboard Shortcuts there is a Sleep action associated with fn+f4. Through some testing and swapping I found out that fn+f4 is being recognized but that the Sleep action has no effect. Does anyone know where I can find what Sleep is supposedly doing so I can try to fix it?

Also, does anyone's battery monitor show less time remaining in linux than in windows? When I am running on battery my cpu frequency applet shows that the machine is running at its slowest speed, but the battery time remaining is setill lower in linux.

Is there a tool that I can use to graphically change the sensitivity of my synaptics touchpad? I'd also like to be able turn tap-to-click on and off graphically (other people use the machine sometimes)

It seems that my fan never turns off in linux whereas in windows it turned on and off.  Is there something that doesn't get installed by default that will fix this?

Thanks.

---

### Post by ys4_sinau on 2006-01-11
helo jimmyp

i have same problem.

i use travelmate 2355, i can hibernate my laptop, but my battery indicator didn't work properly. 

when i boot with battery power, indicator show 29% remaining, everytime i boot. then i connect to ac power until charge 100%. then i disconect ac power. the battery indicator show properly.

i try to find information
cat /proc/acpi/battery/BAT1/state
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            0 mA
remaining capacity:      992 mAh
present voltage:         15243 mV

i wonder why present rate show 0 mA on charge or discharge

---

### Post by jimmyp on 2006-01-12
Our problems are probably different.  You seem to have a display problem whereas mine is probably caused by linux taking more power than windows.  I'm going to take the passive route, abandon my linux partition and hope that these problems are fixed in dapper.  I'm a law student and I'm not going to be the only  one whose fan blows throughout class.

---

### Post by GuyveR800 on 2006-01-13
sounds like CPU Frequency Scaling (or even ACPI) isn't working, this would explain both the fan being on and the shorter battery life.

---

### Post by jimmyp on 2006-01-13
I know cpu scaling is working because I have the gnome applet showing me the fluctuations in frequency.  I had to use the acpi-cpufreq module though because speedstep-centrino won't load.  apparently speedstep-centrino is the only one that will do voltage scaling, which should help with power.  The others only do frequency scaling.  This plus the fan running all the time is a probable cause of the diminshed battery life in linux.  I filed a bug report about it here:

[http://bugzilla.ubuntu.com/show_bug.cgi?id=22347](http://bugzilla.ubuntu.com/show_bug.cgi?id=22347)

---

### Post by jimmyp on 2006-01-14
Apparently ubuntu is upgrading their bug database or something.  The bug is listed here now:

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/28433](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/28433)

---

