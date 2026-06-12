---
title: "cpufreq not installed? speedstep not working, help a partial n00b"
date: 2007-02-02
forum: Hardware &amp; Laptops
---

### Post by xbytes on 2007-02-02
Hi and hello to you all, finally trying to get setup in ubuntu I'm almost done apart from a few small issues, and I know that speedstep issues have been talked about before but I am unable to locate any other thread with my issues regarding speedstep and cpufreq!

in short:

1.I don't seem to have CPUfreq installed
2.My BIOS doesn't support speedstep on a C0 stepping CPU (I can get speedstep working in windows xp with NHC)
3.Do any of the utils for linux actually override the BIOS CPU tables?

I don't seem to have cpufreq installed by default on my system just re-installed the whole OS and no change, I'm running 2.6.17-10-generic SMP i686... here is a readout from powernowd for example:

$ sudo powernowd
powernowd: PowerNow Daemon v0.97, (c) 2003-2006 John Clemens
powernowd: Found 1 scalable unit:  -- 1 'CPU' per scalable unit
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq: No such file or directory

PowerNowd encountered and error and could not start.

Now on my system I'm running a Dothan 735A OEM cpu and I know that the CPU table in BIOS doesn't support this C0 stepping CPU, in windows I was using Notebook Hardware Control to override the BIOS and control the CPU, so this leads me to another question do you think that the reason cpufreq isn't installed is because my BIOS doesn't support my CPU? 

and last question does cpufreq. wmthrottle or linux-phc actually override BIOS tables?!

also if I run:

$ cat /proc/cpuinfo

model name      : Intel(R) Pentium(R) M processor 1.70GHz
stepping        : 8
cpu MHz         : 599.586

glxgears runs at 700fps and everything else is good

yes I am a n00b but If I can get Speedsteps to work I may never go back to windows ):P

---

### Post by RandomJoe on 2007-02-03
Have you checked to see if cpufreq is loaded at all?  The kernel you mention is Edgy, and Edgy by default doesn't use powernowd - it uses the 'ondemand' governor which doesn't require an external daemon.

Looking at your CPU listing, it would appear scaling is in fact running already - it shows your CPU as 1.7GHz but frequency as 600MHz.  Check that again with GLXGears running, and I believe it will change to 1.7GHz.  (So I've read - I'm running Dapper, and my /proc/cpuinfo always shows the max speed even when scaled down.)  Or, add the CPU Freq Scaling Monitor applet to the toolbar to monitor it in realtime.

You can check to see if any of the modules have loaded by running 'lsmod' and see if you can find any with 'cpufreq' in the name.  There should be several.

Or you can check for the /sys/devices/system/cpu/cpu0/cpufreq directory.  It gets created whenever the modules are properly loaded.

If they aren't loaded, try 'sudo modprobe speedstep_centrino' and see what happens.  It may give an error message that indicates the trouble.

---

