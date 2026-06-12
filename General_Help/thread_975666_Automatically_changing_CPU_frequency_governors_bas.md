---
title: "Automatically changing CPU frequency governors based on keyboard/mouse activity"
date: 2008-11-08
forum: General Help
---

### Post by susanne260 on 2008-11-08
Using various keywords, I tried googling for the solution, but unfortunately had no luck.

I'm trying to get the "CPU Frequency Scaling Monitor" to automatically switch from the "Performance" governor to the "OnDemand" governor if there hasn't been any keyboard/mouse activity during 5 minutes.

And then automatically set it back to "Performance" if keyboard/mouse activity is detected.

---

### Post by susanne260 on 2008-11-13
Ok, I found out the command to change the CPU frequency governors. And after reading its manpage I figured out the commands I needed:

```
cpufreq-selector -g ondemand   # changes the governor to "ondemand"
```

and

```
cpufreq-selector -g performance   # changes the governor to "performance"
```


So, now all I need is to figure out how to make it run in the background as a daemon or something... and change the governor to "ondemand" if there hasn't been any keyboard/mouse activity in the past 5 minutes and automatically change it back to "performance" if keyboard/mouse activity is detected.

What ways are there to accomplish this? :KS

---

### Post by susanne260 on 2008-11-29
Ok, I've now installed Intrepid Ibex over Hardy Heron, but I'm still looking into this issue...

Pidgin allows you to do the same thing -- it automatically changes its status from "Online" to "Away" based on keyboard/mouse activity. So the same concept can somehow also be applied here, right? =)

---

### Post by sdennie on 2008-11-29
Is there a particular reason you want to do this?  Modern CPUs generally switch frequencies so quickly that it's impossible for a human to tell the difference between "performance" and "ondemand".

---

### Post by susanne260 on 2008-12-14
Thanks for the reply. =)

Well, the reason that I would like to do this is because the CPU on my computer (AMD Athlon X2 3800+) does not seem to switch frequencies very quickly if the "OnDemand" governor is selected. It appears that the CPU has to be in full load for at least about 4 seconds until it switches to a higher frequency.

That's a bit inconvenient, because all the windows lag quite a lot if the "OnDemand" governor defaults back to the lowest frequency. And it doesn't switch to a higher frequency unless it has been under full load for at least 4 seconds...

But then perhaps there is a way to decrease the time the CPU takes to switch to a higher frequency? Like from the default 4 seconds to perhaps 0.1 seconds? That would also solve the problem. :KS

---

### Post by sdennie on 2008-12-15
That's very odd behavior.  Are you sure the CPU is set to "ondemand" and not "conservative"?  Try using:

```

cpufreq-info

```

Also, what graphics card do you have?  Nvidia?  If so, this guide may solve the problem: [ HOWTO: Improve NVidia Laptop Graphics Performance]("http://ubuntuforums.org/showthread.php?t=828369")

---

### Post by susanne260 on 2008-12-16
Yes, it is switched to OnDemand, not Conservative. I'm using the "CPU Frequency Scaling applet" on gnome-panel to switch governors/frequencies.


Here's the output of "cpufreq-info" (I had to install the "cpufrequtils" package in order to run "cpufreq-info"):
```

$ cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: powernow-k8
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 1000 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 1.80 GHz, 1000 MHz
  available cpufreq governors: conservative, powersave, ondemand, userspace, performance
  current policy: frequency should be within 1000 MHz and 2.00 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz.
analyzing CPU 1:
  driver: powernow-k8
  CPUs which need to switch frequency at the same time: 0 1
  hardware limits: 1000 MHz - 2.00 GHz
  available frequency steps: 2.00 GHz, 1.80 GHz, 1000 MHz
  available cpufreq governors: conservative, powersave, ondemand, userspace, performance
  current policy: frequency should be within 1000 MHz and 2.00 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz.

```


> Also, what graphics card do you have? Nvidia?

Nope, I have the Ati Radeon x1900xtx graphics card.


Thanks for trying to help, though. :)

---

### Post by tfy on 2008-12-16
What ways are there to accomplish this.

---

### Post by Ahadiel on 2008-12-16
The first thing that popped into my mind was making a pidgin plugin to hook status changes (ie. going idle), and have it run the appropriate commands. However I've never made a plugin for pidgin before, so best of luck to you :D

---

### Post by susanne260 on 2009-03-18
Still looking for a way to do this. Anyone? :)

---

