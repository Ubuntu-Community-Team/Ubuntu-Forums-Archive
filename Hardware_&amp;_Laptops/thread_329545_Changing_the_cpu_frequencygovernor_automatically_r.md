---
title: "Changing the cpu frequency/governor automatically reverted in 3 sec"
date: 2007-01-01
forum: Hardware &amp; Laptops
---

### Post by khiraly on 2007-01-01
Hi!

If I change the governor or directly the cpu speed, my changes are reverted  in 3-4 seconds. No matter if I change this through the gnome applet, or directly the cpufreq-selector command, normal user or root.

Its really strange, does anybody encountered the same symptom?

My available cpu frequencies and governors:
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
powersave performance conservative ondemand userspace

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
1600000 800000

I use the 2.6.19.1 kernel (custom).
Tried to google it, but no luck.
Any idea is really appreciated!

---

### Post by invizibility on 2008-01-17
I have the same issue and I run xfce.

---

### Post by Yellow Pasque on 2008-01-17
That's probably because the cpufreq daemon is running and changing the setting. What kind of setup are you trying to achieve?

Rules for the cpufreq daemon are located in /etc/cpufreqd.conf  Maybe you should post the file.

---

### Post by TimKraemer on 2008-05-03
Same Problem here.... I'm also running XFCE (xubuntu 8.04)

I tried to look up my config in /etc/cpufreqd.conf, but it seems that I don't have that file.

Any ideas where to find the configs for the acpi frequency governor?

---

### Post by Yellow Pasque on 2008-05-03
> **TimKraemer said:**
> Same Problem here.... I'm also running XFCE (xubuntu 8.04)

I tried to look up my config in /etc/cpufreqd.conf, but it seems that I don't have that file.

Any ideas where to find the configs for the acpi frequency governor?
Try the following command or looking in that directory. Which frequency governor module are you using? (acpi-cpufreq.ko?):
```
cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
```
```
lsmod | grep acpi
```

---

### Post by TimKraemer on 2008-05-04
> **Temüjin said:**
> Try the following command or looking in that directory. Which frequency governor module are you using? (acpi-cpufreq.ko?)


```
cat /sys/devices/system/cpu/cpu0/cpufreq/phc_controls
```
Turns out: 13:22 10:10 8:5 6:0 (I undervoltaged my cpu)


```
lsmod | grep acpi
```
Turns out:
acpi_cpufreq           12204  0 
freq_table              5536  3 cpufreq_ondemand,cpufreq_stats,acpi_cpufreq
pata_acpi               8320  0 
libata                159344  3 pata_acpi,ata_generic,ata_piix
processor              36872  3 acpi_cpufreq,thermal


I'm using the acpi-cpufreq.ko governor.

Where do I find the configs for this Governor?

---

### Post by Yellow Pasque on 2008-05-04
This site should help you :)
[http://www.go2linux.org/how-to-configure-cpufreqd](http://www.go2linux.org/how-to-configure-cpufreqd)

---

### Post by TimKraemer on 2008-05-04
> **Temüjin said:**
> This site should help you :)
[http://www.go2linux.org/how-to-configure-cpufreqd](http://www.go2linux.org/how-to-configure-cpufreqd)

Thanks, but this howto explains how I can configure my governors using the cpufreqd.conf. But I don't have this file anywhere on my system, and there is no cpufreqd* programm or manpage available. My frequency governor seems to work without this config.

Should I try to create it myself? Where exactly?

---

### Post by Yellow Pasque on 2008-05-04
```
sudo apt-get install cpufreqd cpufrequtils libcpufreq0
```

---

### Post by Zhu on 2008-05-18
Hi,

I also run Xubuntu (8.04), and the frequency governor is working fine without cpufreq. I must be lucky..

But I'd like to define the frequency governor at startup. It looks like cpufreq could do the trick.
There's a nice guide right here (topic 1.4.1):

[http://ubuntuguide.org/wiki/Ubuntu:Feisty/Hardware]("http://ubuntuguide.org/wiki/Ubuntu:Feisty/Hardware")

---

