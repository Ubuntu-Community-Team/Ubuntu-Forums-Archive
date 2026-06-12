---
title: "Lenovo ThinkPad X121e loud fan"
date: 2011-10-18
forum: Hardware
---

### Post by ghsdrggr on 2011-10-18
Hello I'm running Ubuntu 11.10 64bit on a Lenovo ThinkPad X121e with Intel i3-2357M CPU. The problem is that even when the Laptop is in idle the fan seems to run at max speed (or at least so fast that i can hear it good). When running windows the fan is inactive most of the time and only starts every few minutes.  /proc/acpi/ibm/fan says the fan is running at 566rpm with level "auto".  /proc/cpuinfo says the CPU is running at 800mhz so i assume it already gets clocked down automatically.  According to lm-sensors "temp1" and "temp3" are 52°C and Core0 50°C.  Is there any way to make my laptop less noisy?

---

### Post by ghsdrggr on 2011-10-19
Bump

---

### Post by ghsdrggr on 2011-10-20
Last try -Bump-

---

### Post by lads on 2011-11-10
Hi, I'm having a similar problem with a Lenovo ThinkPad T420.

With 11.04 the battery would run for more than 5 hours, but after upgrading to 11.10 it usually dries in little over an hour (it doesn't last a 2 hour meeting).

Though this laptop is generally silent, I noticed that the fan seems to be now constantly at full speed, you don't hear it slow down when you close the lid for instance. Could this be the cause of the higher power consumption?

Thank you.

---

### Post by lads on 2011-11-11
Here are the latest developments:

[LIST]
[*]I found [a guide that explains how to activate the ThinkPad Fan]("http://putokaz.wordpress.com/2011/11/02/fixing-cpu-fan-on-lenovo-thinkpad-t520/"). These instructions worked for my ThinkPad T420 and should possibly work for yours too.
 
[*]When I boot Ubuntu disables back the thinkfan, which may be . I hope to get thinkfan running at startup soon.

[*]Most importantly, the fan never goes below level 5 with the graphical environment. You just need to be moving between workspaces, changing between windows and the like to get the fan to full speed (7). I experimented closing all windows and disconnecting from the internet and still the fan didn't get below level 5. Apparently this latest version of Compiz is a processor hog. In the coming days I'll install Xfce or Fluxfox to see if it improves things.
[/LIST]

Best.

---

