---
title: "CPU frequency (centrino), Fan speed control, no control"
date: 2007-01-23
forum: Hardware &amp; Laptops
---

### Post by longman on 2007-01-23
Hello everybody!
I was rying to solve my problem for a while, googling, searching on ubuntu forums and various others. No success so far using the information from threads posted by others, so i have to start my own one.

Ok, here we go: i have Acer Travelmate 4150 laptop with Ubuntu dapper installed, upgraded to Edgy.

The problem is that i can't change the CPU load anyhow. For example i have the panel applet loaded. Which shows that the processor frequency can't be changed (Frequency scaling unsupported). It shows that it's all the time 100% loaded. As the result the fan is working all the time too. Which is really, really annoying, and if nothing else it reduces the battery life time. 

As many other people report here, it works well out of the box in Windows, but not in Linux, which is a real pity.

So... i have been trying to use cpufreq. No success coz it simply seems to be not working. Is there a good guide how to make it working, from the beginning? There are many people saying that one should try to look for frequencies available, for example minimal ones, through: cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_min_freq

But the only folder in '/sys/devices/system/cpu' is cpu0 where the only file is crash_notes... i am quite lost, and really would appreciate some guildness and help. 

So far i was rather good in convincing friends to switch to Linux, but not in tweaking my system myself, simply had no time for that. But i really believe that the problem is solvable, just lack of experience is what is preventing me to configure my laptop well.

Greetings, count for some constructive respond. Would love to provide the data about my computer that one might ask, just please, give me understandable questions.

Thanks in advance, 
Misha

---

### Post by RandomJoe on 2007-01-23
Have you checked to see if any of the cpufreq modules are loading?  Since the relevant directories in /sys aren't present I would say not.  For a speedstep system, it should be something along the lines of the following:

cpufreq_conservative
cpufreq_ondemand
cpufreq_powersave
freq_table
cpufreq_stats
cpufreq_userspace
speedstep_centrino

The first three and cpufreq_userspace are the "governors" - you only need one, really.  The rest are what actually support the chip's scaling functions.  By default Ubuntu runs powernowd which interfaces with the _userspace governor.

If they aren't loaded, you can try loading them manually to see what happens - either error messages that may help find the issue, or just load and work, then you would need to figure out why they aren't loading automatically.  (Or just throw the lot into /etc/modules if you don't want to mess with it...!)

Some of them depend on others, so doing something like "sudo modprobe speedstep_centrino" will load the other modules it requires first.

---

### Post by longman on 2007-01-24
Ok, thank you! Here i came to something:

$ sudo modprobe speedstep_centrino
FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.17-10-386/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-centrino.ko): No such device

So here somewhere must be the issue. Ok, but this seems to be a misconfiguration, laptop does have centrino.
My first guess would to recompile kernel and include that speedstep-centrino support. But i actually have tried it recently and ran into  "Kernel panic - not syncing VFS: Unable to mount root fs on unknown-block(0,0)". So before struggling with Kernel (what is definately in my todo list now)  i would like to know what are the possible ways to enable centrino support in general. Will keep on googling but any ideas?

---

### Post by xbytes on 2007-02-09
I have the exact same problem, CPU frequency scaling unsupported, and the cpufreq dir doesn't seem to exist... I know the CPU I have late stepping C0 Dothan isn't compatible with my IBM T40 BIOS, I use Notebook Hardware Control in windows to get around this, it overrides the BIOS tables, Linux-PHC Processor Hardware Control? is a similar app for linux but I can't get that to work either?!:mad:

---

### Post by xbytes on 2007-02-09
I have the exact same problem, CPU frequency scaling unsupported, and the cpufreq dir doesn't seem to exist... I know the CPU I have late stepping C0 Dothan isn't compatible with my IBM T40 BIOS, I use Notebook Hardware Control in windows to get around this, it overrides the BIOS tables, Linux-PHC Processor Hardware Control? is a similar app for linux but I can't get that to work either?!:mad: 

-xbytes

---

### Post by indiver on 2007-02-10
This has been troubling me as well.

But then I found the following links:

[http://doc.gwos.org/index.php/CPUFreq](http://doc.gwos.org/index.php/CPUFreq)
[http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/](http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/)

They worked very well for me.

---

### Post by Mark C on 2007-02-21
Enabling CoolNQuiet in the BIOS and following this guide made things possible. :)

[http://doc.gwos.org/index.php/CPUFreq](http://doc.gwos.org/index.php/CPUFreq)

or if gwos server down:

[http://72.14.235.104/search?q=cache:d4b0IbTVtpUJ:doc.gwos.org/index.php/CPUFreq+http://doc.gwos.org/index.php/CPUFreq&hl=en&client=firefox-a&strip=1](http://72.14.235.104/search?q=cache:d4b0IbTVtpUJ:doc.gwos.org/index.php/CPUFreq+http://doc.gwos.org/index.php/CPUFreq&hl=en&client=firefox-a&strip=1)

Happy Hacking!

Edit: We first cuppers should stick together! XD

---

