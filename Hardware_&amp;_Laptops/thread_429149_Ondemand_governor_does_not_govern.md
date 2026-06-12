---
title: "Ondemand governor does not govern"
date: 2007-04-30
forum: Hardware &amp; Laptops
---

### Post by Cansy on 2007-04-30
Here I go:

My problem is that the ondemand governor does not change frequencies at all while my laptop is plugged in.  (It's a Sony Vaio S460.  I'm running Feisty Fawn.)  The conservative governor appears to have exactly the same issue.  It stays at the full frequency all of the time.

When I am on the battery the ondemand governor works properly, meaning it stays at 800mhz unless the processor actually needs to go higher.  This is how I would like the processor to work all of the time.

I've been using the "CPU Frequency Scaling Monitor" desktop panel applet to watch the frequency change, and its frequencies seem to be accurate.

---

Some things that I have tried:

I have found that laptop-mode has no effect on my problem with the ondemand governor.  With a bit of effort, I was able to use laptop mode to determine which governor to use.  (You can change laptop-mode settings by editing /etc/laptop-mode/laptop-mode.conf .  You can check to see if laptop_mode is running with "cat /proc/sys/vm/laptop_mode".  Anything but 0 means it is running. 2 is the only other value I can remember seeing.)

(Here's the most useful tip to anyone who is having trouble controling the cpufreq governor: ) The Gnome Power Manager seems to be the default method of controlling the governor, but the normal gui does not give you access to the right options, so you have to use gconf.  Open gconf-editor (It's the Configuration Editor under Applications>System Tools) and look at the entries under apps > gnome-power-manager.  You can use cpufreq_ac_policy and cpufreq_battery_policy to control which governor is used under ac and battery power.  Setting cpufreq_ac_performance to the same value as cpufreq_battery_performance has had no effect.

I've been able to change which frequency the ondemand governor sticks at by echoing various values to /sys/devices/system/cpu/cpu0/cpufreq/ondemand/powersave_bias .  It takes values from 0-1000 and reduces the frequency requested by the ondemand governor by 0-100%.  (0 is the default value.)  This hasn't helped the governor ramp up and down though.  It just stays around a lower frequency.

Manually setting the governor to the ondemand governor has had no helpful effect for me.

---

For the moment I have the governor set to userspace and I am using powernowd to do frequency stepping when I am plugged in, but I am not particularly happy with it.  The ondemand governor works exactly as I want it to, but only when I am running on the battery, so any help in getting it to work the same way on ac would be appreciated.

---

### Post by nick122147 on 2007-05-01
I have the same problem - sometimes. Sometimes it works as normal. havn`t investigated further.

---

### Post by VuDu on 2007-05-01
I had the same problem on Edgy, but then searched adn tried everything and happened to solve the problem and forget it... too bad that now that I made a fresh install of Feisty the problem is back :(
I don't know what I did before, I just recall trying everything till finally solving it...

---

### Post by Cansy on 2007-05-02
Ok, I've figured out how to fix the problem for me.

It turns out that I had considerably more cpu usage on ac than on the battery.  I thought I had eliminated that possibility but I didn't look closely enough.  The cpu usage is being caused by a buggy smp enabled kernel and this bug apparently affects some Sony and Asus laptops specifically.  Who knows what switching off ac has to do with anything.

[http://bugzilla.kernel.org/show_bug.cgi?id=8193](http://bugzilla.kernel.org/show_bug.cgi?id=8193) is a Kernel bug that was filed and apparently fixed, so maybe the next Ubuntu kernel won't have any problems.

In the mean time, I was able to get everything working by adding "nosmp acpi=noirq" to the kernel boot options.  Also, "nosmp irqpoll" works.  Both of these give (different) error messages, but I have not yet seen any negative side effects.

[https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=219852](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=219852) is where I found this solution, one person reported problems with printing and automount (with irqpoll) and with wireless (acpi=noirq)

Recompiling the kernel with smp disabled also should work, but that causes enough other troubles that I didn't try.

---

### Post by VuDu on 2007-05-02
Nice, I noticed that high processor too, but again... I thought it wasn't related to the governors (I thought it had to do with the graphics drivers and reported it the wrong topics).

When will that fix be implemented to the kernel? Next release?

---

