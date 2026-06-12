---
title: "cpu frequency scaling"
date: 2008-07-02
forum: Hardware
---

### Post by acrobat on 2008-07-02
hi,
since i migrated to hardy heron  my processor is not scalling anymore..
i've installed cpufreq but it still not scalling..
my cpufreq-info output is this:
cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 996 MHz - 1.99 GHz
  available frequency steps: 1.99 GHz, 1.66 GHz, 1.33 GHz, 996 MHz
  available cpufreq governors: userspace, conservative, powersave, ondemand, performance
  current policy: frequency should be within 1.99 GHz and 1.99 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.99 GHz.
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 1
  hardware limits: 996 MHz - 1.99 GHz
  available frequency steps: 1.99 GHz, 1.66 GHz, 1.33 GHz, 996 MHz
  available cpufreq governors: userspace, conservative, powersave, ondemand, performance
  current policy: frequency should be within 1.99 GHz and 1.99 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.99 GHz.


does anyone have an idea of what this could be? i've already tryed a lot of solutions found on google and ubuntu foruns.. and nothing :|

thanks in advance
paulo f

---

### Post by starcannon on 2008-07-02
I posted a little guide for this on a Dell 5100 laptop, you'll need to insmod the module appropriate to your cpu, but thats the only change in the guide you should need to make.

[http://ubuntuforums.org/showpost.php?p=5289658&postcount=12](http://ubuntuforums.org/showpost.php?p=5289658&postcount=12)

GL

---

### Post by acrobat on 2008-07-02
i've already done that before, and it still does not work, i have the menu to select the diferent governors and speeds but when i select it nothing happens

---

### Post by starcannon on 2008-07-02
Please post the output of:
```
 sudo lshw | grep CPU
```

and the output of:

```
lsmod | grep cpu
```

I'll see if I can help, I'm no guru, but I've set up 5 different laptops with cpu frequency scaling successfully so far.

---

### Post by acrobat on 2008-07-02
sudo lshw | grep CPU
          description: CPU
          product: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz
             description: Logical CPU
             description: Logical CPU
             description: Logical CPU
             description: Logical CPU

 lsmod | grep cpu
acpi_cpufreq           10796  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
cpufreq_powersave       2688  0 
freq_table              5536  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
processor              36872  4 acpi_cpufreq,thermal

---

### Post by starcannon on 2008-07-02
> acpi_cpufreq 10796 0
cpufreq_userspace 5284 0
cpufreq_ondemand 9740 0
cpufreq_conservative 8712 0
cpufreq_stats 7104 0
cpufreq_powersave 2688 0 
freq_table 5536 3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
processor 36872 4 acpi_cpufreq,thermal


The problem is showing itself here:

> 
acpi_cpufreq 10796 0


there should be a couple things using it.
**freq_table** and **processor** are supposed to be using it, and indeed they say they are, but **acpi_cpufreq** says 0 and that no-one is using it.

If you loaded the p4_clockmod you don't need to, your cpu is much newer than that, I run the Intel T7250 and had to add no modules at all, just the ubuntugeek guide and I was up and running.

I'm at a loss sorry, my best advice is to rerun the guide again, being very careful not to skip steps. And possibly search google to see if you do need a module for the T7200.
[http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html](http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html)
 
Sorry I'm not of more help, but perhaps someone with more experience can help.

---

### Post by acrobat on 2008-07-02
i've tryed it over and over again... always the same result.. also if i change the governor to conservative it's changed a few minutes after to performance..
i'm really clueless!
and my pc is really hot :|

---

### Post by starcannon on 2008-07-02
Mine did that under gutsy... now I'm trying to remember how I fixed that. I now have mine set to On Demand and like that much better. Hang on I fixed the same exact problem your describing on this laptop running nearly the same cpu, if I dug it up once I can dig it up again... oh did you try a reboot yet?

---

### Post by starcannon on 2008-07-02
Do you have speed step enabled in bios?

---

### Post by starcannon on 2008-07-02
Are you running 64bit or 32bit Ubuntu?

---

### Post by starcannon on 2008-07-02
This thread is definitely worth reading, at the moment I'm at a loss as to why your cpu frequency scaling monitor isn't working with that particular cpu. If your running Ubuntu 8.04 it should just work :(

This thread is covering this topic in depth though, so might be worth a read:

[http://ubuntuforums.org/showthread.php?t=847424](http://ubuntuforums.org/showthread.php?t=847424)

---

### Post by acrobat on 2008-07-02
i'm running gutsy 32 bits and i have rebooted most times today then in the past week :) really clueless.. i will read that thread, Thanks a lot for all the help

---

### Post by starcannon on 2008-07-02
Heres a forum thats dealing with your problem under gutsy, it may be worth a look. I wish I could remember what I had to do when I had that issue, it didn't follow me into Hardy 
[http://foldingforum.org/viewtopic.php?f=12&t=2342&st=0&sk=t&sd=a](http://foldingforum.org/viewtopic.php?f=12&t=2342&st=0&sk=t&sd=a)

---

### Post by acrobat on 2008-07-02
i've been looking i think i've tryed everithing thats there, but i will take a better look.. the strange think is that frequency applet works and has all the options about the governors BUT the frequency is allwasy 1.99 GHz :|

---

### Post by acrobat on 2008-07-03
up

---

### Post by Steveway on 2008-07-03
Did you try installing powernowd?
If you install it it should remove cpufreqd or whatever you allready have for that purpose installed.
It worked for me after I changed to it.

---

### Post by AlesUbu123 on 2008-07-03
> Did you try installing powernowd?
Yes Sir! That did it. Thanks a lot! I'll post this to some other threads working on this problem!

I haven't a clue why Ubuntu developers included cpufreqd in the default installation?

---

### Post by acrobat on 2008-07-03
many thanks for reminding me this!!! the strange thing is that i had it installed before and it didn't worked :| now it's working without any issue! many nay thanks

---

