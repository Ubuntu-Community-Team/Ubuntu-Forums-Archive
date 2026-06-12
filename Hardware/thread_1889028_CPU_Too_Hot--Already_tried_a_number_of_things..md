---
title: "CPU Too Hot--Already tried a number of things."
date: 2011-11-30
forum: Hardware
---

### Post by abgemacht on 2011-11-30
Recently, I installed 11.10 on a 2nd partition on my laptop so I could easily ssh into my lab computer.  I really like it, and I'd love to use it as my main OS, but I'm having a serious CPU heating issue.

Of my four cores, at least one is always running at 2GHz (max freq), even when my computer is idling.  According to Psensor, I'm running at around 77C, which is just too hot.  I don't have heating issues on my Win7 partition, so I know it isn't a heatsink issue.

Here's what I've tried:  

Used the CPU Frequency Scaling monitor to try "conservative" and "on demand" settings.  Also tried locking the cores at the lowest clock speed.  Didn't help the heating problem.

Followed this ([http://ubuntuforums.org/showthread.php?t=539365&highlight=fan+speed]("http://ubuntuforums.org/showthread.php?t=539365&highlight=fan+speed")) link and did what it said.  This actually seemed to help.  For a while, my CPU was running at a nice 55C and there were no performance issues.  However, after a day or so, the heating issue resumed, so maybe this was just a coincidence?

Followed this ([http://www.go2linux.org/how-to-configure-cpufreqd]("http://www.go2linux.org/how-to-configure-cpufreqd")), but I always get a "no socket found error", even though I have enable_remote=1 uncommented.

Finally, I tried this ([http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html]("http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html")), although, honestly, I'm not sure what it is supposed to do.  Again, no change.

I've read something about the newest kernel having it's on scaling services, so I'm not sure if anything I've listed above even did anything, but I'm a little nervous going into the kernel without learning more.

So, if anyone is able to help me get my CPU down to a reasonable temp, I'd greatly appreciate it.  I'd love to start using 11.10, but it is not functional in this condition

Thanks!


[EDIT] For reference, while browsing the web on Win7, my CPU ranges from 40-45C.  While doing nothing on Ubuntu, it's around 75-78C.

---

### Post by Dlambert on 2011-11-30
Install the latest, or roll back to a previous kernel maybe? Just a suggestion.

---

### Post by abgemacht on 2011-11-30
I would prefer not to mess with the kernel unless that's really the  only way to fix it.  Plus, I'd have no idea which version to upgrade/downgrade to, as it seems people have this issue over a number of versions.

---

### Post by Corporation on 2011-12-01
Try installing [indicator-cpufreq]("https://launchpad.net/indicator-cpufreq") and turning CPU down to a lower speed.

Oneiric may have your CPU constantly running at top speed.

---

### Post by Mark Phelps on 2011-12-01
> **Corporation said:**
> Try installing [indicator-cpufreq]("https://launchpad.net/indicator-cpufreq") and turning CPU down to a lower speed.

Nice reference ... but on the same page, it has a bug listed that says this is NOT working in Oneiric.  Maybe this is due to the kernel bug that is preventing CPU scaling in Oneiric.

---

### Post by Basher101 on 2011-12-01
if rolling the kernel back is no option, try downgrading to 11.04 until a new kernel comes out that fixes your problem. otherwise, pop in some live CDs/USBs and see if you have the same problem with other distros and if you found one that does not have it, to use it until it gets fixed on ubuntu.

---

### Post by jinchuricki on 2011-12-05
Hi, I have the same problem with my Toshiba M505. I have tried anything but I've got nothing. Then I find the trick to solve this problem.
You can try this trick [B][Solution How to Fix Toshiba Laptop Fan Error (Overheat) on Linux (Ubuntu, etc)]("http://jinchuricki.blogspot.com/2011/11/solution-how-to-fix-toshiba-laptop-fan.html")


[/B]

---

### Post by vasa1 on 2011-12-05
> **abgemacht said:**
> ...
Of my four cores, at least one is always running at 2GHz (max freq), even when my computer is idling.  According to Psensor, I'm running at around 77C, which is just too hot.  I don't have heating issues on my Win7 partition, so I know it isn't a heatsink issue.
....

Have you tried another means of monitoring? For example, does "Hardware Sensors Indicator 0.1: Application Indicator for Unity showing hardware sensors" by [Alex Murray]("https://launchpad.net/~alexmurray/+archive/indicator-sensors") give the same results?

---

