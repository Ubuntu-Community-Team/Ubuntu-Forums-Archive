---
title: "Laptop Intel Core 2 Duo - lowering vcore"
date: 2014-01-17
forum: Hardware
---

### Post by Akova on 2014-01-17
Hello everyone. I'm running Ubuntu 12.04 on my laptop and I'm trying hard to lower the vcore. I've been googling this and installing whatever I find online for a week now. sudo app-get install xyz. Praying it will magically work out in the end. I've found out that I have a speedstep-centrio and not a acpi-cpufreq.... yeah. 

I need to unload the current driver typing this
sudo modprobe -r acpi-cpufreq

And I get this back
FATAL: Module cpufreq_stats is builtin
FATAL: Error running remove command for acpi_cpufreq


I want to use acpi-cpifreq and blacklist the speedstep-centrio, then I can follow this guide ([http://ubuntuforums.org/showthread.php?t=786402](http://ubuntuforums.org/showthread.php?t=786402)) and maybe it will work out. 

Please guys, I L-O-V-E Ubuntu but the cpu is reaching 90C. Don't let me go back to WinXP for the RM-Clock undervolt

---

### Post by tgalati4 on 2014-01-17
You might have other problems.  Undervolting will lower temperatures, but only a few degrees.  Too much undervolt and your system will just crash randomly.  

To undervolt you need a custom kernel that has the correct hooks.  That means compiling a custom kernel and running *phctool*.  I did it for my Jaunty machine running a centrino and it dropped the temperatures 5 to 7C.  Battery life was improved about 20%.  I'm not sure what is required for 12.04.  Some of those hooks are in the newer kernels so you don't need to recompile.

Spend some time here:  [www.linux-phc.org/forum/viewforum.php?f=3](www.linux-phc.org/forum/viewforum.php?f=3)

Let us know what works for you.

---

