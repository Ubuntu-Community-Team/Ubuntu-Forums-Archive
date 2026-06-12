---
title: "Pentium M Speed Step Vs. Low Priority Processes in Feisty"
date: 2007-07-20
forum: Hardware &amp; Laptops
---

### Post by F-3582 on 2007-07-20
Hi,

I just noticed a strange thing which I suppose is related to my upgrade to Feisty (probably kernel-related):

Whenever there is a low priority process, it doesn't matter how high its CPU usage might be, it never gets the CPU to enter high performance mode (in my case: switching from 600MHz to 1.7 GHz). Not much of an issue, you might think, but a few programs acually show issues because of this. Just let me give you two examples:

- Folding@Home: Before upgrading to Feisty it almost instantly made my CPU switch to maximum clock speed, but now only the benchmark at the beginning (obviously no low priority process) does this, the actual calculations only use the slower mode taking thrice the time it would normally take to finish a work unit.

- Opera: In order to prevent plugins from slowing down the browsing experience (wise choice) and because no one writes native plugins for Opera they use a plugin wrapper which is also run as a low priority process. Unfortunately this slows down almost any Flash animation I've seen so far while my CPU still runs with 100% usage at 600MHz.


Does anyone know if there's a workaround for this? Puh-Leeze :cry:

EDIT: I just confirmed this using the system monitor - Any process with a nice value higher than 0 is rendered unable to trigger the aforementioned event. Looks more like a feature than a bug...

---

### Post by F-3582 on 2007-08-04
Bumping this.

Okay, this might be a feature to save battery life or something. Unfortunately my laptop mostly runs on AC power and I also checked that there's no laptop mode activated.

My question is: Aside from setting the nice value <=0 are there any other ways to make these processes use the highest clock speed?

---

### Post by jpkotta on 2007-08-06
They changed the frequency throttle in Feisty.  It used to be a daemon in userspace, now it's in the kernel.  The defaults and the user interface are just about the only difference.  The following will make nice'd processes influence the governor:
```
sudo -i
echo 0 > /sys/devices/system/cpu/cpu0/cpufreq/ondemand/ignore_nice_load
exit
```
Put just the "echo" line in /etc/rc.local to autonomously do this at bootup.

---

### Post by F-3582 on 2007-08-06
Excellent! Thank you.

---

### Post by FluffyChicken on 2007-08-06
Same problem here, but using BOINC instead.

Pain in the butt.  I've been all around the control panel looking for Power Saving options, but there is only lid close etc..
I did find that adding the CPU Scaling Frequency Panel I could override the setting to my liking Performance or just locking it at max.  You also get the steps in between.

It still seems like an after thought though with nothing in the control panel to override these settings :(

---

### Post by michael37 on 2007-10-02
OK two major problems here.

First, the trick for manually setting ignore_nice_load to zero works only so far.  You see, when the computer goes to battery power, the settings for the ondemand governor (/sys/devices/system/cpu/cpu0/cpufreq/ondemand) reset!!!  I can't find which process resets those settings and how it does it.  

When computer goes back onto AC power, the ignore_nice_load is back set to 1, and the CPU is running in powersafe mode.

Second, previous version of Ubuntu didn't behave this way, so I have no idea what changed.  

Update:  I found something which I thought would make a difference.  It doesn't.  Creating a key
/apps/gnome-power-manager/cpufreq_consider_nice
and checking it (as in, yes, consider nice) achieves absolutely nothing.

---

### Post by michael37 on 2007-10-24
Another major update.  Gutsy seems to fix the problem.

Open gconf-editor, go to /apps/gnome-power-manager/cpufreq

and check box consider_nice.

Takes effect immediately.

---

### Post by F-3582 on 2007-10-26
Cool. No more crude hacks, then.

---

