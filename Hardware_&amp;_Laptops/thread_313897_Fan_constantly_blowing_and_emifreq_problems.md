---
title: "Fan constantly blowing and emifreq problems"
date: 2006-12-06
forum: Hardware &amp; Laptops
---

### Post by DiZASTiX on 2006-12-06
Hey, I'm currently trying to install emifreq-applet to deal with the fan constantly blowing problem which numerous edgy users on laptops have reported.

Well, I was reading that it may have to do with my cpu frequency, thats the reason I'm trying to get emifreq to work. (My problem is very similar to the one described in [this ](http://ubuntuforums.org/showthread.php?t=307805&highlight=laptop+fan)thread). Basically, as soon as ubuntu starts loading the fan blows very hard and continues most of the time.

My problem is that when I try to install emifreq I get this error:

```
dizastix@petra:~$ sudo apt-get install emifreq-applet 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
emifreq-applet is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up emifreq-applet (0.18-1ubuntu3) ...
[b]Starting CPU frequency scaling daemon: CpuFreq support not available. Check sysfs is mounted and your CPU-specific module is loaded or built in the kernel.
invoke-rc.d: initscript emifreq-applet, action "start" failed.
dpkg: error processing emifreq-applet (--configure):
 subprocess post-installation script returned error exit status 2[/b]
Errors were encountered while processing:
 emifreq-applet
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I get the same error when trying to install powernowd (I'm guessing since powernowd depends on emifreq?) 

Here is some information on my system which my be of some help. My laptop is a Dell Inspiron 1300. /proc/cpuinfo says my CPU is a "Intel(R) Celeron(R) M processor" running at 1.4ghz. When I check the temperature of my system using "acpi -V" it reads from 68 to 77 degrees celcius, correct me if I'm wrong, but isn't this bad?

I'm dual booting windows XP pro on the same laptop and the fan runs fine in that. Also, there is no options I could find in my BIOS that effected temperature, cpu speed or the fan. However, my cpu usage is always very low, I can just be running firefox and the fan will be blowing at its highest speed. 

Any help would be great, thanks in advance...

---

### Post by ingo on 2006-12-08
The following appears to be a heavy handed hint as what to do next:

> **DiZASTiX said:**
> **Check sysfs is mounted and your CPU-specific module is loaded or built in the kernel.**


Unfortunately I am no kernel expert, but the command lsmod (list modules). If in doubt over your CPU do lshw (list hardware). Anything that is mounted should be listed in your fstab.

Sorry not to come up with a "here-you-go" answer but hope this will help to some extent.

---

### Post by eeknay on 2007-04-28
I have the same laptop with the temperature readings.
Unfortunatly, I don't know either whether this temperature is "ok", I think it weired and way to hot while almost not using the cpu.

---

