---
title: "cpu frequency"
date: 2011-08-07
forum: Hardware
---

### Post by kr651129 on 2011-08-07
I'm on a dell 1545 laptop -- Ubuntu 11.04 x64

I installed indicator-cpufreq so I can adjust my cpu speed when rendering video.  I was wondering if there is a command that will display the current cpu speed.  The indicator-cpufreq allows me to select Conservative, OnDemand, Power save, and performance.  It also allows me to select a specific speed 1.20GHz, 1.60GHz, or 2.10GHz but it does not display the current speed when using one of the profiles.  Any suggestions?

Thanks!

---

### Post by Toz on 2011-08-07
From the command line, this will show you the current frequencies of all cpus:
```
cat /sys/devices/system/cpu/cpu*/cpufreq/cpuinfo_cur_freq
```

---

### Post by kr651129 on 2011-08-07
Nice, thank you!  How would I make an alias for this command so I could type something like "checkfreq" ?

---

### Post by Toz on 2011-08-07
Edit your ~/.bashrc file:
```
gedit ~/.bashrc
```
.....add to the bottom of the file:
```
alias checkfreq='sudo cat /sys/devices/system/cpu/cpu*/cpufreq/cpuinfo_cur_freq'
```
.....save the file and source it:
```
source ~/.bashrc
```
.....then run **checkfreq** (and type in password if/when prompted).

---

