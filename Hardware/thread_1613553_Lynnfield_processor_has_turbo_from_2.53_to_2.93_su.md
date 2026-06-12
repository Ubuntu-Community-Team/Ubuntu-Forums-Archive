---
title: "Lynnfield processor has turbo from 2.53 to 2.93 supported under Maverick ?"
date: 2010-11-04
forum: Hardware
---

### Post by swimfish on 2010-11-04
Lynnfield processor has turbo from 2.53ghz to 2.93ghz supported under Maverick ?  anyway to force an always 2.93ghz turbo mode without overclocking ?  

i'm afraid to use a frequency scaling app as the highest they show is 2.53ghz.  

my processor is actually a xeon 3440 which is a bit like an i7 intel.  see:

[HTML]http://ark.intel.com/Compare.aspx?ids=41316,42928[/HTML]

thank you all for any clarification.

---

### Post by dabl on 2010-11-04
Here's a very good guide on the topic:  [http://www.pantz.org/software/cpufreq/usingcpufreqonlinux.html](http://www.pantz.org/software/cpufreq/usingcpufreqonlinux.html)

Also, note that some Intel CPUs have the factory default speed as part of the CPU's name.  My x6800 for example always shows up as "x6800 @2.93GHz", even though it's overclocked to 3.45GHz.  So don't be mislead by the output of /proc/cpuinfo.

---

### Post by swimfish on 2010-11-04
in the intel url i posted for my xeon its supposed to have a turbo that will kick it to 2.93ghz.  the max cpu scaling text file would only have it at 2.53ghz.  add a few digits, and minus the ghz.  i'm wondering if this turbo feature can work under maverick.  

in the intel url it calls "max turbo frequency"

i'm not sure how intel gets people to achieve that.  

thank you

i think i'll give intel a ring.  :)

---

### Post by dabl on 2010-11-06
I don't know whether this helps, but it won't hurt:

```
sudo apt-get update && sudo apt-get install intel-microcode
```

---

