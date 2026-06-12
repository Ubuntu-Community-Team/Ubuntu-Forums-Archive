---
title: "Laptop overheats (only in ubuntu)"
date: 2009-03-12
forum: Hardware
---

### Post by quirijnquintus on 2009-03-12
Hey, I recently installed ubuntu, so I am noob. But the problem is my cpu doesn't rev up when temp is getting to high. It does work properly in WindowsXP.. 
I read some articles and tried lm-sensors to work, but the my old laptop doesn't have any sensors which are found. 
After about 15min it reaches a temp of 85C and rising :(

Is there another way to control my CPU fan?

[SIZE="1"]Iam running:
Fujitsu Siemens Amilo L1310G
1.60Ghz Celeron
512DDR RAM 
80GB HDD[/SIZE]

---

### Post by quirijnquintus on 2009-03-16
anyone?

---

### Post by brandon88tube on 2009-03-16
Not sure exactly what your problem is, but I made a thread a while back that might be of some help. [http://ubuntuforums.org/showthread.php?t=1008478](http://ubuntuforums.org/showthread.php?t=1008478)

---

### Post by quirijnquintus on 2009-03-16
He thanx for your reply. I did try that, but changing my CPU frequency is not supported, unfortunately :(

---

### Post by quirijnquintus on 2009-03-18
bump up!

---

### Post by opto-laptop on 2009-03-18
The CPU fan speed is usually maintained by the hardware not the O/S. It may just be that it only runs the CPU full speed/full voltage (ie hot) in ubuntu and keeps it throttled in your other OS.

As I've answered in another thread today 
[LIST]
[*]Clean the vents out
[*]clean the fan blades if you can
[*]remove the battery if you only use it on a desk and plugged in. Charging adds heat to the chassis.
[/LIST]

Otherwise, check the bios settings to ensure there are no "quiet" mode settings. Make sure the fans actually are running. Running the CPU 100% for days should not get above 50 degrees ideally.

Good luck.

---

### Post by quirijnquintus on 2009-03-18
The fan has been repaired with new bearings and grease and is properly working, as it works perfectly in windows. It revs up when it gets too hot and eases up when cool.
However in Ubuntu, it does work but only at one speed, a very low one, which is not enough to cool the processor down, so gradually it will heat up.

I'll check my BIOS but I never saw any feature like you mentioned.

---

### Post by lebbok on 2009-05-02
> **quirijnquintus said:**
> Hey, I recently installed ubuntu, so I am noob. But the problem is my cpu doesn't rev up when temp is getting to high. It does work properly in WindowsXP.. 
I read some articles and tried lm-sensors to work, but the my old laptop doesn't have any sensors which are found. 
After about 15min it reaches a temp of 85C and rising :(

Is there another way to control my CPU fan?

[SIZE="1"]Iam running:
Fujitsu Siemens Amilo L1310G
1.60Ghz Celeron
512DDR RAM 
80GB HDD[/SIZE]

Have you tried adding the following switch at boot <edit /etc/boot/menu.lst> acpi.power_nocheck=1, but this seems to only work 50% of the time.  What I have done as well is in a terminal window to use the following switches
sudo echo 3 > /proc/acpi/fan/FAN0/state
sudo echo 3 > /proc/acpi/fan/FAN1/state
and the echo 0 > /proc/.... both fans and that seems to kick start the fans if the switch doesn work.

---

### Post by quirijnquintus on 2009-05-02
I have just switched to jaunty jack 2 mins ago. And it seems that this doesn't have effect on the problem. I'll have to find out how to these things. I'll report later.

---

### Post by endre on 2009-05-02
I tried posting a thread on a very similar issue yesterday - my laptop gets very hot, despite there being plenty of fan-noise, and CPU scaling is apparently not supported - Ubuntu claims it is running the CPU at 100% capacity when running at roughly 600 MHz (but still, oddly, heats up immensely)

And, also oddly - this is not an issue in XP at all.

Anyone, any ideas? Without a fix for this, Ubuntu will never really be able to work as a primary system for me, or for anyone else with a similar problem, I suspect - the noise and the heat is just too much.

(System is a 5 year old Pentium M, 1.6 GHz, 1Gb RAM)

---

