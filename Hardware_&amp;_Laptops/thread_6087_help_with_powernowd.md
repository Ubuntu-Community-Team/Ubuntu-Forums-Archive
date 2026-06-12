---
title: "help with powernowd"
date: 2004-11-24
forum: Hardware &amp; Laptops
---

### Post by ramzez on 2004-11-24
hi, 

all of the acpi modules and powernowd is running ok, but i can't make it work. the reason is that my /sys/devices/system/cpu/cpu0 directory is empty.

if i do dsmeg | grep ACPI there no errors. 

i tried to create a folder cpufreq but failed.

please help

---

### Post by jellocat on 2004-11-28
I am having similar trouble.  my cpu is maxed out in terms of freq.  (even at 0% utilization).  I have tried to get cpufreq going, and I see a pid, but I also don't have anything at all in /sys/devices/system/cpu/cpu0

powernowd seems to want info from here.

I also have nothing in /proc/cpufreq except the column headers.

dmesg also shows no errors with acpi.

my laptop is always hot, with the fan kicking on ever 2 or 3 minutes.

help would be greatly appriciated.  let me know if there is anything I can post to help explain my situation.

btw, i LOVE this distribution.  A suse linux user for a few years now, I'm on board from here on out.  Thanks!

---

### Post by e.j. on 2004-11-29
i don't know if this will help, but I had a similar problem. Two things helped fix it: 1) Ubuntu didn't load the speedstep module for my processor, in my case speedstep-centrino, so I loaded it. 2) Cpufreqd was also not installed, although I think powernowd is supposed to do cpufreqd's job. Anyway, I made sure speedstep was loaded at boot and installed cpufreqd and that fixed me up.

---

### Post by feneks on 2004-12-20
I don't think that poernowd rely on APM or ACPI but on sysfs. 

perhaps
**man powernowd**
can help you configuring this deamon. I haven't played with it yet.

---

### Post by dave_euser on 2004-12-28
First, powernowd does require a 2.6 series kernel with sysfs (creates a simpler clock speed daemon at the cost of newer requirements, but not too much of a problem in ubuntu).

Second, I found that on my laptop, the required modules were not all installed. Mine has a desktop P4, so I added a line with "p4-clockmod" to /etc/modules (modules to load a boot time).

If you go to /lib/modules/[your kernel version here]/kernel/arch/i386/kernel/cpu/cpufreq you will see a list of cpufreq modules that can be installed:
p4-clockmod, powernow-k6, powernow-k7, powernow-k8, speedstep-centrino, speedstep-ich, speedstep-lib, speedstep-smi

Pick the appropriate module, and use modprobe to load it....restart powernowd, and make sure that /etc/modules has the module to force it to load at boot...

---

### Post by feneks on 2004-12-29
I removed powernowd because my laptop uses a simple PIII which has no support for scaling.

---

### Post by dave_euser on 2004-12-30
[QUOTE=feneks]I removed powernowd because my laptop uses a simple PIII which has no support for scaling.[/QUOTE]
 nice, easy solution :-)

---

### Post by roongpatoong on 2005-01-02
hi

I just did this to get powernow running on my averatec 3250H1

sudo echo "powernow-k7" >> /etc/modules

*update*

oops - forgot that I also did this to get it working ...

sudo modprobe powernow-k7
sudo /etc/init.d/powernowd start


hope it might help you out

---

### Post by adamvert on 2005-01-19
[QUOTE=e.j.]i don't know if this will help, but I had a similar problem. Two things helped fix it: 1) Ubuntu didn't load the speedstep module for my processor, in my case speedstep-centrino, so I loaded it. 2) Cpufreqd was also not installed, although I think powernowd is supposed to do cpufreqd's job. Anyway, I made sure speedstep was loaded at boot and installed cpufreqd and that fixed me up.[/QUOTE]

brillliant, thankyou!

modprobe speedstep-centrino was the step that i was missing out.  now powernowd works just fine.

ta
adam

---

