---
title: "Can't get CPU governing to work on a Celeron M"
date: 2008-09-03
forum: Hardware
---

### Post by TehDooMCat on 2008-09-03
I've got a laptop with a Celeron M 550, which from doing a little research does allow for kernel-mode CPU frequency governing in linux, and I've seen the threads on these forums that state to modprobe 'p4-clockmod' and/or 'acpi-cpufreq'.

However, modprobing either driver tells me that there's 'No such device'.

There's no setting in the BIOS to enable/disable the governing, but the preinstalled copy of Vista in it has no problems with scaling back the CPU when I set it to 'power save' mode.

Could it be that the kernel's detecting my CPU wrong? It tells me it's an 'Intel Celeron 550', but not a Celeron 'M'... only from looking at Wikipedia did I work out it was.

It seems that others are having success in getting things like powernowd and cpufreq working with this CPU, but not me :(

A little help seeing if I can get this working would be much appreciated. However much I like the responsiveness of the laptop under Linux as it's always running at 2GHz, maximum speed, I'd like to save a bit of battery when I'm running it unplugged.

Which leads me on to my other question: can I disable certain devices when the laptop's unplugged, through shell scripts that automatically run or something? For instance: I don't need my LAN ports working, so that network can go down, and being able to tweak it to save the most power (would lowering the wifi's txpower do much? and I could disable compiz when unplugged too) would be very helpful.

---

### Post by linarator on 2008-09-03
Hello all,

This is also relevant to me. I am running Ubuntu 8.04 on a HP Compaq Presario C700. My CPU is a Intel Celeron M 530 running at 1.73GHz... all the time. Of course this is horrible for my battery life. All cpu frequency options are disabled and/or dysfunctional.

If this helps at all here is the output for a recent update which I believe is relevant:
```

Unpacking replacement libtiff4 ...
Setting up emifreq-applet (0.18-3ubuntu2) ...
Starting CPU frequency scaling daemon: CpuFreq support not available. Check sysfs is mounted and your CPU-specific module is loaded or build in the kernel.
invoke-rc.d: initscript emifreq-applet, action "start" failed.
dpkg: error processing emifreq-applet (--configure):
 subprocess post-installation script returned error exit status 2

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 emifreq-applet
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
Setting up emifreq-applet (0.18-3ubuntu2) ...
Starting CPU frequency scaling daemon: CpuFreq support not available. Check sysfs is mounted and your CPU-specific module is loaded or build in the kernel.
invoke-rc.d: initscript emifreq-applet, action "start" failed.
dpkg: error processing emifreq-applet (--configure):
 subprocess post-installation script returned error exit status 2
```

Any ideas how to fix the problem? I think this is fundamental to the entire issue?

Any help is greatly appreciated! Thanks so much in advance!

Regards,
-linarator

---

### Post by Flying caveman on 2008-09-03
this may help?

[http://technowizah.com/2007/01/debian-how-to-cpu-frequency-management.html](http://technowizah.com/2007/01/debian-how-to-cpu-frequency-management.html)

---

### Post by linarator on 2008-09-03
> **Flying caveman said:**
> this may help?

[http://technowizah.com/2007/01/debian-how-to-cpu-frequency-management.html](http://technowizah.com/2007/01/debian-how-to-cpu-frequency-management.html)

Unfortunately no. The problem seems to be with emifreq-applet... anything I try to install revolving around the CPU frequency gives me errors involving emifreq-applet... hm. Any ideas?

Output from installing some of the software from your link:

```
Unpacking sysfsutils (from .../sysfsutils_2.1.0-4_i386.deb) ...
Setting up emifreq-applet (0.18-3ubuntu2) ...
Starting CPU frequency scaling daemon: CpuFreq support not available. Check sysfs is mounted and your CPU-specific module is loaded or built in the kernel.
invoke-rc.d: initscript emifreq-applet, action "start" failed.
dpkg: error processing emifreq-applet (--configure):
 subprocess post-installation script returned error exit status 2
Setting up sysfsutils (2.1.0-4) ...
 * Setting sysfs variables...                                            [ OK ] 

Errors were encountered while processing:
 emifreq-applet
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

And then when trying to run the next step:

```
sudo modprobe speedstep_centrino
FATAL: Error inserting speedstep_centrino (/lib/modules/2.6.24-19-generic/kernel/arch/x86/kernel/cpu/cpufreq/speedstep-centrino.ko): No such device

```

?!?!? Any ideas?

Thanks for the help so far!

---

### Post by linarator on 2008-09-03
Also this might be relevent or important:

if I run: ```
cpufreq-info
```

I get:

```
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
```

---

### Post by linarator on 2008-09-03
Duplicate post, whoops!

---

### Post by linarator on 2008-09-05
Anyone have any ideas?

---

