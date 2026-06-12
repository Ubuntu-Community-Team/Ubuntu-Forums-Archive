---
title: "Potentially fan-related sudden performance kill"
date: 2008-06-19
forum: Hardware
---

### Post by keillor on 2008-06-19
Hi all,
I have a Toshiba Portege m200 which was, up until very recently, working VERY well with Ubuntu 8.04.  

Seemingly for no reason at all, however, the performance of my machine simply died.  I can't watch youtube videos without massive lag, I can't do anything in addition to listening to music or the music skips, etc.  My 1.8 GHz processor is constantly maxed out, as if it were a 233 MHz.  

Correlated (very strongly in my mind, but I could be wrong) with this is the sudden disappearance of the sound of my very noisy and frequently 'on' fan.  

Here's where I'm at:

cat /proc/acpi/fan/FAN/state 
status:                  off

cat /proc/acpi/toshiba/fan 
running:                 1
force_on:                0

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq 
1800000

Yet my cpu is almost ALWAYS pegged at 100% unless my computer is completely idle.  I thought this might be a software problem (i.e. I botched something and made an unending do-loop somewhere that ate up cpu time) so I reformatted (pretty fresh install so no worries) to no avail.

My hypothesis: my fan broke/burned out and now the bios is throttling the cpu to stop the computer from overheating.  But why is my cpu still usually at max (1.8 GHz)?  

Can someone please suggest the next step?  I'm working in a field camp FAR AWAY from any techs so I unfortunately can't get the fan looked at for another 4 weeks.  Having a barely functional computer up here is close to injuring my sanity so any help would be greatly appreciated.  

Thanks so much in advance,
Cam

---

