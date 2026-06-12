---
title: "Set cou frequency scaling on powersave"
date: 2008-08-23
forum: Hardware
---

### Post by sonnet on 2008-08-23
Hi I as per title want to set the cpu frequency scaling on powersave.
I usually graphically do it with the gnome applet named "cpu frequency scaling" that I add to the gnome panel.
But for some strange reason the option to change from "on demand" to "powersave" doesn't appear on the in the applet.
Does anybody know a way to do it with cli and check that's working?

---

### Post by Sam Lars on 2008-08-23
I think that the command
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```
will tell you what governor you're using.
You can then do
```
sudo cpufreq-set -g powersave -d 1000000
```
Where "powersave" is the governor you're setting and 1000000 is the minumum frequency (which may or may not be needed).

---

### Post by sonnet on 2008-08-24
> **Sam Lars said:**
> I think that the command
```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```
will tell you what governor you're using.
You can then do
```
sudo cpufreq-set -g powersave -d 1000000
```
Where "powersave" is the governor you're setting and 1000000 is the minumum frequency (which may or may not be needed).

Hi thanks for the reply,
the cat.. command worked and it showed that actually the cpu is set "on demand".
But the command cpufreq-set didn't work as I get error message "command not found" .Do I have to install anything to use that command?Or maybe the syntax is wrong?

---

### Post by Sam Lars on 2008-08-24
You have to install cpufrequtils
```
sudo apt-get install cpufrequtils
```
From the fact that the cat worked, you probably have cpufreqd installed... you can check.

---

### Post by Perkins on 2008-08-27
You actually don't need the utilities.

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
will tell you what you're currently using.

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
will tell you which ones are installed and usable.

Just alter the contents of scaling_governor to match the one you want to use.  The tools are nice for scripting purposes though.

---

### Post by Perkins on 2008-08-27
Oh.  Two more things.  The 8.04 seems to have 
"cpufrq-selector" installed, and it seems to work for my machine.  It must be run as root though.

Second, depending on which governor you select, there may be subdirectories off of cpu0 where you can set additional parameters that give more detailed control of how it behaves.

---

